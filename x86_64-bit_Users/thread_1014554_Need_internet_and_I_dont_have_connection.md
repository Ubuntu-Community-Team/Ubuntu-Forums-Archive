---
title: "Need internet and I dont have connection"
date: 2008-12-17
forum: x86 64-bit Users
---

### Post by hnocnir on 2008-12-17
Hi;
I finished U Studio installation but I can't connect to the internet. Wireless was not detected when installing.  
I have: HP 60-120US, wireless 802.11a/b/g/n and 2wire internet.
I need help. Thanks, H.

---

### Post by soxs on 2008-12-18
append the output of ```
lspci
```

---

### Post by hnocnir on 2008-12-18
How do I 'append the output of Code: lspci'?  
What exactly do I have to do/go?  
Because I go to networks and have try putting 2wire codes but this is not like ubuntu 8.04 or 8.10.  It like it doesn't read the wireless.

---

### Post by soxs on 2008-12-18
> **hnocnir said:**
> How do I 'append the output of Code: lspci'?  
What exactly do I have to do/go?  
Because I go to networks and have try putting 2wire codes but this is not like ubuntu 8.04 or 8.10.  It like it doesn't read the wireless.

Open a terminal and give me the ouptu of that command.

---

### Post by hnocnir on 2008-12-18
Ok. I'm not a tech.  I have dual boot.  Might it be posible to find what you are asking with windows running or should I restart on Ubuntu Studio? And where do I look for that terminal?

---

### Post by nlz on 2008-12-18
go to applications > accessories > terminal

type: lspci
then copy and paste the outcome here..

---

### Post by hnocnir on 2008-12-18
Hahaha So funny. Now the U Studio won't run and I cant find what you guys told me.  I guess I have to remove it and install again. Agrrr. Well, Thank u, See u when I have this fix.

---

### Post by danielpalos on 2008-12-18
Was the physical (hardware) portion of your internet connection "on"?  I know this may seem like a simple question, but sometimes I forget to double check all of the physical connections.

If you have another network adapter, you may want to try that.  A USB wireless adapter may need to go through a hub in order to be recognized.

---

