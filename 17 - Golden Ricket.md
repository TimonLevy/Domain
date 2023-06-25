# KERBEROS GOLDEN TICKET

A Golden Ticket is an exploitation of the Kerberos mechanism that allows an actor to generate a custom TGT, the attacker can choose what permissions to give that TGT and hence  he can get access to any resource in the domain that atleast one user has access to.

```diff
- It impersonates users?
+ Create TGTs using different user SIDs in order to get their permissions. 
- Unpriviledged privileged access?? (dfuk)
+ I don't know....
- A golden ticket gets access to any place in the domain?
+ If you give yourself domain admin privileges, then basically yes.
```

In order to create a golden ticket an actor has to know these things:
* The ntlm hash of krbtgt's password.
* The SID of the domain (which if he has a domain account he can know)

In order to get the hash of krbtgt's password an actor may perform an attack called DCSync. In which he poses as a Domain Controller and asks to be replicated to, giving him the `NTDS.dit` file and all the information about the domain structure and objects. To perform that attack the actor would have to already be a domain admin, that is why the golden ticket attack is mostly used for _lateral movement_ and not _privilege escalation_. Further, a Golden Ticket's expiration date will usually last 10 years, though that is variable.

To create a golden ticket an actor can use the Mimikatz malware or the Impacket exploitation tool bundle.
```diff
- Impacket bundle of malware? what malware? (is this a grammar mistake or explain what do you mean?)
+ Tools, sorry for confusing you.
```
```diff
- How can you detect usage of the attack??
+ Gotchu.
```
### CATCHING THE ATTACK

The attack is not impossible to catch, since the DC logs TGT and TGS requests and audits a lot of useful data it could be used in the search for golden tickets.<br>
**User and Domain Names** - some attackers will use made up user and domain names in their TGTs.<br>
**Mismatched Data fields** - User names and mismaching RIDs (group identifiers in the SID) and memberships.<br>
**Source IPs** - Some TGTs can be used from machines that aren't even members of the domain.<br>
**TGS Requests Without Prior TGT Requests** - This could indicate that the TGT wasn't given by the DC.

And also information on the machines could help like:<br>
**Tickt Lifetime** - If a ticket lifetime exceeds the domain default ticket lifetime it could point to malicious activity.
**Logon Audit Logs** - Check for mismatching SIDs in the logon audit logs.

### Mitigations

The attack can be mitigated in different ways:
1. Change the krbtgt account password on a regular basis - That is so any currently active Golden Tickets will lose their validity.
2. Monitor Ticket lifetimes - If a ticket lifetime surpasses the domain policy it's a sign of foul play.
3. Monitor DC Replications.
4. Set Honeypots - Like priviledged acounts that no real personnel can access. And monitor any use of their account name.
