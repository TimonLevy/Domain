# NTLM Relay

## What is NTLM Relay?
The NTLM protocol is a response challange protocol used for authentication inside the LAN. An attack that is possible to produce on that protocol is called a `relay attack`.

In it, an actor poses as a man-in-the-middle between a user machine and a service the user wants to access. Then, that actor can relay the authentication messages between the two machines, since they cannot authenticate the identity of the attacker as the actual machine the attacker acts as the other machine for them both. Meaning that the Client thinks the attacker is the server and the server thinks the attacker is the client.

Finally, by forwarding the messages between the two endpoint the attaker can get access to the server resources **that the client has access to** without knowing the password of the client. The attacker authenticated to the server as the client **instead of the client**.

![](/Pictures/NTLM/NTLM_Relay_Process.png)

## NTLM Relay using LLMNR and NBTNS Spoofing
Kali has a tool caled Responder, using it an actor can respond to typo'd share-names that de-escalate to the llmnr and nbns protocols. Then relay the ntlm authentication to the real server.

Imagine a Scenario:
```
Server [Server.DomainSubName.Domain]
 __     _        __     _        __     _
[Ll]   |=|      [Ll]   |=|      [Ll]   |=|
====`o '-'      ====`o '-'      ====`o '-'
 |                | User          | Attacker
 +----------------+---------------+
```

User wants to access the server using it's FQDN, they type `srver.DomainSubName.Domain` by accident. The user's machine caanot find the fqdn because of the type so it broadcasts an llmnr request for that fqdn. The Attacker uses Kali's Responder tool and returns a response.
The attacker then poses as the real server and simply relays the authentication to some target that it want to try and authenticate to as the user.

![](/Pictures/NTLM_Relay/01_Responder.png)

Here we can see the responder tool, notice that the SMB and HTTP server are off as we will use those for the ntlmrelayx tool to relay the packets. The Responder is responding to a share name the user wrote wrong.

![](/Pictures/NTLM_Relay/03_Run_SMB_Typo.png)

And here we can see the ntlmrelayx script as it relays the authentication to the target server which is another machine on the local network. And runs the `whoami /all` command.
![](/Pictures/NTLM_Relay/02_ntlmrelayx.png)

Here are sniffings of those actions.

**Responder**
![](/Pictures/NTLM_Relay/99_Wireshark_NBNS_LLMNR_Poisoning.PNG)

192.168.100.4 - Attacker                                                                                                        <br>
192.168.100.1 - Victim

**NTLMRELAYX**
![](/Pictures/NTLM_Relay/99_Kali_To_Target_Relay.PNG)



## Why The Attack Isn't As Prevelant

NTLM relay attacks were a popular technique, which was also their downfall. Mitigations to protect against the NTLM relay attacks were published, spread and applied in many domains. And I will g over a few of them:

1. **The Rise of Kerberos**
> Kerberos was created in order to replace the ntlm protocol overall, made NTLM obsolete in domains with new machines and the NTLM relay attack impossible.

2. **Extended Protection for Authentication**
> Is a method in which the authnetication process is bound to the TLS/SSL session it is transfered in, that means that the authentication key will only be valid for the SSL tunnel that is passed through. Passing it through any other ssl tunnel will make it invalid.
>
> ```
> User             Attacker        Server
>  __     _        __     _        __     _
> [Ll]   |=|      [Ll]   |=|      [Ll]   |=|
> ====`o '-'      ====`o '-'      ====`o '-'
>  +---------------+---------------+
>    SSL TUNNEL 1    SSL TUNNEL 2
> ```
>
> In this scenario, with EPA, the authentication token of the user is bound the first tunnel between the client and attacker. So once the Attacker relays it on the second tunnel between them and the server, (Assuming the server is Channel Binding Token aware) The server wil reject that authentication.

3. **Server Message Blocking Signatures**
> SMB signing became more preveant as well. SMB signing is the process of adding a signature of the entire message in the SMB Header, which is the message's contents encrypted with the AES elgorithm and a session key derived from the NTLM Session key of that session (it is an option that can be enabled). That basically authenticates the sender for that session, meaning an attacker cannot relay those messages as they are not the original sender of those messages.
>
> Note: SMB does not support EPA, idealy you'd want to use Kerberos anyways.