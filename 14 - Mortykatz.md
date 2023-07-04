```diff
-you didn't answer question 13!!
```
# MIMIKATZ, THE SWISS KNIFE OF THE DOMAIN ATTACKS

Mimikatz is a cyber exploitation tool aimed at the windows operating system. The tool is most often used to extract passwords from memory as well as tickets and hashes.

The tool is open source and written in C, it is non-graphical, meaning it is executed through the command line. Also features really cool
<details>
    <summary>ascii art</summary>
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣀⣤⣤⣤⣤⣤⣤⣀⣀⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣤⡾⠛⠉⠁⠀⠀⠀⠀⠈⠉⠉⠉⠛⠷⢶⣤⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⡄⣹⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⣿⣄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⡶⠿⠛⠋⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠘⢿⣧⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⣾⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠸⢿⣿⡀⠀⠀⢀⣤⡶⠖⠛⠛⠛⠷⠶⠶⠶⠶⠾⠶⢶⣦⡄⠀⠀⢸⣷⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡿⠁⠀⣰⡿⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⢷⡀⠀⢸⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣸⡇⠀⢀⡿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣧⠀⢸⡷⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⣿⡀⠀⣸⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⠀⢸⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢹⣇⢰⡟⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⠀⣸⣧⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣤⡶⠾⠿⠛⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⣿⣿⣿⠋⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠘⢿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⣿⠋⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠘⣷⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⢻⣾⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠘⣷⣄⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣾⠏⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠉⢹⡗⠂⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣃⣿⠏⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⣾⡿⠋⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣷⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⣾⠏⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣸⡿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣸⣿⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣰⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⠻⢦⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⣴⣿⣿⣧⣤⣤⣤⣤⣄⠀⠀⠀⠀⠀⠀⠀⠀⣼⢻⡇⠈⠻⠶⣶⣤⣄⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣤⡶⠿⢿⡟⣿⡟⠀⠀⠀⠀⠹⣿⠀⠀⠀⠀⠀⠀⠀⢠⡿⢸⣇⠀⠀⠀⠀⠀⠉⠉⠻⠿⢶⣦⣤⣄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣠⣴⠾⠛⠉⠀⠀⣾⡇⢸⡇⠀⠀⠀⠀⠀⣿⠀⠀⠀⠀⠀⠀⣰⡿⠁⢸⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠉⠛⠷⠶⣤⣄⣀⠀⠀⠀⠀⠀⠀
    ⠀⠀⠀⠀⠀⠀⣀⣴⠶⠛⠉⠀⠀⠀⠀⠀⢸⣿⠀⢸⡇⠀⠀⠀⠀⡆⣿⠀⠀⠀⠀⣠⣾⠏⠀⠀⣸⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠉⠛⠷⣦⡀⠀⠀
    ⠀⠀⢀⣤⡶⠟⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⠀⢸⡇⠀⠀⠀⠀⣿⡟⠀⠀⣀⣴⠟⠁⠀⠀⢠⣿⠑⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢻⡆⠀
    ⢠⣾⠋⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡿⠀⢸⡇⠀⠀⠀⠀⠸⣿⣴⠾⠋⠀⠀⠀⠀⢠⡿⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢻⡦
    ⣼⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣼⣧⠀⣸⣿⣀⣀⣤⣀⣘⣿⣷⣄⠀⠀⠀⢀⣰⢿⣧⠄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠘⣷
    ⣿⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠻⢿⣿⡏⠉⢩⣽⣿⣏⠉⠉⠀⠙⠳⢶⣤⠞⠁⣸⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿
    ⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢹⣧⠀⣿⠟⠉⣿⠆⠀⠀⠀⠀⠀⠀⠀⠀⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣴⡿⠿⣷⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿
    ⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⠀⣿⠀⠀⣿⠀⠀⠀⠀⠀⠀⠀⠀⠂⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠸⣿⣇⠀⠸⣧⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣰⣿
    ⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⠀⡿⠀⠀⣿⡆⠀⠀⠀⠀⠀⠀⠀⢶⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⠀⠀⢻⡆⠀⠀⣠⣴⣶⣤⠀⠀⢸⡟⠇
    ⢻⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⢸⡇⠀⠀⣿⡆⠀⠀⠀⠀⠀⠀⠀⢸⣇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢹⡇⠀⠘⣷⣠⡾⠋⠀⣽⡟⣷⡀⠘⣷⣤
    ⠸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢻⡿⣧⠀⣰⡿⠃⠀⠀⠀⠀⠀⠀⠀⢸⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡇⠀⠀⠙⠟⣥⡶⠟⣻⣿⠟⠧⣴⣿⣧
    ⠀⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣷⣹⣿⣿⡀⠀⠀⠀⠀⠀⠀⠀⠀⢘⣿⠆⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢾⡇⠀⠀⠀⣴⢷⣄⠠⣿⣧⡀⠈⣿⣄⣀
