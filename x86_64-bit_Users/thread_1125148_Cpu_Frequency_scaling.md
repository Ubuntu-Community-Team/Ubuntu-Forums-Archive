---
title: "Cpu Frequency scaling"
date: 2009-04-14
forum: x86 64-bit Users
---

### Post by wfp on 2009-04-14
So I am on a desktop not a laptop for one thing. Not sure how this works. I added cpu frequency scaling to my panel.  It says cpu is set to on demand which is 1Ghz and its running at about 45%. If I run lshw from a terminal it list my cpu as a 1Ghz processor. Not to sound like a smart *** but if i wanted a 1Ghz processor I would be using my old pentium. Is there any way to set the processor to use it full 2.2Ghz. I do a lot of heavy photo editing so would like to take advantage of cpu. Oh just to let you know I am on jaunty64 can not post in jaunty forum. But was getting same error message with Hardy-lts

---

### Post by orethrius on 2009-04-14
First thought, which I'm sure isn't the problem, is that CPU Frequency Scaling Monitor is running so that you can select the mode, right?  On-demand will only run at 1 GHz until more is needed, unless...

Second thought, **noapic** needs to be in your /boot/grub/grub.conf file after your current kernel line (**uname -r** will give you the current kernel version; **gksudo gedit /boot/grub/grub.conf** should show some options and allow you to make the necessary changes).  If you have **nolapic** in there, it may cause problems with your chipset.

(Source: [http://happylinuxthoughts.blogspot.com/2007/09/linux-cpu-frequency-scaling.html](http://happylinuxthoughts.blogspot.com/2007/09/linux-cpu-frequency-scaling.html))

---

### Post by wfp on 2009-04-14
thanks for the reply will look more into it.

---

### Post by wfp on 2009-04-14
Hey thanks again I figured it out. Gee I am such a Noob at times.

---

### Post by wfp on 2009-04-15
So I added acpi=off to my kernel re-booted and cpu's are at 2.2Ghz. I noticed temps are higher but no where near being dangerous. Checked the air coming out of my box and it's cool. So used to runing intel processors where you can fry and egg on your box. Any way are there any drawbacks from having acpi=off.

---

### Post by youph on 2009-04-15
The kernel is smart enough to clock the CPU up as load increases and when idle to scale down in increments defined by the CPU. This design is more efficient than always clocking the CPU at max frequency which uses more power and more importantly creates more heat. For example, my athlon 3.0ghz x2 idles @ 1 ghz. The other possible states are 1.8 - 3.0 in 200 mhz increments. Generally my system stays at 1 ghz (still io bound with a raptor) but will peg the cpu @ 3.0 ghz for short bursts; rarely do I see the in between states.

People seem to get freaked out when they cat /proc/cpuinfo and see a fraction of the hertz they paid for :lolflag: but I can understand the confusion.

Other CPUs (phenom) allow for individual cores to be scaled independently of each other and can even be halted individually giving much more power & heat savings. You wouldn't want a classic phenom to sit spinning its 4 cores in a polling loop @ 2.8 ghz now would you? So the point is don't worry and let the on demand governor to do its thing to keep your power draw and temps down.

---

### Post by wfp on 2009-04-15
Thanks for the reply the problem is I get this message when grub loads>   1.can't evaluate _CRS: 12298<6>pnp: PnP ACPI: found 12 devices. I found that even on a heavy load the cpu would stay at a constant 1Ghz. One problem was I could not play any flash full screen. My second problem was that if I had desktop effects enabled the desktop would lock up right away. With acpi off flash plays great now at full screen and desktop effects are working great. I am on jaunty64 just to let you know can not post in jaunty forum at this time. Was getting same error message with Hardy-lts thou.

---

### Post by youph on 2009-04-15
Sounds like a chipset issue. When on demand is working (sounds like you have a bad driver or funky configuration) there is no noticeable difference in performance between enabling or disabling the governor. The transition latency is on the order of microseconds (I'm sure there are some corner cases where this latency is exposed but not in my experience.) Also, lots of work loads are io bound so you'll see the CPU sometimes @ 100% usage in the wait/poll state waiting for io to complete, On demand will not throttle up (in my experience) if its blocking on io. But realistically since you're running a desktop, power draw is probably less a concern for you. I would be more concerned about my temps and increased wear on the CPU, but if you gotta turn off acpi off to get a stable system you don't have much of a choice. I'm not familiar with that error message, sorry I can't help but you may learn a whole lot if you try and find the root device or conflict causing the issue.

---

### Post by wfp on 2009-04-15
Hey thanks again for replying. I did recently install the new nvidia beta driver 185.19, but I was having same issues with the 180 driver. I will keep a close look at my temps thou. I Have the latest bios update not sure why I am getting those errors. Any way have a good night.

---

### Post by Yellow Pasque on 2009-04-15
I personally disagree with not using CPU scaling for the sake of performance, but I digress...

You shouldn't turn off ACPI unless it's causing a problem. In fact, you shouldn't be messing with grub or passing kernel parameters just to turn off CPU scaling (then again, you might be the type that enjoys destroying twigs with a chainsaw).

This command should do what you want:
```
sudo cpufreq-set -g performance
```

If you want it to run at every boot, add it to /etc/rc.local (that script runs as root, so you don't need 'sudo' there). I think that'll do the trick.
If it doesn't work, maybe editing /etc/init.d/cpufrequtils and changing the GOVERNOR= line from ondemand to performance will.

EDIT: do you still have *noapic* in your menu.lst?

---

### Post by luckykar on 2009-04-15
If you dont want cpu scaling just remove the package powernowd:
sudo apt-get remove powernowd

If you want it back again just reinstall it:
sudo apt-get install powernowd

I would not be playing with the grub or kernel parameters...as Temujin has pointed out.

Just remove the package and be done with it.

---

### Post by wfp on 2009-04-15
Thanks again for all your replies. I Turned acpi back on to play it safe. Thanks for the performance code.

---

