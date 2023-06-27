# NTLM \ NEW TECHONOLOGIES LAN MANAGER

```diff
-you didn't answer question 4
```

Windows **New Techologies Lan Manager**, is a suite of security protocols used to authenticate a user's identity. NTLM replaced the old Lan Manager Authentication suite, due to it's weakness.<br>
At it's core NTLM is an SSO (Single-sign on) authentication protocol that doen't send the password on the wire. There are two versions to the protocol, V1 and V2 where V2 is the "more secure" one.

```diff
- if it is the new technologies what is the old one?
- name the suite of security protocols
+ LM (Lan Manager) was an authentication protocol belonging to the LANMAN (Lan Manager) OS.
+ It was severly flawed so it was built upon with NTLM Authentication in Windows NT 3.1.
```

### How Does It Work?

![The Process of NTLM Authentication](Pictures/NTLM/NTLM_Process.png)
<p style="font-size:11px">NTLMv1 process.</p>

There is little to no difference in the process between V1 and V2 so Ill explain it and elaborate on the slight difference later.

The process is as goes:

> When a **client** wants to authenticate themselves to a server, it will send an **authentication request**.

> Then The **server** will generate a random *nonce*. A 16 bit random number which is called a **challange**, to send to the **client**.
```diff
- Send it back to the server?
+ Client, it was a typo.
```
> The **Client** will *encrypt* that challange with the **LM hash** of the user's password. an LM Hash is a 32 hexadecimal digit digest of the password (as seen below).

![LM HASH](https://www.netspi.com/wp-content/uploads/2014/10/HashExample.png)
<p style="font-size:11px">An example of an NTLM Hash.</p>

> After recieving the Client's answer the **Server** will check the answer by decrypting the challange with the hash of the password that it has. The password may be stored inside the server's SAM storage or it will forward that encrypted channage to the Domain Controller for decrypting.
>
> In the first case, the **server** will validate the user by encrypting the nonce with the saved password and comparing the **client**'s response.<br>
> In the second case, the DC will validate the user. <br>
> In the case of local ntlm authentication: you may think of the Winlogon.exe as the client, lsass as the server and SAM as the database.
```diff
- It validates the user by decrypting the password?
+ No, it validates the user by encrypting the nonce using the password hash it has stored locally or on the DC, then comparing the two results.
- can a user authenticate locally?
+ Yes, a user can authenticate locally using LSA (Local Security Authority) as the server and SAM (Security Account Manager) as the hash database.
```

In terms of the process, NTLMv2 doesn't about the same. However, the content of the messages is different.<br>
- Both client and server generate challenges which are used in the process.<br>
- A variable length hash of client information like domain name and timestamp is used to further authenticate the user.<br>
- The hashes themselves are stronger.
- The challange isn't encrypted using the password but rather hashes together with the password.
```diff
- Variable length hashes? explain
+ The hash would be made up of variables such as the domain name, flags that were used during the conversation and a timestamp.
-give another difference
+ In NTLMv2 the challange isn't encrypted using the password but rather hashed together with the password.

-that is incorrect or not phrased well - try to explain again more clearly
```

### Why Is It So God Damn WEAK!

There are multiple reasons for that, and we will go over them one by one.

> **Weak Cryptography**
>
> The hashes and cryptographic practices used in the NTLM Protocol are outdated and weak. It is easy enough to be able to crack a cleartext 8 character password in less then a day with standard hardware.
>
> 1. The hashing algorithm is based on MD4, which is weak.
> 2. The hash is saved as is with no salt in the machine's memory, making it susceptible to memory attacks (pth).

> **Relay Attacks**
>
> The "3 way handshake" that the protocol operates by is suceptible to MitM relay attacks. An attack where an attacker places themselves in a position inbetween the client and the server and simply relays the messages back and forth. In that position, the client believes the attacker is the server and the server believes the attacker is an innocent client. The attacker is then authenticated to the server instead of the client and has acces to all the rsources the client would have.

![Relay Attack Process](Pictures/NTLM/NTLM_Relay_Process.png)
<p style="font-size:11px">NTLM Relay Attack.</p>

> **No Mutual Authentication**
>
> This flaw is based on the fact that the client doesn't authenticate the server's identity. Meaning an attacker can identify as a server in a MitM attack and gain the credentials of the client.<br>
> It does that by recieving the client hash, and trying to bruteforce hashes until one matches. meaning it will have the string that was used to create the hash, which is the password. Popular tools to do that are JohnTheRipper and Hashcat.

```diff
- How can he gain the credentials of the client?
+ It does that by recieving the client's challange response, using information he already knows like domain name and timestamp the attacker can generate hashes until one matches.
+ At which point he will have accquired the cleartext password.
```
