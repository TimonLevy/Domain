# THE CYBER KILL CHAIN

Developed at 2011 by the company Lockheed Martin, is a theoretical flowchart model used to identify the stages that an attacker would perform in a cyber attack. The original model has 7 stages but there is another model that is a little different.<br>
so let's wabba-labba-do-it babyyyyyy.

```diff
- Was this company the first to use the term kill chain?
+ It was the first company to adapt the term "kill chain" from the military speech to the cyber space.
```
## LOCKHEED MARTIN MODEL
### 1. Reconnaissance
![Binos](https://cdn-icons-png.flaticon.com/256/868/868457.png)

The attacker will perform reconnaissance operations on the network.<br>
It could be **passive**, like sniffing a network to find machines and available services.<br>
It could be **active**, like ping sweeping, port scanning or fingerprinting.

The reconnaissance will be done in order to locate a target and attack vectors that the attacker will later use.

### 2. Weaponization
![Virus](https://cdn-icons-png.flaticon.com/256/2913/2913465.png)

The attacker will create malware\payload to use in their attack.<br>
The attacker can use the knowledge that he found in the first step. Malware can be: exploits, customized malware or even an attack plan.

### 3. Delivery
![Mail](https://cdn-icons-png.flaticon.com/256/4829/4829879.png)

The attacker will infiltrate the network.<br>
He will execure the plan he made in the former step. An entrance could be achieved by social engineering attacks, exploits or physical access.

```diff
- What do you mean by hacking into the network?
+ Exploits.
```

### 4. Exploitation
![Hacker](https://cdn-icons-png.flaticon.com/256/6070/6070774.png)

This stage comes after performing reconnaissance, weaponization and delivery. In it, the attacker makes their way trough the network to their target, exploiting weaknesses. Often the attacker will perform lateral movement.

### 5. Installation

![Gears](https://theapollotheme.weebly.com/uploads/7/6/2/4/76249187/8_3.png)

After gaining access to the network and their targets the attackers will start to install the malware that they posses.<br>
The malware could assist the hacker is many ways: persistency, data leakage, ransomware, etc.
The attacker deploys the malware to get what he needs.

```diff
- what is the goal of this stage?
+ Depends on the malware.
```

### 6. Command and Control (C²)
![Joystick](https://cdn-icons-png.flaticon.com/256/113/113805.png)

In this stage the attacker will create a communication channel with the malware they deplayed beforehand. Creating a botnet or maybe just controlling their RATs.

### 7. Actions On Objectives
![Mouse](https://icon-library.com/images/mouse-and-keyboard-icon/mouse-and-keyboard-icon-8.jpg)

In this stage, the attacker has gained control of the network, installed all of his tools, installed all of ih malwares, created a C2 server and a botnet. After all of this, the attacker will finally achieve his original final goal. They may use their C2 server to make the computers perform certein actions like mine bitcoin, ddos some machine, steal and leak data, or spam mails.

After this stage, the attacker is pretty much free to do whatever he wants.

```diff
-find an example of another different cyber kill chain model
+ Aight.
```

## The Second Model
I couldn't pinpoint the exact origin of this model.

### 1. Reconaissance
Same as the first step in the Lockheed Martin model. 

### 2. Intrusion
This model combines the 2nd and 3rd step of the Lockheed Martin Model into one, crafting the malware/plan and entering the network.

### 3. Explotation
The attacker looks for valnurable points and exploits them.

### 4. Privilege Escalation
The attacker perform privilege escalation techniques by explotation or misconfiguration.

### 5. Lateral Movement
The attacker will perform lateral movement to get access to more assets on the network, spreading his influence.

### 6. Obfuscation
The attacker will perform obfuscation opertaions on points of interest to the investigators to make their activity cocealed.<br>
What this means is: faking timestamps of files, deleting and tampering with logs, deleting files, changing networking configuration.

### 7. Denial of Service
Attackers will then target the network infrastructure, denying access to services and network as a whole. Flooding the servers and services can make the servers crash and suspend user services.

### 8. Exfiltration
In this final step the attacker will implement an "exit path"  in order to get the data outside the network, credentials, classified files, ecryption keys.
