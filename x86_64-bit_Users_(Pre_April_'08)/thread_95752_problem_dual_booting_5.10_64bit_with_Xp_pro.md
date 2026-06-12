---
title: "problem dual booting 5.10 64bit with Xp pro"
date: 2005-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by paulf on 2005-11-27
Hello. I'm a complete newcomer to the world of Linux and have been trying to run Ubuntu since yesterday. I'm having some problems and I wonder if anyone here might be able to shed some light for me. Yesterday I installed Ubuntu 5.10 64 bit on my AMD64 3200 system. I have windows XP Pro (Sp2)installed on an NTFS formatted hard drive and I installed Ubuntu onto a second drive, allowing it to automatically format and partition the drive. The install went fine and the first time ubuntu booted without any problem. It was only when I rebooted into windows to get some drivers for my modem that the problems began. After booting into windows I was unable to reboot into Ubuntu ... I'll write out what the screen says in a moment, but before asking anyone anything I decided to format the whole thing, fix the mbr for windows and then reinstall ubuntu.

As before all went well. This time I repeatedly booted into ubuntu with absolutely no problems (5 times). Then I booted into windows and since then have been unable to reboot ubuntu! Here is what the screen says (you'll have to forgive me here because I'm a total illiterate whyen it comes to all this command line stuff):

Booting the kernel.
Loading please wait ...
mount: mounting /dev/hdb2 on /root failed: invalid
mount: mounting /root/dev on /dev/.statistic/dev failed: no such device or statistic
Mount: mounting /dev on /root/ dev failed: no such device or statistic Target file system doesn't have /sbin/init

Then there's some stuff about 'Busybox' which ends:

/bin/sh: can't access tty; job can't be turned off

That's more or less it.I've tried to write out what is says as closely as I can, though there may be one or two errors with spaces etc. 

I have no idea what could be causing this problem as I don't have much in depth knowledge of software - maybe it's something to do with dual booting a 32bit system and a 64 bit?? I really have no idea. I've had a look around the web to see if I could find any solutions but as yet nothing has appeared. I hope someone here might be able to help. I've also filed this post as a bug report though I'm not sure if it is a bug or if it's something I've done wrong (I really don't think so). However, it doesn't seem to be a very common problem

Here's my specs ... don't know if anymore would be helpful or not:

AMD64 3200
Nvidia nforce4 chipset CK8-04 ultra chipset
Nvidia gforce 5200 fx
1280ddr pc400 ram
Generic 120gb
Maxtor 160gb


Thanks very much in advance.

---

### Post by paulf on 2005-11-28
Oh dear, this is a little discouraging. No one seems able to help! I've been spending quite a lot of time looking around to try to find answers to my question but so far it seems there aren't too many to be had. I'm now thinking that maybe I ought to supply a little more information, as after reading through loads of posts, web pages and forums etc, I've come to a basic understanding of what  mount: mounting /dev/hdb2 on / root failed: invalid and whatever else it says might be referring to. 

So: I have windows xp pro (sp2) installed on an NTFS partition on the primary master drive. ON my second hard drive - the slave - I now have three partitions, one in NTFS (98gb), and the other two which Ubuntu automatically created from what was designated freespace: one logical drive of 2.26GB where I assume Ubuntu is installed and another 'primary' (according to windows disc manager) partition of 52.75gb.

Does this help anyone to help me in anyway? Hope so. Is it just something to do with grub? Does windows mess about with the mbr or something?? I am so in the dark about all these things so I'd be hugely grateful for any advice ...

cheers

---

### Post by TestUser on 2005-11-28
Hi

First I have to add I am no expert but I hope I can guide you anyway.
I have dual boot but only one HDD, else seems to be the same. 
Since you had it working you got grub installed at master when you installed.

Do you get the grub menu, if so try to boot in recover and write fixmbr .
I had problem with grub once, I installed a encryption SW in windows that messed up the mbr and I managed to solve it by using the live cd. 
I think this is the way to go and check so your partitions are correct. Sometimes it is tricky to get them right.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
I know this was not of much help but post again and hopefully someone else can help. If if you might be a bit tired of linux I hope you continue and use it, you wont regret it.


TU

---

### Post by paulf on 2005-11-28
Hi, thanks for that. Yes, I've got grub and it was, and as far as I can tell still is, working. I can boot into windows no worries. I just tried to boot into recovery with ubuntu but I got a worse sequence of errors than before! As far as I can tell my partitions are OK ... I deleted a large space on my second hard drive and allowed Ubuntu to partition that automatically. I find it really odd that Ubuntu works fine and repeatedly only until I boot windows again. I know the easy answer is for me to ditch windows (and maybe I will eventually) as it is obviously windows that is causing the problem, but for now it isn't practical for me to do that. 

Is it right for me to assume that as Ubuntu begins to boot and that as windows does boot Grub is fine?

I'm going to delete it all again anyhow and go through all the windows fixmbr hassle one more time. Hopefully some solution will appear soon and the free space will be waiting! I'm very keen to get using something linux based so I'm not about to give up.

---

### Post by Patsoe on 2005-11-28
yes, I think Grub is ok, from what you're describing. (but I'm not an expert either...) It works since it boots Windows, and gets to the point where Linux wants to mount partitions.
It has nothing to do with 64bit and 32bit OS'es clashing either. These run separately.

Usually, Windows doesn't mess with the mbr (only when you're installing it), but it seems as if it changes your second hard disk setup in this case.

Maybe the partitioning scheme is not accepted by Windows? Does Windows mention that it is correcting any file systems on boot?
Alternatively, is one of the drives a SATA drive (in that case, perhaps it is running in compatibility mode under Linux, then changes to another mode because Windows has drivers for it - and then it looks wrong to Windows?)?

Sorry, my guesswork may only confuse. The last time I looked into such problems was with Windows98 which got all messed up if a drive had more than one primary partition. I think that problem does not affect WinXP.

---

### Post by paulf on 2005-11-28
Windows obviously does, or at least did, something when it first boots after Ubuntu has been installed. Unsurprisingly it has never told me that it was doing anything. Also I'm pretty sure both my HDs are IDE. I don't have a huge amount of time right now but I imagine the error messages I got when trying to start Ubuntu in recovery mode could shed some light ... I hope so. They set out differently but terminate with the same line as the normal disastrous boot. I'll have a look tomorrow, and maybe post what it says. 

Also, my second HD has only got 40gb worth of data on it. Perhaps - and this is probably a very obvious next step!! - I ought to move all that over to the disc with windows and dedicate the second one entirely to Ubuntu?? I don't know if the lack of physical proximity makes any difference tho.   

Thanks for the help anyhow!!:smile:

---

