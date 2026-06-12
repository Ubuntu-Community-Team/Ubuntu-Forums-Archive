---
title: "First bumpy night of Kubuntu"
date: 2007-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by enderandrew on 2007-06-27
Howdy, I've been using Gentoo for a few years, but my wife never had the patience for compiling.  Finally I convinced her to dump Windows on her laptop and we installed Kubuntu yesterday.  So far we have had nothing but problems.  I'm hoping you guys can help me out.

1 - The binary ATI driver is not loading correctly.  DRI is failing and when I run fglrxinfo I'm getting the Mesa error.  We have a Radeon X300 on her laptop, and I followed the following guide, including the so called "mesa-fix".

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

2 - There appears to be no package for the sun-java6-plugin, nor a sun-java5-plugin on x64.  Given that Sun has always supported x64, and most of the Sun Java code is GPL'ed now, I found this disheatening, especially when all the documentation and forum posts I've found keep saying just "apt-get install sun-java6-plugin".  I'd sure like to if the package existed for me.

3 - Kicker, Krunner, and Kdesktop have each crashed at least twice in the first 24 hours.  I updated to the latest KDE, and still we've had crashes.  memtest is good, and the HDD is good as far as I know.  We never really had any problems with apps crashing in Windows x64.

4 - We've had all kinds of crazy issues with her touchpad and the keyboard.  I'm not sure if this is Xorg or the Kernel, but I may trying upgrading the kernel later.  Her touchpad isn't very responsive, and again we didn't have any issues with it in Windows.  If we hit a key on the keyboard, often it will pause, repeat ten times, or not repeat when we want it to.  If you hold down backspace, it won't repeat at all for instance.  When I'm typing, I'll randomly get ten t's in a row.  However, at times I will be tapping left repeatedly on the console, and waiting as it takes a few seconds before the cursor moves.

5 - This may be a Windows issue, but I have a printer shared on a Win2k box, which is a temporary thing, trust me.  However, I'm upgrading all the hardware in my desktop, and I'm waiting on the time to reinstall Windows x64 and Gentoo on my new desktop.  In the mean time, I needed a box up to share files and printers, so I put up one of my old clunkers.  From Windows I could see the Printer shared, but in Linux, I can only see the file folders shared, and not the printer.

6 - I know this is vague, but overall performance and system responsiveness has been a bit disappointing.  OpenOffice in particular loads incredibly slow.  Honestly, I may just build a new toolchain with some of the Suse patches, and then compile OpenOffice with the -Bdirect flag, because we tried Suse briefly, and OpenOffice did load quicker on that.  A big reason for choosing Kubuntu is that we heard it was supposed to be a very fast distro.  Are there any guides for speeding up Ubuntu/Kubuntu out of the box?

As a suggestion, I would have liked to see either Reiser4 or Ext4 support.  Your HDD is often the slowest component on your computer, and using a fast FS can and does make a difference.

I hate to sound so negative.  My wife loves KDE and is eager to learn Linux.  However, we're hoping we can find solutions for some of these problems.

---

### Post by kuja on 2007-06-27
> **enderandrew said:**
> Howdy, I've been using Gentoo for a few years, but my wife never had the patience for compiling.  Finally I convinced her to dump Windows on her laptop and we installed Kubuntu yesterday.  So far we have had nothing but problems.  I'm hoping you guys can help me out.

1 - The binary ATI driver is not loading correctly.  DRI is failing and when I run fglrxinfo I'm getting the Mesa error.  We have a Radeon X300 on her laptop, and I followed the following guide, including the so called "mesa-fix".

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

2 - There appears to be no package for the sun-java6-plugin, nor a sun-java5-plugin on x64.  Given that Sun has always supported x64, and most of the Sun Java code is GPL'ed now, I found this disheatening, especially when all the documentation and forum posts I've found keep saying just "apt-get install sun-java6-plugin".  I'd sure like to if the package existed for me.

3 - Kicker, Krunner, and Kdesktop have each crashed at least twice in the first 24 hours.  I updated to the latest KDE, and still we've had crashes.  memtest is good, and the HDD is good as far as I know.  We never really had any problems with apps crashing in Windows x64.

4 - We've had all kinds of crazy issues with her touchpad and the keyboard.  I'm not sure if this is Xorg or the Kernel, but I may trying upgrading the kernel later.  Her touchpad isn't very responsive, and again we didn't have any issues with it in Windows.  If we hit a key on the keyboard, often it will pause, repeat ten times, or not repeat when we want it to.  If you hold down backspace, it won't repeat at all for instance.  When I'm typing, I'll randomly get ten t's in a row.  However, at times I will be tapping left repeatedly on the console, and waiting as it takes a few seconds before the cursor moves.

