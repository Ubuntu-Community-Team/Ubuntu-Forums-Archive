---
title: "Complete system lockup, NOT ext4, maybe related to vmplayer"
date: 2009-05-01
forum: x86 64-bit Users
---

### Post by arobinson on 2009-05-01
I am having complete system lock ups on my desktop ubuntu box after upgrading to jaunty that I never experienced with Intrepid. I am **NOT** running ext4, so please do not suggest that as a source of lockups.

Right now, I can reproduce the problem 100% of the time with vmplayer 2.5.2 although the problem is not at the same time. First it was when the VM was booting and then it was after a while during an iPod sync with iTunes.

When this happens, the computer is completely unresponsive (the gnome applets are not animating), keyboard is dead, mouse is dead, I cannot use ctrl+alt+f2 to get to a terminal session, ctrl+alt+backspace doesn't exit X and ssh does not respond. Only using the computer reset button works, very nasty.

I am using the new nvidia drivers (180.44) and this is amd64. 

The worst part of it is that I see nothing in my log files to hint at what may be going on. I see no kernel panics, nothing special.

Any ideas?

---

### Post by arobinson on 2009-05-01
Just happened again without running vmware (except for the services in the background). I was just using firefox to browse.

I was using some compositing affects, I am not trying with all of them disabled and ensuring that compiz is not running.

---

### Post by Arup on 2009-05-02
> **arobinson said:**
> Just happened again without running vmware (except for the services in the background). I was just using firefox to browse.

I was using some compositing affects, I am not trying with all of them disabled and ensuring that compiz is not running.

Its most likely your video drivers.Try updating to 180.51 and see if the issue goes away.

---

### Post by arobinson on 2009-05-02
Graphics drivers did not help. I reformatted and am now installing from the Ubuntu Jaunty CD, so far no lockups, so it may have been a corrupted upgrade.

---

### Post by aLmastro on 2009-05-02
I have been having the same problem lately. I replaced my motherboard a few weeks ago and ever since my system has been randomly locking up on me. My xorg seems to be using an insane about of system resources and everything I have read has suggested to turn off desktop effects and use Envyng to change video drivers. I have turned off all effects and have tried every compatible driver but the problem still persists. I thought the problem might be hardware related but when I boot into XP I have had no problems at all. I'd like to avoid formatting and reinstalling but I'm running out of ideas.

---

### Post by iMerlin on 2009-05-03
Experiencing the same, on Athlon64, 64bit version running Ubuntu 9.04 (with ext4 though).

But this is happening at random, not just during disk i/o. Weird stuff.

---

### Post by arobinson on 2009-05-03
Its back. After a full day of no crashes it happend twice in a row.

Right before it crashed I installed vmware workstation (crashed while syncing my iPod again).

The second time was after I installed TurboPrint and added its applet to the panel (I have a Canon photo printer not supported by Linux) and installed Adobe AIR.

The one thing that does make me curious is that alarm-clock is having the same hanging problems that is being related to Python 2.6 with PyGTK. So I wonder if it could be GTK related? If anyone is curious, that bug is [https://bugs.launchpad.net/bugs/321176](https://bugs.launchpad.net/bugs/321176)

Hopefully it is found soon as it is extremely debiliting. BTW, I ran the computer all night with no hangs and it was fine, so it seems that something is causing the crash while I am using it (not background tasks). It seems definite that vmplayer is having issues.

If it continues to hang, I may consider going back to nvidia 177, but I am starting to think this is not graphics related.

---

### Post by arobinson on 2009-05-03
> **iMerlin said:**
> Experiencing the same, on Athlon64, 64bit version running Ubuntu 9.04 (with ext4 though).

But this is happening at random, not just during disk i/o. Weird stuff.

FYI, I mentioned that I am not running ext4 as there are documented bugs that ext4 **will** freeze your computer up. You probably want to go back to ext3 unless you don't mind the instability of your file system

---

### Post by arobinson on 2009-05-03
Okay, I performed an iPod sync in vmplayer again as I know it hangs Ubuntu Jaunty 100% of the time for me, but this time I was SSH'd into my computer and tailing /var/log/syslog

1) there was no message on the console that it was dying
2) Here is the output from syslog:

