---
title: "Kernel Panic - not syncing: attempting to kill init!"
date: 2006-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmb062082 on 2006-06-14
I had this problem every time I tried to load a 64 bit version on Dapper Drake live cd, 64 bit only, the 32 bit version worked fine, as well as any older 64 bit version build. It was a thorn in my side. I read up on the matter at hand on these forums, and saw that many other people were having the same problem, a lot of you. I found a fix that may help other people.

I found I could boot the cd, if I were to disable acpi via my system bios, or by placing the command acpi=off in my boot paramaters. With that said I still had many bugs during install, and random lock ups during install which I could not fix. I was getting upset and willing to give up on Ubuntu as my 64 bit version of fedora worked like a charm. So I decided to update my bios for the heck of it, and you know what? EVERYTHING worked like a charm after that.

Keep in mind during this time I was getting similar errors with the 64 bit version of gentoo, another linux flavor I have been wanting to try for some time. The bios update also fixed that error. So after being a long time Debian user, I figured I would give Gentoo a wack :-$ before trying to install ubuntu as I want to try something brand new. No gentoox, the xbox version does not count! Please no offense to the amazing Ubuntu! I am on hour number 8 of emerge, if for some reason this locks up on me once I will be back to Ubuntu.

I hope this thread helps at least one person, and for the record I am using a emachines t6522 box. Over all I am pleased with this system, its a shame that they had to shim the system with a horrible BIOS option, with no BIOS update options. I had to use  HP bios, ha!

---

### Post by dmb062082 on 2006-06-14
Update, post reserve, I can post some links to bios files soon! Just post your machine set up!

---

### Post by GR3G on 2006-07-08
Do you have any links to what Bios update you used.  I'm using a T6522 and cannot get Ubuntu to install (i386 or 64).  I'm assuming at this point it's because of the Bios needing updated.

Any help would be greatly appreciated!

---

