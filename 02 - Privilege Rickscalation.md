# PRIVILEGE ESCALATION
**Privilege escalation** is a technique used by an attacker to get elevated privileges over the network/domain/host machine. Escalated privileges allow an attacker to perform more operations in the network, like:
- Authenticate to more machines.
- Permissions to more secured files.
- System management users. like databases, firewalls, smtp servers, etc.
- Kernel space code execution.
Idealy, the attacker would want to get a local admin on his current machine or a domain admin user.
```diff
- Just the privileges you noted are elevated? explain what are elevated privileges
+ Escalated privileges allow an attacker to perform more operations in the network\domain\local machine.
```

## How Can It Be Done?
Privilege escalation techniques usually exploit coding mistakes or miscofiguration of systems.
```diff
- what do you mean by human mistakes?
+ Miscofigurations, service accounts with cleartext password in their files for example.
```
* Admins user credentials can be extracted from local password cache (memory carving).
  - An attacker can access the memory of the lsass process on the machine and extract the stored tickets\hashes.
```diff
- Ptt/pth are things to do with the extracted creds not a way to extract them, give a way for that
- Also, mimikats is not a way it is a tool - i want you to understand behind the scenes
+ I changed the bullet to be more accurate.
```
* Running code in the kernel space allows attackers access to every part of the OS and FS.
  - This can be achieved by running exploits on the OS or even installing malicious drivers.
* Credentials can be "cracked" using bruteforcing methods.
  - After gaining password hashes an attacker would crack them offline using tools like Hydra/John the Ripper.
* An attacker might perform a social engineering techniques in order to get the password from the user.
  - An attacked can send misleading links to spoofed login pages of popular websites in order to get the user's password.
* Systems can have code valnurability that lets attackers run code under the system's account.
  - Websites could have SQL injection valnurability which could lead to an attacked running code under the sql user's permissions.

```diff
- Give an example for each techniqe.
+ Served fresh and hot. (listed with the hollow bullets)
-don't use words like "might" and "maybe" when explaining a term or giving an example (say he can\would)
+ Okie dokie.
```

[Here](https://www.exploit-db.com/) is a cool link for you if you want to escelate yourself some bitches.