</details>

### What can it do?

Mimikatz can perform many attacks on the NTLM and Kerberos authentications methods, but not only:

* Pass-The-Hash (NTLM)
* Pass-The-Ticket (Kerberos)
* Overpass-The-Hash/Pass-The-Key (NTLM)
* Kerberoast
* Golden Ticket
* Silver Ticket
* Pass-The-Cache (Windows/Linux)
```diff
- Kerberoast, golden ticket and silver ticket are 3 different attacks
+ Noted and seperated.
```
### A Little History

Mimikatz was written by Benjamin Delpy in order to show Microsoft that their authentication protocols are insecure, Mimikatz is a slang for "Cute cats" in French.
The first version was published by him **closed-source** in May of 2011. It was written after Benjamin found a flaw in Microsoft's authentication protocol, alerting Microsoft about it, being dismissed and realizing that the exploit was really useful.

### 3 Modules In Depth

In here I will summarize about 3 modules.
```diff
- Name the rest of the modules
+ Named them all.
```
> **LSADUMP**
>
> Stands for **Local Security Authority Dump**, this module houses commands that are used to interact with LSA (Local Security Authority) and extract/dump credentials.
> These operations require debug privileges.
> Using this module allows an attacker to:
> * dump creds from local or remote LSA.
> * dump creds from SAM.
> * dump "SECRET"s - application credentials from dpapi, domain credentials from LSA
> * change passwords for users.
> * Replicate from DC.
> * Push replications to DC.
> 
> et cetera.
```diff
- What do you mean by "SECRETS" and et cetera?
+ Services like dpapi and LSA keep sensitive information like application credentials and local user credentials in registry keys, files and memory, these are often called secrets.
+ Et cetera ("etc") mean "and more things" in Latin.
- The english word is eccetera
+ It's a synonim, eccetera = et cetera. But just pronounced with a c.
```
> **SEKURLSA**
>
> This module's target is to interact with the portected memory of **LSASS** (Local Security Authority Subsystem Service) and dump credentials as well as tickets, keys, pins and hashes from it. This Module requires debug priviliges to interact with memory, but on a memory dump file (.DMP) does not.
> Using this module allows an attacker to:
> * List Credentials (of both users and services) from **Credential Manager**, **WDigest**, **SSP**, **LSASS Memory and Dump Files**, **Kerberos**.
> * List Kerberos Encryption Keys.
> * Get KRBTGT password hashes.
> * create an lsass memory dump.
> * Execute a pass the hash attack to create a process as another user.

> **KERBEROS**
>
> This modules interfaces with the official Microsoft Kerberos (MS-KILE) API. Because of that it does not need any special privileges.
> Using this module an attacker can:
> * Execute Pass-The-Ticket and Pass-The-Cchace attacks.
> * Create Silver and Golden Tickets.
> * Dump Currently logged on user's tickets.
> * List tickets from the Kerberos credentials cache (ccache).

The other modules are:
* busylight
* crypto
* dpapi
* event
* iis
* misc
* minesweeper
* net
* privilege
* process
* rpc
* service
* sid
* standard
* sysenv
* token
* ts
* vault

```diff
- you forgot BUSYLIGHT, IIS, MINESWEEPER and SYSENV
+ Added, I missed those.
```

These modules either allow more credential harvesting from other places in the widows OS like the credential vault or interaction with the processes\sessions on the machine.

```diff
- Why are calling an attacker actor?
+ Idk, I changed it.
```

### Mimikatz Vs. Mimidogz

Mimidogz is actually a thing... A way to "obfuscate" invoke-mimikatz, it does help to avoid detection and bypass some AVs... Bruh.

Anyways, Mimidogz is actually better because dogs are cuter than cats, beat it loser.

(I read the question wrong and thourgh that it said Mimikatz was better, sorry if I offended you.)

```diff
- I am deeply offended, so give 2 more reasons mimiDOGS > mimiKATZ
+ Sorry :(
+ Two more reasons mimiDOGS > mimiKATZ:
+ - Some anti-viruses don't recognise mimidogs as malware and let it run.
+ - The animal part of the name (dogs/katz) is actually spelled correctly on Mimidogs as opposed to Mimikatz, because dogs aren't script kiddies who write with Zs.

-good, now give 2 reasons dogs>cats
```

