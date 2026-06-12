---
title: "Ubuntu freezes with keyboard lights flashing"
date: 2008-05-26
forum: x86 64-bit Users
---

### Post by beatzombies on 2008-05-26
Hello,

So I just performed a fresh install of Ubuntu 8.04 on my desktop. It is an AMD 64-bit processor set up with 2 harddrives as a RAID0 array. Every so often, I experience a complete lockup of my system and and my keyboard lights start flashing. I can't use my mouse or keyboard and am forced to do a hard reset every time it happens.

There does not appear to be a rhyme or reason as to why this happens. Sometimes it does not occur for quite some time, and sometimes it occurs after a couple of minutes. And it does not appear to be based on what application I am using at the time.

I tried to figure out what was going on by looking at the system log, but I can't find anything that screams out to me (then again, I have no idea what to look for).

I also installed the non-supported ATI drivers for my graphics card, but I'm not sure if that could be the cause.

Any help or even a place to start looking for a problem would be _immensely_ appreciated.

Please let me know what kind of information about my system would be helpful in tracking down this problem and I will post it.

---

### Post by Sukarn on 2008-05-27
I'm sorry, I cannot help much in fixing the issue, but what you're facing is a kernel panic (kernel lock-up). There's some code in the kernel that makes all three of the keyboard LEDs flash when the kernel locks up.

For starters, you could try disabling the ATI drivers and using the VESA drivers for a couple of days and see whether you still get the kernel panic. If it still happens, then its not being caused by the ati drivers. In this case, you can try to install and run a different kernel from synaptic (look for package names starting with linux-image) or you can try compiling your own kernel.

If you do not know how to do something that I suggested, then please post back and I will try to help you with it.

---

### Post by pbeesley on 2008-05-27
OK I'm getting the same thing but I'm using the Nvidia drivers, its only started happening the last couple of days (also only 2 of my keyboard lights flash?) anyway I've started making a note of when it happened on mine ;

* While blanking a DVDRW
* While writing a DVDRW
* While playing music in amarok and coping data from NTFS drive to second NTFS drive

