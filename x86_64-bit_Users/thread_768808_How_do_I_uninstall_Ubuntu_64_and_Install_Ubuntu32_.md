---
title: "How do I uninstall Ubuntu 64 and Install Ubuntu32 instead?"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by puifais on 2008-04-26
I recently decided to try out linux and installed Ubuntu 64 on my computer since it has an AMD Athlon 64 processor.  I found out later on about the small problems this version has in comparison to the 32 bits.  I really don't care that 64 has more processing power or whatever.  I just want to get the 32 on since it seems to be less problematic especially at getting programs to work.  How do I uninstall 64 and put 32 on?  I downloaded+burnt the ISO CD for 32 bits (correctly).  Once I put the CD in, my current Ubuntu64 doesn't run this CD unlike the old Windows XP I had.  Since my computer only has Ubuntu now, I can't just try to run this from my windows partition since I didn't want to keep me windows and did not keep it...  I tried to restart the computer while the CD is in the tray but the trick didn't do its magic :(

Any ideas?  Man, I feel like an idiot!

---

### Post by John.Michael.Kane on 2008-04-26
> **puifais said:**
> I recently decided to try out linux and installed Ubuntu 64 on my computer since it has an AMD Athlon 64 processor.  I found out later on about the small problems this version has in comparison to the 32 bits.  I really don't care that 64 has more processing power or whatever.  I just want to get the 32 on since it seems to be less problematic especially at getting programs to work.  How do I uninstall 64 and put 32 on?  I downloaded+burnt the ISO CD for 32 bits (correctly).  Once I put the CD in, my current Ubuntu64 doesn't run this CD unlike the old Windows XP I had.  Since my computer only has Ubuntu now, I can't just try to run this from my windows partition since I didn't want to keep me windows and did not keep it...  I tried to restart the computer while the CD is in the tray but the trick didn't do its magic :(

Any ideas?  Man, I feel like an idiot!

First you might want to make sure you have boot from cd set in your system bios.

Second you might want to make sure you have burn the cd correctly, and it is not a bad burn.

Third depending on the iso you downloaded one allows you to install direct to disc during the boot, and the other is a live/install cd which can also install the OS.

Fourth since this seems to be your first post in this part of the forums would mind explain exactly what problems you are having with the 64bit version of Ubuntu. The reason I ask this is it may be possible to fix your issues  if you explain to the forum members what the issues are.

Also depending on the issue you are have with 64bit you may have those same issues under 32bit.

---

### Post by puifais on 2008-04-26
> **John.Michael.Kane said:**
> First you might want to make sure you have boot from cd set in your system bios.

Second you might want to make sure you have burn the cd correctly, and it is not a bad burn.

Third depending on the iso you downloaded one allows you to install direct to disc during the boot, and the other is a live/install cd which can also install the OS.

Fourth since this seems to be your first post in this part of the forums would mind explain exactly what problems you are having with the 64bit version of Ubuntu. The reason I ask this is it may be possible to fix your issues  if you explain to the forum members what the issues are.

Also depending on the issue you are have with 64bit you may have those same issues under 32bit.

1.  I'm not sure what you mean by system bios.  I just put the CD in, nothing happened--no menu that lets you select to boot from the CD or anything, so I just restarted the computer with the CD in the tray.

2.  I definitely burnt it correctly and it was not a bad burnt.

3.  I got the live/install CD.

4.  My issue with the 64 version is that a whole bunch of programs are not available for this version.  I looked around and found that they can be easily fixed by inputting a 1-line command for each program I want (such as VLC for instant).  I know it's not that difficult but it'll just be a little fixing here and there all the time and I don't want to deal with that since the tradeoff is higher processing power, which I really don't care about.  I use this particular desktop for stuff like watching a movie, checking email, etc.  I don't even burn a DVD or play games on it so there's no need.  I use a different computer for stuff like Matlab and burning DVD or whatever, so the desktop doesn't need to be that sophisticated to serve its purpose.

Thank you for your help.

---

### Post by mobiryder on 2008-04-26
JMK,
I can tell you one very big reason I'm considering moving to 32 bit version also, and it's a fatal reason, Flash.

I've yet to find someone post how to make flash work on x64 ubuntu... does a way exist?  if so, is there a beginner's explanation of how to pull this off?

thx

Mobi
[Forgoing.com]("http://forgoing.com") Newbies Ubuntu blog

> **John.Michael.Kane said:**
> First you might want to make sure you have boot from cd set in your system bios.

Second you might want to make sure you have burn the cd correctly, and it is not a bad burn.

Third depending on the iso you downloaded one allows you to install direct to disc during the boot, and the other is a live/install cd which can also install the OS.

Fourth since this seems to be your first post in this part of the forums would mind explain exactly what problems you are having with the 64bit version of Ubuntu. The reason I ask this is it may be possible to fix your issues  if you explain to the forum members what the issues are.

Also depending on the issue you are have with 64bit you may have those same issues under 32bit.

---

### Post by Sef on 2008-04-26
> I've yet to find someone post how to make flash work on x64 ubuntu... does a way exist? if so, is there a beginner's explanation of how to pull this off?

Read [this]("http://ubuntuforums.org/showthread.php?t=765780").

---

### Post by thekat on 2008-04-26
> **mobiryder said:**
> JMK,
I can tell you one very big reason I'm considering moving to 32 bit version also, and it's a fatal reason, Flash.

I've yet to find someone post how to make flash work on x64 ubuntu... does a way exist?  if so, is there a beginner's explanation of how to pull this off?



