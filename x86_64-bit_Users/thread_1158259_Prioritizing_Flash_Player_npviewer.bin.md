---
title: "Prioritizing Flash Player npviewer.bin"
date: 2009-05-13
forum: x86 64-bit Users
---

### Post by LesterPalooza on 2009-05-13
Is there any way I can prioritize to High Priority npviewer.bin when I startup Ubuntu? I wish to alot a large amount of system resources to get the best flash playback possible. I think I can achieve this by writing a script, but I do not what to write. Please advise. Thank you!

---

### Post by pixel :-) on 2009-05-13
I don't feal, it a good idea. I simply download rip flash video and then play them in an external video player, unless when i'm too lazy.

command "renice" read the man page i din't used it for a whille.

---

### Post by pixel :-) on 2009-05-13
renice is for when the proces is running she will nead pid number

pgrep -x npviewer.bin

command "nice" is when you first run the application, you may whant to write a small wrapper, in

/usr/lib/nspluginwrapper/i386/linux

rename npviewer.bin say npviewer.bin.real

and put your wrapper named npviewer.bin in the folder

more or less, read the man page and fix it

!#
nice -20 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin.real

---

### Post by LesterPalooza on 2009-05-13
> **pixel :-) said:**
> I don't feal, it a good idea. I simply download rip flash video and then play them in an external video player, unless when i'm too lazy.

command "renice" read the man page i din't used it for a whille.

I don't have any external video players except my psp. which will take time to rip, convert to mp4 and transfer before i can watch the video. :(

EDIT: Checking out your solution.

---

### Post by pixel :-) on 2009-05-13
No i meant with totem. It doesn't need conversion at all. Set caching in flash at 100%, then in the tmp folder, you simply drag and drop it on totem.

---

