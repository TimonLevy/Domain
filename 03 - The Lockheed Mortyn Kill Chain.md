# THE KILL CHAIN

The **Kill Chain**, developed by the company Lockheed Martin, is a **model** used to identify the stages that an attacker would perform in a cyber attack. The model has 7 stages, so let's wabba-labba-do-it babyyyyyy.



### **Reconnaissance**
```
"Harvesting E-mail addresses, conference information, etc."

⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⣄⠀⠀⠀⠀⠀⠀ ⣠⣄
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠚⠻⠿⡇⠀⠀⠀⠀ ⢸⠿⠟⠓
⠀⠀⠀⠀⠀⠀⣠⣴⣾⣿⣶⣦⡀⢀⣤⣤⡀⢀⣴⣶⣿⣷⣦⣄
⠀⠀⠀⠀⠀⣴⣿⣿⣿⣿⣿⣿⡇⢸⣿⣿⡇⢸⣿⣿⣿⣿⣿⣿⣦
⠀⠀⠀⠀⠘⠋⣉⡉⠙⠛⢿⣿⡇⢸⣿⣿⡇⢸⣿⡿⠛⠋⢉⣉⠙⠃
⠀  ⢀⣤⣾⡟⠛⠛⠻⢷⡙⠃⢸⣿⣿⡇⠘⢋⣤⣾⡟⠛⠛⠛⠷⣤⡀
⠀⢀⣾⠋⠀⠀⠀⠀⠀⠀⠀⠙⣷⠀⠘⠛⠛⠃⠀⣾⡿⠀⠀⠀⠀⠀⠀⠀⠈⢷
⠀⢸⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡆⢰⣿⣿⡆⢰⡟⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡇
⠀⠸⣧⠀⠀⠀⠀⠀⠀⠀ ⢀⡾⠀⠀ ⠉⠉⠀ ⢷⡀⠀⠀⠀⠀⠀⠀  ⣼⠇
⠀⠀⠙⢷⣄⣀⠀⠀⣀⣤⡾⠁⠀⠀⠀⠀⠀⠀⠀ ⠈⢷⣤⣀⠀⣀⣠⡾⠋
⠀⠀⠀⠀⠉⠛⠛⠛⠋⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀ ⠈⠙⠛⠛⠉
```

In this stage, the attacker will perform reconnaissance on the network. It could be **passive**, like sniffing a network to find machines, ips, public available services. And it could be **active**, like ping sweeping, port scanning or fingerprinting. Here are some techniques:

 * Active: Ping Sweep.
 * Active: Port Scan & Fingerprinting.
 * Quiet: Social Engineering.
 * Quiet: Sniffing.

The reconnaissance will be done in order to locate a target and attack vectors that the attacker will later use (Like machines with guest operating systems that have known vulnarabilities, systems with known vulnarabilities, applications with known weaknesses or open ports).



### **Weaponization**
```
"Coupling exploit with backdoor into deliverable payload."

 ⠀⠀⠀⠀⣀⣀⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
 ⠀⣰⡾⠛⠛⠉⠻⣦⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⢀⣿⠀⠀⠀⠀⠀⠀⠀⠈⠻⣦⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠸⣧⡀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠻⣦⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠈⠻⣦⡀⠀⠀⠀⠀⠀⠀⠀⣰⡏⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠈⠻⣦⣀⣀⣀⣠⠞⠛⣦⡀⠀⠀⠀⠀⠀⠀⠀⣀⣀⣀⣠⣤⡤⠀
⠀⠀⠀⠀  ⠈⠛⠉⠙⣷⣴⠟⠛⣷⣄⠀ ⠀⠀⠀⢿⡟⠛⠉⠉⠀⠀⠀⠀
⠀⠀⠀⠀⠀ ⠀⠀⠀⠀⠀⠈⠻⣦⡾⠋⢙⣷⣄⠀⠀⢸⡇⠀⢠⡶⣶⣦⣤⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠻⣶⡟⠉⣹⣷⣄⠘⣿⢀⣿⠁⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠻⣿⡏⢀⣿⢷⣿⣾⠃⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠻⣿⣁⣴⠟⣿⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠻⣿⡿⠷⢶⣾⣿⣷⣴⠟⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⣨⣿⣾⠛⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⠀⠀⠙⣷⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠛⠀⠀⠀⠈⠛⠂⠀⠀⠀⠀⠀⠀⠀⠀⠀
```

