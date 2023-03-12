# Mimikatz

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
* Kerberoast Golden/Silver Ticket
* Pass-The-Cache (Windows/Linux)

### A Little History

Mimikatz was written by Benjamin Delpy in order to show Microsoft that their authentication protocols are insecure, Mimikatz is a slang for "Cute cats" in French.
The first version was published by him **closed-source** in May of 2011. It was written after Benjamin found a flaw in Microsoft's authentication protocol, alerting Microsoft about it, being dismissed and realizing that the exploit was really useful.

### 3 Modules In Depth

In here I will summarize about 3 modules.

> **LSADUMP**
>
> Stands for **Local Security Authority Dump**, this module houses commands that are used to interact with LSA (Local Security Authority) and extract/dump credentials.
> These operations require debug privileges.
> Using this module allows an actor to:
> * dump creds from local or remote LSA.
> * dump creds from SAM.
> * dump "SECRET"s.
> * change passwords for users.
> * Replicate from DC.
> * Push replications to DC.
> * et cetera.

> **SEKURLSA**
>
> This module's target is to interact with the portected memory of **LSASS** (Local Security Authority Subsystem Service) and dump credentials as well as tickets, keys, pins and hashes from it. This Module requires debug priviliges to interact with memory, but on a memory dump file (.DMP) does not.
> Using this module allows an actor to:
> * List Credentials (of both users and services) from **Credential Manager**, **WDigest**, **SSP**, **LSASS Memory and Dump Files**, **Kerberos**.
> * List Kerberos Encryption Keys.
> * Get KRBTGT password hashes.
> * create an lsass memory dump.
> * Execute a pass the hash attack to create a process as another user.

> **KERBEROS**
>
> This modules interfaces with the official Microsoft Kerberos (MS-KILE) API. Because of that it does not need any special privileges.
> Using this module an actor can:
> * Execute Pass-The-Ticket and Pass-The-Cchace attacks.
> * Create Silver and Golden Tickets.
> * Dump Currently logged on user's tickets.
> * List tickets from the Kerberos credentials cache (ccache).

### Mimikatz Vs. Mimidogz

Mimidogz is actually a thing... A way to "obfuscate" invoke-mimikatz, it does help to avoid detection and bypass some AVs... Bruh.

Anyways, Mimidogz is actually better because dogs are cuter than cats, beat it loser.

(I read the question wrong and thourgh that it said Mimikatz was better, sorry if I offended you.)

### H4X0R T1M3!!!! >:D

Finna hack some stuff.

I chose the Windows 7 machine so it would be easier <3 and logged on as an IT account to have local admin and CMD rights.

**Step 1 - Open mimikatz**
> ![Open Mimikatz](/Pictures/Mimikatz/01_First_Open.PNG)
> First, we open Mimikatz! this shows I can use it :)

**Step 2 - Get Passwords**
> ![](/Pictures/Mimikatz/02_SEKURLSA_Logonpasswords.PNG)
> In this step we get the cached passwords from the memor of the computer.

### Persistency

There are a few ways to leave a persistency using Mimikatz.

1. Golden Tickets
> A golden ticket is a persistenct technique in which you gain access to the hash of the **krbtgt** password and generate a spoofed tgt.
> Using that tgt you may masquarade as any user in the domain and give yourself domain/enterprise admin permissions. 

2. Changing passwords
> The Mimikatz tool can send queries to change passwords of users using ntlm, meaning they now got a hold of a user in the domain. That can act as a backdoor for a long time.

3. Creating new Users
> Using the mimikatz tool an attacker can gain domain admin access and create new users in the AD, and leave them there as a backdoor to the domain.