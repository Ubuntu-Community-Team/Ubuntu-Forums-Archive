---
title: "Can I upgrade 32bit Gutsy to 64 but gutsy?"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by bergersau on 2007-10-25
I'm currently running Gutsy 32 bit and I'm curious as to weather you can simply upgrade to the 64 bit version or if a clean install will be called for.

Has anyone had experience in this?

---

### Post by gmc on 2007-10-25
Short answer is: NO

If you want to upgrade/switch from 32bit to 64bit, you'll need to re-install the system. The good news is, if your home directory is on another partition and you don't format it during re-installation, all your current customization will remain intact.

Gord

---

### Post by dptxp on 2007-10-25
> **bergersau said:**
> I'm currently running Gutsy 32 bit and I'm curious as to weather you can simply upgrade to the 64 bit version or if a clean install will be called for.

Has anyone had experience in this?

NO.

---

### Post by jenhsun on 2007-10-25
> **bergersau said:**
> I'm currently running Gutsy 32 bit and I'm curious as to weather you can simply upgrade to the 64 bit version or if a clean install will be called for.

Has anyone had experience in this?

NO NO.

---

### Post by hashimoto on 2007-10-25
Direct upgrading is a no-go. 

I did a clean install with Gutsy 64 and left my home partition from Feisty 32. Install was a breeze as always, but I experienced problems with Firefox. It started OK first time after installation but not after that: core dumped. I had to reinstall Firefox to make it run and even then it would run only once.

I finally deleted my ./mozilla folder and the problems were gone. Bugs me what was wrong...

---

### Post by rsambuca on 2007-10-25
> **hashimoto said:**
> Direct upgrading is a no-go. 

I did a clean install with Gutsy 64 and left my home partition from Feisty 32. Install was a breeze as always, but I experienced problems with Firefox. It started OK first time after installation but not after that: core dumped. I had to reinstall Firefox to make it run and even then it would run only once.

I finally deleted my ./mozilla folder and the problems were gone. Bugs me what was wrong...

If you look in the compatibility.ini and compreg.dat files, it looks like there may be reference to x86_64 and some libraries in the 64bit.  I assume that there must be something similar in the 32bit config files for firefox.

---

### Post by bergersau on 2007-10-26
Just as I suspected - It would be asking a lot from the installer to cope with this type of upgrade.

Ah well,  I'll wait until a clean install is warranted then go  the go the 64 bit route.  I'll make sure /home is on it's own partition before I try.

Thanks all.

---

