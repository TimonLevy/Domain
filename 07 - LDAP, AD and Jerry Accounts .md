```diff
-you didnt answer question 6!
```
# LDAP, COMPUTER ACCOUNTS AND ACTIVE DIRECTORY

A domain is made up of many machines and users, it is a collection of objects that are grouped by the controller, appropriately called the **Domain Controller**. Those objects are categorized and decentrelized into different groups under the *Active Directory* structure and they are managed using permissions. The structure is also used to authenticate and manage users.

When we need to get information about those object we can ask the domain for it using a **Directory Access Protocol**. Using it, we can enumerate informationg about which users are in what directory, what machines are in what directory and even perform actions on those objects.
```diff
-you only get information about what objects are in directorys?
```

## Active Directory

As written above, the active directory is the logical directory used to store all of the containers, users, computers, permissions and policies belonging to a Domain. Simply put, if the DC is the heart of the domain, the Active Directory (AD) is the skeleton of the domain and users and computers themselves are the flesh of the domain.


## Computer Accounts

In the Active Directory not only user accounts are stored but also computer accounts, to add a machine to the domain it is crucial that it will have it's own account in the domain. Only with a computer account will a machine be able to authenticate itself to the DC and be able to connect to the domain network and it's resources.
```diff
-only computer accounts authenticate in the domain?
```

## Lighweight irectory Access Protocol

There were many "DAP"s over the course of Internet history, but LDAP is the most popular today. As the name suggests it is Lightweight. For a detailed more explanation you may read [my summary](https://github.com/TimonLevy/Networking/blob/main/03.%20Bigous%20Protocolous.md#lighweight-directory-access-protocol-aka-ldap).

LDAP is a protocol that lets a user perform enumeration and operations on the objects of the Active Directory. One of those operations is the Search operation.

    "
     The Search operation is used to request a server to return, subject to access
     controls and other restrictions, a set of entries matching a complex search criterion.
     This can be used to read attributes from a single entry, from entries immediately subordinate
     to a particular entry, or from a whole subtree of entries.
    "
```diff
-explain what is an entry
```
This is the description of the Search operation according to the [official LDAP rfc](https://www.rfc-editor.org/rfc/rfc4511). Explaining that the client needs to provide a set of *complex search criterion*.

More directly, the client needs to provide these criterion (but not only):
```diff
-name all the criteria (since these are not the only ones)
```

> **baseObject** - The base object to search relative to (may be the root).

> **scope** - The scope to search whithin relative to the baseObject, can be immidiate children, all children (recursively) or only the base object.

> **sizeLimit** - the maximum amount of entries to be returned as a result of the search operation.

> **filter** - A filter for the object's attributes using logical operators (like, DistinguishedName == "PC1").

> **attributes** - A list of attributes to be returned from every object that matches the filter.


## So let's sum it all up

If we want to find all of the computer in the domain, we may use LDAP to search for all of the computer accounts in the Active Directory using LDAP :)

```diff
-this is not a a summary.. this is an example of an operation you can do
```
