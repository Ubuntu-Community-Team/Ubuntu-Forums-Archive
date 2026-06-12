---
title: "Upgrade / Synaptic issue"
date: 2009-04-03
forum: x86 64-bit Users
---

### Post by xigen on 2009-04-03
Hi,

I lost my KDE applications and sound when I hit the upgrade icon yesterday.

My guess is that it is related to KDE.

Depends: kdebase-runtime but it is not going to be installed
Depends: kdelibs5 (>=4:4.1.96) but 4:4.1.4-0ubuntu1~intrepid1.1 is to be installed

I tried:  $ sudo apt-get dist-upgrade
The issues persisted.

I tried a simple reboot.  The sound works when the system goes to the login page... then it stops working. 

Any suggestions?

AMD 64/gnome/ubuntu 8.10

Cheers,

MW

---

### Post by dcstar on 2009-04-04
> **xigen said:**
> Hi,

I lost my KDE applications and sound when I hit the upgrade icon yesterday.

My guess is that it is related to KDE.

Depends: kdebase-runtime but it is not going to be installed
Depends: kdelibs5 (>=4:4.1.96) but 4:4.1.4-0ubuntu1~intrepid1.1 is to be installed

I tried:  $ sudo apt-get dist-upgrade
The issues persisted.

I tried a simple reboot.  The sound works when the system goes to the login page... then it stops working. 

Any suggestions?
.....

Wait until the repository you are using gets **all** the new packages, then run the Update Manager again.

---

### Post by spoon_ on 2009-04-04
Same thing happened to me yesterday! Now I've no KDE4 apps :(

---

