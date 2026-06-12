---
title: "[SOLVED] HD write every 5 sec"
date: 2007-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by VincenzoAMD64 on 2007-11-09
Hello,
my hard disk is writing few bytes every 5 sec, I see it from the HD led and also from the System Monitor application.
My wireless interface is turned off, I can't understand if the problem is related to some service running..
I have Ubuntu Gutsy 64, on HPTX1000 TURION 64x2.
Is there a command to show which is the process that is writing so frequently?
Someone can help me to understand if this behaviour is correct?

Thank you
Vincenzo

---

### Post by Biggus on 2007-11-09
I don't think it's anything in particular to worry about.

One of the few commands I know of 'top' will give you a list of some of the running processes, those most intensive in terms of memory usage, cpu usage, or whatever, I don't actually know to be honest.

---

### Post by VincenzoAMD64 on 2007-11-09
Yes, 

I used the command  but there is no info about disk I/O usage.
I am worried about this activity because it causes my hard disk working also when I do not use my notebook. This behaviour could reduce the life of my disk. 
(my notebook is power on every day for 8 hours)
Could it be the cause that I read somwhere in internet about Ubuntu Gutsy damage hard disks?

I love my Ubuntu HP mini notebook
Vincenzo

---

### Post by wieman01 on 2007-11-09
See post #3 of this thread:

[http://ubuntuforums.org/showthread.php?t=531866]("http://ubuntuforums.org/showthread.php?t=531866")

Used to have the same problem. Solved it.

---

### Post by VincenzoAMD64 on 2007-11-09
Thnak you very much for your help,
I tried the instructions suggested... they do not work for my HP (after reboot).

I tried also from the shell:
sudo hdparm -B 255 /dev/sda

and the response was correctly:
/dev/sda:
 setting Advanced Power Management level to disabled.

but when I type:
sudo hdparm -i /dev/sda
it appears:
AdvancedPM=yes: mode=0x80 (128)

It seems my SATA HD parameters can not be changed by hdparm tools!
Could it be possible?

Help
Vincenzo

---

### Post by ChrisNiemy on 2007-11-09
Hi!

I guess this could also be considered as the interval of the ext3 journaling system.
It's the so-called commit-Interval, by default it is set to 5 seconds. In fact, it says, which state can be recovered by the journal, e.g. if a crash or something happens. On a desktop system you probably can set this to 30 seconds or even 60. (I tested also with 100 seconds, seems to work).

For more information and how to change this I'v wrote it step-by-step here:
[http://ubuntuforums.org/showthread.php?t=84130](http://ubuntuforums.org/showthread.php?t=84130) (post #3)
(BE CAREFUL with the OTHER  tuning ideas there, you just need to edit /etc/fstab with the commit=-option and addings this to the rootflags in /boot/grub/menu.lst.)

---

### Post by wieman01 on 2007-11-09
Try this instead:
> sudo gedit /etc/default/acpi
Then set:
> ENABLE_LAPTOP_MODE=false
Reboot & the click sound should have disappeared. Taken from:

[http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/]("http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/")

---

### Post by VincenzoAMD64 on 2007-11-09
> **wieman01 said:**
> Try this instead:

Then set:

Reboot & the click sound should have disappeared. Taken from:

[http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/]("http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/")

Thank you for the help,
I checked the file /etc/default/acpi-support
and the ENABLE_LAPTOP_MODE is false
what about the option SPINDOWN_TIME=12
in the same file?
I will continue to study...
Vincenzo

---

### Post by VincenzoAMD64 on 2007-11-09
> **ChrisNiemy said:**
> Hi!

I guess this could also be considered as the interval of the ext3 journaling system.
It's the so-called commit-Interval, by default it is set to 5 seconds. In fact, it says, which state can be recovered by the journal, e.g. if a crash or something happens. On a desktop system you probably can set this to 30 seconds or even 60. (I tested also with 100 seconds, seems to work).

For more information and how to change this I'v wrote it step-by-step here:
[http://ubuntuforums.org/showthread.php?t=84130](http://ubuntuforums.org/showthread.php?t=84130) (post #3)
(BE CAREFUL with the OTHER  tuning ideas there, you just need to edit /etc/fstab with the commit=-option and addings this to the rootflags in /boot/grub/menu.lst.)

Very kind,
I will investigate this possibility

Vincenzo

---

### Post by VincenzoAMD64 on 2007-11-11
Hello again,
starting the laptop this morning I noticed that when I am at the initial login screen the HD activity is not present. This means that it is related to some Desktop application and not to HD Kernel handling.

Some suggestions?
Thank you
Vincenzo

---

### Post by Octagonal on 2007-11-11
System->Preferences->Indexing Preferences 
and disable indexing.

Just a suggestion to see if that stops it...

---

### Post by VincenzoAMD64 on 2007-11-11
Thank you, I tried your suggestion and did not work for me.
I am sure, it is related to software, I have installed ubuntu gutsy on x86 32 bit desktop and the behaviour is normal (no disk activity).
I have gutsy 64 bits on HP TURION64x2 .... strange problem!

---

### Post by VincenzoAMD64 on 2007-11-12
Thank you to ChrisNiemy!
Your solution has worked for me!

I have written "noatime" in fstab for root partition,
this will avoid the usage of disk every 5 sec

I was very worried... because I need my linux for my everyday work.
Vincenzo

---

### Post by rah003 on 2008-05-21
Actually I don't think noatime will do what you want. According to man:
 noatime:   Do  not  update  inode  access  times on this file system (e.g, for faster access on the news  spool  to  speed  up news servers).

What you want to do is to increase time to VM dirty writebacks (by default every 5 secs). To increase writebacks to 15 seconds, run:

# echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

---

