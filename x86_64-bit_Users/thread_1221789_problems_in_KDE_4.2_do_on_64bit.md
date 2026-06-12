---
title: "problems in KDE 4.2 do on 64bit?"
date: 2009-07-24
forum: x86 64-bit Users
---

### Post by Grobsy on 2009-07-24
Hello,
I recently installed ubuntu 9.04 64bit. Later i installed KDe 4.2 on my computer. I like 9.04, and i don't have any problems on GNOME, but on KDE i have a lot of problems. Sometimes, especially when i watch a video, listen to music or change my KDE settings, my UI disappears, comes back again and that over and over. Sometimes KDE just wont start up, while GNOME runs fine. 
So how is KDE doing in combination with 64bit? 
And would it be better for me to go back to 32bit? 
Would going back to 32bit solve my KDE 4.2 problems? 
I would like to know if the problem is somewhere on my side or on the side of kDE/Ubuntu/64bit.
A simple solution would be to just run GNOME, but I'm a big KDE fan, and willing to have some trouble to run it.

I have a Ati Radeon 4850, with propietary drivers
AMD Athlon 64 6000+ and 4 GB ram

Oh, and im sorry for my bad English, it isn't my native language :P

---

### Post by markbuntu on 2009-07-24
Since you have installed KDE4 over gnome, you should read this to help with your sound issues.

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

---

### Post by Grobsy on 2009-07-25
It not just sound issues, i have issues all over the place. Sometimes KDE just crashes, or won't start up, or will only start up if i launch GNOME first. Crashes Always happen if i change my effects settings in the control panel.

---

### Post by mgranet on 2009-07-25
It sounds like plasma crashing. I have the same problem, from time to time (it seems to come and go). Very annoying, to say the least. Atleast it fixes itself after a few seconds.

It seems to be a Kubuntu problem, as I have no similar problems in any of my other KDE4.2 distros.

---

### Post by Grobsy on 2009-07-25
well, with me it doesnt fix in a few seconds. If its plasma it keeps itself turning on and off and i have to turn the power off to stop my computer.

---

### Post by mgranet on 2009-07-25
Ugh. That's an ugly way to do things, and a quick way to trash a filesystem. You can try Ctrl-Alt-Backspace if you have dontzap disabled. This will restart your X-server, dropping you back to the login screen. 

Alternatively, you can try Ctrl-Alt-F1 to drop to a console to try a sudo reboot. If it's truly locked, Press and hold Ctrl-Alt-PrintScreen/SysRq, then type in reisub, waiting a dozen seconds or so between each letter to let it do it's thing. This will sync, unmount, and reboot for you without damage to the filesystem. It's hard to hold all the keys, so I usually enlist the help of my nose.

As for the original problem, it seems unusual. Are you running the proprietary drivers from the Hardware Drivers app/repos, or did you manually install the latest one from the nvidia website?

EDIT: Also, one can't overlook the possibility of this occurring because you added KDE onto an existing Ubuntu install. It's been my experience that KDE4 likes to play alone. You may want to even consider a re-install with native Kubuntu if nothing else helps. Or you can just keep Ubuntu, and then run Kubuntu in a virtual machine, or vice-versa. It's what I do, and it works very nicely.

---

### Post by Grobsy on 2009-07-25
From Hardware drivers.
All other Desktop enviroments work fine, except KDE. Is it because i had a messy install of KDE? Is it because i use 64bit?

---

### Post by mgranet on 2009-07-25
See my edit in the above post

---

### Post by mgranet on 2009-07-25
Also, there have been a lot of fixes for KDE4 problems in the later Nvidia driver releases. You could try to uninstall the repo version from your package manager, then install the one from the nvidia website. It might help.

---

### Post by Grobsy on 2009-07-25
EDIT: I'm installing Kubuntu 64-bit now, how this works better and that I don't have to switch to 32-bit

---

### Post by markbuntu on 2009-07-25
Do you have the latest driver from ati?
the one in the repos is not so good.

---

