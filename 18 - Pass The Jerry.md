# PASS THE TICKET

A pass the ticket attack is very similar to a pass the hash attack, an actor steals the TGS/TGT tickets of another user and uses them to authenticate as the other user.

```diff
-explain what the attack actually is
```
### How Is It Performed?

The first thing that we need is to get the tickets of another user, it may be the TGS or the TGT. we can do that by either fake delegation or by dumping the lsass memory locally.<br>
What is fake delegation? Let's say a domain service wants to perform actions on a domain resource on a user's behalf, if Kerberos delegation is configured that service would be able to do that. (Like a web server accessing a database on a user's behalf). Fake delegation is when an attacker poses as a domain service and asks to delegate on behalf the client, meaning he would get the client's TGT.

Next is using the ticket, that can be done by various different exploitation tools like: Mimikatz, Rubeus, Kekeo and Impacket. The ticket is injected into the memory of the lsass process and it's permissions and privileges are given to the attacker. Pretty nifty.

```diff
- The attack is just TGTs?
+ No.
- No clue what you are trying to say, do research again and rewrite the paragraph (read what you wrote before submitting!!)
+ Fixed it.
```
### How Do We Mitigate The Attack?

Here are some things we can do:
1. **Disable** Delegation on servers that don't need it, since they may store the TGT's of users that log onto them. (Based on neccessity, this is a useful functionality)
2. **Check** who has the privilege to enable delegation on servers.
3. **Disable** the ability for high value users to get delegated.
4. **Detect** hooking of lsass process.
5. **Detect** mismatch between logged on user and kerberos tickets.

```diff
- What ticket usage should you find abnormal to detect the attack?
+ Tickets that do no belong to the logged on user.
```
