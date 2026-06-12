---
title: "x86_64 Ubuntu-compatible scanners?"
date: 2007-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by adamc55 on 2007-11-07
Does anyone have currently available models they would recommend?

---

### Post by John Jason Jordan on 2007-11-07
> **adamc55 said:**
> Does anyone have currently available models they would recommend?
I use a Canoscan Lide 30 and it works perfectly. You can still occasionally find a new one in an overstock or closeout site. Don't get the later Canon scanners, as they do not work.

Having said that, there is a problem with USB scanners in Feisty. The problem occurs only in Feisty (both 32-bit and 64-bit), so if you are using an earlier version of Ubuntu or Gutsy, you won't have any trouble.

---

### Post by John.Michael.Kane on 2007-11-07
These might be of some help.
[Scanners]("http://www.sane-project.org/sane-backends.html#SCANNERS")
[Scanners2]("http://www.sane-project.org/sane-mfgs.html#SCANNERS")

---

### Post by crjackson on 2007-11-07
> **adamc55 said:**
> Does anyone have currently available models they would recommend?

Cannon Lide 20 works great in Gutsy.  Won't work in Feisty 64 for me.

---

### Post by John Jason Jordan on 2007-11-08
> **crjackson said:**
> Cannon Lide 20 works great in Gutsy.  Won't work in Feisty 64 for me.
No USB scanner will work correctly in Feisty. The kernel that Feisty installs added a feature called USB-suspend, which broke all USB scanners. It wasn't an Ubuntu problem - the glitch was caused by the kernel developers. The problem was fixed with Gutsy. I don't know if the kernel that Gutsy installs was fixed, or if it's still broken but Ubuntu figured out a workaround. All I know is that USB scanners work fine now in Gutsy. But if you want a USB scanner, stay away from Feisty.

---

### Post by Total_Biscuit on 2007-11-08
> **John Jason Jordan said:**
> No USB scanner will work correctly in Feisty. The kernel that Feisty installs added a feature called USB-suspend, which broke all USB scanners. It wasn't an Ubuntu problem - the glitch was caused by the kernel developers. The problem was fixed with Gutsy. I don't know if the kernel that Gutsy installs was fixed, or if it's still broken but Ubuntu figured out a workaround. All I know is that USB scanners work fine now in Gutsy. But if you want a USB scanner, stay away from Feisty.
Coo.  I guess that nobody told my usb scanner, which works perfectly in feisty :-P

---

