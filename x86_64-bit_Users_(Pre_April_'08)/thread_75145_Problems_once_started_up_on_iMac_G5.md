---
title: "Problems once started up on iMac G5"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by zedwards on 2005-10-13
I have posted a problem in bugzilla but have yet to hear anything from it. [http://bugzilla.ubuntu.com/show_bug.cgi?id=17272](http://bugzilla.ubuntu.com/show_bug.cgi?id=17272)

I have a 2.0 Ghz iMac G5 with Breezy installed. After the command prompt comes
up (I have removed the gdm startup thinking this may be an X problem) I am able
to log in, but then maybe 20 seconds later, the prompt will freeze and I cannot
enter anything in. I have been able to quickly log in and update my computer and
everything will work fine, but about 20 seconds after the update/upgrade
completes, it freezes. After waiting for a minute or so, I will get these errors
at the prompt:

ata1; command 0x35 timeout, stat 0x50 host_stat 0x4
mpic_enable_irq timeout

and it will repeat and I have to force a reboot by powering off

---

### Post by slaine on 2005-10-13
I can confirm having the same problem on a rev A iMac G5 1.8GHz (The one with the nVidia gfx).

This happened with one of the later Breezy colony CD's (it could have been the preview releas).

Most frustrating as I was looking forward to have a Linux partition on this lovely machine.

--
slaine

---

### Post by farmer on 2005-10-13
Thirded. Is there a bug on this?
 
 
17" 1.8 GHz SuperDrive iMac G5 rev. A. I'm guessing it's USB support. It works, and then it shuts off. Its a kernel problem.
 
I tried Gentoo when their 2004.3 PPC64 livecds came out, and I could log in, and then I emergeed gnome. The output kept scrolliong across the screen, but the keyboard didn't work. Most def. USB support in the kernel.
 
You can use the kernel from the gentoo 2004.3 imacg5 livecd from dev.gentoo.org/~tgall/ .

---

### Post by Smeggy on 2005-10-13
Same problem here with a PowerMac G5 tower (DP 1.8ghz)

---

### Post by zedwards on 2005-10-17
I posted a bug, yet has not been confirmed. I have noticed someone posting that they are running a g5 imac, so I guess it is possible? funny, my first imac (G3 500 mhz DV SE) i had issues with linux and now with my new one, things just don't quite work. Very annoying because this is one sweet machine.

---

### Post by LudovicRousseau on 2005-10-18
I also have the same symptoms :( . I have an iMac G5 20" 2Ghz.

After some search/tries I discovered that the freeze occurs when a sound is played (or tried to). It is the case when gdm is started. It is also the case on the console if you use Tab for the completion and the shell wants to beep.

I found a work-around for now:
[LIST]
[*] boot using "Linux single" so gdm is not started
[*] do not use tab on the console
[*] disable sound in gdm by setting
[/LIST]
SoundProgram=/bin/true
#SoundOnLogin=true

I can now log in :razz:

---

### Post by mnasimh on 2005-10-19
I tried with Linux single but still it doesn't find keyboard. I think it's USb keyboard problem!

---

### Post by zedwards on 2005-10-25
What keyboard are you using? I have been able to follow Ludovic's suggestions, and log in using Blackbox using startx (and blackbox in the xinitrc file). So I can at least experience some ubuntu goodness! That is, until I type the tab key.

---

