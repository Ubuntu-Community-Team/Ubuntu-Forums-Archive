---
title: "Looking for full 64 bit wireless networking"
date: 2005-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Convert on 2005-08-02
Hi everyone.  I've been secretly  ;-)  using everyone's posts to work on getting my wireless connection up and running.  To that end, I have a few questions for all of you out there who have also been involved in the same goal, and hopefully I can make some small contribution as well by the time I get this figured out...

First, let me say I a doing this on an eMachines M6811 with the AMD64 Athlon cpu and the broadcom wireless card that comes from the manufacturer.  I know that many of you have a very similar (if not the same) machine.

Second, I need to get a full 64 bit implementation of 802.11g with WPA-PSK working.  My network requires the WPA-PSK and the SSID is not broadcast.

I have installed the 32 bit version of Ubuntu on the machine in the past and I could see that the 32 bit version of ndiswrapper was supported.  However, when I install the 64 bit version of Ubuntu, ndiswrapper is not listed, which I assume means that it is not officially supported by Ubuntu.

One question I have about all of the work being done by this (fine) community...I have not seen anyone create a 64 bit version of ndiswrapper yet you are all using ndiswrapper.   So, are you guys running the 32 bit version?  Or is there a 64 bit version that everyone knows about but me (if so, where would it be found)?  Or did everyone compile their own deb package?

Assuming that you guys can point me to a 64 bit version of ndiswrapper, I have rounded up all of the dependent packages required to enable WPA-PSK functionality using wpasupplicant to the wireless connection.  Here is the list and I would request if someone would be so kind as to grade my research (I am also listing them in the order that I think they should be/must be installed):

ndiswrapper (unknown location)

libgcc1_4.0.1-3_amd64.deb
[http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/g/gcc-4.0/libgcc1_4.0.1-3_amd64.deb](http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/g/gcc-4.0/libgcc1_4.0.1-3_amd64.deb)

libc6_2.3.2.ds1-22_amd64.deb
[http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/g/glibc/libc6_2.3.2.ds1-22_amd64.deb](http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/g/glibc/libc6_2.3.2.ds1-22_amd64.deb)

libssl0.9.7_0.9.7g-1_amd64.deb
[http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/o/openssl/libssl0.9.7_0.9.7g-1_amd64.deb](http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/o/openssl/libssl0.9.7_0.9.7g-1_amd64.deb)