In this stage, the attacker will create a malware\payload to use in their attack after finding out all of the neccesary information about their target and weaknesses. That payload is not neccessarily a single malware or even neccessary a piece of code, it can be a plan of what methods to use and little payloads that each use an known exploit on a system.



### **Delivery**
```
"Delivering weaponized bundle to the victim via email, USB, etc."

⠀⠀⠀⠀⠀⠀⠀⠀⢀⣀⠀⣶⣤⣤⣄⣀⡀
⠀⠀⠀⠀⠀⠀⢀⣴⣿⣿⡀⢻⣿⣿⣿⣿⣿⣿⣷⣦⣤⣀
⠀⠀⠀⠀⠀⣠⣾⣿⣿⣿⣇⠸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣶⣤⣀
⠀⠀⠀⠀⣴⣿⣿⣿⣿⣿⣿⠀⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⠷⠆
⠀⠀⠀⣼⣿⣿⡿⠟⠛⠉⣉⣀⠘⣿⣿⣿⡿⠿⠿⠟⠛⠛⠉⣉⣀⣤⣤⣶⠂
⠀⠀⣼⠟⠉⣀⣤⣶⣿⣿⣿⣿⣦⣤⣤⣤⡀⢠⣶⣶⣾⣿⣿⣿⣿⣿⣿⠃
⠀⠀⢠⣶⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣧⠈⢿⣿⣿⣿⣿⣿⣿⣿⠃
⠀⠀⠀⠈⠙⠿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡆⠸⣿⣿⣿⣿⣿⡟⠁
⠀⠀⠀⠀⠀⠀⠀⠉⠛⠻⢿⣿⣿⣿⣿⣿⣿⣿⠀⣿⣿⣿⡿⠋
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠉⠛⠿⠿⣿⣿⡇⢻⠿⠋
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀ ⠈
```

The attacker will infiltrate the network using some kind of means, it can be either a phishing email containing some form of payload or even hacking into the network. In the delivery stage the attacker will gain access to the network and the users.



### **Exploitation**
```
"Exploiting a vulnerability to execute code on the victim's system"

⠀ ⠀⠀⠀⠀⠀⠀   ⣠⣶⣶⣶⣶⣶⣄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀ ⠀ ⣴⠟⠛⢿⣿⣿⡿⠛⠻⣦⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀  ⢸⣿⠀ ⠀⢸⣿⡇⠀ ⠀⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀  ⠸⣿⣦⣤⣾⠿⠿⣷⣤⣴⣿⠇⠀⠀⠀⠀⠀⠀⠀⠀
⠀ ⣴⣶⣶⣶⣦⣌⡉⢹⣿⣿⣴⣦⣿⣿⡏⢉⣡⣴⣶⣶⣶⣦
⠀ ⣿⣿⣿⣿⣿⣿⣷⠈⢿⣿⣿⣿⣿⡿⠁⣾⣿⣿⣿⣿⣿⣿
⠀ ⣿⣿⣿⣿⣿⣿⣿⣷⣄⡉⠛⠛⢉⣠⣾⣿⣿⣿⣿⣿⣿⣿
⠀ ⣿⣿⣿⣿⣿⣿⠟⠁⢙⣿⣿⣿⣿⡋⠈⠻⣿⣿⣿⣿⣿⣿
⠀ ⣿⣿⣿⣿⣿⣇⠀⠐⢿⣿⣿⣿⣿⡿⠂⠀⣸⣿⣿⣿⣿⣿
⠀ ⣿⣿⣿⣿⣿⣿⣷⣄⣠⣿⣿⣿⣿⣄⣠⣾⣿⣿⣿⣿⣿⣿
⠀ ⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿⠿
⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⣶⠀⠀
⠹⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡿⠏⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
```

