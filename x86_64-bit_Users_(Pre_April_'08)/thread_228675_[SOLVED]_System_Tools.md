---
title: "[SOLVED] System Tools"
date: 2006-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cariboo1938 on 2006-08-03
](*,) Hi everybody,
today I got the LiveCD Ubuntu 6.06. During the installation I run into two mayor problems:
1) Under "Aplications" I can't find 'System Tools' to create my Internet Dial-Up connection.
2) I can't create a root, i.e. SuperUser password.
Please can somebody give me a hint what I would have to do. 
Thanks 
Juergen:(

---

### Post by FenrisAbraxas on 2006-08-03
> **Cariboo1938 said:**
> ](*,) Hi everybody,
today I got the LiveCD Ubuntu 6.06. During the installation I run into two mayor problems:
1) Under "Aplications" I can't find 'System Tools' to create my Internet Dial-Up connection.
2) I can't create a root, i.e. SuperUser password.
Please can somebody give me a hint what I would have to do. 
Thanks 
Juergen:(

Ubuntu uses sudo to do maintainance tasks just type:

sudo command 

and enter your user password :S you can make a root account anyway or type sudo -s -H to stay as root

---

### Post by McMarley on 2006-08-03
1. try rerunning the installation and then it should probably ask you what you want as root password
2. the networking is under: SYSTEM>>ADMINISTRATION>>NETWORK TOOLS

you should find it pretty easaly

---

### Post by FenrisAbraxas on 2006-08-04
> **McMarley said:**
> 1. try rerunning the installation and then it should probably ask you what you want as root password
2. the networking is under: SYSTEM>>ADMINISTRATION>>NETWORK TOOLS

you should find it pretty easaly

Ubuntu installer will never asks for a root password because by default Ubuntu will use sudo instead of a root account.

First time i used Ubuntu i was confused but is not that bad, it's just im used to have a mid-level password for my user account (so my girlfriend or brother can log without too much problem) and a random generated password changed every month for the root account (hey it's dangerous to have a sshd open to the internet!).

So. sudo command (password your user password) or sudo -s -H (your user password again) to use super-user powers!

---

### Post by Cariboo1938 on 2006-08-04
> **FenrisAbraxas said:**
> Ubuntu installer will never asks for a root password because by default Ubuntu will use sudo instead of a root account.
..........So. sudo command (password your user password) or sudo -s -H (your user password again) to use super-user powers!
Thank you McMarley and FenrisAbraxas ...Coming from Libranet I can get used to this 'sudo' solution.
The real struggle is how to set up the Dial-Up connection to the Internet? The 'system administrator' shows me that there is a Topic PCI-card Modem in the system. In >System>Administration>Networking two Ethernet ports (eth0, eth1) are listed and a modem is listed.
But I always get the message that the modem is not configured. Do you have any solution for me? I'm certainly not the only one who depends on Dial-Up.
Juergen

---

### Post by FenrisAbraxas on 2006-08-07
> **Cariboo1938 said:**
> Thank you McMarley and FenrisAbraxas ...Coming from Libranet I can get used to this 'sudo' solution.
The real struggle is how to set up the Dial-Up connection to the Internet? The 'system administrator' shows me that there is a Topic PCI-card Modem in the system. In >System>Administration>Networking two Ethernet ports (eth0, eth1) are listed and a modem is listed.
But I always get the message that the modem is not configured. Do you have any solution for me? I'm certainly not the only one who depends on Dial-Up.
Juergen

I'm not sure i've never got my winmodem to work a few years ago (DSL rulz :D) but probably you have to mess with pppod (or something like that :S). Have you searched through the forums?

---

### Post by Cariboo1938 on 2006-08-07
I got it running: there is a excellent HowTo which helped me to solve the problem...see at:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
Thanks FenrisAbraxas
and bye,bye for now
Juergen

---

