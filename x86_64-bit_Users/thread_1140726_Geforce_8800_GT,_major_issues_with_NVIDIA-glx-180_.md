---
title: "Geforce 8800 GT, major issues with NVIDIA-glx-180 driver"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by spiritfox on 2009-04-27
I just installed Ubuntu 9.04 after a short stint with OpenSuSE.  In 8.10, the nvidia 177 driver worked fine.  Now that option has been removed, and we're left with the 173 or the 180.  Both drivers cause serious problems on my machine.  I initially had the same issue as [http://ubuntuforums.org/showthread.php?t=1136343](http://ubuntuforums.org/showthread.php?t=1136343) but after following the instructions of TheLions on that thread, that has since been replaced by a screen that, after maybe 10 minutes of use, shows up with pretty, stripey colors splotched over certain windows, ridiculous lag, and unsolicited logouts.  Does anyone know a: if it is possible to revert to the 177 driver or b: fix these issues?  It seems a lot of people with the 8800 GT are having problems.

---

### Post by bhtek on 2009-05-06
I am having a similar problem with my GeForce 7900 GT/GTO... have you found a solution yet?

---

### Post by dabl on 2009-05-06
> **spiritfox said:**
> 

Now that option has been removed, and we're left with the 173 or the 180.  


Au contraire -- you can certainly download and install the Beta driver, 185.18.08.  The release notes for it have some interesting bug fixes.

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

---

### Post by Artemis3 on 2009-05-06
I wonder what your gpu temp is (install nvclock)... Never had these problems on mine.

---

### Post by Raguster on 2009-05-07
I have a 8600gts and have tried all the applicable drivers. I'm on the 185 driver and still get black screens after the slash screen. 

I looked up my xorg.config file and it doesn't look right, after referencing examples. I have various other xorg.config files that have numbers appended to them and they look correct. I think renaming one of the file with the appended number  to xorg.config will work but I can't. The properties of these file say that they are property of the root user. **How can I edit the files then?  **

---

### Post by hiflyer on 2009-08-01
I forgot to add I have a GeoForce 7500 le

---

### Post by hiflyer on 2009-08-01
In another thread on complete system lockup I have posted this. I know it does not agree with the above but...

I also get the complete system lockup. I have not noticed any harddrive problems. This machine has been upgrade since version 6 of ubuntu with out being totally reinstalled. It is an AMD 64 bit hp unit and was working fine under Intrepid with GeoForce 7500 LE. Since the Upgrade to 9.04 it has been locking up. My solution I am testing is to downgrade to the NVIDIA 173 driver. while I have only short term testing (couple hours so far), it has not locked up. I find if I turn on the Matrix screen saver under 180 driver it will lock up in seconds. It did not lock up under 173 driver.

you might try this and see if it helps.

---

### Post by gila_monster on 2009-08-01
Just a thought for you folks -- I, too, had trouble with the system under GNOME and some with KDE. Upgrading to the 185 driver seemed to help. Upgrading to the 2.6.29 kernel ALSO seemed to help. There are issues in some versions of the 2.6.28 kernel that may be part of the equation.

I'm currently running Xubuntu (yes, went through GNOME, KDE, and XFCE all in a three-week period, long story), and it installed an upgraded 2.6.28, and things seem fine with that kernel and the 180 driver. Of course, Xubuntu does not use Compiz or pound the GPU particularly heavily, and that may matter.

Best of luck.

---

### Post by hiflyer on 2009-08-01
well, 173 did eventually fail as it has for others. I am now trying 185. I have had 1 lockup with 185 when playing with the screen saver. So I turned screen saver off and see how things go.

I will note that 180 is the most likely version of the 3 to lock up on my machine.

#-o

---

### Post by saviger on 2009-08-02
I had a similar problem with mine. It was a problem with SLI. here is the thread: [http://kubuntuforums.net/forums/index.php?topic=3105042.0]("http://kubuntuforums.net/forums/index.php?topic=3105042.0") I posted my working xorg.conf file when I go it working.

---

