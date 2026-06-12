---
title: "64-bit drivers for Broadcom wireless released!!!"
date: 2004-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by oberon on 2004-12-29
Linuxant (Driver Loader) just announed support for AMD64 and a 64-bit ndis driver for broadcom (bcmwl5 series) wireless cards.  Needless to say I am downloading it now.  :mrgreen:   Now you can try out the driverload for free, but have to pay for a permanent solution or maybe someone with much more talent than I can port NDISwrapper to 64-bit.  Anyway, I thought this to be something to share.  I know some people (maybe just a few) that might have been hoping for this to happen.

[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

-oberon

I will attach the file when I can actually download it, the site must be getting hammered.

---

### Post by oberon on 2004-12-30
Okay... so well... after leaving it downloading all night I got a womping 120KB, still running.  So it turns out that the driver was striped out of XP-64.  I have a copy of it around here somewhere and will load it up and pull the files out.  Once I try it out I will post whether it actually works or not.

-oberon

---

### Post by oberon on 2004-12-30
The drivers are in XP-64 build 1260 and later, MS is currently only letting non beta-testers get 1218 for free.  :x   So... since I can't seem to get the download to complete from the link above, any one have  a copy of this?  Can maybe pull out the files (bcmwl564.sys and netbc564.inf) from drivers.cab? Please!!! 

I managed to finally get it to download!!  It is attached.  :D

---

### Post by Kareema on 2004-12-30
Thanks for the driver file. Just downloaded driverloader and tried to install it on Ubuntu Hoary AMD64: drdrinstall.run did not work (tries to install a rpm and fails) and the driverloader-2.20-i386.deb on the homepage is for the wrong architecture (as the name suggests). So I downloaded driverloader-2.20.tar.gz and tried a "make debdist". Got a driverloader_2.20_i386.deb - what's that? OK, looked into the makefile and found a reference to driverloader-2.20/modules/imported/makeflags.mak. In this file I changed the line IMPORTED_ARCH=i386 to IMPORTED_ARCH=amd64 and now it compiled correctly with a driverloader_2.20_amd64.deb as output. And it's installable!!!

Next I'll try to get my Broadcom BCM4306 802.11b/g WLAN mini-PCI card running. Will report back later whether I succeded or not. Please report your (success) stories to learn from.

---

### Post by oberon on 2004-12-30
Thanks for the update I will try it out when I get home this evening. 

-oberon

---

### Post by Kareema on 2004-12-30
Installation with dpkg -i driverloader_2.20_amd64.deb worked without problems. System reboot without problems. Used webinterface to install the 64-bit BCMWL564 drivers and got the answer that the device was not found or is not supported by the drivers. Looked into dmesg and found a kernel oops:
```
driverloader: stack=8192/88/0 REGPARM
usbcore: registered new driver driverloader
Unable to handle kernel paging request at ffffff00003a9cd0 RIP: 
[]
PML4 3f4063 PGD 17f0067 PMD 1f929067 PTE 800000000260e163
Oops: 0011 [1] 
CPU 0 
Modules linked in: driverloader rfcomm l2cap bluetooth powernow_k8 proc_intf freq_table cpufreq_userspace cpufreq_ondemand cpufreq_powersave ds button ac battery ipv6 af_packet ipt_limit ipt_state ipt_LOG ipt_REJECT ip_conntrack_irc ip_conntrack_ftp ip_conntrack iptable_filter ip_tables usb_storage snd_via82xx snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc gameport snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore ehci_hcd uhci_hcd tg3 firmware_class ohci1394 ieee1394 yenta_socket pcmcia_core md dm_mod eeprom i2c_sensor i2c_viapro i2c_core parport_pc lp joydev parport evdev tsdev ide_cd cdrom rtc mousedev psmouse sd_mod scsi_mod ext3 jbd mbcache ide_generic via82cxxx ide_disk ide_core unix thermal processor fan fbcon font vesafb cfbcopyarea cfbimgblt cfbfillrect
Pid: 7351, comm: dldrconfig Tainted: P   2.6.9-1-amd64-k8
RIP: 0010:[] []
RSP: 0018:0000010002671ad0  EFLAGS: 00010246
RAX: ffffff00003a9cd0 RBX: 000001001f53b808 RCX: 000001001f53b808
RDX: ffffffffa03c26e8 RSI: ffffffffa03c26e8 RDI: 0000010002bf9940
RBP: 0000000000000000 R08: 000000000000000e R09: ffffff000041a1b0
R10: ffffff0000392000 R11: 0000000000000000 R12: 0000000000000007
R13: 0000010002647828 R14: 0000010002bf9a48 R15: ffffffffa03bbec1
FS:  0000002a95b074a0(0000) GS:ffffffff803f01c0(0000) knlGS:0000000000000000
CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
CR2: ffffff00003a9cd0 CR3: 0000000000101000 CR4: 00000000000006e0
Process dldrconfig (pid: 7351, threadinfo 0000010002670000, task 0000010002b317a0)
Stack: ffffffffa03aed6b 000001000237f008 0000010002bf9a54 000001000237f008 
       0000010002bf9a48 000001001f5e1cc0 0000010002647828 ffffffffa03bbec1 
       ffffffffa03af30f 0000000000000041 
Call Trace:{:driverloader:NdisWrapInitializeAdapter+539} 
       {:driverloader:NdisWrapCreateAdapter+607} 
       {snprintf+131} {:driverloader:OsRestoreIrql+28} 
       {:driverloader:dldrpci_probe+270} 
       {file_read_actor+0} {vsscanf+1586} 
       {sscanf+136} {pci_device_probe_dynamic+145} 
       {__pci_device_probe+57} {pci_device_probe+48} 
       {bus_match+71} {driver_attach+70} 
       {store_new_id+357} {drv_attr_store+31} 
       {flush_write_buffer+43} {sysfs_write_file+58} 
       {vfs_write+242} {sys_write+83} 
       {system_call+126} 

Code: 48 81 ec 18 01 00 00 4c 8b c2 48 8b d1 48 8d 0d 34 9e 06 00 
RIP [] RSP <0000010002671ad0>
CR2: ffffff00003a9cd0
 <3>dldr_init: call_usermodehelper /usr/sbin/dldrconfig returned 9
```
That's it for now. Perhaps you have more luck (please report). I'm sending my installation protocol to linuxant and wait for help...

---

### Post by Kareema on 2004-12-31
Did you know: We are not alone! Somewhere in the endless space is a good support team from Linuxant... :-) They obviously have a very good response time and the solution is underway.

