---
title: "Extremely sluggish amd64 ubuntu"
date: 2007-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by omrsafetyo on 2007-03-02
I have a problem every once in a while with Ubuntu becoming extremely slow.

So far, it seems to happen mostly after long periods of idling.

What happens is that programs do not seem to open very quickly - and sometimes not at all.  I will try to open an application, and in the task bar I can see "Loading mozilla-firefox" or whatever - and when the loading disappears, instead of the program popping up, nothing happens.  The icon does not go to the system tray, and there is no window in the task bar.

I can also try opening the console, and at first it may not open up at all - except with the same results as above - and other times, it may just sit for a minute - I'll try again - and still it will sit, and then it will eventually just randomly come up.  I will even have trouble getting the log/shutdown dialog box to come up - and of course, I can't open up the console to shut it down with the shutdown command. Most of the time, I have to do a hard shutdown/reboot.

I'm running an AMD Athlon 64 X2 3600+ - so yes, I do have a 64 bit system.

Any ideas what might be the cause?

AMD Athlon 64 X2 3600+
512 MB OCZ Gold DDR2 800 (PC2 6400)
WD Caviar 160 GB SATA
GeForce 7300GT 256MB GDDR2 PCIE x16
Samsung 18x DVDRW/CDRW

Just for reference

---

### Post by manjo on 2007-03-02
Which kernel are you running? Mine is 

Linux version 2.6.20-9-generic (root@crested) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu3)) #2 SMP Sun Feb 25 22:59:06 UTC 2007
manjo@sleepy:~$ 

I have feisty herd4 running happily on my new HP Media centre AMD64 (but I have 2GB RAM).  I have an uptime of 4 days now and suspended the machine some 4 times so far and no problems waking up.

---

### Post by omrsafetyo on 2007-03-03
I'm actually not sure my kernel version..   I was trying to figure out the other day how to display information about my OS... it took me a while to figure out I was running Edgy!  I'm still pretty new to the linux stuff at this point.  I've been using SCO UNIX for over a year at work - but thats 100% command line, using mostly proprietary binaries, with little to no administration - most of which is scripted anyhow.  The GUI interface combined with command line is still a little unfamiliar to me.  

I haven't had a lot of time to play with it yet either.  I built my new PC off newegg on wednesday - and starting thursday, I'm at work for 7 days straight on 12 hour shifts - not much free time afterwards.  So I really only had wednesday night (I got the parts from UPS around 5-6PM) to build the PC, install Ubuntu - which I had trouble with, because I needed to use the -noapic -nolapic options from the command line to start the install.  Also, my MOBO recognizes the IDE channel as channel 0 - and my SATA HDD is on channel 2, which means that when I boot, I have to hit f1 to let it know that it doesn't have to try to boot from channel 0 (still trying to figure out how to fix that...)  etc. etc. etc.

I have only really had a little bit of "play with it" time.  I only tonight found out that I had to use MY password when using sudo, not the root password.  I spent a lot of time trying to get flash installed on firefox; but having to use sudo, and using the wrong password - that was just a lot of time wasting! :lolflag: 

Anyway.. at work right now.. just let me know what command to run to figure out my OS specs, and I'll let you know.

Think it may be the RAM issue?  I was making a budget build... so for now I'm only running 512 DDR2; until my next paycheck - or at least after mortgage, etc. is paid for the month.

---

### Post by angryfirelord on 2007-03-03
To display the kernel info, type **uname -a**.

---

### Post by mconway0003 on 2007-03-05
> **angryfirelord said:**
> To display the kernel info, type **uname -a**.

here you are..

```
marcus@Marcus:~$ uname -a
Linux Marcus 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

```

---

### Post by youph on 2007-03-06
I would start by monitoring the CPU usage on your system.

Since you are having issues in X (the GUI) you should switch to one of your virtual consoles; control-alt-f1 should work fine. Note: to get back into X, type control-alt-f7.

Login (doesn't have to be root) and type top

You should see a list of processes and information about CPU/memory usage. On the top of the screen you will see things like User, System, Idle. Those are the CPU usage statistics.If your system is super busy you will have small idle values and this could be the cause of you sluggish system.

Actually, if the system is responsive in the console, just not in X Windows, I would venture a guess and say its your graphics card. Either you don't have the proper drivers (nvidia drivers need to be installed as they are not allowed to be released by the distro due to a draconian licensing policy by nvidia) or you are using the basic software rendering drivers.

So my suggestions are to check the CPU usage and if that's cool verify that you system is slow in console and not just X. If the console is sluggish as well the issue may be a bit more complicated.

Hope that helps.

EDIT:
I see you are *not* using the amd64 kernel: Linux Marcus 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux
You are using the i686 SMP kernel which is 32 bit.

FYI

---

### Post by omrsafetyo on 2007-03-06
> **youph said:**
> I would start by monitoring the CPU usage on your system.

Since you are having issues in X (the GUI) you should switch to one of your virtual consoles; control-alt-f1 should work fine. Note: to get back into X, type control-alt-f7.

Login (doesn't have to be root) and type top

You should see a list of processes and information about CPU/memory usage. On the top of the screen you will see things like User, System, Idle. Those are the CPU usage statistics.If your system is super busy you will have small idle values and this could be the cause of you sluggish system.

Actually, if the system is responsive in the console, just not in X Windows, I would venture a guess and say its your graphics card. Either you don't have the proper drivers (nvidia drivers need to be installed as they are not allowed to be released by the distro due to a draconian licensing policy by nvidia) or you are using the basic software rendering drivers.

So my suggestions are to check the CPU usage and if that's cool verify that you system is slow in console and not just X. If the console is sluggish as well the issue may be a bit more complicated.

Hope that helps.

EDIT:
I see you are *not* using the amd64 kernel: Linux Marcus 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux
You are using the i686 SMP kernel which is 32 bit.

FYI

That was not me posting the kernel information - I meant to do that when I was at home earlier, but I left the post on screen, and never hit "submit".

I think you may have solved my problem - though, I have not tried to implement your solution.  I have not installed any nVidia drivers for my 7300GT - so I should probably isntall the most recent drivers for that.  I actually haven't had any issues with this in a few days - but I would like to prevent it from coming back if possible, so I will try the drivers.

I highly doubt it is a CPU usage issue, as I have not put any substantial demand on the system resources yet - and am running a very decent budget system.  I'll give it a whirl, and let you know.  Thanks.

---

