---
title: "How can I downgrade to wine 1.0.1?"
date: 2008-10-28
forum: x86 64-bit Users
---

### Post by nbtrap on 2008-10-28
Hi, I'm running 8.04 amd64, and I upgraded to wine 1.1.7 using sudo commands.  Now I can't find the appropriate .deb to downgrade to 1.0.1.  Is is possible to downgrade using the Terminal?  If not, what can I do?

---

### Post by philinux on 2008-10-28
Just use synaptic to completely remove it.

---

### Post by Kilz on 2008-10-28
You also might want to try [play on linux.]("http://www.playonlinux.com/en/") Its  a wine application utility that helps you install windows applications. One nice feature lets you install multiple versions of wine and run different windows applications under different versions. Its kind of like a free cedega that works with all kinds of windows apps, not just games.

---

### Post by nbtrap on 2008-10-28
> **philinux said:**
> Just use synaptic to completely remove it.

I already have, but when I try to install it again, I can only install 1.1.7.  It's not like it asks which version I want.

---

### Post by ronnielsen1 on 2008-10-28
> I already have, but when I try to install it again, I can only install 1.1.7.  It's not like it asks which version I want. 	
Find wine in synaptic and highlight it. On the tabs below, you will see a versions tab. Click on this and it will show you available versions. 

On the top click Package Tab - Force Version. This will ask you which version to install.

---

### Post by nbtrap on 2008-10-28
> **ronnielsen1 said:**
> Find wine in synaptic and highlight it. On the tabs below, you will see a versions tab. Click on this and it will show you available versions. 

On the top click Package Tab - Force Version. This will ask you which version to install.

This seems to work, except version 1.0.1 is not there.  Just 1.0.0.

---

### Post by ronnielsen1 on 2008-10-28
[https://launchpad.net/ubuntu/intrepid/i386/wine/1.0.1-0ubuntu1](https://launchpad.net/ubuntu/intrepid/i386/wine/1.0.1-0ubuntu1)

---

