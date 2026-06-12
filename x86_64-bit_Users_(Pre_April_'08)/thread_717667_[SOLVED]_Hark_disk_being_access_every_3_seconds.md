---
title: "[SOLVED] Hark disk being access every 3 seconds"
date: 2008-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by wangrui on 2008-03-07
Hi,

I got a problem here. I don't know if anyone have the same problem. Everything works when I using Ubuntu 32bit. But after I upgrade my desktop and changed to 64 bit. My hard disk can't spin down any more.

Here is what happen, recently I upgrade almost everything of my desktop. I bought an ASUS P5K motherboard, a Colorful G8500 video card, four Kingmax DDR2-800 2GB memory and a E4500 cpu. And also a Western Digital 500GB Green Power Hard disk. And also upgrade to Ubuntu 64 bit. I have changes everything so I don't know which one is the root cause of the problem. The problem is that I can hear my hard disk click every 3 seconds. I bought the hard disk for only two week, but the Load_Cycle_Count returned by "sudo smartctl -d ata -a /dev/sda" is already more than 8,000, and is increasing very quickly. Under this rate, my hard disk will break soon. 

After did some googling, I learnt that it's because my hard disk want to park the head but linux want to touch the disk. So I modify "/etc/init.d/mountkernfs.sh", I mount flash+memory as my root partition and mount the hard disk as a data directory which is never used by the system.  Yes, after I did that, I can't hear the click any more. But still, I can see the hard disk light blinking every 3 seconds.  And I also can't spin down the hard disk by hdparm.

So I umount all hard disk partition, but the hard disk light is still blinking every 3 seconds. I set the block_dump to 1, but there isn't any process writing or reading to sda according to dmesg.

So I reboot the computer to single user mode, which only /etc/rcS.d is executed. The hard disk light is still ok there. Then I execute the scripts under /etc/rc2.d one by one, to see which one is causing the problem. When I execute the script /ect/rc2.d/S12hal, a daemon process hald started, and my hard disk start blinking for ever.

It seems if I kill the daemon hald, my hard disk will stop blinking. But then I will not be able to use my secondary network card. 

And even before I started hald, when the hard disk light is not blinking at all. I still can't spin down the hard drive by hdparm.

I don't know why my hard disk can't spin down. Why the hard disk light will blinking for ever after hald started.

Is it because the motherboard? Or the harddisk? Or the OS? Does anyone have the same experience?

---

### Post by wangrui on 2008-03-07
Can anyone share some experience? For example, if anyone have the "hald" process running but the hard disk light is not blinking. Then I will know it's not caused by "hald" but by the hardware. Thanks!

And my problem is not caused by any kernel process other than hald. Because I don't have any partition mounted.

---

### Post by wieman01 on 2008-03-07
Wangrui, 

Nice to see you again. I used to have the exact same problem. I have posted a solution here:

Oh, need to run.

Please search for my user name, hard disk, spin up/down, you will find it.

I'll post back later if you cannot find it. :-)

---

### Post by wangrui on 2008-03-07
> **wieman01 said:**
> Wangrui, 

Nice to see you again. I used to have the exact same problem. I have posted a solution here:

Oh, need to run.

Please search for my user name, hard disk, spin up/down, you will find it.

I'll post back later if you cannot find it. :-)

Thank you for the quick reply. I found the url

[http://ubuntuforums.org/showthread.php?t=531866](http://ubuntuforums.org/showthread.php?t=531866)

but it might not solve my problem. Because the hard disk start blinking when /etc/rc2.d/S12hal executed. In that script, only one daemon process started, the hald. If I kill the process, the hard disk will stop blinking. 

Maybe it's a hardware problem, because I got error while trying to modify the PM settings
```

wangrui@wangrui-desktop:~$ sudo hdparm -B 254 /dev/sda
/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error

wangrui@wangrui-desktop:~$ sudo hdparm -S 120 /dev/sda
/dev/sda:
 setting standby to 120 (10 minutes)

```

This is kind confusing. Because I did a lot of survey before buying the motherboard and harddisk. I thought P5K with ICH9 and Western Digital Green Power HD is the best combination. But I can't even spin down the hard disk. Maybe I should have a try with other hard disks to see whether they can work.

---

### Post by Steveway on 2008-03-07
Did you stop Tracker from indexing? That is the most obvivious reason.

---

### Post by wangrui on 2008-03-07
> **Steveway said:**
> Did you stop Tracker from indexing? That is the most obvivious reason.

Tracker is the first program I removed after each installation. I don't need tracker at all. 
Besides tracker, there is another bad program must be stopped. It's the updatedb, it will run everyday against the entire filesystem. But actually it may not be needed in the whole life.

I have to say I don't have any hard disk mounted while the problem appears. My root partition is on a extern USB flash disk. And I use unionfs with a tmpfs to make the root partition writable. And I don't have any swap partitions. My entire system is not relavent to any hard disks. The hard disk is just connected because sometime I need to mount it to do some read/write. My target is to have it spin down most of the time. But it seems impossible. Because hdparm -S has no effect on it. And the hard disk light is blinking every three seconds.  But I can't hear any disk movement now which is a good thing.

I have found some post on the web. The problem might comes from the Green Power hard disk. Maybe it's a failure hardware design. But not quite sure now.

---

### Post by wangrui on 2008-03-07
Hi, I have found the reason. It's neither because ubuntu nor because the motherboard.

Today I installed a SAMSUNG hard disk to test it out. After the daemon hald started, the hard disk light start blinking, but I still can spin down the hard disk as I like. It seems the hard disk light just blinking for no reason. But there isn't any hard disk access at all.

The problem is Western Digital don't seems to accept anything from hdparm. But it's ok, because the hard disk is very quiet, I don't really need to spin it down. As long as I know it's not being accessed all the time.

---

### Post by csisgro on 2008-03-10
I see this is marked as solved. So I just will make a comment. The cd/dvd is polled every 3 seconds with the default setting looking for a disc insert. Perhaps your system is showing the light during the polling activity. Mine doesn't but that does not mean that all won't.

---

### Post by annapitcher on 2008-03-11
Wangrui,

I was having same problems as you did, and today I finally solved them.
Just want to say what smartctl -d ata -a /dev/hda says for my hd about Load_cycle_count .. its value is: 71017 :D  ups.. about 2 years running ubuntu with a clicking hd.. just to give some compassion ..

---