### H4X0R T1M3!!!! >:D

Finna hack some stuff.

I chose the Windows 7 machine so it would be easier <3 and logged on as an IT account to have local admin and CMD rights.

**Step 1 - Open mimikatz**
> ![Open Mimikatz](/Pictures/Mimikatz/01_First_Open.PNG)
> First, we open Mimikatz! this shows I can use it :)

**SekurLSA::LogonPasswords | Get Passwords**
> ![](/Pictures/Mimikatz/02_SEKURLSA_Logonpasswords.PNG)
> We get the cached passwords from the memor of the computer.

**LsaDump::DCSync | To get the ntds.dit credentials**
> ![](/Pictures/Mimikatz/03_SEKURLSA_DCSYNC.PNG)
> In here we can get all the credentials stored on the DC, inside the ntds.dit file by imposing as a Domain Controller in the domain and asking for a replciation. There was no permission block we I was able to perform this procedure.
>
> ![](/Pictures/Mimikatz/04_DCSYNC_krbtgt_account_creds.PNG)
> Here we pulled `krbtgt`'s NTLM hash.
>
> ![](/Pictures/Mimikatz/05_DCSYNC_domain_users_creds.PNG)
> Some more domain users NTLM hashes.
>
> ![](/Pictures/Mimikatz/06_DCSYNC_Rick.PNG)
> Performing a DCSync on a specific user.

#### Golden Ticket time

**SekurLsa::pth | Open a session with another user's ntlm hash**
> ![](/Pictures/Mimikatz/07_CMD_on_MortyAcc_(DONT_USE).PNG)
> This is an attack that lets an attacker create a process with the token of another user using their ntlm hash. In this scenario I launched the Mimikatz process as a *Local Admin* so I had no access to the domain resources (This session is different t the one is the former examples). I listed the passwords that were stored in the cache and passed-the-hash to create a new cmd session with a domain user's token.

**Mimikatz | Launch Mimikatz on the new impersonated session**
> ![](/Pictures/Mimikatz/08_Mimikatz_on_CMD.PNG)

**Token::Elevate /domainadmin | Elevate token to get domain admin permissions**
> ![](/Pictures/Mimikatz/09_Impersonated_Domain_Admin.PNG)
> This command is used to elevate token permissions to those of a domain admin. This command uses the WindowsAPI and steals a token from the system's memory.

**Runas | Run a cmd as a domain user to get domain sid**
> ![](/Pictures/Mimikatz/11_RUNAS_Get_Domain_Sid.PNG)
> This is a step needed to create a golden ticket. The command requires the domain's sid to create the ticket (you can see it marked in gold).

**Kerberos::Golden**
> ![](/Pictures/Mimikatz/12_Golden_Ticket.PNG)
> Finally we create the ticket, the arguments go as such:
> * **DOMAIN** (Domain FQDN) - Microverse.Battery
> * **SID** (Domain Security IDentifier) - domain sid shown in the last image
> * **USER** (User to create the ticket for) - Administrator
> * **KRBTGT** (The ntlm hash of the krbtgt account) - I got it using a DCSync attack after elevating the token, didn't show it as I already showed it above.

### Persistency

There are a few ways to leave a persistency using Mimikatz.

**Skeleton Key**
> A skeleton key is an injected "master key" that is injected into the LSASS/KDC process on the DC, then an attacker can log on to any machine on the domain using any user with the master password.<br>
> The attack is done by hooking the authentication function in the process' memory (in Kerberos, the encryption algorthim is downgraded to HMAC-RC4), writing a new function with the "master key" that acts a fail-over incase normal authentication fails (In order to no disrupt authentic user logon).

**DCShadow**
> This attack pushes data into the DC by pretending to be another DC in the domain, using this attack we may change password hashes of domain users (like krbtgt), add and delete data to any partition of the domain structure. This attack also allows creation of objects in the directory structure with false timestamps, impersonated SIDs and also deletion.<br>
> using this attack we can change password hashes of users, add users or change permissions of already aqquired users. Which is very cool B)

**More minor and very traceable attacks**
Changing passwords
> The Mimikatz tool can send queries to change passwords of users using ntlm, meaning they now got a hold of a user in the domain. That can act as a backdoor for a long time.

Creating new Users
> Using the mimikatz tool an attacker can gain domain admin access and create new users in the AD, and leave them there as a backdoor to the domain.
```diff
- Name at least 2 attacks to create a backdoor with mimikatz
+ Skeleton Key, DCShadow.
```