It always seems to happen when I'm doing something....so I don't think its that random on mine :(

---

### Post by beatzombies on 2008-05-27
Alright, so I tried disabling those ATI drivers and it still happened. 

Pbeesley: I think  you're right. I left my computer alone for a couple of hours a few times and nothing happened. It does seem to only occur when I'm browsing the web or playing a game or doing *something*.

I will try what you suggested, Sukarn, and download a new kernel. I will post back with my results.

Is there a log anywhere that would help in tracking down exactly what could be causing the kernel panic?

Thank you so much for getting back to me promptly guys. I'll let you know what happens.

---

### Post by Sukarn on 2008-05-27
Unfortunately, I am not well versed with the kernel. I just know bits and pieces of it. I'm sure someone else in this forum can help you two much better with this issue than I can.

---

### Post by dichtbijzee on 2008-05-27
This totally seems to be a hardware related issue, especially for pbeesley.

Only when you use a lot of power (dvd/2hd's) it happens. try upgrading your PSU.

This can be the problem for beatzombies as well.

---

### Post by pbeesley on 2008-05-27
> **dichtbijzee said:**
> 
Only when you use a lot of power (dvd/2hd's) it happens. try upgrading your PSU.

huh that might be bang on, thinking back this could be due to the fact I just installed a 4 port USB thingy into a spare PCI slot. I wonder if this could be the issue? what do you think? :confused:

---

### Post by dichtbijzee on 2008-05-27
I think it is, try doing stuff without the pci-card, try and disconnect as many things as you can;

spare HD's,
any other addon cards except your graphic card of course,
all but one stick of ram,
dvd/cd drives.

This will hopefully help you.

---

### Post by pbeesley on 2008-05-27
yeah I might try using everything at once and see if that kills it, then unplug new pci card and try test again. I'll let you know how it goes

---

### Post by Chriis on 2008-05-27
I dont want to troll , but if it can help ,..

I had this bug which freeze with kernel panic ( keyboard led flashing )
but since kernel update to 2.6.24-17 i do not experience it anymore. 

Do ya?

Chriis

---

### Post by beatzombies on 2008-05-28
> **Chriis said:**
> I dont want to troll , but if it can help ,..

I had this bug which freeze with kernel panic ( keyboard led flashing )
but since kernel update to 2.6.24-17 i do not experience it anymore. 

Do ya?

Chriis

I see that I am still running 2.6.24-16-generic. How would I go about upgrading to the newest kernel?

Sukarn suggested installing another kernel from Synaptic. I tried installing an amd64 I saw there, but after I did there was not a new kernel available from the grub boot menu nor was there anything new in my /usr/src/ folder. I think perhaps I am doing something wrong. If anyone could point me in the right direction it would be appreciated.

As for the power issue suggestion: I will try unplugging my extra stick of RAM and DVD drive to see if that makes a difference.

Thank you everyone for posting suggestions, I didn't expect this kind of support so quickly!

---

### Post by Megatog615 on 2008-05-28
Try enabling the additional repositories(like the Proposed updates repository) in Software Sources, let it update, then install the new kernel.

---

### Post by beatzombies on 2008-05-28
Thanks for the tip Megatog.

Alright, so I am now running the new kernel 2.6.24-17-generic.

I will try and run things normally for a while and see if I get that kernel panic to occur again.

---

### Post by pbeesley on 2008-05-28
I have no idea what kernal I'm running. I have Hardy Heron installed? anyway I took the USB card out last night and no freezes yet :)

---

### Post by beatzombies on 2008-05-28
> **pbeesley said:**
> I have no idea what kernal I'm running. I have Hardy Heron installed? anyway I took the USB card out last night and no freezes yet :)

That's great, I haven't had anything happen since upgrading my kernel, but I'm still a bit apprehensive.

If you want to find out what kernel you are running, you can type

```
uname -r
```

into a terminal and it will print out what version you are using.

---

### Post by beatzombies on 2008-05-28
Well things were running well for some time, but unfortunately I just had another kernel panic :(.

I did run with one less stick of RAM, but I left my DVD drive plugged in. It seems odd to me that this could be a power related issue because the panic did not occur when I suddenly started a large number of applications, but only after running a constant number of applications for a while. Also, at no point in time did I use my DVD drive.

So it seems my problem might not necessarily be related to the kernel I am using.

I decided to do some more snooping and I found something interesting in my syslog around the time when the kernel panic occurred. The following entry is repeated over and over again:

```

May 28 01:30:59 mdmshuttle kernel: [   43.786752] sda: rw=0, want=285153755, limit=145226112
May 28 01:30:59 mdmshuttle kernel: [   43.786754] attempt to access beyond end of device
May 28 01:30:59 mdmshuttle kernel: [   43.786755] sda: rw=0, want=285153756, limit=145226112
May 28 01:30:59 mdmshuttle kernel: [   43.786757] attempt to access beyond end of device
May 28 01:30:59 mdmshuttle kernel: [   43.786758] sda: rw=0, want=285153757, limit=145226112
May 28 01:30:59 mdmshuttle kernel: [   43.786760] attempt to access beyond end of device
May 28 01:30:59 mdmshuttle kernel: [   43.786761] sda: rw=0, want=285153758, limit=145226112
```

I cut out a lot of it for brevity's sake. As far as I can tell, the only thing changing between the entries is the value for 'want'.

I do not understand what these entries mean other than the fact that they pertain to one of my hard drives and is probably related to the fact that I have 2 hard drives in a RAID0 array.

If anyone could provide some insight as to what could possibly be causing this type of behavior, it would be greatly appreciated.

---

### Post by alcfez on 2008-05-28
Hello,
We have the same issue [here.]("http://ubuntuforums.org/showthread.php?p=5061062#post5061062")

Can some one please HELP!!!!!!!!!!!!!!!!!

---

### Post by beatzombies on 2008-05-30
I decided to try an experiment to figure out when these kernel panics actually happen. I downloaded and installed wine and installed Steam. Then I left Steam downloading CS:S overnight, an operation that would use my internet connection as well as my hard drives.

I wake up in the morning and my computer is still running happily. This seems extremely strange. I have left my computer alone for large periods of time and this time even performing an actual task and nothing has gone wrong. The ONLY times I have seen that my computer has gone into a kernel panic is if I am sitting there and actively using it.

I'm not sure if this is a symptom of the underlying problem, or if I have just gotten so lucky that each time I leave my computer alone for extended periods of time, it avoids having a kernel panic.

Has anyone experienced a similar problem or have any suggestions for how to hunt down what's at the bottom of this?

---

### Post by beatzombies on 2008-05-30
Woops, double post.

---

### Post by pbeesley on 2008-05-30
Can I suggest mouse movment? I left my PC on yesterday downloading torrents (legal ones! :S !), ripping a movie (for backup purposes) and downlaoding some other stuff as well. no crashes! got home went to browse to were the film had ripped to and BAM! instant crash. Maybe it has something to do with compiz?  I'll do some tests

---

### Post by aaron.d on 2008-05-30
That's a good idea. I hate to state the obvious, or be repetitive, but things that require extra hardware accelleration, or offer a non essential service should definitely be turned off when troubleshooting.

If dmesg etc isnt giving you any leads, and a kernel upgrade still panics, then you'll have to use plain scientific method to deduce the issue. Start a non-accelerated x session (remove any proprietary drivers, as mentioned before). test, if you still get issues, try disabling other modules, for your sound card perhaps. if you get down to a bare shell software wise, that still gives you panics, then you can start REMOVING hardware, one peice at a time. Test memory (using memtest86, which should be on the Ubuntu cd) and remove any non essential cards, drives etc.
You cant go half asseed at this, try one thing, then entirely change your direction and try another, do it logically and im sure you will find the bug eventually.
Trickier porblems are with PSU (mentioned) and motherboard, since this generally contains controller cards that you, obviously, cant remove.
Check your bios for any onboard things that can be disabled too.

good luck

---

### Post by beatzombies on 2008-06-04
I thought this might be of interest. Sometimes when a panic occurs and I simply reset my computer instead of shutting it down, waiting, and starting it back up again, I get a kernel panic at boot. I copied down what I thought were the important parts of the message I get when this occurs:

direct mapping tables up to 100000000 @ 8000-d000

Call trace:
free_hot_cold page +0x170/0x1a0
free_init_pages +0x49/0xe0
free_initrd +0x57/0xd0
populate_rootfs +0xdb/0xf0
kernel_init +0x164/0x350
child_rip +0xa/0x12
kernel_init +0x0/0x350
child_rip +0x0/0x12

Code: 48 8b 03 4c 8b 06 48 c1 e8 38 4c 89 c2 48 c1 ea 38 39 d0

RIP free_pages_bulk +0x188
kernel panic - not syncing : Attempted to kill init


Is there anyone smarter than me that can interpret what this might mean or point me to somewhere that explains this? I omitted what I took to be memory addresses from the post for brevity's sake.

Also, I will try incrementally disabling stuff to try and narrow down what's causing the problem.

---

### Post by eduardoeltortuga on 2008-06-05
I've been experiencing the same problem. Call me crazy, but I think it's Firefox issue. Every time it happens, I just opened up firefox. My windows XP partition crashes sometimes as well. When it does happen, it's just when I open Firefox.:-?

---

### Post by Sukarn on 2008-06-06
> **eduardoeltortuga said:**
> I've been experiencing the same problem. Call me crazy, but I think it's Firefox issue. Every time it happens, I just opened up firefox. My windows XP partition crashes sometimes as well. When it does happen, it's just when I open Firefox.:-?

o.O
maybe your computer hates firefox.

---

### Post by beatzombies on 2008-06-15
So I think I figured out what the problem was. I had checked to see if my computer was overheating and thus causing a kernel panic early on by doing  ```
cat /proc/acpi/thermal_zone/THRM/temperature
```. I didn't notice that this temperature reading always stayed at 40 C and didn't indicate my actual temperature. I tried sensors instead and saw my computer was running at a scorching 60 C when being actively used. I got fancontrol running on my computer to make sure the temperature stays reasonably low and that seems to have stopped the panics so far.

My computer still freezes occasionally (but much less frequently), however I think this may be a different problem because the screen goes blank and the mouse stops working, but my keyboard appears to continue functioning.

Lesson learned: double check the temperature of your computer to make sure overheating isn't the cause of your problems.

---

### Post by DR1665 on 2008-08-01
Hello world!

First post over here.  Sorry to be bumping an older thread and really hope I'm in the right area.  Used the search before joining and this is the first problem annoying enough that I feel I should chime in.

I am really new to Linux, but I'm picking it up (as most people do) through playing around with it.  So far, I really love it.  This kernel panic deal is bogus, though.

System:
Dell Inspiron 1521 laptop, AMD Turion 64X2, running Gutsy 7.10 - kernel = 2.6.22-15-generic
(I had to have a long time Linux buddy help me out to get a bunch of random things working, so I'm hesitant to step up.  Been running with just the updates since April 08.)


Kernel panic seems to have been happening randomly lately.  Pulled my logs  tonight and didn't see the same thing as the OP earlier.  Here's what I get just before the restart:

```
Jul 31 18:36:14 driggs-laptop kernel: [  212.176000] audit(1217554574.445:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5223 profile="/usr/sbin/cupsd"
Jul 31 18:36:15 driggs-laptop kernel: [  212.348000] apm: BIOS not found.Jul 31 18:36:15 driggs-laptop kernel: [  212.348000] apm: BIOS not found.2.

Jul 31 20:29:38 driggs-laptop kernel: [   29.276000] audit(1217561378.139:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5197 profile="/usr/sbin/cupsd"
Jul 31 20:29:38 driggs-laptop kernel: [   29.336000] apm: BIOS not found.
```

Part of me wonders if this isn't shenanigans resulting from having to hard boot the machine once the panic sets in and it's completely frozen.  Other entries in the log look suspicious as well...

```
Jul 29 20:15:02 driggs-laptop kernel: [   50.692000] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul 29 20:15:21 driggs-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jul 29 20:15:28 driggs-laptop kernel: [   77.364000] NET: Registered protocol family 17
Jul 29 20:15:38 driggs-laptop kernel: [   86.744000] NET: Registered protocol family 10	
Jul 29 20:15:38 driggs-laptop kernel: [   86.744000] lo: Disabled Privacy Extensions
Jul 29 20:15:38 driggs-laptop kernel: [   86.744000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 29 20:15:40 driggs-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Jul 29 20:15:40 driggs-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Jul 29 20:34:36 driggs-laptop -- MARK --
Jul 29 20:34:36 driggs-laptop -- MARK --
Jul 29 20:34:36 driggs-laptop -- MARK --
```

I wonder if it's just one or more of the updates I've been installing as they become available running into issues with the older kernel. :confused:  I like seeing regular updates for Ubuntu because I know it means there's people out there doing some good in the world, rather than the Windows updates, which signify Microsoft still not having their ish together on an overpriced product.  :)

Any help or comments is greatly appreciated!

---

### Post by mp035 on 2008-09-04
Hi All, I am experiencing the same problems, only recently.

My system is Intel 2160 (2x64) Nvidia 7?00 GT 2GB ram.

No problems until I pulled an old (Dlink) wifi card out of the cupboard.

This card has always been awful under linux (that's why it was in the cupboard.)

The card uses the Ralink 2561 chipset which uses the (rt61.ko) RT61 drivers.

Just did an lsmod to check, and these apprear to be the modules that are installed. 

rt61pci                27648  0 
rt2x00pci              12800  1 rt61pci
rt2x00lib              25344  2 rt61pci,rt2x00pci


I see a few people with rt2561 in the 6 pages of this post that I read, so perhaps people should be looking into what drivers/chipset their wifi is using, maybe we'll have a common point?

Thanks to all posters on this thread.:)

---

### Post by mp035 on 2008-09-04
Oh no! the post above was meant for another thread, I have switched to epiphany because I thought firefox was the problem, and It doesnt log in properly.

Sorry all, hope the info helps someone anyway:oops:

---

### Post by elmoosecapitan on 2008-09-05
If both CapsLk AND ScrLk flash the Kernel is PANIC-ing and you have a hardware issue. Try running sensor programs to figure out if it is temperature related, SWAP related, or something of that sort.

---

### Post by maim that tune on 2008-12-17
I had the flashing lights/freeze issue: I went through and uninstalled stuff that I didn't need/want or had downloaded mindlessly... still freezing so I reduced compiz to bare essentials. still getting random freezes so I booted into Vista and surfed this forum till I found a post recommending disabling two boxes in Firefox/preferences/security screen (the two "Tell me..." boxes). Things have run pretty smoothly since then [fingers crossed]

Maim

HP pavilion dv6XXX
Intel Centrino Duo Core 2g
4 GiB RAM
Intrepid Ibex XXX.9

---

