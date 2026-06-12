---
title: "Jaunty 9.04 x86 64-bit freeze, whitescreen, &amp; more problems"
date: 2009-08-31
forum: x86 64-bit Users
---

### Post by snailkeeper on 2009-08-31
First off, I'd like to apologize - I'm pretty much a noob, so I'm not sure what information you'll all need to help me out with these problems. However, I am capable of following instructions! :D That said, I have spent days reading over the forum but haven't found any threads that seem to cover the same problems I'm having. 

I've installed Ubuntu 9.04 x64 version on my pc. I've got an ASUS M3N78 Pro motherboard, and am using onboard NVIDIA GeForce 8300 chipset video and using the HDMI output to a high-def TV. My processor is an AMD Phenom 64. I've got a NEC DVD reader/writer (model ND-3540A with firmware v1.01).

When I run uname -a to find my kernel version, I get:

```
Linux mediacomp 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```Okay, now, the problems I'm having. 

Periodically, the computer will either freeze (I can still move the mouse, but nothing really responds; I can move windows that are already open but cannot open any new programs) or crash into a plain white screen (if I've got music running the music will stop). In either case a hard reset is needed. No idea what I need to put in the terminal to find out what's happening here.

If I have a DVD in the DVD drive when I boot up, I can read it, no problem. However, I can't seem to be able to switch a new DVD in and still be able to read it. I've tried just ejecting and putting the new one in, and I've tried umounting then ejecting and mounting when I put the new one in, and neither method works. I have gotten a variety of errors. Please let me know what I ought to try so I can provide the appropriate error messages. (Note: I only seem to have trouble with DVDs, but haven't had any trouble with data CDs burned with mp3s - NOT audio CD format.)

I know I haven't even begun to provide enough information, and I'm sorry, I just don't know what is needed! I am willing and (hopefully) able to run whatever commands are needed to puzzle these problems out! So please, don't hesitate to boss me around. :D

Thanks so much in advance! I really appreciate any and all help provided!

---

### Post by snailkeeper on 2009-09-01
Some more information: I can pretty much reliably reproduce a white-screen lockup by booting with a commercial DVD in the DVD drive, and right-click -> "Open with Disc Copier" and attempting to rip the .iso using Brasero, saving the file on a secondary hard drive in my system. The process will get about a third to a half of the way through (resulting in a file approximately 2GB) before the screen turns white and the system becomes nonresponsive, requiring me to press the reset button.

This isn't the only time I get the white-screen lockup, but it's the only way I've noticed it happen for any sort of reason. Usually it just seems random, and I haven't noticed any other pattern to determine why sometimes it whitescreens and sometimes it just locks up.

Any ideas?

---

### Post by mirca_sp on 2009-09-01
ok,
is the system updated? before any conclusion, close all windows and try this in terminal:

sudo apt-get dselect-upgrade

then reboot the machine. post results. thx

---

### Post by snailkeeper on 2009-09-02
Thanks for the reply! I did the upgrade -- I've run the upgrade from the dialogue that pops up saying upgrades are available, but maybe that method never completed. Regardless, I did this terminal upgrade.

It upgraded 3 packages: dnsmasq-base, libnss3-1d, and python-gobject. The last thing on the terminal screen before the new prompt said "ldconfig deferred processing now taking place". I rebooted.

Would any of those packages being updated help, do you think? Thanks again!


Edit: I tried ripping a DVD iso again, and still got the whitescreen of death. Still no random freezes, but they can be hours apart, so I've got my fingers crossed.

---

### Post by mirca_sp on 2009-09-03
hi pal,
these packs you updated don't seem to be related to the system's freezing. i forgot to ask, what program are you using to rip the dvd iso? 
could you check the cpu usage while you're ripping the dvd until it get the whitescreen and post it? you can do it by System > Administration > System Monitor.
thx!

---

### Post by snailkeeper on 2009-09-03
I'm using Brasero to rip the DVD iso. It's default, I guess, when you go to Computer -> right click on DVD drive -> "Open with DVD copier".

I will attempt to get some useful information from the System Monitor. I wonder, is there a log file I could look at for that, or do I just have to watch it?


In other news, I just had to hard reboot twice in just a few minutes from non-whitescreen freezes. The first time I had File Browser looking at my 200GB hard drive (attached via Raid array, filesystem type xfs, ~42GB used), Firefox open with 3 tabs, and System Monitor open to the Resources tab. Because the screen didn't white out, I was able to copy down the Resources:

CPU1 3%, CPU2 .9%, CPU3 0%, CPU4 7.8%
Memory 416MiB (11.4%) of 3.6GiB

The second time, I only had File Browser open to Computer, and Firefox (3 tabs) open, so I wasn't able to see any Resource listings.

No idea if this information will be useful at all, but here are some log files I found under the "syslog" heading. 

Right before the first freeze tonight, and the first reboot:

```
Sep  3 18:00:01 mediacomp /USR/SBIN/CRON[19979]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Sep  3 18:05:58 mediacomp kernel: [73268.094933] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Sep  3 18:05:58 mediacomp kernel: [73268.097878] SGI XFS Quota Management subsystem
Sep  3 18:05:58 mediacomp kernel: [73268.282325] XFS mounting filesystem sdb1
Sep  3 18:05:58 mediacomp kernel: [73268.369326] Starting XFS recovery on filesystem: sdb1 (logdev: internal)
Sep  3 18:05:59 mediacomp hald: mounted /dev/sdb1 on behalf of uid 1000
Sep  3 18:05:59 mediacomp kernel: [73268.602596] Ending XFS recovery on filesystem: sdb1 (logdev: internal)
Sep  3 18:16:29 mediacomp syslogd 1.5.0#5ubuntu3: restart.
```
Right before the second freeze tonight, and the second reboot:

```
Sep  3 18:17:01 mediacomp /USR/SBIN/CRON[3658]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  3 18:20:01 mediacomp /USR/SBIN/CRON[3725]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep  3 18:26:35 mediacomp syslogd 1.5.0#5ubuntu3: restart.
```Now I'm going to play with the DVD iso rip. I'll look through the log viewer after it whitescreens; let me know if there's any place in particular I ought to check out, since I probably wouldn't recognize anything weird if I saw it!

Thanks again!

---

### Post by snailkeeper on 2009-09-12
I tried ripping a DVD iso onto my secondary hard drive and got the whitescreen freeze again. I wasn't able to get any information from the System Monitor, as the screen goes white.

Are there any logs I can look at to try to find the cause of these whitescreen freezes? I poked around in the logs I found earlier (the ones I posted from), but I didn't notice anything listed around the time of the freezes. Maybe I just don't know what I'm looking for. Any idea where I ought to look?

---

### Post by mirca_sp on 2009-09-12
hi pal,
i've been looking for some ideas and i believe it's a good one to install the k9copy package. ([http://k9copy.sourceforge.net/](http://k9copy.sourceforge.net/))
install it via terminal. remember to have the medibuntu repository added in your sourcelist. ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)).
try it and post results.

---