Here's what they told me: "...other users also reported a similar problem and the developers are currently working on it. I have forwarded the 'dumpdiag' as well as the kernel oops you have provided to the developers and we will contact you back if we need more information or if a fix is available.

The 'make debdist' command in the TAR package was desiged to work on our build system and this is not a command that the user is expected to use, so it is quite possible and normal that you had to modify the files in order to generate the DEB package.

The DEB package we provide at : [http://www.linuxant.com/driverloader/wlan/full/downloads.php](http://www.linuxant.com/driverloader/wlan/full/downloads.php) should work fine on x86_64 machines even if 'i386' is in the file name of the package.

The problem you have reported is unlikely related to the fact that you have generated the DEB package from the TAR package."

---

### Post by oberon on 2004-12-31
Glad to know that.  Didn't get to work on anything last night. :(   And definetly won't be tonight, maybe Saturday.

-oberon

---

### Post by Kareema on 2005-01-01
I've got it working (partially). The Linuxant support instructed me to download the new version of driverloader (v2.22) from [http://www.linuxant.com/driverloader/wlan/full/downloads.php](http://www.linuxant.com/driverloader/wlan/full/downloads.php). I downloaded the tar.gz changed the architecture to amd64 as before and did a make debdist. The installation of the deb, the Windows drivers and the trial license was without problems. Driverloader seems to work OK, but the card can't find my AP. Don't know why... I will report back when I've found a solution.

---

### Post by oberon on 2005-01-02
Well not really much progress here.  I downloaded the tar ball, and changed the config file you mentioned.  When I run make debist I get the following error.
```
oberon@epoch:~/wireless/driverloader-2.22$ sudo make debdist
<command line>:9861507:1: /usr/src/kernel-headers-2.6.9-1-amd64-k8/include/linux/version.h: No such file or directory
<command line>:9861507:1: /usr/src/kernel-headers-2.6.9-1-amd64-k8/include/linux/config.h: No such file or directory
make[1]: Entering directory `/home/oberon/wireless/driverloader-2.22/modules'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd
make[1]: Leaving directory `/home/oberon/wireless/driverloader-2.22/modules'
make[1]: Entering directory `/home/oberon/wireless/driverloader-2.22/scripts'
rm -f  ./dldrmodconflicts  ./rcdldr  ./dldrinfparse  ./rcbuilddldr  ./dldrconfig  ./dldrparser.pm  ./dldrstop
make[1]: Leaving directory `/home/oberon/wireless/driverloader-2.22/scripts'
make[1]: Entering directory `/home/oberon/wireless/driverloader-2.22/webconf'
rm -f  ./webconfd  ./webconfdocs/includes/mainhead.inc  ./webconfdocs/includes/config.inc  ./webconfdocs/includes/header.inc  ./webconfd.conf
make[1]: Leaving directory `/home/oberon/wireless/driverloader-2.22/webconf'
rm -f driverloader.spec packages/SPECS/driverloader.spec
unset LANG; unset LOCALE; unset LC_TIME; dpkg-buildpackage -aamd64 -us -uc
parsechangelog/debian: error: badly formatted trailer line, at changelog line 5
dpkg-buildpackage: unable to determine source package
make: *** [debdist] Error 1
```

I have never built a deb file before so I am not sure if there is something I should be doing that I am not.  I tired it as my self and through 'sudo'.  Thanks for your help.

---

### Post by Kareema on 2005-01-02
Hmm. Don't know what's the problem with your system environment. Perhaps a wrong version of the debian package tools or a missing package. I'll send you the driverloader deb package if you tell me your email adress via PM (I need an email account which has enough free space for a 500KB attachment).

---

### Post by oberon on 2005-01-05
Kareema:

Thanks for sending the deb to me. How did you use the web interface?  It try to authenticate with the root uname and password.  Did you config it using "dldrconfig" on the command line?  I am waiting for Linuxant to re-generate a license for the MAC address, but once this is done I will try to load the driver.

---

### Post by Kareema on 2005-01-05
[QUOTE=oberon]How did you use the web interface?  It try to authenticate with the root uname and password.  Did you config it using "dldrconfig" on the command line.[/QUOTE]

After the installation of the deb, the web interface should be availabe. If not, run "dldrconfig". I configured everything using the web interface. Login with username "root" and your root password. 

BTW: My Broadcom BCM4306 802.11b/g WLAN mini-PCI card is running now using the newest driverloader v2.23.

---

### Post by oberon on 2005-01-05
Alright, I will try that out tonight!  Thanks for the update.

---

### Post by Kareema on 2005-01-05
One small problem remains: After booting, pinging my WLAN router/AP does not work. I think the problem is that 'ifup eth1' is done before loading 'driverloader' and because of that my settings in '/etc/network/interfaces' are not applied. Doing a 'ifdown eth1' , 'iwconfig' and 'ifup eth1' resolves the problem.

How can I change the boot order so that 'driverloader' is loaded before the rest of the network initialization?

---

### Post by jdodson on 2005-01-05
i am wondering why you cant get the broadcomm driver for xp64 and compile ndiswrapper from source to get it working?

---

### Post by Kareema on 2005-01-06
[QUOTE=jdodson]i am wondering why you cant get the broadcomm driver for xp64 and compile ndiswrapper from source to get it working?[/QUOTE]

Last time I checked, ndiswrapper didn't work under the amd64 architecture.

---

### Post by oberon on 2005-01-06
Okay... I installed the driverloader 2.23 and loaded the right driver and it worked wonderfully.  The only thing was that after I rebooted X wouldn't load.  I had to reinstall nvidia-glx and gdm, but then everything was fine.  It doesn't seem to initialize the wireless nic intime to sync time, but it is always online and by the time I log into gnome.  Seems to work GREAT, but if I run into any other problems I will post them.

---

### Post by jdodson on 2005-01-06
[QUOTE=Kareema]Last time I checked, ndiswrapper didn't work under the amd64 architecture.[/QUOTE]

if you build ndiswrapper from source it shouldnt(theroetically) have a problem.  the reason why it wouldnt have worked in the past is trying to use a 32 bit driver in a 64 bit OS.  a 64 bit driver should work in a 64 bit os.

all linuxant is doing(it seems to me) is take the xp 64 driver and wrapping it in the same way ndiswrapper does, except with linuxant you have to pay.

---

### Post by Kareema on 2005-01-06
[QUOTE=jdodson]if you build ndiswrapper from source it shouldnt(theroetically) have a problem.  the reason why it wouldnt have worked in the past is trying to use a 32 bit driver in a 64 bit OS.  a 64 bit driver should work in a 64 bit os.

all linuxant is doing(it seems to me) is take the xp 64 driver and wrapping it in the same way ndiswrapper does, except with linuxant you have to pay.[/QUOTE]

You are right, Linuxant is doing the same thing as ndiswrapper AFAIK. But when I checked two weeks ago, ndiswrapper didn't compile under AMD64. It may compile now, I don't know.

I'd prefer an OSS solution, too. But in the first place I need a working system and if that means that I have to use closed source software then this is OK for me. I bought a license and get a good piece of software and very good support for it.

Further investigation of the 64-bit capabilites of ndiswrapper could be very helpful for others. But I don't have time for that and maybe starting a new thread about this topic would be a good idea.

And please: I don't want to start one of those endless OSS vs. closed source discussions here!

---

### Post by jdodson on 2005-01-06
[QUOTE=Kareema]
And please: I don't want to start one of those endless OSS vs. closed source discussions here![/QUOTE]

in this arena(personally speaking) for me its not closed source vs. open source, its cost vs. no cost(i am a huge cheapskate, not to say i don't appreciate value) :mrgreen:

---

### Post by oberon on 2005-01-07
I resemble that remark! :D But, I can't get it to compile all sorts of errors. The last time I tried this I think I remember there being something that need to re-coded to port to the AMD64 platform. Since I am by no means a programmer, I would have no idea where to even look. I am sure that some one, some where will do it since there is now a driver to use with it.

---

### Post by yippy on 2005-02-16
I compiled DriverLoader from source, without error, and downloaded the Broadcom driver from the linuxant site.  When I connect to the dldrconfig web interface all is good, configure the device and put in my linuxant key.  eth1 shows up in iwconfig, scanned for AP's and my router appears, configure essid and stuff, but when I try to ping anything it doesn't work.

So scratch that, I'd rather use OSS anyway, I compiled ndiswrapper.  Using that I installed the 64-bit Broadcom driver and it seemed to be working.  I configured wlan0, scanned for AP's and my router came up, configured myself to talk to it and...  nothing.  I can't ping or do anything else.  The light flashes on the nic, but ping always says "Destination Host Unreachable".

I checked my configs, set essid, made sure to disable eth0 so it doesn't conflict with wlan0, set them up on different static ip's just in case, disabled all security on the router, but I can't get it to connect to anything.

That's frustrating, is there something I'm overlooking?  I'll use either driverloader or ndiswrapper, as long as they work.  I'm not that picky.  It looks right now like the driver is the problem, though, since I get the same results with both.

Joejoejoe

---

### Post by yippy on 2005-02-17
Oooh...  I finally decided to just back out the changes I had made, but when I came to the WEP settings, I found that something I changed didn't get saved.  So I changed it again, made sure it saved this time, and now everything is working grand!

It worked with both DriverLoader and ndiswrapper, so I ditched DriverLoader for the free alternative.  I have to give huge thanks to linuxant for providing the 64bit driver though, maybe I'll make a donation.

Joejoejoe

---

### Post by Bubbling Zombie on 2005-02-18
what version of ndiswrapper did you use?

---

### Post by unco on 2005-03-30
Not related to 64, but I am trying to install the driverloader from linuxant, but after "dpkg -i driverloader_{version}_{arch}.deb" then going to the browser for "http://127.0.0.1:18020/" I am unable to get the authentication to work with the root and root's password entered, just repeatedly asks for root and password.

I have only been on linux platform a week so is new all new to me, and need help.  I think my root password is correct as Applications\System Tools\Root Terminal accepts it and lets me in ...

Any suggestion will be a help, thanks.

---

### Post by unco on 2005-03-30
Previously didn't read the whole thread, now see that there is a way of creating the wrapper myself, but no idea how.

Is this something I should try? If so where do I get started.

---

### Post by andyman on 2005-04-08
[QUOTE=unco]Not related to 64, but I am trying to install the driverloader from linuxant, but after "dpkg -i driverloader_{version}_{arch}.deb" then going to the browser for "http://127.0.0.1:18020/" I am unable to get the authentication to work with the root and root's password entered, just repeatedly asks for root and password.

I have only been on linux platform a week so is new all new to me, and need help.  I think my root password is correct as Applications\System Tools\Root Terminal accepts it and lets me in ...

Any suggestion will be a help, thanks.[/QUOTE]
 unco, i had this problem, use:

sudo passwd root

then enter your normal password and then you can change and activate the root password.

i'm very much a newbie so if anyone has better ideas, feel free.  worked for me though!

---

### Post by Rogers on 2005-04-21
[http://www.runithard.com/HOWTO-BCOM64WIRELESS/](http://www.runithard.com/HOWTO-BCOM64WIRELESS/)

I wrote a HOWTO for 64 BIT Systems and BROADCOM wireless cards .... i'm running an ACER FERRARI  \\:D/ 

Hope it helps.

---