5 - This may be a Windows issue, but I have a printer shared on a Win2k box, which is a temporary thing, trust me.  However, I'm upgrading all the hardware in my desktop, and I'm waiting on the time to reinstall Windows x64 and Gentoo on my new desktop.  In the mean time, I needed a box up to share files and printers, so I put up one of my old clunkers.  From Windows I could see the Printer shared, but in Linux, I can only see the file folders shared, and not the printer.

6 - I know this is vague, but overall performance and system responsiveness has been a bit disappointing.  OpenOffice in particular loads incredibly slow.  Honestly, I may just build a new toolchain with some of the Suse patches, and then compile OpenOffice with the -Bdirect flag, because we tried Suse briefly, and OpenOffice did load quicker on that.  A big reason for choosing Kubuntu is that we heard it was supposed to be a very fast distro.  Are there any guides for speeding up Ubuntu/Kubuntu out of the box?

As a suggestion, I would have liked to see either Reiser4 or Ext4 support.  Your HDD is often the slowest component on your computer, and using a fast FS can and does make a difference.

I hate to sound so negative.  My wife loves KDE and is eager to learn Linux.  However, we're hoping we can find solutions for some of these problems.
Java was only recently GPL'd, Java 5 and Java 6 aren't GPL'd, the not yet released Java 7. 
ATI's drivers are lousy, I don't trust them. Heck, I have half the mind to blame them for crashes after some of the stuff I've heard about. Weird crashes and freezes and such. 
Perhaps setting up prelink could help with the OpenOffice slowness, though, I'd expect it to be a bit slow on a laptop to begin with. (prelink would make it load much faster after the initial load).
If the overall performance is a bit sluggish, perhaps a lightweight install would run better. People have found that starting from the ground up rather than using the kubuntu-desktop package results in much better responsiveness. ("sudo apt-get install kde-core xorg xserver-xorg kdm" would be a good place to start if you're working from the ground up)

---

### Post by enderandrew on 2007-06-27
I've only used Mandrake (years back before it was Mandriva), Suse and Gentoo before.

Honestly I was a little shocked Kubuntu simply installed without asking me what packages I want or don't want.  I imagine if I poke or prod, there are some packages I can remove to remove some cruft.

I plan on disabling some unnecessary services, checking the journaling settings on ext, checking the hdparm settings, etc.

Too bad I don't think recent kernels allow you to set vm.swappiness anymore.

The big things are discovering why input is so screwy, getting Java and Flash to work in Firefox, and getting her to print.

The input one I'm not sure about.  I'm running xorg-7.2 with the proper input drivers.  I'm planning on upgrading kernels as soon as Andrew Morton puts out a new -mm kernel with the latest CFS fixes.  I like living fairly bleeding edge.

The printing thing may be a Windows issue, because sharing (Windows samba support) changed significantly between 2k and XP.

The ATI driver isn't a big deal, except I was talking up all the nifty 3D desktop tricks Linux can do these days, and as far I know, you need the binary drivers to get DRI and all the nifty beryl tricks.  I don't bother with them personally, but she'd like to see them.

---

### Post by michaelzap on 2007-06-27
Are you running the 64-bit version of Kubuntu? If so, you may find that many of your issues magically disappear if you install the 32-bit system instead. I'm running 32-bit Ubuntu on a Core 2 Duo, and given how amazingly fast it runs, how easy setup was, and how many horror stories I've heard about people trying to get the 64-bit version to work right for them, I don't have any plans to switch.

---

### Post by enderandrew on 2007-06-27
> **michaelzap said:**
> Are you running the 64-bit version of Kubuntu? If so, you may find that many of your issues magically disappear if you install the 32-bit system instead. I'm running 32-bit Ubuntu on a Core 2 Duo, and given how amazingly fast it runs, how easy setup was, and how many horror stories I've heard about people trying to get the 64-bit version to work right for them, I don't have any plans to switch.

Yep.  I don't get the logic however that the 32-bit version should run faster.  If that is the case, then I imagine the 64-bit binaries were poorly constructed.

---

### Post by jespdj on 2007-06-27
> **enderandrew said:**
> 1 - The binary ATI driver is not loading correctly.  DRI is failing and when I run fglrxinfo I'm getting the Mesa error.  We have a Radeon X300 on her laptop, and I followed the following guide, including the so called "mesa-fix".
Unfortunately the ATI video drivers for Linux are still crappy... :(

> **enderandrew said:**
> 2 - There appears to be no package for the sun-java6-plugin, nor a sun-java5-plugin on x64.  Given that Sun has always supported x64, and most of the Sun Java code is GPL'ed now, I found this disheatening, especially when all the documentation and forum posts I've found keep saying just "apt-get install sun-java6-plugin".  I'd sure like to if the package existed for me.
Unfortunately, Sun does not provide 64-bit Java plug-ins (not for Linux and not for Windows). However, you could run a 32-bit browser and use the 32-bit Java plug-in on your 64-bit system. Look around the forums for guides on how to install that.

---

### Post by enderandrew on 2007-06-27
My wife tried following the guide to do a ndiswrapper around Flash and couldn't get that to work, so really the 32-bit version of Firefox sounds like the best bet on all accounts.

---

### Post by praxis22 on 2007-06-27
[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

[http://onlyubuntu.blogspot.com/2007/03/performance-tip-for-ubuntu-edgy-and.html](http://onlyubuntu.blogspot.com/2007/03/performance-tip-for-ubuntu-edgy-and.html)

[http://www.goitexpert.com/entry.cfm?entry=Speed-Up-UBUNTU-704-Startup-Time-On-Your-Laptop](http://www.goitexpert.com/entry.cfm?entry=Speed-Up-UBUNTU-704-Startup-Time-On-Your-Laptop)

Oh, and while you're at it:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Stay away from the proprietary ATI drivers, nothing but trouble.

---

### Post by crjackson on 2007-06-27
> **praxis22 said:**
> [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

[http://onlyubuntu.blogspot.com/2007/03/performance-tip-for-ubuntu-edgy-and.html](http://onlyubuntu.blogspot.com/2007/03/performance-tip-for-ubuntu-edgy-and.html)

[http://www.goitexpert.com/entry.cfm?entry=Speed-Up-UBUNTU-704-Startup-Time-On-Your-Laptop](http://www.goitexpert.com/entry.cfm?entry=Speed-Up-UBUNTU-704-Startup-Time-On-Your-Laptop)

Oh, and while you're at it:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Stay away from the proprietary ATI drivers, nothing but trouble.

Thanks for the tweaks - I'm concerned about the HD tweak where it speaks of corrupting the data.

I have 4 systems with ATI video cards - it sounds like more hastle than it really is.  They run smooth but I can't use desktop effects or Beryl.

---

### Post by praxis22 on 2007-06-27
I run an AGP X800XT and I run Beryl without problems, using the Radeon driver.

---

### Post by crjackson on 2007-06-27
> **praxis22 said:**
> I run an AGP X800XT and I run Beryl without problems, using the Radeon driver.

Perhaps you could tell me how to set that up.  I'll start a new thread with your handle in the title so as not to infringe on someone elses therad.

---

### Post by praxis22 on 2007-06-27
> **crjackson said:**
> Perhaps you could tell me how to set that up..
[http://ubuntuforums.org/showthread.php?p=1837517#post1837517](http://ubuntuforums.org/showthread.php?p=1837517#post1837517)

---

### Post by enderandrew on 2007-06-27
> **praxis22 said:**
> [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

[http://onlyubuntu.blogspot.com/2007/03/performance-tip-for-ubuntu-edgy-and.html](http://onlyubuntu.blogspot.com/2007/03/performance-tip-for-ubuntu-edgy-and.html)

[http://www.goitexpert.com/entry.cfm?entry=Speed-Up-UBUNTU-704-Startup-Time-On-Your-Laptop](http://www.goitexpert.com/entry.cfm?entry=Speed-Up-UBUNTU-704-Startup-Time-On-Your-Laptop)

Oh, and while you're at it:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Stay away from the proprietary ATI drivers, nothing but trouble.

Can you get DRI and acceleration with the open-source drivers.  I was under the impression you couldn't.

Thank you very much for the links.  I'll check them out when I get home from work.

---

### Post by praxis22 on 2007-06-28
Yes, provided you're using MesaGL, check the link to my "Beryl howto" entry above. the Open Source Radeon drivers have "experimental" 3D support for my card, but to be honest I don't use it, it's easier to just brute force it with the CPU:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

> 
This is what I get out of xdriinfo:

xdriinfo
Screen 0: r300


---

