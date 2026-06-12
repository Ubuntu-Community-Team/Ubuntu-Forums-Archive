---
title: "ndiswrapper driver problems with DWL-G510"
date: 2006-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by UbuntuJohan on 2006-03-18
Hi,

I have a D-link DWL-G510 Rev.C1 wireless PCI card.
It uses the ralink chipset and has pciid 1814:0302

I'm trying to use this card in the AMD64 HTPC I'm building.
I've after som struggle managed to compile and install ndiswrapper
Then I downloaded the driver from D-links swedish homepage
(I think this card revision only is available in europe)
I used the Win2kXp dirver and it installed fine.

```
ndiswrapper -l
Installed drivers:
netrt61g                driver installed, hardware present
```

But when I look in dmesg I get
```
[  406.623367] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[  406.627357] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[ 2730.408766] ndiswrapper version 1.10 loaded (preempt=no,smp=no)
[ 2730.425576] ndiswrapper (check_nt_hdr:149): Windows driver is not 64-bit; bad magic: 010B
[ 2730.425582] ndiswrapper (load_sys_files:213): couldn't prepare driver 'netrt61g'
[ 2730.425788] ndiswrapper (load_wrap_driver:111): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
```

So I guess the driver I got isn't ok to use on AMD64?????
Does anyone have any Idea on where to get a driver????

Thanks!
//Johan

---

### Post by ruudiculus on 2006-03-19
You'll need a 64 bit driver indeed.

You may find it on [www.driverloader.com]("http://www.driverloader.com"). This site also provides a commercial alternative to ndiswrapper, but since your hardware is detected I think you should use ndiswrapper.

If the driverloader site turns our to be of no use to you, you could try to look for 64 bit drivers on Acer or Asus sites for example. I got my HP laptop's driver this way.

Good luck!

---

### Post by UbuntuJohan on 2006-03-19
Thanks for the suggestion, but I have already checked there.
On this card it's a RALINK RT61 chipset which they don't have a driver for.

