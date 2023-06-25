# PASS THE HASH

A pass the hash is an attack on authentication protocol like NTLM, where the attacker uses a stolen password hash to authenticate. This gives them access to the impersonated user's resources like domain access, privileges and gpo and permissions.
```diff
- What is their own passwords hash?
+ The hash of the user they are logged on as, nevertheless removed the line. It was meaningless.
```

An attacker will dump hashes from memory, registry or files using tools like *fgdump*, *pwdump7* and [*Mimikatz*](/14%20-%20Mortykatz.md).<br>
Using those password hashes he will send impersonated NTLM authentication requests and valid responses to the authenticating entity (usually the DC).<br>
Basically this means he can freely authenticate as the user the password hash belongs to.

One protocol that is weak to Pass-The-Hash attacks is [NTLM](/05%20-%20New%20Technologies%20Lan%20Morty%20(NTLM).md).

The attacker needs the following to execute the attack:
- Access to a domain machine which has the password hashes.
- Ability to run tools like Mimikatz to dump memory and access specific registry keys.
- Communication with the DC.

```diff
- What are the requirements to perform this attack?
+ Added.
```
Here I executed the attack on the NTLM Protocol, gained Domain Administrator privileges and Mapped The DC's `C:\` share on my pc.
![](/Pictures/Pass_The_Hash/01_Dumping_Credentials.PNG)
![](/Pictures/Pass_The_Hash/02_Pass_The_Hash.PNG)
![](/Pictures/Pass_The_Hash/03_POC.PNG)

On the left is a normal cmd session, notice even though I am logged on to a domain user I am unprivileged and unable to map the remote drive. However with the PTH'd session I can do it very easily using the exact same command.
