---
title: "Boot error"
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chozo01 on 2007-08-09
Alright, so I decided I would finally try Ubuntu, and I installed it through Wubi. Installed fine, except for when I try to boot into it, I get the following error (along with some other random numbers):

..MP-BIOS bug: 8254 timer not connected to IO-APIC
Kernel panic - not synching: IO-APIC + timer doesn't work! Boot with apic = debug and send a report. Then try booting with the 'noapic' option


...I have no clue what any of this means. Help?

---

### Post by splintercellguy on 2007-08-09
Follow the instructions here: [https://answers.launchpad.net/ubuntu/+question/1808](https://answers.launchpad.net/ubuntu/+question/1808) Basically you want to edit the /boot/grub/menu.lst where your Ubuntu is installed.

---

### Post by Chozo01 on 2007-08-09
I can't find out where to download GRUB from the website. >_<

---

### Post by Chozo01 on 2007-08-09
In case you didn't get the hint, how do I get GRUB?


I know I'm hopeless, but help me! D:

---

### Post by Arwen on 2007-08-09
[if it's what you need]("http://linux.softpedia.com/get/System/Boot/GNU-GRUB-1092.shtml")

---

### Post by Chozo01 on 2007-08-20
> **Arwen said:**
> [if it's what you need]("http://linux.softpedia.com/get/System/Boot/GNU-GRUB-1092.shtml")

And what do I do with that again?

---

### Post by Chozo01 on 2007-08-24
> **Arwen said:**
> [if it's what you need]("http://linux.softpedia.com/get/System/Boot/GNU-GRUB-1092.shtml")

Once again, what am I supposed to do with the grub-1.95.tar.gz.sig and grub-1.95.tar.gz files?

---