This stage comes after performing reconnaissance, weaponization and delivery. In is, the attacker makes their way trought the network to their target, exploiting weaknesses. Often the attacker will perform lateral movement.



### **Installation**
```
"Installing malware on the asset."

⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢰⣿⣿⡆
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⣿⡇
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⣿⡇
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⣿⡇
⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⣤⣤⡀⠀⠀⣿⣿⣿⠀⠀⣠⣤⣤⣄
⠀⠀⠀⠀⠀⠀⠀⠀⠘⢿⣿⣿⣿⣷⣸⣿⣿⣇⣾⣿⣿⣿⡿⠃
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⠋
⠀⢀⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⢿⣿⣿⣿⣿⡿⠋⠀⠀⠀⠀⠀⠀    ⢀⣀
⢰⣿⣿⡆⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⢿⡿⠋⠀⠀⠀⠀⠀⠀⠀⠀ ⠀⠀⢰⣿⣿⡆
⢨⣿⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀   ⢸⣿⣿⡇
⠸⣿⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀   ⢸⣿⣿⡇
⢸⣿⣿⣷⣤⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣀⣤⣾⣿⣿⡇
⠀⠙⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡿⠋
⠀⠀⠀⠀⠈⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠁
```

In this stage, after gaining access to the network and their targets the attackers will start to install the malware that they posses. From trojan horses to injectors and shells.



### **Command and Control (C²)**
```
"Command channel for remote manipulation of the victim."

⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣴⣶⣶⣦⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⣿⣿⣿⣿⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢻⣿⣿⣿⣿⡟⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣈⠙⠋⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⣿⠇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⣿⡿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⣿⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣾⣿⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⢀⣤⣤⣭⣭⣥⣤⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠘⠛⠛⠛⠛⠛⠛⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⢿⣿⠀⠀⠀⢰⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡆⠀⠀⠀⣿⡿⠀⠀⠀⠀
⠀⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⣤⡄⠀⠀⠀
⢸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡇⠀⠀⠀
⠈⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠁⠀⠀⠀
```

In this stage the attacker will create a communication channel with the malware they deplayed beforehand. Creating a botnet or maybe just controlling their RATs.

### **Actions On Objectives**
```
"With `hands on keyboard` access, intruders accomplish their original goals."

⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⠳⢶⣄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⣤⣤⣤⣤⡿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠸⣯⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠛⠂⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⢸⣛⣟⣻⣟⣻⣟⣻⣟⣻⣛⣿⣛⣿⣛⣿⣟⣛⣛⣻⣿⣿⣟⣛⣻⡇
⢸⣹⣿⣏⣹⣏⣹⣏⣹⣏⣹⣏⣹⣿⣹⣿⣏⣉⣹⣏⣹⣏⣹⣏⣻⡇
⢸⣉⡇⣏⣹⣏⣹⣏⣹⣏⣹⣏⣹⣏⣹⣿⣏⣉⣹⣏⣹⣏⣹⣏⣿⡇
⢸⣉⣹⣏⣹⣏⣹⣏⣹⣏⣹⣏⣹⣏⣹⣏⣹⣏⣹⣏⣹⣏⣹⣏⣽⡇
⢸⣭⣯⣽⣯⣭⣭⣭⣭⣭⣭⣭⣽⣯⣽⣯⣽⣯⣽⣯⣭⣭⣽⣯⣽⡇
```

In this stage, the attacker has gained control of the network, installed all of his tools, installed all of ih malwares, created a C2 server and a botnet. After all of this, the attacker will finally achieve his original final goal. They may use their C2 server to make the computers perform certein actions like mine bitcoin, ddos some machine, steal and leak data, or spam mails.

In this stage, the attacker is pretty much free to do whatever he wants.