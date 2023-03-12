# Group Poicy Object

A GPO or Group Policy Object, is a set of rules and instructions to be carried by all machines in the domain.

> **Policy**
>
> a definite course or method of action selected from among alternatives and in light of given conditions to guide and determine present and future decisions

For example, using a group policy I can set a single wallpaper that all computers in the domain must use.

## HOW DOES IT WORK?

The Policy is changed using the **Group Policy Manager**, it looks like a huge list of options and configurations that can be applied. A domain admin can create a policy then, choosing what rules he wants to set and enforce. And finally push that policy to the entire domain or a group or groups or even a specific OU.

When a computer logs into the domain it will then pull all of the poliies that apply to it and apply all the configurations. That can be disabling cmd, disabling the ctrl + alt + dlt key combination or even disabling communication using particular protocols.

## HOW CAN WE USE IT TO BE MORE SECURE?

Like I said, GPO can be used to set different configurations. Some even regarding endpoint security. Here are some configurations that ma help you avoid being hackered:

1. Disable communications using SMBv1.
2. Disable communications using NTLM.
3. Force encryption when communicating.
4. Disable CMD on normal user accounts.
5. Stop password enforcement.
6. Disable remote desktop\ssh on machines that shouldn't have those.

And much more...

## Group Policy Preference

GPP or Group Policy Preference, was originally a 3rd-party extention for GPO that wanted to expand on the functionality of GPO and to replace most of the work what login scripts was used to do. The extension was adopted by microsoft with Windows Server 2008.

The tool could be used to push files to computers, create folders, create env variables, edit registry/ini files and shares. Also, it can be used to edit local groups/users, network options and more.

However, a Privilege Escalation vulnerabiity was found in the extension. It is "patched" now so no biggie though. The vulnerability had to do with the fact that you could edit users and groups using the GPP, more specifically, change password. The way these changes would actually work is by storing all the configuration data on the SYSVOL share in the DC, inside of files called `groups.xml`. Now, the computers would simply import those configurations and apply them, so what's the problem? **ANYONE CAN ACCESS SYSVOL**, it's actually a must. Anyone can look at these files, which again, is a must for it to be appilable.

[Here is what the file looks like](https://assets-global.website-files.com/601959b8cde20c101809c86a/603e5d033489813b8f15268d_groups_xml_content.jpeg)
<p style="font-size:11px">What the file looks like.</p>

Notice the `cpassword` variable, this is the password that the user will change to. It is encrypted in AES using a **32 bit** key, which is [**PUBLICCCC**](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-gppref/2c15cbf0-f086-4c74-8b70-1f2fa45dd4be?redirectedfrom=MSDN). Notice the `userName` varialbe as well, the user which we are changing the credentials to is the local admin, [das fucked up](https://www.youtube.com/watch?v=CuycuV0E4KU&ab_channel=ZachMemes).

Sooooo, as long as I have access to the domain, even with an unpivileged user. I can access the `group.xml` file**s**, decrypt the passwords using the AES algorithm and the key from the website and simply get all of the user passwords that are located there and move laterally across the network.

## My Domain's GPOs

1. Developer Group GPO
   
Honestly, in here I didn't feel like restricting too much.

I disbaled autoruns from the resitry, and disabled the show password button to avoid any peepers who might wanna see the password.
I also made the group members the local admins on the `WIN7-1` machine (10.0.0.3).

2. Simple Users GPO

In here I went a bit more strict.

I disabled access to control panel, CMD and powershell.
Then prevented them to login onto the machine 10.0.0.3.

3. IT GPO

Simply created a Policy Object that would make them local admins on all machines.