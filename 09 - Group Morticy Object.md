# GROUP POLICY OBJECT

A GPO or Group Policy Object, is a set of rules and instructions to be carried by machines in the domain.
```diff
- every GPO applies to all the machines in the domain?
+ No, machines in the domain are "linked" to gpos based on hierarchical structure and security groups. A machine will apply all the policies of all the GPOS that are Linked to it.
```
> **Policy**
>
> a definite course or method of action selected from among alternatives and in light of given conditions to guide and determine present and future decisions.

For example, using a group policy I can set a single wallpaper that all computers in the domain must use.

## HOW DOES IT WORK?

The Policy is changed using the **Group Policy Manager**. Only domain/enterprise admins can create policies and apply them.<br>
Group policies are applied in a process called **linking**, in the AD structure a group policy will be linked to an OU, object/Security Group/Domain/Site. Afterwhich the policy will apply it's regulations on to the objects inside the linked object. 

When a computer in the domain logs on it will pull all of the policies that are linked to it and apply all the configurations/limitations.

There are different types of GPOs:<br>
**Local GPO**
> A GPO that exists by default on all windows machines, it is a gpo that applies only to the local machine/user and is used when that kind of configuration is needed.<br>
> It is applied by default and in order to edit it you may user the local grou policy editor. Non-local GPO take preference over local GPOs and may even disabled them completely.

**Non-local GPO**
> A GPO that is applied to multiple machines by the linking process, will be used when configuration of multiple machines/users is required.

**Starter GPO**
> It is a template of group policy settings that be can used in future GPOs, used by administrators to establish a baseline for their GPOs.<br>
> This kind of gpo isn't applied to the user/machine but rather used in other gpos.

```diff
- What are the different types of GPOs and how are they applied to an object?
+ Added.

- the types are local, site-level, domain-level and OU. answer again.
```
## GROUP POLICY SECURITY

Group Policies allow administrators to set limitations and enable security features to the machines, ones that can help attackers infect them, using those limitations and features help us preserve the security of the network and the domain. Active Directory gives us a way to apply GPOs for security measures quite easily, in the AD you may create what's called a **Security Group**. A Security Groups is a group of machines and users that when a Policy is applies to, applies the policies to it's members. Using it we can easily link GPO to certein machines/users.

Here are some useful security settings:<br>

1. Force encryption when communicating.
2. Disable CMD on normal user accounts.
2. Strong password policy enforcement.
```diff
- What is password enforcement?
+ Enforcement of a strong password policy, allows the domain admin to set a "mask" to the password. 
+ Meaning that there would be a strict requirement for a password to have atleast 12 characters, a special sign and more.
-איך נשתמש בצורה תשתיתית ואיך בצורה אבטחתית?
+ Added, please read 'SUPPORTING DOMAIN INFRASTRUCTURE'.
```
## SUPPORTING DOMAIN INFRASTRUCTURE

GPOs may also be linked to entire domains, sites and OUs to enable or disable features on different assets in the domain. For example if we want to disable strong users from logging on to certein machines we may do that using a GPO. GPOs can also be used to prevent access between machines, prevent usage of weak authentication protocols and disable features that aren't needed on some machines. 

Here are some:
1. Disable remote desktop\ssh on machines that shouldn't have those.
2. Disable communications using SMBv1.
3. Disable authentication using NTLM.

By building a GPO for each segment in the network/domain we can provide better management that is more centralized.

## GROUP POLICY PREFERENCE

GPP or Group Policy Preference, was originally a 3rd-party extention for GPO that wanted to expand on the functionality of GPO and to replace most of the work what login scripts was used to do. The extension was adopted by microsoft with Windows Server 2008.

The tool could be used to push files to computers, create folders, create env variables, edit registry/ini files and shares. Also, it can be used to edit local groups/users, network options and more.

However, a Privilege Escalation vulnerabiity was found in the extension. It is "patched" now so no biggie though. The vulnerability had to do with the fact that you could edit users and groups using the GPP, more specifically, change password. The way these changes would actually work is by storing all the configuration data on the SYSVOL share in the DC, inside of files called `groups.xml`. Now, the computers would simply import those configurations and apply them, so what's the problem? **ANYONE CAN ACCESS SYSVOL**, it's actually a must. Anyone can look at these files, which again, is a must for it to be appilable.

![Here is what the file looks like](https://assets-global.website-files.com/601959b8cde20c101809c86a/603e5d033489813b8f15268d_groups_xml_content.jpeg)
<p style="font-size:11px">What the file looks like.</p>

Notice the `cpassword` variable, this is the password that the user will change to. It is encrypted in AES using a **32 bit** key, which is [**PUBLICCCC**](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-gppref/2c15cbf0-f086-4c74-8b70-1f2fa45dd4be?redirectedfrom=MSDN). Notice the `userName` varialbe as well, the user which we are changing the credentials to is the local admin, [das fucked up](https://www.youtube.com/watch?v=CuycuV0E4KU&ab_channel=ZachMemes).

Sooooo, as long as I have access to the domain, even with an unpivileged user. I can access the `group.xml` file**s**, decrypt the passwords using the AES algorithm and the key from the website and simply get all of the user passwords that are located there and move laterally across the network.

## MY GR

1. Developer Group GPO
   
Honestly, in here I didn't feel like restricting too much.

I disbaled autoruns from the resitry, and disabled the show password button to avoid any peepers who might wanna see the password.
I also made the group members the local admins on the `WIN7-1` machine (10.0.0.3).

2. Simple Users GPO

In here I went a bit more strict.

I disabled access to control panel, CMD and powershell.
Then prevented them to login onto the machine Developer and DC machines.
```diff
- They need to be able to login ONLY to 192.168.100.0 stations, there are more machines in the domain they should not be able to login to
+ I made it so just didn't write it apparently.
```
3. IT GPO

Simply created a Policy Object that would make them local admins on all machines.
