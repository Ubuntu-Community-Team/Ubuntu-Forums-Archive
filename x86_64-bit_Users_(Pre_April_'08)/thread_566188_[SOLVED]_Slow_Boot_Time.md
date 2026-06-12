---
title: "[SOLVED] Slow Boot Time"
date: 2007-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by steveneddy on 2007-10-03
I just installed the 64 bit version of Feisty, and it works very well with the exception of the boot times. It will stop sometime in the middle and just "hang" there for approximately one minute, and then carry on as usual.

Is there a little utility that I could install or a log file that I could, or post, to determine the problem with the long boot times?

I have a Core 2 Duo laptop with 2 gig of RAM. The laptop is fairly new (this year) and is in fine working order.

I have Compiz-Fusion, Adobe and a few other programs installed after the initial installation, but the boot problem was noticed even before the addition of other added software.

Any help appreciated and thank you in advance.

---

### Post by dabl on 2007-10-03
First, immediately after booting you can issue the ```
dmesg
``` command and see if there's anything obvious in the output.

Then there's there's a log file at /var/log/boot.

Probably you want to temporarily remove the "quiet" option from your /boot/grub/menu.lst kernel line, so you can see what's going on at the point when it hesitates.

Here's details about the boot options:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

:)

---

### Post by praxis22 on 2007-10-03
could be disk related, mine sometimes stalls (desktop) as one of my drives is temperamental. Do you have any pluggable drives or USB devices that you could remove etc. see if that speeds it up.

---

### Post by steveneddy on 2007-10-03
I installed bootchart and when I first came home, I had a slow boot, but after looking at the boot options file, I just decided to reboot, and it was so much faster this time.

Here is my boot chart, 1 & 2.

The shorter one is the second boot.

---

### Post by steveneddy on 2007-10-04
Bump (sorry)

can anyone make any sence of these boot time charts?

I have only had one fast boot time, which is the smaller chart.

The rest of the time, the boot hangs about 10 - 15 seconds into the boot process and then after about 30 seconds, it finishes up.

I can't figure it out. 

It only started after I installed the 64 bit version, the 32 bit booted under 30 seconds daily. It may have something to do with bluetooth, which I don't think I have any bluetooth devices or transmitters installed on my laptop, but I noticed that there are listings for software in the Accessories menu now that reference the hardware having Bluetooth set up already.

Maybe it's something with the IPW3945, (I don't know what that is).

I also suspect the networking end of this file, like the dhclient3. Notice how it is active on the chart almost at the beginning of the boot process where there is very little activity, and if you look at the end of the chart, where the boot activity takes back up, look down the list and there is the dhclient3 again.

Maybe I should research this?

Any help accepted and appreciated.

Thanks in advance.

---

### Post by steveneddy on 2007-10-05
My boot time is getting longer and long with each boot. Does anyone have an answer.

I'm trying to make sense of the log files, but I don't know what I'm looking at.

Please help.

---

### Post by chris-m1210 on 2007-10-05
I have the exact same thing going on.  It seems like it has to do with the Intel 3945 Wireless.



[   17.908000] EXT3 FS on sda2, internal journal
[   18.092000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   18.164000] NTFS volume version 3.1.
**[   18.748000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)**
[   61.448000] NET: Registered protocol family 10
[   61.448000] lo: Disabled Privacy Extensions

---

### Post by steveneddy on 2007-10-05
> **chris-m1210 said:**
> I have the exact same thing going on.  It seems like it has to do with the Intel 3945 Wireless.



[   17.908000] EXT3 FS on sda2, internal journal
[   18.092000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   18.164000] NTFS volume version 3.1.
**[   18.748000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)**
[   61.448000] NET: Registered protocol family 10
[   61.448000] lo: Disabled Privacy Extensions

Dang - I wonder what we can do about this? 

Sometimes it boots fast. No problems - others it is very slow.

EDIT:

I just tried rebooting with the wireless turned off at the switch on the laptop. This seemed to help this time, but I will try it again in the morning to see what happens.

---

### Post by chris-m1210 on 2007-10-05
Ooops, never mind.  Not fixed.

---

### Post by steveneddy on 2007-10-06
I think I found my problem, maybe.

I went to the /etc/dhcp3/dhclient.conf file and noticed that it was looking for netbios networks.

I know that netbios networks are almost non existent now a days, so I commented them out this way:

```

request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name;
#netbios-name-servers, netbios-scope;


```

So far it seems to be working. I'll give it a few days and report back.

The log files look like they are better also.

EDIT:

I forgot to mention that if you do that, you have to add the ; to the end of the file.

In other words, change the comma that would normally come after the word "host-name" to the ; symbol.

---

### Post by steveneddy on 2007-10-07
Getting rid of the netbios settings seems to have fixed the problem.

I am marking this solved.

:popcorn:

---

