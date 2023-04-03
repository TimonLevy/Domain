# KERBEROASTING & SILVER TICKETS

## Kerberoasting

A kerberoasting attack is an attack where an attacker cracks the credentials used to encrypt a TGS offline after recieving that ticket using an SPN.

> SPN - ServicePrincipalName is a unique identifier of a service instance.

Kerberos associates SPNs with actual service accounts, meaning that these services have actual privileges, groups and permissions. But SPNs aren't limited to service accounts, user accounts can have SPNs too. Meaning, actors can kerberoast user accounts as well.
```diff
-fact check yourself. how will you kerberoast a user account? what does SPN stand for?
```

### How Does The Attack Work?

> * An actor with an authenticate domain user gets the SPN of some service on the network, say an sql server and requests to connect to it. 
> * As a part of the authentication process they will get a TGS (Ticket Granting Service) that is encrypted with that service account's password hash.
> * The Actor keeps that ticket and goes offline.
> * The actor will attempt to crack that encryption and solve for the password using hash-cracing tools like `johntheripper` or `hashcat`.

### Mitigating The Attack

Honestly, it's pretty impossible to stop the attack itself. Getting the TGS is really easy and there is nothing we can do about offline cracking. However we can:
* **Detect** when the actor logs on to that account and stop them.
* **Employ** a **STRONG PASSWORD POLICY** to impede any cracking attempts.
* **Use** Multi-factor authentication, making users enter more than one authentication methods.
* **Install** systems in the domain that pick up on suspicious user activity, like that of a compromised account.
```diff
-what is a common configuration mistake that can be good for an attacker doing kerberoasting?
```
## SILVER TICKETS

A Silver Ticket is like the inverse of kerberoasting instead of extracting a cleartext password to the service account using a TGS. An actor creates a forged new TGS using the password to that service's account.
```diff
-not inverse. these attacks will usually come toghther (kerberoast followed by a silver ticket)
```

Using a silver ticket allows an actor unlimited access to that service and it's resources.

### How Does The Attack Work?

> * Get the password of the service account, that can be done using a multitude of ways like: DCSync, SAM dump etc.
```diff
-what attack could you do to get it? (hint: its a few lines up)
```
> * Forge a ticket using some tool like `Rubeus`, `Impacket`, `Mimikatz` or `Kekeo`.

### Mitigating the Attack

While there is no way to stop the forgery of the ticket itself, as a defender you can imit the effect that this ticket has. And also limit the ability to password dump.

* **Install** AVs to detect password dumping tools
* **Enable** PAC Validation on kerberos in the domain, that would check if the DC was the one to issue the ticket.
* **Enforce** A **STRONG PASSWORD POLICY**!!!!!!!!!!!!!!!!

```diff
-how can you detect the attack?
```
