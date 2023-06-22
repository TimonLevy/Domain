```diff
- You didnt answer question 6!
+ Yes I did...
```
# LDAP, COMPUTER ACCOUNTS AND ACTIVE DIRECTORY

Objects in the domain are exist in a structure called an *Active Directory*. The active directory is a structure that lets the domain group instances, manage permissions and keep track of instances, just like an actual directory. In order to interact with the Directory we will use a **Directory Access Protocol**. An example for a Directory Access protocol is LDAP, which i covered about in the protocols part. LDAP allows users with permissions to query, enumerate, view, create, edit and delete instanced in the Active Directory.

```diff
- You only get information about what objects are in directories?
+ No.
```

## Active Directory

The `Active Directory (AD)` is the logical directory used to store all of the containers, users, computers, permissions and policies belonging to a Domain. Simply put, if the DC is the heart of the domain, the AD is the skeleton of the domain and users and computers themselves are the flesh of the domain.


## Computer Accounts

Computer accounts are the parallels to user accounts, just for computers. To add a computer to the domain it has to have a computer account, using those accounts we can apply policies and permissions to specific computers or computer groups.
```diff
- Only computer accounts authenticate in the domain?
+ No, but it also wasn't implied.
```

## Lighweight Directory Access Protocol

There were many "DAP"s over the course of Internet history, but LDAP is the most popular today. As the name suggests it is Lightweight. For a more detailed explanation you can read [my summary](https://github.com/TimonLevy/Networking/blob/main/03.%20Bigous%20Protocolous.md#lighweight-directory-access-protocol-aka-ldap).

LDAP is a protocol that lets a user perform enumeration and operations on the entries (objects, instances) of the Active Directory. One of those operations is the Search operation.<br
The search operation let's users query the Directory tree and apply filters in order to find specific entries. Entries may be computer accounts, user accounts, security groups or any other instance in the AD.
```diff
- explain what is an entry
+ Gotchu.
```

The client needs to provide these criteria in order to perform the search:
```diff
-name all the criteria (since these are not the only ones)
```

> **baseObject** - The base object to search relative to (may be the root).

> **scope** - The scope to search whithin relative to the baseObject, can be immidiate children, all children (recursively) or only the base object.

> **derefAliases** - A value that determines whether or not to defer alias entries. (like link files in a file system)

> **sizeLimit** - The maximum amount of entries to be returned as a result of the search operation.

> **timeLimit** - The maximum amount of time for a search operation to take.

> **typesOnly** - A value that indicates whether to return only attribute descriptors or values as well.

> **filter** - A filter for the object's attributes using logical operators (like, DistinguishedName == "PC1").

> **attributes** - A list of attributes to be returned from every object that matches the filter.

> **attributes** - The attribute fields to be returned for all the entries that match the filter.


## So to answer the question

If we want to find all of the computer in the domain, we may use LDAP to search for all of the computer accounts in the Active Directory using LDAP :)

```diff
- this is not a a summary.. this is an example of an operation you can do
+ Nisuah -2, I meant something else.
```
