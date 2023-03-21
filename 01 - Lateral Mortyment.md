# LATERLAL MOVEMENT

Lateral movement is a technique employed by attackers to expand their control over a machine to other machines on the same network, this isn't necessary an attack but simply a way to label the act of expanding an attacker's control. Lateral movement will often be using as a way to navigate through a network to a traget machine, using exploits on each of them to step through the systems to the next ones.

```diff
-give me another way\reason for it
```

Lateral movement could be performed using spear-phishing, pass-the-ticket/hash, session hijacking or maybe even network shares.

```diff
-maybe or for a fact?
```

## When Will We See Lateral Movement?

When attacking a network, an attacker needs to perform privilege escalation. That is, get higher permissions to the domain and local machines. There are several ways to escalate your privileges, stealing passwords from the local cache\ leveraging bad permission practices\ leveraging bad segmentation. In order to do that the attacker will need to find a computer that fulfils one of those weaknesses.


An attacker could perform lateral movement to a machine that an admin had logged on to recently to extract their credentials from the cache. Or, they could perform lateral movement to a computer that has RDP permissions to some other machine that could be a potential attacker vector. Or maybe they could perform laterval movememnt to a server that is located in the same lan and could be accessed with the attacker's current user. Maybe one that has some known vulnurability.

```diff
-maybe?
-give examples of the lateral movement (not the privilege escalation after it)
```
