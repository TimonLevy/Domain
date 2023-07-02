# KERBEROASTING & SILVER TICKETS

## Kerberoasting

A kerberoasting attack is an attack where an attacker cracks the credentials used to encrypt a TGS offline after recieving that ticket using an SPN.

> SPN - ServicePrincipalName is a unique identifier of a service instance.

SPNs are the service names that are used to request TGSs, Kerberos associates SPNs with domain accounts. Meaning that these services have privileges, belong to groups and have permissions. The KDC will give any domain user the TGS to any service he will ask without checking if they are authorized to log on to the service. The TGS is encrypted with the service account's ntlm password hash and so the attacker can keepthe TGS and crack it offline.

```diff
- Fact check yourself. how will you kerberoast a user account? what does SPN stand for?
+ Fact checked.
+ SPN is a name that is used when asking for a TGS.
+ It will have a constat string prefixing it describing the type of service, then it's user name and domain name.
+ Optionally, the SPN will have a port number at the end.
```

### How Does The Attack Work?

1. An attacker with an authenticate domain user gets the SPN of some service on the network, say an sql server and requests to connect to it.
2. As a part of the authentication process they will get a TGS (Ticket Granting Service) that is encrypted with that service account's password hash.
3. The attacker keeps the ticket.
4. The attacker will attempt to crack that encryption and solve for the password using hash-cracking tools like `johntheripper` or `hashcat`.

### Mitigating The Attack

Honestly, it's pretty impossible to stop the attack itself. Getting the TGS is really easy and there is nothing we can do about offline cracking. However we can:
* **Detect** when the actor logs on to that account and stop them.
* **Employ** a **STRONG PASSWORD POLICY** to impede any cracking attempts.
* **Use** Multi-factor authentication, making users enter more than one authentication methods.
* **Install** systems in the domain that pick up on suspicious user activity, like that of a compromised account.
* **Make sure** that service accounts do not have any uneccesary & strong privileges.

```diff
- What is a common configuration mistake that can be good for an attacker doing kerberoasting?
+ I would like sqluser with a little domain admin on the side :)
```
## SILVER TICKETS

Silver Tickets are forged TGS tickets that are encrypted with the service account hash, usually that will be a hash cracked using kerberoasting.<br>
Using a silver ticket allows an attacker unlimited access to that service and it's resources.

```diff
- Not inverse. these attacks will usually come toghther (kerberoast followed by a silver ticket)
+ Noted.
```

### How Does The Attack Work?

1. Get the password of the service account, usually by Kerberoasting it's TGS.
2. Forge a ticket using some exploitation tool like `Rubeus`, `Impacket`, `Mimikatz` or `Kekeo`.

```diff
-what attack could you do to get it? (hint: its a few lines up)
+ Kerberoasting? I don't know... ;)
```

### Mitigating the Attack

While there is no way to stop the forgery of the ticket itself, as a defender you can imit the effect that this ticket has. And also limit the ability to password dump.

* **Install** AVs to detect password dumping tools
* **Enable** PAC Validation on kerberos in the domain, that would check if the DC was the one to issue the ticket.
* **Enforce** A **STRONG PASSWORD POLICY**!!!!!!!!!!!!!!!!
* **Detect** discreptencies using logs
  - If a user machine authenticated using a service's TGS. It means that there is foul play.
  - If a machine requests a lot of Service tickets.
* **Consider Implementing** honeypot service accounts in the domain, ones that will never be accessed by normal users but could attract attackers and will raise siem rules if accessed.

```diff
- How can you detect the attack?
+ Detect discreptencies using logs, such as:
+ - User machine authenticated using a service's TGS.
+ - A machine requests a lot of Service tickets.
+ Honeypot service accounts.

- what can indicate a ticket has been manipulated?
```