This doesn't work for you..??
I have done this 2 times on 2 installs..
```

sudo apt-get install flashplugin-nonfree

```
If Firefox is open close it and restart it.. 


Unfortunately I have to run 64-bit and Flash was my big concern..
No longer an issue in this release..

---

### Post by pixel :-) on 2008-04-26
1. I'm not sure what you mean by system bios. I just put the CD in, nothing happened--no menu that lets you select to boot from the CD or anything, so I just restarted the computer with the CD in the tray

When the computer starts.It says somewhere press *** to enter setup.Or something like that,it's very brief,just at the begining of the boot,usally it's DEL,but depending on your machine it could be many other things.Once you are in the setup(or bios) look for boot sequence or something similar,and tell him to boot from the CD.The Cd is bootable, but you have to tell him to boot it.Then tell us what happend

---

### Post by Cappy on 2008-04-26
> **puifais said:**
> 
4.  My issue with the 64 version is that a whole bunch of programs are not available for this version.  I looked around and found that they can be easily fixed by inputting a 1-line command for each program I want (such as VLC for instant).  

This isn't a 64-bit problem. 32-bit Ubuntu doesn't come with those installed by default either. You may want to use Synaptic rather than the command line. **System-->Administration-->Synaptic Package Manager**

By the way, you used Wubi to install ubuntu from windows. To uninstall/reinstall ubuntu you would have to boot into Windows.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by digisoft on 2008-04-26
I wouldn't give up on 64 so fast, in the amount of time it would take you to remove 64 and then install and configure 32 is more than enough to solve all your issues. I just did a 64 bit install on my laptop yesterday and 99% of evey thing worked instantly. The few things I had issues with like wireless were solved very fast with the help of some great people here. I am even running some 32 bit apps like skype with ease. 

Thanks to the help of the people here in less than 24 hours from when I first put the Ubuntu CD in my drive I've got a very sweet OS running and its getting better by the minute. I'm even going to install windows XP through virtualbox so I can run any windows apps right from inside Ubuntu. 

The way I see it is on any OS you install you will spend at least 24 hours tweaking it and configuring things anyhow, why not spend the time configuring on a good 64 bit OS? Any problems you might have can easily be fixed, just ask and you'll see how fast people will help anyone get this working perfectly.

digi

---

### Post by puifais on 2008-04-26
> **Cappy said:**
> This isn't a 64-bit problem. 32-bit Ubuntu doesn't come with those installed by default either. You may want to use Synaptic rather than the command line. **System-->Administration-->Synaptic Package Manager**

By the way, you used Wubi to install ubuntu from windows. To uninstall/reinstall ubuntu you would have to boot into Windows.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

With the help of Pixel:-), I was able to boot from the Ubuntux32 CD.  And, like you said, I still can't install many apps.  Instead of saying I can't install stuff because I have an (amd64), now it just says (i386) instead...  So anyway, you are absolutely right.  I still don't know how synaptic package manager can enable me to install apps since I don't know what its functions are, but I'll go look around more.

---

### Post by Perfect Storm on 2008-04-27
Sounds more like user problem than Ubuntu 64-bit problem ;) - flash on Ubuntu 8.04 64-bit have very painless.

Check out how you add medibuntu which have flash (and other stuff): [http://www.medibuntu.org/](http://www.medibuntu.org/)

make sure that synaptic and/ add&remove is closed.
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by HunterThomson on 2008-04-27
Trouble installing VLC? How are you trying to install programs? The are 5 ways to install programs that I know of. Try them in order:

1- Add/Remove Programs... Just look for the program you want (VLC is in here) check the box and click apply.

2- Synaptic Package Manager... this is better because it install all the dependencies for you and has a better selection. You just click the box and click apply.

3- Sudo apt-get install (the name of the program you want)

4- Look for the Debian package on the web download it and the click on it like a exe in window$

5- Download the source code compile it and install it (this is vary EZ) look at this page for instructions.

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

Don't feel bad Ubuntu was hard for me too after a life of window$ and a stint of OS/2:KS But it is well worth it:guitar:

---

### Post by wily_wolverine on 2008-04-27
VLC and flash can both be installed through the package manager.  Once you download the proper files to your home folder, or other favourite location, you can open the .tar.gz  or  .rpm with said package manager.

Beforewarned!!!!    DO NOT INSTALL THE VERSION OF VLC THAT INCLUDES ACTIVE-X OR DIRECT-X, it might mess up your MBR.  That seems to be what I am now dealing with.  I istalled VLC and watched a two hour long .avi.   The next day my bootloader     grub    will not install,  it freezes in stage 1.5 giving    "Grub error 18" as its' reason for inactivity.


:lolflag:  That is me trying to learn how to mount an ext3 filespace from the Linux RescueCD.


Best of Luck:KS  "Party-On People" :guitar:

---

### Post by rajivv on 2009-05-07
Hi,

I am also having the same problem.
I installed 64bit but my issue is flash and also a bigger problem
2-5 minutes into running ubuntu the system restarts and this happens every time.
Its definitely not a hardware issue as I am on dual boot and XP runs perfectly.

Should I move to 32 bit

Rajiv

---

### Post by Perfect Storm on 2009-05-07
Have you tried the native 64-bit flash player; [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by cybrsaylr on 2009-05-13
Flash is easy to fix on 64bit 9.04 Ubuntu. Got the fix from the helpful people here in 6 minutes.

My biggest issue with 9.04 64bit is my fav browser Opera crawls on 64bit  while it flys faster than Firefox on all the other 32bit flavors of Ubuntu. 

This seems to be an Opera issue not Ubuntu.

---

