---
title: "freezy badger?"
date: 2005-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by fassan on 2005-10-23
:KS First- Like many I had several freezes when I first installed.  I would get tinto X, but never all the way into KDM.  This was a graphics problem, easily solved by installing the Nvidia driver and adjusting xorg.conf.  Just writing this incase anyone else is still trying to fix that problem.

:( I was having a strange problem where I would go away for five minutes or more and when I came back, I was back at the login screen.  I found out that open GL was crashing my screen saver and resetting X.  So, I disabled composite.  Has anyone else had success with composite and having it be fairly stable.? if not...it is just eye candy and not mission critical, *but I would like to use it*.

:confused: I still have one freezing issue - I think that it has to do with ACPI.  When I am away for extended peiods of time, and maybe that is more than 15 minutes or maybe it is more than an hour...my computer will not respond.  No keyboard, mouse, nothing - well except the unfortunately useful reset button.  I would try disabling ACPI, but I need a few things(maybe they are not part of acpi, but I think they are...)  I need the monitor blanking, both to save wear on the monitor and so that my wife can sleep at night.  The second one I have found a suggestion for was stopping /etc/init.d/powernow.d- only thing is, this causes some nasty ringing in amarok, or perhaps that is tha machine itself?  So, I need the powernow daemon to throttle CPU when not being fully used.  I hope there is a way to fix it, maybe in the kernel, or maybe bey editing a config...unfortunately I never know what I am looking at in init scripts and the like.  

If it helps:
Nforce 4 mobo
AMD64 dualcore
latest kubuntu smp kernel (with restricted drivers)
sb audigy(emu10k1)
Madwifi
Nvidia geforce 6600 

Thanks

---

### Post by Drain on 2005-10-23
[QUOTE=fassan]:( I was having a strange problem where I would go away for five minutes or more and when I came back, I was back at the login screen.  I found out that open GL was crashing my screen saver and resetting X. [/QUOTE]

It says right up front in this [forum thread]("http://ubuntuforums.org/showthread.php?t=75527") that OpenGL screensavers and composite effects do not mix. (Bug #4, I believe) I imagine that you can just set the screensaver to "blank screen", and keep the composite effects if you'd rather have the eye candy when you're actually using your computer. 

All I can say about the ACPI issues are to try and turn it off and see if you can live without it. My monitor goes into standby/idle without ACPI installed.  

I have no idea what's going on with the powernowd/amaraok problem - could you give a better description?

---

### Post by fassan on 2005-10-23
The powernow thing isn't really an amarok problem- It's just that when I turn it off and let the CPU stay at 2000, I get a really high pitched squeel from the tower case, maybe it's a fan or something.  Still, I like to not hear that sound.

Thank you for quick replies- If I can still use openGL in games and composite in X, I don't care about the screensaver.  It's blanked out more often than screen savered.

I hav just stopped the /etc/init.d/acpid service.  We'll see how it goes.

Thanks for the help- I've been using linux < 1` year and I am trying to be more informed, or at least less ignorant.

---

### Post by fassan on 2005-10-24
Update- I ran ```
/etc/init.d/acpid stop 
```- I think it may have helped, but my computer still froze up - maybe it is wifi related?

---