wpasupplicant_0.4.2-1_amd64.deb
[http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/w/wpasupplicant/wpasupplicant_0.4.2-1_amd64.deb](http://mirror.espri.arizona.edu/debian-amd64/debian/pool/main/w/wpasupplicant/wpasupplicant_0.4.2-1_amd64.deb)

I would also ask if anyone has an opinion on a good HOWTO for using wpasupplicant.  I have read a number of posts regarding wpasupplicant but I would have to say most of them assume a person knows a lot more than the basics or they tend to start strong but trail off in the end so that a newbie like me gets lost before we reach a successful implementation.

On the other hand, if there is a better (make that easier) package that would enable WPA-PSK for a wireless connection, I would be interested in hearing about that also.

Thanks for your input in advance.  Looking forward to any feedback.

:D

---

### Post by hod139 on 2005-08-02
ndiswrapper is in the queue [here](http://ubuntuforums.org/showthread.php?t=48905)

---

### Post by tmilam on 2005-08-18
I built ndiswrapper from source :)

wpa-supplicant....I had trouble finding a guide for that too! 

The problem with ndiswrapper on ubuntu amd64 is that alot of the .inf files that are written for wireless cards are 32 bit. You can't use a 32bit driver file with ndiswrapper in a 64 bit environment :(

I wonder if there is someway to emulate stuff in a 64 bit environment? Wish I could help you with a how-to on wpa-supplicant, but I never really found one.....

---

### Post by amastronardi on 2005-08-19
I downloaded standard winXP driver and it works fine on my adm64. 
Are you sure that your ndiswrapper compilation was successful? Do you have the file /sbin/loadndisdriver ?

Cheers, Adrian.

---

### Post by tmilam on 2005-08-20
Turns out I was using the wrong .inf file. Works fine now :D

---

### Post by texasflyfisher on 2005-09-02
[QUOTE=tmilam]Turns out I was using the wrong .inf file. Works fine now :D[/QUOTE]

I am trying to do the same. Which one did you use? I built ndiswrapper version 1.2 and have the /sbin/loadndisdriver and when i added the ndiswrapper to /etc/modules it gave some errors about loading that looks like this:

ndiswrapper (ndiswrapper_load_driver:93): loadndiswrapper failed (9); check system log for messages from 'loadndisdriver'

I get a message before that that says apperently after checking the NT header, that the driver is not 64-bit.

I used the Win XP driver version 06/17/2004,6.0.5.30 of the NetGear wg311v2 card. Where can I get the 64-bit version?

---

### Post by tmilam on 2005-09-02
It's hard to know what wireless driver you need without knowing the actual chipset. You can find this out by running lspci. For example:

```

$lspci
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

A bunch of other hardware should show up too. You'll need to find the section dealing with your wireless card. From there you can better determine what driver you need, and if there is a 64 bit driver available. For *my* card the most relevant section was 'BCM4318'. It was hard to find a 64 bit driver for it, but I found one [here](http://runithard.com/HOWTO-BCOM64WIRELESS/).

---

### Post by mlomker on 2005-09-02
Not that many companies have 64-bit drivers available...and even then generally only on their very last products.  You're looking for a Windows XP 64-bit driver and Netgear's website would be the first place to check...their docs don't mention 64-bit, though.

[Netgear](http://kbserver.netgear.com/products/WG311v2.asp) 

You could try lspci to see if it uses a generic chipset...that way you could see if another manufacturer has written a driver for their card.

---

### Post by h17m4n on 2005-09-02
Since this thread is about 64-bit wireless, I'll ask you guys this question(which is related to it).

When I follow these lines:
> 
wget [http://aleron.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.1.tar.gz](http://aleron.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.1.tar.gz)
tar -xzvf ndiswrapper-1.1.tar.gz
cd ndiswrapper-1.1
make
make install


Does it compile ndiswrapper in the same architecture as the distro is based or what? If so, in my case it was made into amd64?

---

### Post by jpasini on 2006-10-01
Hello,

I have a netgear wg311v3 pci card and tried to install drivers via ndiswrapper. As most of you are now aware, the windows drivers are 32bit and won't work on amd64. So I have two questions:

1) Is there a way of making this card work under amd64 linux?

2) If not, what pci card will work in a simple manner? I'm willing to go out and buy one that will work.


To give you a sense of the things I've looked at, here's some background:

I was a confused at first, because I get this message that seems to say that everything's fine:

> ndiswrapper -l
Installed ndis drivers:
wg311v3         driver present, hardware present

But then dmesg has this message.

> dmesg | grep ndiswrapper
[   35.417680] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[   35.480298] ndiswrapper (check_nt_hdr:149): Windows driver is not 64-bit; bad magic: 010B
[   35.480303] ndiswrapper (load_sys_files:218): couldn't prepare driver 'wg311v3'
[   35.480646] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

Which is what we've been talking about (Windows driver is not 64-bit). Has anyone here been able to make this work on amd64 in maybe some other way? The wg311v3 has a Marvell chip:

> lspci | grep -i wireless
0000:03:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

And this led me to look at this part of dmesg, which I simply do not understand: is it even relevant to my question?

> dmesg | grep mrv8k
[   27.395678] mrv8k: Marvel 8xxx Wireless driver, 0.0.2
[   27.395681] mrv8k: Copyright(c) 2005 Luc Saillard <luc@saillard.org>
[   27.395709] mrv8k: mrv8k_init_one: enter
[   27.396634] mrv8k: bar1 (0xfdde0000) relocated at 0xffffc20010100000
[   27.396637] mrv8k: bar2 (0xfddd0000) relocated at 0xffffc20010120000
[   27.537459] mrv8k: Firmware 'mrv8k-b.fw' not available or load failed.
[   27.537463] mrv8k: mrv8k_init_one: return -2
[   27.537467] mrv8k: Command SET_RADIO. len=12 state=off preamble=auto
[   27.537470] mrv8k: queue command (ffff810039a69400)
[   27.537472] mrv8k: kickoff command (ffff810039a69400)
[   28.565333] mrv8k: mrv8k_init_one: return -2
[   28.565336] mrv8k: probe of 0000:03:0a.0 failed with error -2

For reference,

> uname -a
Linux cavafy 2.6.15-27-amd64-generic #1 SMP PREEMPT Sat Sep 16 01:50:50 UTC 2006 x86_64 GNU/Linux


Thanks in advance,
Jose Miguel Pasini

---

### Post by noeldescallar on 2006-10-01
We tried D-LINK G510 wireless lan for our 64bit sempron using the ubuntu os 64bit, it's working fine, plug and play. :)

---

### Post by Sohum on 2006-11-09
**bump**
Just to second jpasini's request. Am using Netgear wg311v3, chipset Marvell 88w8335.

---

