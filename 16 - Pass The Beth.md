# PASS THE HASH

A pass the hash is an attack on authentication protocol like NTLM, where the malicious actor uses a stolen password hash instead of their own passwords hash to authenticate. This gives them access to the impersonated user's resources like domain access, privileges and gpo and permissions.
```diff
-what is their own passwords hash?
```

Usually an actor will dump hashes from lsass process or SAM file using tools like *fgdump*, *pwdump7* and [*Mimikatz*](/14%20-%20Mortykatz.md). If there were any other logged on users or local users on the machine the attacker will then pass-their-hash and open a new session using heir authentication token. That can be cmd, powershell, or even network/domain services like smb.

One protocol that is weak to Pass-The-Hash attacks is [NTLM](/05%20-%20New%20Technologies%20Lan%20Morty%20(NTLM).md).
```diff
-what are the requirements to perform this attack?
```
Here I executed the attack on the NTLM Protocol, gained Domain Administrator privileges and Mapped The DC's `C:\` share on my pc.
![](/Pictures/Pass_The_Hash/01_Dumping_Credentials.PNG)
![](/Pictures/Pass_The_Hash/02_Pass_The_Hash.PNG)
![](/Pictures/Pass_The_Hash/03_POC.PNG)

On the left is a normal cmd session, notice even though I am logged on to a domain user I am unprivileged and unable to map the remote drive. However with the PTH'd session I can do it very easily using the exact same command.