```
May  3 18:39:07 drewpc kernel: [82518.989137] usb 1-4.3: new high speed USB device using ehci_hcd and address 8
May  3 18:39:07 drewpc kernel: [82519.105517] usb 1-4.3: configuration #1 chosen from 3 choices
May  3 18:39:08 drewpc kernel: [82519.821054] usb 1-4.3: reset high speed USB device using ehci_hcd and address 8
May  3 18:39:08 drewpc kernel: [82520.510053] usb 1-4.3: reset high speed USB device using ehci_hcd and address 8
May  3 18:39:09 drewpc kernel: [82521.675823] usb 1-4.3: usbfs: process 9168 (vmware-vmx) did not claim interface 1 before use
May  3 18:39:10 drewpc kernel: [82522.068368] usb 1-4.3: usbfs: process 9168 (vmware-vmx) did not claim interface 0 before use
May  3 18:40:01 drewpc /USR/SBIN/CRON[13858]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  3 18:40:38 drewpc kernel: [82609.870900] NVRM: Xid (0005:00): 26, Ch 000001ff M 00001ffc D ffffffff intr ffffffff

```

There were also a couple of logs of connection refused regarding my UPS as I don't have that 100% re-setup again after rebuilding the box, but I don't think that is an issue. Than last line could be something though.

screen/ssh was completely locked up at this point, so I know that it is not X crashing, it is the kernel, I just wish I could get a stack trace or something so I could report a bug.

---

### Post by arobinson on 2009-05-03
Giving launchpad a try:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/371472](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/371472)

---

### Post by brntoki on 2009-05-06
Misery loves company...

Same thing here.  Fresh install from DVD.  Thought it may be graphics related, tried different nvidia drivers (none but 180.44 would even work no matter what I tried), uninstalled all nvidia stuff, still freezes up.  Fresh installed again, deleting the old root dir and reformatting, froze within a minute, before, I might add, I even tried to install the nvidia drivers.

One thing that does seem to be related in all but perhaps one or two instances was that there was network activity going on.  I.E., starting web-browser, doing an update, or trying to look for answers via google.  It just seems there is possibly some connection to the network activity.

The video on this page seems to reproduce the crash without exception: [http://linuxcrypt.net/?p=255](http://linuxcrypt.net/?p=255)

I don't know what logs or anything to look for.  FYI, no ext4, though I did use my old /home dir in order to keep settings.  I wonder if there is some conflict within those settings.  I was coming from a totally trashed upgrade attempt of 8.10 (didn't last long), so essentially I was coming from 8.04.

gigabyte ga-p35-ds3l, intel dual core, ge-force 7300 gt, 4gb mem.

---

### Post by CheeseEatingBulldog on 2009-05-06
Yep, same problem on my girl's box, 64 bit install worked fine on 8.10, but now on 9.04 it crashes randomly. It can go days fine and then today three times. Turning off desktop effects seems to help, so that would point to a graphics driver problem.

:(

---

### Post by arobinson on 2009-05-08
Woohoo! Issue "fixed"

I uninstalled **all** 180 debs and installed the 171 nvidia debs. Everything is working. Went an entire day with no hangs and my iPod is syncing again without issues.

It appears to be a problem with 180.44 and hthe 7300 GPU. It may be because Ubuntu installed the libvdpau package, and I don't believe the 7300 supports the vdpau extensions, but I am not sure.

---

### Post by grege on 2009-05-09
Hi,

The problem is with 180.44 and compiz, the moment you try and resize or move a window it comes crashing down. The simplest solution is to turn off desktop effects.

The previous poster found using the older version of the driver will work.

My solution was to uninstall everything 180.44 through Synaptic and manually install the latest 180.51 from Nvidia.

My system is rock solid now.

If you know you way around then try these instructions, just ensure you grab the x86_64 driver :-

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#nVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#nVidia_Driver)

cheers

Warning: If you go down this path the drivers will need to be re installed after each kernel update.

---

### Post by clackamas on 2009-06-28
I am also having random lockups however I am pretty sure it is the Nvidia driver.

Things I did to help narrow  the problem:

The machine had previously been run SuSE 10.3 for the past year without this issue.
I let the memtest run for 12 hours  / 12 passes with no failures.

I disabled ACPI and still had the lockup, no kernel messages.

I discovered if I hit the system reset (soft reset) that Init would register that and restart the system.

I am running the latest 180 driver on a 7300 X-PCI MSI board.

So, anyway, it would be useful to know, I think, if people hit the soft-reset if they see the shutdown messages.  That would then indicate the driver.

I am trying to figure out how to further debug this now.

---

### Post by hiflyer on 2009-08-01
I also get the complete system lockup. I have not noticed any harddrive problems I have had any harddrive problems. This machine has been upgrade since version 6 of ubuntu with out being totally reinstalled. It is an AMD 64 bit hp unit and was working fine under Intrepid. Since the Upgrade to 9.04 it has been locking up. My solution I am testing is to downgrade to the NVIDIA 173 driver. while I have only short term testing (couple hours so far), it has not locked up. I find if I turn on the Matrix screen saver under 180 driver it will lock up in seconds. It did not lock up under 173 driver.

you might try this and see if it helps.

---

### Post by hiflyer on 2009-08-01
I forgot to add that I am using a GeoForce 7500 le

---

