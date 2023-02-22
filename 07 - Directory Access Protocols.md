# DIRECTORY ACCESS PROTOCOL

A domain is made up of many machines and users, it is a collection of objects that are grouped by the controller, appropriately called the **Domain Controller**. Those objects are categorized and decentrelized into different groups under the *Active Directory* structure and they are managed using permissions. The structure is also used to authenticate and manage users.

When we need to get information about those object we can ask the domain for it using a **Directory Access Protocol**. Using it, we can enumerate informationg about which users are in what directory, what machines are in what directory and even perform actions on those objects.

## Lighweight irectory Access Protocol

There were many "DAP"s over the course of Internet history, but LDAP is the most popular today. As the name suggests it is Lightweight. For a detailed you may read [my summary](https://github.com/TimonLevy/Networking/blob/main/03.%20Bigous%20Protocolous.md#lighweight-directory-access-protocol-aka-ldap)