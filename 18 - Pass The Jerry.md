# PASS THE TICKET

A pass the ticket attack is very similar to a pass the hash attack, an actor assumes the identity of their victim without knowing their credentials.
```diff
-explain what the attack actually is
```
### How Is It Performed?

The act of passing another user's TGT and using their token snt the hard part, that can be achieved using Mimikatz, Rubeus, Kekeo and Impacket.
The real difficult part is getting that TGT of the other user, without getting too elaborate one way is to impersonate a service that the user want to delegate to, that way the DC will give us their TGT. This can be done with `Rubeus` and `Kekeo`, Kekeo is a tool just like Mimikatz (Developed by the same guy) that uses different APIs and some other code that had to be seperated dude to licensing.
```diff
-the attack is just TGTs?
-no clue what you are trying to say, do research again and rewrite the paragraph (read what you wrote before submitting!!)
```
### How Do We Mitigate The Attack?

Here are some things we can do:
1. **Disable** Delegation on servers that don't need it, since they may store the TGT's of users that log onto them. (Based on neccessity, this is a useful functionality)
2. **Check** who has the privilege to enable delegation on servers.
3. **Disable** the ability for high value users to get delegated.

To detect a PtT attack, you could look in the cached tickets and look for any tickets that don't belong. Tickets that were injected.
```diff
-what ticket usage should you find abnormal to detect the attack?
```
