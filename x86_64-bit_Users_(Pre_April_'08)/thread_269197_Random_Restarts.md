---
title: "Random Restarts"
date: 2006-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by csadowski on 2006-10-01
I keep getting random restarts overnight, and I'm unsure as to why.  This is what my system log gives:

Oct  1 05:41:18 localhost -- MARK --
Oct  1 06:01:18 localhost -- MARK --
Oct  1 06:21:19 localhost -- MARK --
Oct  1 06:41:19 localhost -- MARK --
Oct  1 07:01:19 localhost -- MARK --
Oct  1 07:21:19 localhost -- MARK --
Oct  1 07:41:20 localhost -- MARK --
Oct  1 07:48:04 localhost exiting on signal 15
Oct  1 07:48:05 localhost syslogd 1.4.1#17ubuntu7: restart.
Oct  1 08:08:05 localhost -- MARK --
Oct  1 08:28:05 localhost -- MARK --
Oct  1 08:48:05 localhost -- MARK --
Oct  1 09:08:06 localhost -- MARK --
Oct  1 09:28:06 localhost -- MARK --
Oct  1 09:48:06 localhost -- MARK --
Oct  1 10:08:06 localhost -- MARK --



any ideas as to why this could be happening?

---

### Post by csadowski on 2006-10-01
The last time i touched the computer was about 3:58, and then again around 11:07.  Everything in between those times is when it happened.



here is the whole log:

Oct  1 00:01:14 localhost -- MARK --
Oct  1 00:21:14 localhost -- MARK --
Oct  1 00:41:14 localhost -- MARK --
Oct  1 01:01:15 localhost -- MARK --
Oct  1 01:21:15 localhost -- MARK --
Oct  1 01:41:15 localhost -- MARK --
Oct  1 02:01:15 localhost -- MARK --
Oct  1 02:05:43 localhost kernel: [ 4572.806726] blender-bin[9291]: segfault at 0000000000000000 rip 0000000000000000 rsp 00007fffffefb9f8 error 14
Oct  1 02:17:10 localhost gconfd (root-9674): starting (version 2.14.0), pid 9674 user 'root'
Oct  1 02:17:10 localhost gconfd (root-9674): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct  1 02:17:10 localhost gconfd (root-9674): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Oct  1 02:17:10 localhost gconfd (root-9674): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct  1 02:17:10 localhost gconfd (root-9674): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct  1 02:17:10 localhost gconfd (root-9674): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Oct  1 02:18:40 localhost gconfd (root-9674): GConf server is not in use, shutting down.
Oct  1 02:18:40 localhost gconfd (root-9674): Exiting
Oct  1 02:41:16 localhost -- MARK --
Oct  1 03:01:16 localhost -- MARK --
Oct  1 03:21:16 localhost -- MARK --
Oct  1 03:41:17 localhost -- MARK --
Oct  1 03:45:46 localhost gconfd (root-12534): starting (version 2.14.0), pid 12534 user 'root'
Oct  1 03:45:46 localhost gconfd (root-12534): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct  1 03:45:46 localhost gconfd (root-12534): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Oct  1 03:45:46 localhost gconfd (root-12534): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct  1 03:45:46 localhost gconfd (root-12534): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct  1 03:45:46 localhost gconfd (root-12534): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Oct  1 03:46:46 localhost gconfd (root-12534): GConf server is not in use, shutting down.
Oct  1 03:46:46 localhost gconfd (root-12534): Exiting
Oct  1 04:01:17 localhost -- MARK --
Oct  1 04:18:10 localhost gconfd (sadowski-5152): Received signal 15, shutting down cleanly
Oct  1 04:18:10 localhost gconfd (sadowski-5152): Exiting
Oct  1 04:18:13 localhost gconfd (sadowski-13453): starting (version 2.14.0), pid 13453 user 'sadowski'
Oct  1 04:18:15 localhost gconfd (sadowski-13453): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct  1 04:18:15 localhost gconfd (sadowski-13453): Resolved address "xml:readwrite:/home/sadowski/.gconf" to a writable configuration source at position 1
Oct  1 04:18:15 localhost gconfd (sadowski-13453): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct  1 04:18:15 localhost gconfd (sadowski-13453): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct  1 04:18:15 localhost gconfd (sadowski-13453): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Oct  1 04:18:43 localhost gconfd (sadowski-13453): GConf server is not in use, shutting down.
Oct  1 04:18:43 localhost gconfd (sadowski-13453): Exiting
Oct  1 04:41:18 localhost -- MARK --
Oct  1 05:01:18 localhost -- MARK --
Oct  1 05:21:18 localhost -- MARK --
Oct  1 05:41:18 localhost -- MARK --
Oct  1 06:01:18 localhost -- MARK --
Oct  1 06:21:19 localhost -- MARK --
Oct  1 06:41:19 localhost -- MARK --
Oct  1 07:01:19 localhost -- MARK --
Oct  1 07:21:19 localhost -- MARK --
Oct  1 07:41:20 localhost -- MARK --
Oct  1 07:48:04 localhost exiting on signal 15
Oct  1 07:48:05 localhost syslogd 1.4.1#17ubuntu7: restart.
Oct  1 08:08:05 localhost -- MARK --
Oct  1 08:28:05 localhost -- MARK --
Oct  1 08:48:05 localhost -- MARK --
Oct  1 09:08:06 localhost -- MARK --
Oct  1 09:28:06 localhost -- MARK --
Oct  1 09:48:06 localhost -- MARK --
Oct  1 10:08:06 localhost -- MARK --
Oct  1 10:28:07 localhost -- MARK --
Oct  1 10:48:07 localhost -- MARK --
Oct  1 11:07:19 localhost gconfd (sadowski-14073): starting (version 2.14.0), pid 14073 user 'sadowski'
Oct  1 11:07:19 localhost gconfd (sadowski-14073): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct  1 11:07:19 localhost gconfd (sadowski-14073): Resolved address "xml:readwrite:/home/sadowski/.gconf" to a writable configuration source at position 1
Oct  1 11:07:19 localhost gconfd (sadowski-14073): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct  1 11:07:19 localhost gconfd (sadowski-14073): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct  1 11:07:19 localhost gconfd (sadowski-14073): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Oct  1 11:07:21 localhost gconfd (sadowski-14073): Resolved address "xml:readwrite:/home/sadowski/.gconf" to a writable configuration source at position 0
Oct  1 11:28:07 localhost -- MARK --
Oct  1 11:48:08 localhost -- MARK --

---

### Post by John.Michael.Kane on 2006-10-01
It would help if you told us what your machine spec's are,and if the machine is overclocked. what add on cards are inside said machine.

---

### Post by csadowski on 2006-10-01
Processor 	AMD Athlon 64 3200+(2.0GHz)
Processor Main Features 	64 bit Processor
Cache Per Processor 	512KB L2 Cache
Memory 	1GB DDR400
Hard Drive 	160 GB
Optical Drive 1 	16X DVD±RW Drive
Graphics 	NVIDIA Geforce 6150
Audio 	AD1986A 5.1 Channels
Ethernet 	Marvell Gigabite Lan
Power Supply 	300W


Motherboard
Chipset 	NVIDIA nForce6150
Motherboard Name 	ASUS A8N-VM CSM Socket 939 NVIDIA GeForce 6150 Micro ATX

CPU Type 	Athlon 64
Installed Qty 	1
CPU Speed 	3200+
L2 Cache Per CPU 	512KB
CPU Socket Type 	Socket 939
CPU Main Features 	64 bit Processor

GPU/VPU Type 	NVIDIA GeForce 6150
Graphics Interface 	Integrated video

Memory Capacity 	1GB DDR
Memory Speed 	DDR400
Form Factor 	DIMM 184-pin
Memory Spec 	512MB x 2
Memory Slots (Available/Total) 	2/4
Maximum Memory Supported 	4GB

HD Capacity 	160GB
HD Interface 	PATA
HD RPM 	7200rpm

Optical Drive Type 	DVD±RW
Optical Drive Spec 	Write Speed:
DVD+R 16X, DVD+RW 8X, DVD-R 16X, DVD-RW 6X, CD-R 48X, CD-RW 32X, DVD+R DL 8X, DVD-R DL 6X
Read Speed:
DVD-ROM 16X; CD-ROM 48X

Audio Chipset 	AD1986A
Audio Channels 	5.1 Channels
Communications
LAN Chipset 	Integrated
LAN Speed 	10/100/1000Mbps
Front Panel Ports
Front USB 	2
Front Audio Ports 	2
Back Panel Ports
LPT 	1
PS/2 	2
VGA 	1 VGA, 1 DVI
Rear USB 	4
Rear IEEE 1394 	1
RJ45 	1 port
Rear Audio Ports 	3 ports

Expansion:
External Bays 	4 x 5.25"
2 x 3.5"
Internal Bays 	4 x 3.5"
PCI Slots (Available/Total) 	PCI Express x16: 1
PCI Express x1: 1
PCI Slots: 2
Storage Controller 	PATA 2 x ATA100 up to 4 Devices
SATA II: 4
SATA RAID: RAID 0/1/0+1/5
Physical Spec
Dimensions 	21.2" x 8.8" x 18.2"

---

### Post by csadowski on 2006-10-01
oh, and the machine is not overclocked

---

### Post by John.Michael.Kane on 2006-10-01
What are you using the machine for. is it doing heavy rendering ie: blender.


It does not look like a kernel panic,however. it does look like a program crashed taking gconf with it.


The reason i asked about blender is this line.
[B]Oct 1 02:05:43 localhost kernel: [ 4572.806726] blender-bin[9291]: segfault at 0000000000000000 rip 0000000000000000 rsp 00007fffffefb9f8 error 14 
[/B]
It stating that blender is segfaulting.

---

### Post by csadowski on 2006-10-01
I did try to start blender at one point, but that didn't work. I haven't used blender for anything at all tho. I haven't been using the machine for anything heavy, I guess the heaviest its experienced so far is playing movies.

a few days ago I did follow this guide to get compiz and xgl running:
[http://ubuntuforums.org/showthread.php?t=133427](http://ubuntuforums.org/showthread.php?t=133427)

I did comment out the lines that say, because I thought maybe they wer causing problems:
[server-Standard]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer -kb
flexible=true


could any of the above be causing any problems?

---

### Post by John.Michael.Kane on 2006-10-01
That guide might be the cause,however. i have not used that guide for compiz,and from what i understand compiz is being overhauled. 

You could try using dapper with out compiz to see if you still get segfaults,and random reboots.

---

### Post by csadowski on 2006-10-01
yeah this has been happening when I wasn't running compiz, but was using GNOME.  Compiz is installed, but not running. neither is xgl.

---

### Post by phibxr on 2006-10-01
I have this exact problem with the same CPU, although running in 32 bit mode instead of 64. Same messages. My card is NVidia, and yet it crashes while I'm even not running accelerated applications.

---

### Post by John.Michael.Kane on 2006-10-01
What version of nvidia drivers are you both using?

---

### Post by phibxr on 2006-10-02
The current Dapper drivers in the reps. I'm running Ubuntu 64 bits now to see if it in any magical way helps as I have an Athlon 64.

---

### Post by endlesssnowfall on 2006-10-02
I and some others have been having the same problem: [http://www.ubuntuforums.org/showthread.php?t=245216&highlight=random+restart](http://www.ubuntuforums.org/showthread.php?t=245216&highlight=random+restart)

We haven't been able to figure much out yet.

---

### Post by John.Michael.Kane on 2006-10-02
This is odd as i have almost the same setup as the OP just that mines is a Geforce 6100,and 3000+. no random restarts

I'm using the drivers from this guide [http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

---

### Post by csadowski on 2006-10-02
note: I tried using KDE desktop to see if a random restart would happen and it did not, at least in the past 12 or so hours.

---

### Post by Subnet on 2006-11-13
Has anyone found a solution for this problem? I have the exact same processor and using the x86 version of Edgy. However, the random restarts just started happening in the past few days. Any help would be great.](*,)

---