I found a linux driver at RALINKs home page
[http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm")

But I haven't manged to get that to work either I can see the card in ifconfig and network-admin but as soon as I try to configure it  I think i get a crash in the module and after that ifconfig commands etc just hangs.

Any ideas?

---

### Post by UbuntuJohan on 2006-03-19
Maybe my problem is that I have tried with two many drivers so I now have a conflict??

Here is a dmesg from when I try to do a ifconfig on the card
```
[  235.335439] Unable to handle kernel paging request at 00000000006d3000 RIP:
[  235.335443] <ffffffff881ea270>{:rt2561:RT61_open+51}
[  235.335458] PGD 2b59f067 PUD 38bee067 PMD 0
[  235.335462] Oops: 0000 [1]
[  235.335464] CPU 0
[  235.335466] Modules linked in: ipv6 rfcomm l2cap bluetooth powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi i2c_acpi_ec hotkey dev_acpi container button battery ac af_packet floppy pcspkr rt2561 shpchp pci_hotplug snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc i2c_nforce2 i2c_core dm_mod evdev tsdev rtc psmouse mousedev parport_pc lp parport md jfs thermal processor fan forcedeth ehci_hcd ohci_hcd sd_mod ide_cd cdrom ide_generic sata_nv libata scsi_mod amd74xx ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
[  235.335503] Pid: 7779, comm: ifconfig Tainted: P      2.6.12-10-amd64-generic
[  235.335507] RIP: 0010:[<ffffffff881ea270>] <ffffffff881ea270>{:rt2561:RT61_open+51}
[  235.335519] RSP: 0018:ffff81002ce35d98  EFLAGS: 00010206
[  235.335523] RAX: 00000000006d3000 RBX: ffff810038520000 RCX: 0000000000000246
[  235.335527] RDX: 00000000ffffffed RSI: 0000000000001043 RDI: ffff810036770400
[  235.335532] RBP: 0000000000000000 R08: ffff8100323fa4c0 R09: ffffffff80237763
[  235.335536] R10: 0000000000000030 R11: 0000000000000202 R12: ffff810036770400
[  235.335540] R13: 0000000000000000 R14: ffff810036770400 R15: 0000000000000000
[  235.335545] FS:  00002aaaaadf96d0(0000) GS:ffffffff803d8b80(0000) knlGS:0000000000000000
[  235.335549] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  235.335552] CR2: 00000000006d3000 CR3: 000000002b487000 CR4: 00000000000006e0
[  235.335557] Process ifconfig (pid: 7779, threadinfo ffff81002ce34000, task ffff810029b2c820)
[  235.335560] Stack: 0000000000000000 0000000000000000 ffff810036770400 0000000000000000
[  235.335565]        0000000000001002 ffffffff8023f2bd 0000000000000030 ffff810036770400
[  235.335571]        0000000000001043 ffffffff80240299
[  235.335575] Call Trace:<ffffffff8023f2bd>{dev_open+51} <ffffffff80240299>{dev_change_flags+88}
[  235.335590]        <ffffffff802792e1>{devinet_ioctl+627} <ffffffff8011cc59>{do_page_fault+1022}
[  235.335608]        <ffffffff8027a492>{inet_ioctl+124} <ffffffff80237977>{sock_ioctl+532}
[  235.335622]        <ffffffff80172d26>{do_ioctl+30} <ffffffff80172f7e>{vfs_ioctl+554}
[  235.335632]        <ffffffff80172fe4>{sys_ioctl+89} <ffffffff8010e33a>{system_call+126}
[  235.335646]
[  235.335656]
[  235.335658] Code: 8b 10 8b 00 85 c0 75 15 bf e8 03 00 00 e8 4d 37 01 00 89 e8
[  235.335665] RIP <ffffffff881ea270>{:rt2561:RT61_open+51} RSP <ffff81002ce35d98>
[  235.335677] CR2: 00000000006d3000
[  235.335679]
```

How can I check if it is a conflict?
And if so how do I get rid of the conflict??

---

### Post by UbuntuJohan on 2006-03-20
I have now recompiled the drivers and re-installed them and removed the other drivers that I have tried before.
But I still get the same behavior. (It all works untill I try to configure the card)

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776

/etc/dhcp3/dhclient-script: line 139:  7913 Killed                  ifconfig $interface 0 up
```

The last thing just hangs and even a normal cp command or similar also hangs but the GUI's and firefox works fine.
Does anyone has a clue about the error messages in the printout?

Has anyone used these rt61 drivers on a 64 bit system?

---

### Post by ruudiculus on 2006-03-21
UbuntuJohan,

Unfortunately I can't detect an immediate problem, but when other commands also tend to hang something more may be involved. So I haven't got much more advice then this: see if your installation cdrom's checksum corresponds with the one on the Ubuntu download site.

If they match then real strange things happen. Do the **cp** and other commands hang after you tried to configure your wireless settings or even before? Maybe the answer to this will help to see where to focus on. Apart from that you could try this command and see what is returned:

**iwlist ra0 scan**

Well, that's all I can say in 5 minutes. I have to go to my work now. Till soon and good luck.

---

### Post by UbuntuJohan on 2006-03-21
Thanks for your suggestions :) 

Everything is working fine and all commands are working before I try to configure the WLAN card.
So it's the configuration of it is causing some kind of kernel crash, see dmesg printout.

SO I don't think it's my Ubuntu installation that is the problem.

I'll try the command you specified when I get home.
But I fear that the result will be the same 

The following line 
```
sit0: unknown hardware address type 776
```
 in the printours don't look good to me but I have no idea how to findout what it means :???:

---

### Post by ruudiculus on 2006-03-21
Hey, back again :-k 

You shouldn't worry about the
> sit0: unknown hardware address type 776
message. I've got it too, but it hasn't got any effect on my wlan0 (so it probably hasn't got much effect on your ra0 too)

When I have time I'll try to look closer to your problem, meanwhile don't lose hope :cool:
[I]
Edit: 5 minutes later...MAYBE...your system tries to connect with sit0 during startup. You could take a look in the **/etc/network/interfaces** file and see if there's any sit0 mentioned there. If not then that's good, but there should be (in your case a **lo** and a **ra0** and an **eth0**. If the **iwlist** command returns a list of networks, then I think all is well and you only need to configure the interfaces file (see my howto for an example if needed).[/I]

---

### Post by UbuntuJohan on 2006-03-21
The iwlist Ra0 scan command instantly returns something like "no networks found"

My /etc/network/interfaces doesn't have any entry for ra0 or sit0
I have already tried to put in an entry for Ra0 there but it didn't work.

I got a tip about this thread [http://www.averatecforums.com/showthread.php?t=3516]("http://www.averatecforums.com/showthread.php?t=3516")
Where they claim that you must have a 2.6.13 or newer kernel for these drivers.
But I found that starnge since RALINK includes a makefil for 2.4 and one for 2.6

---

### Post by ruudiculus on 2006-03-21
Hey,

I've done some searching for you and I found that Dlink doesn't provide 64-bit windows drivers for the 510: they're not produced anymore so it seems and therefore no 64 bit windows drivers are released.

On the forum below it was said that the 520 driver would work in the 510 too since they have the same chipset namely Atheros . And what was also said is that the Gigabyte drivers work for the 520 series, so with a bit of luck your 510 ra0 works with this one too. This is the link to the forum I came across: 
[http://www.planetamd64.com/lofiversion/index.php/t5287.html]("http://www.planetamd64.com/lofiversion/index.php/t5287.html")

I attached the 64 bit Gigabyte driver for the 520 series to this post. I hope it helps! If not, I think its time to call in some guru's :D 

[ATTACH]7379[/ATTACH]

Good luck!

---

### Post by UbuntuJohan on 2006-03-23
This is the revision C of the 510 series and it uses a RALINK chipset and not atheros so I don't think that will work.

I have now decided to install 32-bit breezy on one partion and see if that goes better.

---

### Post by UbuntuJohan on 2006-03-24
Now I have installed 32-bit breezy on annother partion and ar running the rt61 driver from ralink without ndiswrapper.

So to conclude my findings I have not found any driver for D-LINK DWL-G510 Rev.C that worka on 64 bit Breezy.

Thanks for all replies!!

Cheers
//Johan

---

### Post by janterje on 2006-03-31
Johan,

Thanks for letting me know that there exist rev.C drivers (from the Swedish D-link site) - now my hopes are up again after giving up making this card work in Ubuntu. :D 

You even seem to have made the RT61-driver work with this card, so if ndiswrapper with correct rev-drivers fail, I hope it's ok I ask for some assistance. 


Jan Terje
Oslo

---

### Post by UbuntuJohan on 2006-03-31
Jan Terje,

Good luck 
I hope you get it working without any hazzle.

 If you don't here is the link to the post that helped me to fix mine 
[http://www.ubuntuforums.org/showthread.php?t=132980]("http://www.ubuntuforums.org/showthread.php?t=132980")

Let me know if you still get problems and I'll try to help you.

//Johan

---

### Post by elhumano on 2006-05-03
There are new drivers available with many new feautures and bug fixes from the ralinktech, Im using Dapper and having some problems maybe its time tu upgrade drivers.

[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

---

