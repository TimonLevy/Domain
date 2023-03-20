# KERBEROS GOLDEN TICKET

A Golden Ticket is an exploitation of the Kerberos mechanism that allows an actor to impersonate users and get unpriviledged priviledged access to any place that is accessible in the domain by anyone. A Golden Ticket is a fabricated TGT (Ticket Granting Ticket) that is valid because it is encrypted using krbtgt's password hash.

In order to create a golden ticket an actor has to know these things:
* The ntlm hash of krbtgt's password.
* The SID of the domain (which if he has a domain account he can know)

In order to get the hash of krbtgt's password an actor may perform an attack called DCSync. In which he poses as a Domain Controller and asks to be replicated to, giving him the `NTDS.dit` file and all the information about the domain structure and objects. To perform that attack the actor would have to already be a domain admin, that is why the golden ticket attack is mostly used for _lateral movement_ and not _privilege escalation_. Further, a Golden Ticket's expiration date will usually last 10 years, though that is variable.

To create a golden ticket an actor can use the Mimikatz malware or the Impacket bundle of malware.

### Mitigations

The attack can be mitigated in different ways:
1. Change the krbtgt account password on a regular basis - That is so any currently active Golden Tickets will lose their validity.
2. Monitor Ticket lifetimes - If a ticket lifetime surpasses the domain policy it's a sign of foul play.
3. Monitor DC Replications
4. Set Honeypots - Like priviledged acounts that no real personnel can access. And monitor any use of their account name.