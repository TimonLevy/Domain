# HARDENING THE DOMAIN!!!

Hardened shit.
These are the steps I took in hardening my domain.

| TABLE OF CONTENTS _______________________________________________________________________________________________________________ | NO. |
| --                                                                                                                                | --  |
| Disabling communication using LLMNR [←](#1-disabling-communication-using-llmnr)                                                   | 1   |
| Disabling NTLM authentication [←](2-disabling-ntlm-authentication-in-the-domain)                                                  | 2   |
| Disabling local password caching [←](#3-disabling-local-password-caching)                                                         | 3   |
| Enforcing SMB Signing [←](#4-enforcing-smb-signing)                                                                               | 4   |

<br><br><br>

## 1. **Disabling Communication using LLMNR**

> This step was done in order to avoid any poisoning attempts by bad actors in the local network. Like when I did the NTLM relay attack.

![](/Pictures/Hardening/GPO_Screenshots/Disable_LLMNR_GPO_Settings.PNG)

> Here we can see how there are no LLMNR queries sent between the DNS one and the escalated NBNS ones. I searched `\\SOM` in the run prompt, something random.

![](/Pictures/Hardening/Evidence/No_LLMNR_In_Dirdur.PNG)

<br><br>

## 2. **Disabling NTLM authentication in the domain**

> This was done because our domain has no need for authentication using NTLM, we want only the newest and freshest authentication protocol possible to be used in our domain!

![](/Pictures/Hardening/GPO_Screenshots/NTLM_GPO_Settings.PNG)

> In this image we can see how when trying to access a share no NTLM challange is sent.

![](/Pictures/Hardening/Evidence/No_NTLM_Authentication.PNG)

> In here we can see that the NTLM relay tool isn't working since we don't use NTLM even though the first part of the attack (the poisoning) worked!

![](/Pictures/Hardening/Evidence/NTLM_Relay/NTLM_Relay_Not_Working.PNG)

<br><br>

## 3. **Disabling local password caching**

> This precussion was done in order to make latteral movement harder, ofcourse this single GPO setting doesn't stop password caching as a whole and there are a lot of places passwords get saved locally.

![](/Pictures/Hardening/GPO_Screenshots/Disabling_Password_Caching.PNG)

<br><br>

## 4. Enforcing SMB Signing

> SMB Signing is a feature in SMB that adds a little encrypted digest of the entire SMB message at the SMB header, validating the sender and integrity of the message.
> Enabling it can stop relay attacks.

![](/Pictures/Hardening/GPO_Screenshots/SMB_GPO_Settings.PNG)