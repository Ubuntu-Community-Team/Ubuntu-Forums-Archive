---
title: "My Ubuntu 64-bit frequently freezes. Please help!"
date: 2009-06-14
forum: x86 64-bit Users
---

### Post by daygan on 2009-06-14
I've done a lot of searching over the past couple days to try to figure out what my problem is but haven't resolved it yet. I installed Ubuntu 9.04 64-bit on my computer a few weeks ago, and just recently (last few days) started noting "freezing" problems in which my computer (or compiz?) .. well, I'll just say the "screen", to be as clear as possible, will freeze up entirely (except for the mouse, which is just as livid as ever). I'm not sure why this is happening or what to do to fix it. Can anyone give me some help with this? Yes, I'm sure you'll want some more specific information, but I'm not certain what specific information you might require, so, just tell me, and I'll do my best to get it for you.

Thank you!

---

### Post by nimrod_abing on 2009-06-14
Are you using "Jaunty Jackalope"? If so then welcome to the club: [http://ubuntuforums.org/showthread.php?t=1163584](http://ubuntuforums.org/showthread.php?t=1163584) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)

You have two options:

1. Install a "PPA" Kernel (right now 2.6.29.4) as suggested here: [http://ubuntuforums.org/showpost.php?p=7382178&postcount=29](http://ubuntuforums.org/showpost.php?p=7382178&postcount=29) Get the kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29.4/")

2. Fall back to Intrepid Ibex and wait for an official fix or Karmic Koala to be released.

---

### Post by daygan on 2009-06-14
oh.. great.. okay, I'll look into that first.. thanks..

---

### Post by CurtissS on 2009-06-14
> **nimrod_abing said:**
> Are you using "Jaunty Jackalope"? If so then welcome to the club: [http://ubuntuforums.org/showthread.php?t=1163584](http://ubuntuforums.org/showthread.php?t=1163584) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)
 
You have two options:
 
1. Install a "PPA" Kernel (right now 2.6.29.4) as suggested here: [http://ubuntuforums.org/showpost.php?p=7382178&postcount=29](http://ubuntuforums.org/showpost.php?p=7382178&postcount=29) Get the kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29.4/")
 
2. Fall back to Intrepid Ibex and wait for an official fix or Karmic Koala to be released.
 
I'm just wondering if this new kernel will fix my hard freeze's. Jaunty 64bit freezes on me while copying large amounts of data from one drive to another or from DVD to hard drive what happeneds is the PC will lock up and the keyboard leds start flashing very anoying. If I just copy say 2-3 gigs at a time no problems other then that Jaunty is perfect.
 
Would love to here anyones thoughts.
 
Thanks

---

### Post by daygan on 2009-06-15
great. well, actually, not only did that not resolve my freezing issue, It made things worse. Now none of my settings (desktop background, visual effects, firefox bookmarks, account names that various applications use) are remembered upon startup, and some applications just don't even work any more (amule won't start at all, and firefox is having many problems, and crashes every time I try to click on the "add-ons" option under tools). So now what do I do? is it possible that I installed the kernel improperly? I seem to remember that I selected the top-most option, which was "apply the package-maintaner's kernel" or something... ideas?

---

### Post by H2SO_four on 2009-06-15
Random freezes issue was why I "downgraded" to 32 bit Jaunty.  I seemed to have about a half-dozen bugs that I couldn't get resolved.  If this is all worked out, I will be back with 64 bit Karmic and ext4.  My fingers are crossed :)

---

### Post by willing on 2009-06-16
the symptoms seem very similar to what I'm seeing on 8.04.2 x86_64  with kernel 2.6.24-24-generic.  UI randomly locks up, stops repainting (no updates from clock or top), keyboard is completely unresponsive but mouse still tracks OK, though cursor does not change.   I think I've been able to rule out hardware but am not sure what diagnostics/logs could help pin down the cause.

---

### Post by lyghtkruz on 2009-06-16
I don't know if I should open a new thread for this or if it's the same issue.  

My system has been "freezing" so to speak, but only with Open Dialog windows.  After a few seconds it will come back.  All other windows except the application attempting to open the file will hang.  This has been a recent issue.  At first I thought it was only FireFox, but it appears to do it with ALL applications that have to use the "Open File" dialog window.

I'm running Ubuntu 9.04 64 Bit with the 2.6.28-11-generic Kernel.  I currently do not have an issue with it hard locking.

please note:  If I open Nautilus (I believe that's whut Ubuntu uses by default) and right click "Open With..." The file is opened immediately.  eg.  Right click avi file and open with VLC.  The movie does not hesitate.  If I open VLC and click "File Open" it hangs for a while.  If I run things through the command line and specify the location of the file,  mpg123 filename.mp3, the mp3 plays right away.

---

### Post by MG37221 on 2009-06-16
My symptoms are similar but the freeze always recovers (within a minute or so).  Whenever I try to import, say an image into a document (OpenOffice 3.1), save an attachment or attach a file to an email (I use Thunderbird) it occurs.  Whenever saving a file for the first time or exporting it (at any time) I experience the freeze.  It also happens when I wish to print to a file (in any format (PS, PDF, etc.)).  Screen goes grey and sometimes (infrequently) I receive a message that the app is not responding.  Thus far, it always comes back and I am able to complete what I intended to do.  This is most inconvenient but, in my experience, no worse as in, no reboots required and no loss of programs or data.

This happens on both Jaunty 64bit and 32bit versions.  64bit is running on an AMD Opteron175 with nVidia 7600GT.  32bit is the NetbookRemix on an MSI Wind with Intel Atom N270 with I950 graphics.  Both machines have 2GB RAM and both use EXT3 FS.

***  Update to add that the new 2.6.29 32bit kernel does appear to have resolved my issues with my netbook.  I´ll test it for a few days before updating my main PC.  Thanks to all for the recommendations.

---

### Post by grege on 2009-06-17
Are you using the Nvidia restricted driver? 

If your computer operates happily with compiz turned off, then it is the most likely culprit as the 64bit driver that ships with jaunty has this issue whenever you resize a window. For me just moving a window would freeze the screen. The newer driver fixed everything.

Solution is to activate the "thefirstm" PPA repo and update to a newer Nvidia driver.

[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

But before doing anything, just turn off desktop effects and see what happens.

---

### Post by ddutta on 2009-07-25
Well I have a Gigabyte GA-965P-DS3 1.3 mobo, E6420 Conroe, 8GBRAM, NVidia 8600GT (run binary driver from nv) and here is what I notice:
* Jaunty 64 bit freezes .... I guess X crashes
* Hardy 64 bit is running fine, however the monitor cant be turned off and the sleep stuff doesnt work well. 

Hence I feel that Jaunty 64 bit isnt as robust as the earlier versions. But I would love to get a Jaunty that works well, I like it

---

### Post by MG37221 on 2009-07-25
> **ddutta said:**
> Well I have a Gigabyte GA-965P-DS3 1.3 mobo, E6420 Conroe, 8GBRAM, NVidia 8600GT (run binary driver from nv) and here is what I notice:
* Jaunty 64 bit freezes .... I guess X crashes
* Hardy 64 bit is running fine, however the monitor cant be turned off and the sleep stuff doesnt work well. 

Hence I feel that Jaunty 64 bit isnt as robust as the earlier versions. But I would love to get a Jaunty that works well, I like it

All of my issues have been resolved, most likely through recommended updates.  The lag I previously experienced has gone away.  There have been some reports about some issues with nVidia's drivers of late.  I'm using the latest version available on Synaptec.  Infrequently Compiz will crap out and, less frequently, so do my selected Screenlets but, I suspect nVidia is the cause and just live with it.

All in all, I'm extremely pleased with Jaunty.  This is both the 32 and 64 bit versions.  IMO, Ubuntu just keeps getting better!  

If you've not done all the updates, If you're willing to be patient, I would recommend you try that first before reverting to Hardy.  

Opinions vary.  This is mine.

---

### Post by daygan on 2009-07-26
Thanks for the update. I personally ended up removing my jaunty install and installing Intrepid, which has worked quite well for me for the last month. There are a few compatibility issues with a few applications that seem to have been resolved better in Jaunty than Intrepid, but I'm still not ready yet to upgrade to Jaunty again. I'm sure the issue has something to do with a hardware peculiarity of mine, and I may just try to install Jaunty as a secondary operating system on an extra partition and see if it works or not after installing all updates. Anyway, thanks, MG37221, for your update!

---

