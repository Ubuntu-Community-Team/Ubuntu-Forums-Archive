---
title: "whats going on with cedega?"
date: 2007-01-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sonic Reducer on 2007-01-11
i just installed cedega Version 5.2.3 and am trying to install command and conquer the first decade, i follow the instructions by clicking install and then and typing in the games name and finding the setup.exe, then clicking next. a dialog comes up saying its setting up and then an error comes up saying i need administrator privileges to run this program.

i'm the only user, i'm root AFAIK (i'm still pretty new to ubuntu and linux in general).

i'm running an XP3200+ 64 bit CPU on a Asus A8N-VM-CSM mobo. need any more info?

also, i was trying to install starcraft and i followed the steps i outlined above and it would come up with the window asking me if i wanted to install, install spawn, view previews, options, etc. i click install, it comes up with a EULA, and the window closes and then nothing else happens.

what am i doing wrong?

---

### Post by pay on 2007-01-11
If you want to gain root privileges, use sudo. If you install the game in /home/yourname/.cedega Then you shouldn't need root privileges.

---

### Post by Sonic Reducer on 2007-01-11
how would i use sudo with cedega though?

---

### Post by pay on 2007-01-11
You wouldn't want to use sudo with cedega, that's why i suggested installing the game into your home folder. You could also do ```
sudo chown -R username:username /path/to/game
```to gain the privileges needed.

---

### Post by Sef on 2007-01-11
Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo") as to why you don't want to run cedega (or any program) as root.

---

### Post by Sonic Reducer on 2007-01-16
i forgot to mention, but it might help you guys: when i did the hardware diagnostic when i first instaled cedega i failed the OpenGL direct rendering and the 3D acceleration simply doesn't run. it says i should wait a few minutes because it might take a while depending on my configuration, but nothing comes up even after fifteen minutes. whts going on with that?

---

### Post by Kilz on 2007-01-16
> **Sonic Reducer said:**
> i forgot to mention, but it might help you guys: when i did the hardware diagnostic when i first instaled cedega i failed the OpenGL direct rendering and the 3D acceleration simply doesn't run. it says i should wait a few minutes because it might take a while depending on my configuration, but nothing comes up even after fifteen minutes. whts going on with that?

Do you have the proprietary video drivers installed for your video card?

---

### Post by Sonic Reducer on 2007-01-16
its an asus A8N-VM-CSM mobo, i did an install with a brand new hard drive with an official ubuntu 6.06 CD. the drive had never been used before and i didn't install any extra drivers. are video drivers saved in the BIOS or something?

---

### Post by Kilz on 2007-01-16
> **Sonic Reducer said:**
> its an asus A8N-VM-CSM mobo, i did an install with a brand new hard drive with an official ubuntu 6.06 CD. the drive had never been used before and i didn't install any extra drivers. are video drivers saved in the BIOS or something?

From a search of that board it has nivida GeForce 6 integrated graphics. You may need to install the nivida drivers to get 3d acceleration. Unfortunatly I dont know much about installing the nvidia drivers since I have ATI graphics. But a search of the Ubuntu wiki or the forum should get you the info you need.

---

### Post by Sonic Reducer on 2007-01-16
so the drivers aren't in the HDD? i'll check everything out when i get home from school/work

my day has been great. i get up @ 8:30 after not being able to sleep (i was worried about my seeing my ex who i am still very much in love with and her new boyfriend at school the next day) for the first day of school. fight traffic for a half-hour in 28 degree F weather in a truck with a broken thermostat (coolant always circulates so the heater NEVER works) in order to get to school and run to the bookstore to drop $30 on a parking pass and run back out to my truck and convince the school cop that i was getting the pass and to not give me a ticket (he didn't though). then i finally find my engineering 22 class (not where it was posted it would be) where i was a half-hour late for but TDB for the teacher.

the class wasn't there, it doesn't meet until next week.

my next class wasn't until 2:00 so i fight my way back home in 30 degree F heat. i have to take a shower and get to school soon, then i get to come home, get dressed, and go to work.

---

### Post by Prometheum on 2007-01-16
I had pretty much the exact same problem as you, except I couldn't get anything to come up when  I whacked at install. 

One of the main problems is that Ubuntu uses dash as the default shell, and cedega needs bash. To fix this, do :
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh
(to see it it worked) ls -l /bin/sh

Also, you may need to install your driver's 32-bit compatible OpenGL libraries (dependant on your driver) and probably the 32-bit emulation libraries, which you can install by doing:
sudo apt-get install ia32-libs*

Once you've done all that, you apparently need to run cedega as root for some reason. I can't explain this, as nobody I've talked to has either. I assume the cedega people are trying to fix it (or just ignoring us and letting us rot in root).

---

### Post by BIGtrouble77 on 2007-01-16
Getting the proprietary nvidia drivers going is pretty important, I can't get anything working right without them.  If you are running Edgy then you have to do what Prometheum suggests.  I would not install it to your home directory because you may be just circumventing whatever the problem is.

I have cedega running well in dapper and edgy so it's probably just some weird config issue on your end.  You might want to remove it and reinstall.  I don't think you need the 32bit libraries, but you do need to force install it.

---

