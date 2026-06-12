---
title: "Virutalbox removal"
date: 2009-08-15
forum: x86 64-bit Users
---

### Post by kiran88pnjr on 2009-08-15
Hai,

I'm now using Ubuntu 9.04 AMD 64. I've recently installed Virtualbox in my system. I built VDI for it using 8.0 GB space of my home partition. But later I've completely removed Vbox, but before that I've removed VDI from home as root. Later my property showed that out of 22.9 GB of my home partition only 5.1 GB is free & 7.9 GB is used. I lost about 9.9 Gb space including 8.0 GB space I've used for Vbox before. 

Please anyone help me to get back 8.0 GB space :(:(

---

### Post by skunkTrader on 2009-08-15
Did you try emptying the trash yet?

---

### Post by kiran88pnjr on 2009-08-15
Yes. I've removed thrash. I've been facing this problem for 5-6 days now.:(:(:(

---

### Post by jocko on 2009-08-16
> **kiran88pnjr said:**
> Yes. I've removed thrash. I've been facing this problem for 5-6 days now.:(:(:(
As you say you removed it while logged in as root, you of course have to empty root's trash... (and stop using root/sudo to make changes in your home directory. You are the owner of that directory, not root).

---

### Post by theZoid on 2009-08-16
> **jocko said:**
> As you say you removed it while logged in as root, you of course have to empty root's trash... (and stop using root/sudo to make changes in your home directory. You are the owner of that directory, not root).

yes per the above....you should keep you .vdi files in your home directory on /home for security if the system gets hosed.

---

### Post by kiran88pnjr on 2009-08-16
Thank Both of u. When I open thrash as root using Rootilus script it shows "contents couldn't be displayed" message.:confused::confused::confused::(:(:(

---

