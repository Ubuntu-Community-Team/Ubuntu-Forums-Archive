---
title: "Changing disks installing stuff with wine"
date: 2008-04-13
forum: Wine
---

### Post by MonkeyPlus on 2008-04-13
I'm installing the orange box with wine and I am having trouble with the disk change. Seems the orange box installer just doesn't want to let go of the last file on the first disk when it prompts me to insert the second disk, so neither umount or eject work (I've tried both through sudo as well).

I've also tried runnin the installer from the hard drive whilst the second disk is inserted to complete the installation but with no success.

Any ideas?

---

### Post by Stormspireiv on 2008-04-13
You may have already tried this, but it doesn't hurt mentioning it.
```

wine eject
```

It is different from the eject command.

---

### Post by SBFC on 2008-04-16
Don't forget to actually setup your cdrom/dvdrom in winecfg though. After you assign it a drive letter you can do as Stormspireiv said and 'wine eject d:'...

---

### Post by PsYcO~KJ on 2008-04-16
I had this same problem with tyring to install counterstrike. All i did was when it prompted me to insert the 2nd cd, i disconnected the power to my cd-rom, used a paperclip to put in the eject hole on the front panel of the cd-rom, opened the drive, took out cd#1, insert #2, closed the cd-rom, and reconnected the power, hit retry, and all was well.

if this doesnt work, and nothign anyelse says helps, just install steam itself, and then install the games you want through steam, ive doen that with CS:S and others

---

### Post by SBFC on 2008-04-16
> **PsYcO~KJ said:**
> I had this same problem with tyring to install counterstrike. All i did was when it prompted me to insert the 2nd cd, i disconnected the power to my cd-rom, used a paperclip to put in the eject hole on the front panel of the cd-rom, opened the drive, took out cd#1, insert #2, closed the cd-rom, and reconnected the power, hit retry, and all was well.

Wow...

---

### Post by PsYcO~KJ on 2008-04-16
> **SBFC said:**
> Wow...

why wow, cause i did it, or wow cause it worked?

---

### Post by Rafadagaffer on 2008-04-17
Probably wow at the fact that the tray wouldn't open at all without the power cable attached or maybe how dangerous it is to be sticking your hand inside your pc's case while the its on, or the fact that you are suggesting other people do these things :lolflag:

---

### Post by stinger30au on 2008-04-17
> **PsYcO~KJ said:**
> why wow, cause i did it, or wow cause it worked?



both:lolflag:

---

