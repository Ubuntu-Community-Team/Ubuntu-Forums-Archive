---
title: "Life is good in 64-bits"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by brpadington on 2008-07-14
I just wanted to say that i am really impressed with Hardy Heron x86-x64. I tried vista x64 on my arcade cabinet in hopes of running mame 64bit but it gave me headache after headache. Mainly the fact that it takes so long to boot made vista impractical for a mame cab. I downloaded the latest vista 64 drivers for my wifi card and it still didnt work. Long story short i decided to try the 64-bit hardy and I was amazed. It found all of my hardware and i was able to get my ntfs hard drive mounted with few issues. It's great to see a modern operating system that actually runs well.:guitar:

Is anyone else running 64bit linux in an arcade cab? If so what are some ways that i could thin ubunutu down to get it to boot even faster?

---

### Post by Kilz on 2008-07-14
> **brpadington said:**
> I just wanted to say that i am really impressed with Hardy Heron x86-x64. I tried vista x64 on my arcade cabinet in hopes of running mame 64bit but it gave me headache after headache. Mainly the fact that it takes so long to boot made vista impractical for a mame cab. I downloaded the latest vista 64 drivers for my wifi card and it still didnt work. Long story short i decided to try the 64-bit hardy and I was amazed. It found all of my hardware and i was able to get my ntfs hard drive mounted with few issues. It's great to see a modern operating system that actually runs well.:guitar:

Is anyone else running 64bit linux in an arcade cab? If so what are some ways that i could thin ubunutu down to get it to boot even faster?

I dont run an arcade, but you can install bum (the boot up manager), it will allow you to stop checking for things during boot. An example is if you have an ati graphics card, you can tell it to stop checking for nvidia cards. But be careful, dont stop something you need. The only other alternative is to compile a kernel, thats more trouble than its worth to me.

---

### Post by prshah on 2008-07-14
> **brpadington said:**
> 
what are some ways that i could thin ubunutu down to get it to boot even faster?

You can install bootchart ```
sudo apt-get install bootchart
```, then keep an eye on the bootchart graphs in "/var/log/bootchart"; each line (section) in the bootchart will show how long a particular component takes to load; you can then consider eliminating components that take very long to load. For ex, I know from bitter experience that during boot, if a vfat (fat32) partition is present, it will stall at loading that partition (integrity check) for atleast 7~10 seconds.

btw, I'm not sure how well or not bootchart works with 64bit.

---

### Post by markbuntu on 2008-07-14
You can also get rid of a lot of extraneous boot stuff in System/Administration/Services and System/Preferences/Sessions. bum is my favorite for speeding up boot time though.

---

### Post by brpadington on 2008-07-15
Thanks for all the suggestions. i'll give them a try tonight when i get home. it's just so great being able to run the roms that my machine couldnt handle under xp. I already went through and turned off some options in appearance to possibly help speed things up. i am running gnome maybe it would be beneficial to try a lighter weight window manager.

---

### Post by Kilz on 2008-07-15
> **brpadington said:**
> Thanks for all the suggestions. i'll give them a try tonight when i get home. it's just so great being able to run the roms that my machine couldnt handle under xp. I already went through and turned off some options in appearance to possibly help speed things up. i am running gnome maybe it would be beneficial to try a lighter weight window manager.

I have icewm on my small file server. Its lightweight, but it doesnt decrease the boot up time. It also requires a more hands on approach and a lot more cli commands. Xfce, the desktop in Xubuntu is a good middle ground. You dont even have to reinstall. The command 
```
sudo aptitude install xubuntu-desktop
``` will install it all and give you the option of starting that desktop in the sessions list on the log in screen.

---

### Post by Jokimoto on 2008-07-15
Thanks very much for the B.U.M. suggestion, Kilz

---

