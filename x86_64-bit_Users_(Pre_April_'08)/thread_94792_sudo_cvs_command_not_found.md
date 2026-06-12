---
title: "sudo: cvs: command not found"
date: 2005-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by bigcanuck on 2005-11-24
when trying to download this file

[PHP]sudo cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login[/PHP]
 
I get this error:

sudo: cvs:  commmand not found

how do I reslove this? I'm really new to Ubuntu and don't know how to slove this.

Thanks

---

### Post by oskude on 2005-11-24
sudo apt-get install cvs :)

---

### Post by bigcanuck on 2005-11-24
thanks

---

### Post by RAOF on 2005-11-24
Additionally, why are you trying to sudo cvs?  You shouldn't need root privs to do anything with cvs :)

---

### Post by bigcanuck on 2005-11-24
it's an install thing, I'm trying to install a DC++ client

---

### Post by oskude on 2005-11-24
[QUOTE=RAOF]Additionally, why are you trying to sudo cvs?  You shouldn't need root privs to do anything with cvs :)[/QUOTE]oh yeah, (didnt notice that :oops: )
DONT do "sudo cvs..."
"cvs..." is enough !

---

### Post by oskude on 2005-11-24
[QUOTE=bigcanuck]it's an install thing, I'm trying to install a DC++ client[/QUOTE]you need sudo only for "sudo make install" (or "sudo checkinstall")

---

