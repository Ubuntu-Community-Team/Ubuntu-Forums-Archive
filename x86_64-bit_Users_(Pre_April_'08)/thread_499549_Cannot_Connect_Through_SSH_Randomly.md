---
title: "Cannot Connect Through SSH Randomly"
date: 2007-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kaao on 2007-07-12
Before it was working fine but for some reason now i get an error when i try to connect to any server via ssh 

when i use the Places> Connect to server i get the message Service Unavaiable SSH://serveraddress

Help Please

i have already tried reinstalling the ssh client

---

### Post by jpkotta on 2007-07-12
Open a terminal and do:
```
ssh serveraddress
```
If it fails, post the output.  If you have editted anything in /etc/ssh, say what you did.

---

