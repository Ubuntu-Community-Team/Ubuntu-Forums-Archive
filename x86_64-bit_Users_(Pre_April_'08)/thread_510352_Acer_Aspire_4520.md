---
title: "Acer Aspire 4520"
date: 2007-07-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by xxdejavu on 2007-07-26
Hi, i just wanna ask you guys before, is that ubuntu support with my laptop, here's the full spec

AMD Turion 64 x2
NVIDIA 7000M
120 GB
1 GB of RAM

i installed the ubuntu, and yes systems running but my Graphic card , Wireless, Sound Card are not running, any idea guys? and BTW thanks before :)

---

### Post by aviez on 2007-07-30
i have also same problem with you..

---

### Post by lamont2k7 on 2007-07-31
I am going to have the same problem, just had a new a acer aspire 4520 with Vista preinstalled w/c I dont like. I am planning to install ubuntu.
Did you dual boot with Vista?

Thanks.

---

### Post by misfitpierce on 2007-07-31
Nvidia drivers can be downloaded or you can use program Envy to auto configure graphics which is great. You need to research what wireless your laptop has and where and how to get working... sound im unsure about.

---

### Post by hulukuya on 2007-08-01
Acer Aspire 4520 has:
-AMD Turion 64 X2
- nForce 610M chipset
- GeForce 7000M (graphics)
- Atheros (Wireless)
 Crystal Eye web cam

Ubuntu Festy not detect all device above or no driver for them so my graphic driver is using safe mode now.
Please help solve my problem

thanks be4

---

### Post by elmi on 2007-08-01
Hi,
Ok, I've got good news and worst news for us:

I succeeded in making the Atheros driver work after 1 day testing this config:
First, you need to install the 32 bit Ubuntu (won't work on 64 bits)
Download the driver given in this post:
[http://ubuntuforums.org/showpost.php?p=3006882&postcount=21]("http://ubuntuforums.org/showpost.php?p=3006882&postcount=21")
and follow the procedure given in this post:
[http://ubuntuforums.org/showpost.php?p=3003336&postcount=19]("http://ubuntuforums.org/showpost.php?p=3003336&postcount=19")

Ok, this was for the good news.

I don't know for you, but I was forced to install in text mode because my screen was not detected. I am under 800x600 resolution at best, and there seem to be no driver for this Geforce 7000M currently. Every driver I installed resulted in a black screen during the startup. If anyone has got a working driver, please inform us!

Worse: the startup seems to crash half of the times on the cd-rom driver loading.

My laptop is Aspire 7520 so it might be different for you, but the devices seem the same except for memory (2Gb). I'm considering bringing back the computer to the seller, even though I assume they won't agree, there is no driver online for this model at all (even for Vista!) so I think I might be in my consummer's rights boycotting Acer for this piece of garbage.

---

### Post by xxdejavu on 2007-08-01
yea, same here, i try so many time one by one and i still got the problem, so now my ACER running on ubuntu but with nothing inside :( my new laptop look like trash.. but if you guys know, is it UBUNTU 7.10 support with our laptop or not?

---

### Post by xxdejavu on 2007-08-01
800x600? why do i got 1024x768? and i try so many times to configure XORG.conf to 1024x800 but result always error... lol.... :P

---

### Post by xxdejavu on 2007-08-01
> **lamont2k7 said:**
> I am going to have the same problem, just had a new a acer aspire 4520 with Vista preinstalled w/c I dont like. I am planning to install ubuntu.
Did you dual boot with Vista?

Thanks.

no i don't dual booting, i don't like Vista too, but i'll wait until UBUNTU 7.10 release then i will try one more time, then if still not supported yet, so... i need to do dual boot :(

---

### Post by elmi on 2007-08-01
> **xxdejavu said:**
> 800x600? why do i got 1024x768? and i try so many times to configure XORG.conf to 1024x800 but result always error... lol.... :P

I don't understand how do you have a 1024 resolution in Safe Mode...

Oh, by the way, I tested Envy too, and it couldn't recognise the gpu. And this error at startup gets really boring...

I hope the shop will take the pc back so that I'll never buy one from this crappy brand again.

---

### Post by xxdejavu on 2007-08-02
> **elmi said:**
> I don't understand how do you have a 1024 resolution in Safe Mode...

Oh, by the way, I tested Envy too, and it couldn't recognise the gpu. And this error at startup gets really boring...

I hope the shop will take the pc back so that I'll never buy one from this crappy brand again.

same here i'm confused too, i do reinstall then what do i got now, totally black color,LOL need to configure xorg.conf again and again...  so Good Luck bro, hope that shop want to take back you laptop

---

### Post by elmi on 2007-08-04
As I feared, they refused to take it back, arguing that no other shop do it...
Now I fear we're waiting for a driver from Nvidia for Nforce 610 working on unix...

---

### Post by habuk on 2007-08-05
i got the same prblem too.
it is too long and nobody yet discovered these problem.
Anybody can gives any idea.
:guitar:

---

### Post by elmi on 2007-08-05
Maybe post en masse on the nvidia forums to ask for a driver for nforce 610 on unix... I don't think any other manipulation could solve our problem.

---

### Post by Jeanie on 2007-08-25
After a whole bunch of black-screens and headaches I managed to get my Nvidia GeForce 7000M working on my Acer Aspire 7520. My solution for my computer was simple, Envy doing a manual install for me and then configuring xorg. Finally!

---

### Post by Auax on 2007-08-25
> **elmi said:**
> I don't understand how do you have a 1024 resolution in Safe Mode...

Oh, by the way, I tested Envy too, and it couldn't recognise the gpu. And this error at startup gets really boring...

I hope the shop will take the pc back so that I'll never buy one from this crappy brand again.

acer is a fine brand, it's not the computer's fault Ubuntu doesn't auto run the drivers. Linux is a free OS, without the same support Windows and Mac OS X have.

---

### Post by Vikcaun on 2007-08-31
> **Jeanie said:**
> After a whole bunch of black-screens and headaches I managed to get my Nvidia GeForce 7000M working on my Acer Aspire 7520. My solution for my computer was simple, Envy doing a manual install for me and then configuring xorg. Finally!

thanx. Now on my Acer Aspire 7520 is Ubuntu.
After installation i had problems with resolution. So change it manualy. But now I have problems with sound. NO  SOUND.  And webcam (with easycam2 have this message - Aucune caméra trouvée ou caméra non compatible )

---

### Post by habuk on 2007-09-03
my NVidia is working using envy app but sound & vid cam is still not working as well.


:guitar:

---

### Post by hyapadi on 2007-09-07
Argh... I'm planning to use buy this laptop for linux. But after hearing all the problems here, I think I'm going to think over again.

How is the status of the problem? Are they solved already?

How about the 4920, 5920? are they having the same problem?

---

### Post by xxdejavu on 2007-09-09
have anyone try this driver ?
[http://www.nzone.com/object/nzone_downloads_rel70betadriver.html](http://www.nzone.com/object/nzone_downloads_rel70betadriver.html)

i'll try that drive ASAP, and hopefully work

---

### Post by hyapadi on 2007-09-16
I got information from the local forum that OpenSuse work better with AMD based laptop. But I haven't try it yet because I don't have this laptop. Could someone test it ?

I need the information before purchasing this laptop.

Thanks

---

### Post by msound on 2007-09-17
Sound is working!

Thanks everyone for your inputs. I got the sound working by getting 1.0.15rc2 version from [http://www.alsa-project.org]("http://www.alsa-project.org") and compiling it. 

I added the following line to the end of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=acer

- msound

---

### Post by dontom on 2007-09-17
Thanks for the tips here. 
Regarding the graphics issues, I just downloaded the driver from here;
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
and installed it, and it worked perfectly.

But my biggest problem right now is that Ubuntu recognizes my harddrive as a scsi drive.
And I can't even boot anymore, not even with recovery mode.

---

### Post by hyapadi on 2007-09-17
> **dontom said:**
> Thanks for the tips here. 
Regarding the graphics issues, I just downloaded the driver from here;
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
and installed it, and it worked perfectly.

But my biggest problem right now is that Ubuntu recognizes my harddrive as a scsi drive.
And I can't even boot anymore, not even with recovery mode.

I think that have something to do with the bios options AHCI mode or IDE mode. Just try them.

---

### Post by dontom on 2007-09-17
> **hyapadi said:**
> I think that have something to do with the bios options AHCI mode or IDE mode. Just try them.

I've tried both on several occassions with no luck. Now I've tried to install 7.04, couldn't boot it, then I tried 7.10 Tribe 5 release, couldn't boot after installation, then finally the 7.04 alternate install cd, still cannot boot it. Also tried with pci=nomsi when using AHCI.

The weird thing is that my harddrive shows up as a SCSI device, any of you other guys noticed that ?

Anyway, I can get in to recovery mode maybe 1 out of 10 restarts, else it just stops at ".. CD-ROM Driver revision 3.20 .." something.

When I try to boot regulary it just stops as soon as the loading screen pops up.

---

### Post by aviez on 2007-09-18
> **msound said:**
> Sound is working!

Thanks everyone for your inputs. I got the sound working by getting 1.0.15rc2 version from [http://www.alsa-project.org]("http://www.alsa-project.org") and compiling it. 

I added the following line to the end of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=acer
- msound

can u give step by step what you say you added the following line to the .................i have install that sound driver but icon volume show the mute.i don't know to settle this problem..

---

### Post by dontom on 2007-09-18
> **aviez said:**
> can u give step by step what you say you added the following line to the .................i have install that sound driver but icon volume show the mute.i don't know to settle this problem..

sudo pico /etc/modprobe.d/alsa-base

add line: 
options snd-hda-intel model=acer 
at the end of the file, ctrl + x to save.

Then reboot, I guess.

---

### Post by hida_berserker on 2007-09-26
They say these are the instructions for installing ubuntu feisty.
> 
You will probably want to download the amd64 or i386 Feisty .iso from [http://www.ubuntu.com](http://www.ubuntu.com) . Burn it to a CD by following [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto) . Boot from the CD.


Will I did this with my 
Acer Aspire 4520
AMD Turion 64x2
NVidia GForce 7000M
1GB DDR2

using i386

But installation does not work for me. 

The setup process does not complete for me unlike in what I've read in [http://ubuntuforums.org/showthread.php?t=510352&highlight=4520](http://ubuntuforums.org/showthread.php?t=510352&highlight=4520)

The setup was not completed because of some XServer problem. 

I rebooted and tested the integrity of the installation CD by using the option that comes with the installation CD. Well, the CD is okay it says no errors found in CD. People! We need to make an effort for this ..... especially that this type of laptop is so in demand right now~  !!!!  :(

---

### Post by rughalt on 2007-09-26
Hi,
I was battling with this problem today for many hours too.

You can try booting with "Safe Graphics Mode", or if this doesn't help you can try to do it the ther way. My not-very-easy solution was to change X11 config file located in /etc/X11/xorg.conf and change graphic device driver from nv to vesa. This is how to do it:

After X server crashes, exit to console. From console execute
```
sudo nano /etc/X11/xorg.conf
```

Serach for the line 
Driver "nv" (or something like that) 
and replace "nv" with "vesa". Pres Ctrl-O (save, if I remember good) and Ctrl-X (exit)

Back in console write 
```
startx
```

XServer should start (maybe with very good parameters and resolution, but enough for the install). 

After instalation, you may want to install Nvidia drivers - but you have to do it manually, since ubuntu ones doean't work.

---

### Post by vitaka on 2007-09-30
This thread is very useful because I am tninking about buying a laptop with a NForce 610M chipset. But I have a question. According to nvidia drivers documentation, nvidia geForce 7000M is not supported. It doesn't appear in the list of supported GPUs . Which drivers did you download?
Is there any problem? For example, freezing, poor opengl performance, etc.? I will only buy that laptop if I can run linux without any problem.
Thanks for your answers.

---

### Post by rughalt on 2007-09-30
I downloaded lastest (101?) drivers for 32bit linux (using 32bit Ubuntu atm) and installed them. I don't have any problems (except for need to manual load kernel drivers - I've just put commands to do this into start scripts) - Beryl runs fine, dual head works.

I didn't test other apps (except for video players - they work fast and stable) - but judging I'm also using "unsupported" drivers on Windows Vista and XP and can play relatively new games (such as STALKER), Linux should perform good too. I had no hangs and crashes (only these I made intentioaly or with bad config files).

Also, I have heared that NVidia drivers are same for nearly all cards (card generations), but NVidia is saying that some card is not supported on purpose. But this is only what i have heared.

---

### Post by vitaka on 2007-09-30
Thanks for your fast answer. I think I'll buy that laptop, now that I know that the GPU works well under linux.

---

### Post by zahris on 2007-10-01
yeah... i guest i'll  buy it too.. :D.. thanx for all the information ;)

---

### Post by '888' on 2007-10-06
> **msound said:**
> Sound is working!

Thanks everyone for your inputs. I got the sound working by getting 1.0.15rc2 version from [http://www.alsa-project.org]("http://www.alsa-project.org") and compiling it. 

I added the following line to the end of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=acer

- msound

i have downloading the file
but when i try to configure
i got this message at the last line

ln: creating symbolic link `include/linux/pci_ids.h' to `../pci_ids_compat.h': Operation not permitted
ln: creating symbolic link `include/linux/i2c-id.h' to `../i2c-id_compat.h': Operation not permitted
Hacking autoconf.h...

is there any packages that i must install anymore?

---

### Post by asprakash on 2007-10-11
Early i was facing the same problem. Aft that I followed the this steps 
* Installed Ubuntu Gutsy version for 64 bit
* login in console mode
* By default, the nvidia driver installed. Install the driver by using 
$apt-get install nivida-glx-new
$sudo nvidia-glx-config enable
Then retsart the Laptop. Now almost the video problem will solved.

* Updated the packages.[kernel also updated]
* Installed build-essential from package manager. It has resolved lot of dep problems. 
* Downloaded alsa-driver-1.0.15rc3.tar.bz2
* Untar it
* $./configure
* $make
* $make install
* sudo vim /etc/modprobe.d/alsa-base
added this  "options snd-hda-intel model=acer" in almost last line. Aft that save it.
* Reboot
* Now my lapy logged in with nice Ubuntu sound. Now the sound card working fine.
Thanks to ALSA and Ubuntu....

---

### Post by astero1ds on 2007-10-12
Ubuntu works superbly in my desktop computers. I like it! However, I have problems installing Ubuntu, any version, in my Acer 4520 laptop. Problems include most of what members have mentioned in this forum. I am  glad some of you fixed your problems. But I am not the technically savvy person and I still can't resolve them. I am thinking of selling off my 4520 laptop at a discount and buy a new laptop that will run Ubuntu without any tunning. Guess I will bring along a live Ubuntu CD to the computer shops to test out the laptops.

---

### Post by xueyan on 2007-10-12
> **elmi said:**
> Hi,
Ok, I've got good news and worst news for us:

I succeeded in making the Atheros driver work after 1 day testing this config:
First, you need to install the 32 bit Ubuntu (won't work on 64 bits)
Download the driver given in this post:
[http://ubuntuforums.org/showpost.php?p=3006882&postcount=21]("http://ubuntuforums.org/showpost.php?p=3006882&postcount=21")
and follow the procedure given in this post:
[http://ubuntuforums.org/showpost.php?p=3003336&postcount=19]("http://ubuntuforums.org/showpost.php?p=3003336&postcount=19")

Ok, this was for the good news.

I don't know for you, but I was forced to install in text mode because my screen was not detected. I am under 800x600 resolution at best, and there seem to be no driver for this Geforce 7000M currently. Every driver I installed resulted in a black screen during the startup. If anyone has got a working driver, please inform us!

Worse: the startup seems to crash half of the times on the cd-rom driver loading.

My laptop is Aspire 7520 so it might be different for you, but the devices seem the same except for memory (2Gb). I'm considering bringing back the computer to the seller, even though I assume they won't agree, there is no driver online for this model at all (even for Vista!) so I think I might be in my consummer's rights boycotting Acer for this piece of garbage.

you can start the installer in safe graphis mode(the 2nd opition)

---

### Post by hida_berserker on 2007-10-12
anybody here made thir 4520s work with two monitors (dual display) on ubuntu? it's very hard working with one screen only. Thanks by the way for the xorg.conf advise (vesa). 

installing updated nvidia drivers does not permit changing vesa to glx argument in xorg.conf. What are other possible arguments that can replace vesa in order to use dual display?

---

### Post by cord-factor on 2007-10-19
> **msound said:**
> Sound is working!

Thanks everyone for your inputs. I got the sound working by getting 1.0.15rc2 version from [http://www.alsa-project.org]("http://www.alsa-project.org") and compiling it. 

I added the following line to the end of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=acer

- msound
And what's about modem?
Audio and modem is a really one device...

---

### Post by hyapadi on 2007-10-20
Has anyone use 7.10 with this laptop?

I'm waiting for the review =)

---

### Post by ups on 2007-10-21
> **hyapadi said:**
> Has anyone use 7.10 with this laptop?

I'm waiting for the review =)
Hi,

I recently bought the Acer Aspire 4520. In brief - I have good news :)

Video - works fine, the restricted driver in Gutsy supports the nVidia 7000M model
Audio - works, without compiling anything. You just need to install the package linux-backports-modules-generic which has the newer Alsa driver backported (see [bug #131133]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133")). After that add this line at the bottom of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=acer

Webcam - works out-of-the-box - Ekiga is able to detect and use it
Mic - works out-of-the-box - Ekiga is able to record

I dont have anything to test the Wifi and Bluetooth with, but it's all detected correctly, so I'm hoping it will work.

Network has some issue (see [bug #153727]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/153727")), but it's no showstopper.
Also facing some issues while booting it (see [bug #67256]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256")), but it's not happening very frequently. It is probably not a generic issue.

Overall, I'm pleased with my Laptop & Gutsy so far!

---

### Post by jkfuss on 2007-10-21
I'm about to buy the same laptop. Did you install the 32-bit or 64-bit version? Thanks.

---

### Post by ups on 2007-10-22
> **jkfuss said:**
> I'm about to buy the same laptop. Did you install the 32-bit or 64-bit version? Thanks.
I'm using the 64-bit version.

---

### Post by cord-factor on 2007-10-22
And the modem works?

---

### Post by ups on 2007-10-22
No idea, can't test the modem unfortunately.

---

### Post by jkfuss on 2007-10-22
After I get everything up and running, I will try to test the modem and also the wifi for connectivity. Probably won't be till later in the week. Thank you for your valuable help, ups.

---

### Post by ups on 2007-10-22
> **jkfuss said:**
> After I get everything up and running, I will try to test the modem and also the wifi for connectivity. Probably won't be till later in the week. Thank you for your valuable help, ups.
No problem, jkfuss. Let us know how it works out for you.

---

### Post by cord-factor on 2007-10-22
**ups**, can you show your "lspci"?

---

### Post by ups on 2007-10-22
> **cord-factor said:**
> **ups**, can you show your "lspci"?
Here you go:
```
$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0533 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
07:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

What do you want to check?

---

### Post by dreamsatt on 2007-10-23
i have same laptop same version and same gutsy gibon but its not working at all 

64 bit version only or should i reinsall that

---

### Post by ups on 2007-10-23
> **dreamsatt said:**
> i have same laptop same version and same gutsy gibon but its not working at all 

64 bit version only or should i reinsall that
Exactly what are the problems you are facing? I'm using it happily, so will be glad to help out.
Is it a fresh install of 64-bit Gutsy?

---

### Post by dreamsatt on 2007-10-23
I dual booted it 

i have vista and server 2003 instaled on this machine. that is working fine.

after that i installed gutsy but that doesnt work. it did not booted from live cd in genral mode.

I tried to boot that in safe graphics mode than it booted. I installed that in safe graphics mode only.

after reboot it didnt moved ahead from first screen of boot status bar

should i go for a clean install by erasing all windows partition

---

### Post by hyapadi on 2007-10-23
Do you set bios to AHCI? Is Ubuntu working with that settings?

How about the network card? is it working?

How about the wireless switch button? bluetooth switch button?

Thanks

---

### Post by dreamsatt on 2007-10-23
do i need to set any thing in bios

---

### Post by ups on 2007-10-23
dreamsatt, have you booted in the "Recovery mode" and seen what is the error you get? Is it the same as [bug #67256]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256") as i mentioned in my post before?

Basically, after 3-4 minutes an error as below appears:
```
ALERT! /dev/disk/by-uuid/ad313939-c7a7-447c-8591-79210c820840 does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)

/bin/sh: can't access tty; job control turned off
(initramfs)
```

---

### Post by cord-factor on 2007-10-23
> **ups said:**
> 
What do you want to check?
- motherboard (MCP67)
I have Acer 7520, and there are MCP67 too. My "lspci" is the same.

Here are the names of "working" modules
Audio - snd_hda_intel (latest alsa)
Networkcard - forcedeth (kernel >=2.6.20)
Web-camera - &#8206;uvcvideo
CardReader - &#8206;sdhci
I cann't check the slot for Express Cards... don't have anyone...

I use Gentoo (suspend2-sources-2.6.22)

---

### Post by hyapadi on 2007-10-24
has anyone tested the wifi?  it is a broadcom chipset and when I tried it with mandrake 2008, it asked for ndiswrapper driver from windows.

---

### Post by ups on 2007-10-24
> **hyapadi said:**
> has anyone tested the wifi?  it is a broadcom chipset and when I tried it with mandrake 2008, it asked for ndiswrapper driver from windows.
Haven't tested, but Gutsy enabled the Atheros restricted driver by default for Wifi for me.

---

### Post by cord-factor on 2007-10-24
[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)
(latest on the page)

On the 7520 laptop (same chip) it work's with ndiswrapper (see this)
[http://ubuntuforums.org/showthread.php?t=545401&page=2](http://ubuntuforums.org/showthread.php?t=545401&page=2)


**ups**, you wrote that mic is working :)
It's working with alsa or with something else?

---

### Post by ups on 2007-10-24
> **cord-factor said:**
> [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)
(latest on the page)

On the 7520 laptop (same chip) it work's with ndiswrapper (see this)
[http://ubuntuforums.org/showthread.php?t=545401&page=2](http://ubuntuforums.org/showthread.php?t=545401&page=2)


**ups**, you wrote that mic is working :)
It's working with alsa or with something else?
cord-factor: ALSA - I've tried to get things to work with the least amount of manual fiddling, so that  the standard stuff works :)
I tested the mic with Ekiga (same for Webcam)

---

### Post by khairulamir on 2007-10-24
i have download the 32 bit version but it still not detect the vga card....
what is the diffrent between 32 and 64 bit?
which one i should use
tq....:confused:

---

### Post by ups on 2007-10-25
> **khairulamir said:**
> i have download the 32 bit version but it still not detect the vga card....
what is the diffrent between 32 and 64 bit?
which one i should use
tq....:confused:
Are you using the same laptop model? If it's a 64-bit CPU, then get the 64-bit version of Ubuntu.
Also, you may need to enable nVidia driver from the restricted driver manager to be able to detect/use your graphics card with full resolution.

---

### Post by mahk on 2007-10-26
> **ups said:**
> Hi,

I recently bought the Acer Aspire 4520. In brief - I have good news :)

Video - works fine, the restricted driver in Gutsy supports the nVidia 7000M model
Audio - works, without compiling anything. You just need to install the package linux-backports-modules-generic which has the newer Alsa driver backported (see [bug #131133]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133")). After that add this line at the bottom of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=acer

Webcam - works out-of-the-box - Ekiga is able to detect and use it
Mic - works out-of-the-box - Ekiga is able to record

I dont have anything to test the Wifi and Bluetooth with, but it's all detected correctly, so I'm hoping it will work.

Network has some issue (see [bug #153727]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/153727")), but it's no showstopper.
Also facing some issues while booting it (see [bug #67256]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256")), but it's not happening very frequently. It is probably not a generic issue.

Overall, I'm pleased with my Laptop & Gutsy so far!



Hi! I also installed gutsy recently but my video is only 800x600...I only mamanged to install in safe graphics...how did you manage to install the nvidia driver? when I enable the restricted driver then reboot, all I get is a black screen then console login...sorry, i'm just a newbie and dont really know much...i also noticed that it detected the wireless card, but them I still cannot connect to the net...do I need to do something or configure something ? thanks for all your help :)

---

### Post by mahk on 2007-10-26
Hi need help again...I reinstalled gutsy then tried to enable the restricted driver for nvidia but then driver won't install, it says "...error commiting changes.Possibly there was error downloading...", any ideas how to fix this? Thanks :confused:

---

### Post by ups on 2007-10-27
well.. do you have the driver installed? check if the repository is enabled first (System > Admin > Software Sources - make sure Restricted is checked here). If not, check it.

If you are connected to the internet, it should update the software list. Then enable it from the Restricted Drivers Manager and it should download/install the driver. 

I had to reconfigure X to get it to install the driver, as my xorg.conf was changed manually when I attempted to make it use the open source driver at full resolution (that didn't work, so finally i had to resort to the restricted driver).

Here are the steps if the above doesn't work:
[LIST=1]
[*]Make sure the restricted driver is installed (in Synaptic search for nvidia-glx-new)
[*]Execute this command in a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
[*]Open Restricted Drivers Manager and enable the nVidia driver.
[*]Reboot, and you should be good to go.
[/LIST]

As for the wireless issue, I don't have anything to test it and don't have experience on wifi either... though I feel since the driver is installed properly it should just be a matter of settings. Someone else should be able to help you there.

---

### Post by sanjbmw2001 on 2007-10-27
A few pointers

for video at 1280x800 resolution

download envy, select the option manually install drivers, follow instructions and then you should be fine

bluetooth

works out of the box and the button also works

sound

the solution is given in the posts ( where you have to add a line at the end )

---

### Post by ups on 2007-10-27
> **sanjbmw2001 said:**
> for video at 1280x800 resolution

download envy, select the option manually install drivers, follow instructions and then you should be finei wouldn't recommend that, since the supported ubuntu packages are able to make it work.
Try the steps given in my previous post, and it should work. That way you also get normal updates from ubuntu without hassles.

---

### Post by sanjbmw2001 on 2007-10-27
Dear Ups

I am using 32 bit rather than 64 bit
Are you still not recommending my method?

---

### Post by ups on 2007-10-27
> **sanjbmw2001 said:**
> Dear Ups

I am using 32 bit rather than 64 bit
Are you still not recommending my method?
Only if you're absolutely sure that it doesn't work...

---

### Post by mahk on 2007-10-30
Hi! Thanks guys for the reply! This is what I did...

installed envy and did manual install...after that video worked fine already...I have a wireless network at home but still I cant connect to the net eventhough its using the restricted driver for atheros...tried the steps posted for the sound to work, but it didnt work for me....already installed compiz fusion and its just worked absolutely fine :)


Thanks for all your help :)

---

### Post by snis1984 on 2007-11-03
> **ups said:**
> Hi,

I recently bought the Acer Aspire 4520. In brief - I have good news :)

Video - works fine, the restricted driver in Gutsy supports the nVidia 7000M model
Audio - works, without compiling anything. You just need to install the package linux-backports-modules-generic which has the newer Alsa driver backported (see [bug #131133]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133")). After that add this line at the bottom of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=acer

Webcam - works out-of-the-box - Ekiga is able to detect and use it
Mic - works out-of-the-box - Ekiga is able to record

I dont have anything to test the Wifi and Bluetooth with, but it's all detected correctly, so I'm hoping it will work.

Network has some issue (see [bug #153727]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/153727")), but it's no showstopper.
Also facing some issues while booting it (see [bug #67256]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256")), but it's not happening very frequently. It is probably not a generic issue.

Overall, I'm pleased with my Laptop & Gutsy so far!

hi,
thanks for the help
is suspend and hibernate options working fine on your laptop??? when my laptop is powered on after hibernate then nothing appears on screen!!!!!!
with suspend , when its powered on then sound card stops working!!!!!
how to solve these problems?????

---

### Post by sanjbmw2001 on 2007-11-04
Dear Mahk

Install wicd for your wireless, should be able to detect your card.
for the webcam install cheese

---

### Post by mahk on 2007-11-04
> **sanjbmw2001 said:**
> Dear Mahk

Install wicd for your wireless, should be able to detect your card.
for the webcam install cheese

Thanks for your suggestion...I just discovered that webcam worked out of the box when I used kopete...as for the wireless I installed kwifimanager (as I'm using kubuntu gutsy now)...but still havent tested if it worked since my wireless network is currently down...all in all I'm very pleased that this laptop works beautifully with ubuntu/kubuntu gutsy :)

---

### Post by hyapadi on 2007-11-05
I was unable to enter the X window. After the live cd boot, it will asked for display configuration and when it finished, it entered the shell mode.

What should I do?

Thanks

---

### Post by igknighted on 2007-11-06
> **ups said:**
> Hi,

I recently bought the Acer Aspire 4520. In brief - I have good news :)

Video - works fine, the restricted driver in Gutsy supports the nVidia 7000M model
Audio - works, without compiling anything. You just need to install the package linux-backports-modules-generic which has the newer Alsa driver backported (see [bug #131133]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133")). After that add this line at the bottom of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=acer

Webcam - works out-of-the-box - Ekiga is able to detect and use it
Mic - works out-of-the-box - Ekiga is able to record

I dont have anything to test the Wifi and Bluetooth with, but it's all detected correctly, so I'm hoping it will work.

Network has some issue (see [bug #153727]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/153727")), but it's no showstopper.
Also facing some issues while booting it (see [bug #67256]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256")), but it's not happening very frequently. It is probably not a generic issue.

Overall, I'm pleased with my Laptop & Gutsy so far!

Many thanks.  Your fix for the sound worked perfectly..

Just for the record, some of these laptops come with broadcom chipsets.  Using the firmware via the restricted driver manager in Gutsy works perfectly.  Also, the restricted driver manager works perfectly for installing the nvidia drivers to get 1280x800 -> do not worry about using envy.

---

### Post by igknighted on 2007-11-06
> **hyapadi said:**
> I was unable to enter the X window. After the live cd boot, it will asked for display configuration and when it finished, it entered the shell mode.

What should I do?

Thanks

Run the command "sudo dpkg-reconfigure xserver-xorg" and select 'vesa' as your driver.  Then select the defaults for everything else.  When it is done, type 'startx' to get to the desktop.

Now, the vesa driver sucks.  So once you get it installed, use the restricted driver manager to get the proper nvidia driver and you should be all set.

---

### Post by manusia_aneh on 2007-11-07
Hi, I`m the owner of Acer Aspire 4520 too. Currently, I`m running Win XP SP2 Pro on this laptop. If necessary, can somebody make step-by-step tutorial on how to install and configure driver for this laptop? I`m planning to use Ubuntu 7.10. Thank you.

---

### Post by zahris on 2007-11-08
> **manusia_aneh said:**
> Hi, I`m the owner of Acer Aspire 4520 too. Currently, I`m running Win XP SP2 Pro on this laptop. If necessary, can somebody make step-by-step tutorial on how to install and configure driver for this laptop? I`m planning to use Ubuntu 7.10. Thank you.

gini loh mas...

if u read it from the first page i think you'll find a step by step of how to install it by yourself.. i don't think a step by step installation is necessary.. :)

---

### Post by hyapadi on 2007-11-08
I did use the safe mode and able to enter the X window.

But the problem is that when I use the installer, it get cut by half, so I am unable to click on the next, unless using tabs, which is very difficult.

How to configure the display for install? thanks

---

### Post by zahris on 2007-11-09
> **hyapadi said:**
> I did use the safe mode and able to enter the X window.

But the problem is that when I use the installer, it get cut by half, so I am unable to click on the next, unless using tabs, which is very difficult.

How to configure the display for install? thanks

kan udah saya kasi tau di chip mas.. :p

you could just delete the bottom panel and moved the upper panel to the side..

---

### Post by hyapadi on 2007-11-10
Oh.. zen kawatari from CHIP forum? hehe

Ic" thanks

---

### Post by vksanthana on 2007-11-11
Thanks a lot for ur help guys...I was able to read through this forum and get  Ubuntu 7.10 up and running on my new Acer 4520...in short its "brillliant!!"....only have wireless to setup.
Having some trouble with my wired static ip, needs a restarting of my networking to set the gateway right...but i can live with that !!

---

### Post by aviez on 2007-11-14
i have atheross wireless at restricted manager and it be used but how to use this wireless..i look at network manager does not have wireless connection to connect..

---

### Post by zahris on 2007-11-17
> **aviez said:**
> i have atheross wireless at restricted manager and it be used but how to use this wireless..i look at network manager does not have wireless connection to connect..

please read the first page.. it's already been solved.

---

### Post by tinycamp on 2007-11-20
i have one of this, and the sd reader is not automounting, any ideas???

```
tinycamp@itacate:~$ lsmod |grep sd
sdricoh_cs             13068  0 
pcmcia                 46232  1 sdricoh_cs
tifm_sd                14472  0 
tifm_core              13832  1 tifm_sd
sdhci                  21004  0 
mmc_core               33416  4 sdricoh_cs,tifm_sd,mmc_block,sdhci
sd_mod                 32512  3 
scsi_mod              172856  4 sbp2,sg,sd_mod,libata

```
```
[ 2845.090432] sdricoh_cs: Ricoh PCMCIA Secure Digital Interface driver
[ 2845.090437] sdricoh_cs: Copyright(c) 2006 - 2007 Sascha Sommer <--- on modprobe
[ 2850.835895] mmcblk10: mmc0:0997 SD01G 1006080KiB 
[ 2850.835925]  mmcblk10: p1    < ---- when inserting SD
[ 2881.397872] mmcblk10: mmc0:0997 SD01G 1006080KiB 
[ 2881.397902]  mmcblk10: p1    < ----- reinserting

```

i can mount it from /dev/mmcblk10p1, but gnome wont do it automagically....

ideas ??

---

### Post by snis1984 on 2007-11-24
can some one please tell me how to make hibernate and suspend work properly on acer aspire 4520??? , i have installed ubuntu gutsy 32bit. does it affect in any way if one install a 32bit version on this machine???

---

### Post by carlexpc on 2007-11-28
> **elmi said:**
> I don't understand how do you have a 1024 resolution in Safe Mode...

Oh, by the way, I tested Envy too, and it couldn't recognise the gpu. And this error at startup gets really boring...
 
I hope the shop will take the pc back so that I'll never buy one from this crappy brand again.


If you are using Envy, you have to select ¨Install NVIDIA driver manually¨ so that the program will do the necessary downloading of required packages for you.

---

### Post by carlexpc on 2007-11-28
Did anyone of you experience the system hangs during boot sequence when it reaches the DVD drive portion of the boot process? This is very common on Feisty and Gutsy versions. How did you solve the problem?

---

### Post by ups on 2007-11-29
Yes, check out [bug 67256]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256"). I haven't found a solution, though there is a workaround mentioned towards the end. Not sure if it works.

Please do add a comment to the bug, so our devs know that several people are having the problem.

---

### Post by '888' on 2007-11-30
for graphic card just installed the driver from restricted driver manager
or you can use this in commande line
apt-get install nvidia-glx-new

for sound card, just type in terminal
apt-get install linux-backports-modules
then edit file at /etc/modprobe.d/alsa-base
add options snd-hda-intel model=acer
at last line...

then reboot your system
you'll get your sound and graphci card works

for wirelles you must send yours model
because in my case, i have broadcom wirelles
but my friend who own acer 4520 also
have different wireless card
that is atheros

---

### Post by manusia_aneh on 2007-12-12
I`ve succesfuly installed Ubuntu 7.10 on my Acer Aspire 4520. Graphics is working well with nvidia-glx-new installed. But the problem happen when I restarted the laptop after I installed linux-backports-modules. Ubuntu is stuck on boot screen, and my HDD busy indicator on my laptop is light up continuosly. How to solve this problem? Ubuntu doens`t told me anything about this, it`s just stuck and it`s forced me to go back to Windows XP to post this message.

Thank you

---

### Post by ups on 2007-12-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256) [br].[/br] ---------------------------- [br].[/br]
				> **manusia_aneh said:**
> I`ve succesfuly installed Ubuntu 7.10 on my Acer Aspire 4520. Graphics is working well with nvidia-glx-new installed. But the problem happen when I restarted the laptop after I installed linux-backports-modules. Ubuntu is stuck on boot screen, and my HDD busy indicator on my laptop is light up continuosly. How to solve this problem? Ubuntu doens`t told me anything about this, it`s just stuck and it`s forced me to go back to Windows XP to post this message.

Thank you

I think you're talking about [bug #67256]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256") (see end of [this post]("http://ubuntuforums.org/showpost.php?p=3593055&postcount=41")). 
To confirm, wait for a while, it will eventually drop you to a shell. You can just try to restart the computer, it works 7 times out of 10 for me. It's a bit annoying when it happens, but fortunately doesn't happen that frequently.

---

### Post by zahris on 2007-12-17
@manusia aneh    

what system did you install, have you tried intstalling "linux-backports-modules-generic" ??


i've tried installing madwifi-ng for atheros AR5007EG chipset and it works GREAT!!..... i following the tutorial from [http://madwifi.org/ticket/1679]("http://madwifi.org/ticket/1679"), but only for i386 system build available..

---

### Post by amitabhishek on 2007-12-21
Hi! Looks like this thread is a boon to 4520 users. I have one and I installed Gutsy on it. However the system freezes right after GRUB (on splash screen).Any solution? How do I connect to internet via eth. To get other things working I need at least internet. Kindly help pls...pls.

---

### Post by ups on 2007-12-21
> **amitabhishek said:**
> Hi! Looks like this thread is a boon to 4520 users. I have one and I installed Gutsy on it. However the system freezes right after GRUB (on splash screen).Any solution? How do I connect to internet via eth. To get other things working I need at least internet. Kindly help pls...pls.
Did you see my previous post (#92)? If you try for a few times, it might let you in.
What is the problem with ethernet?

---

### Post by amitabhishek on 2007-12-21
Inspite of plugging in the LAN wire and configuring PC IP, gateway IP, DNSs still it shows no network. What to do? Thank God I didn't dispose my old desktop atleast I can access the web.

---

### Post by ups on 2007-12-21
After configuring, try restarting the networking interface:
```
sudo /etc/init.d/networking restart
```
Try the command in a terminal.

---

### Post by amitabhishek on 2007-12-21
it didn't work out dude. Is thr any way to configure NIC for this laptop. This last hitch will complete this thread in every sense as an ultimate guide to 4520.

---

### Post by JnMWare on 2007-12-30
I have an Acer Aspire 4250 and the issue with the sound was killing me. 
This is exactly what I did to resolve it. 
I am running Ubuntu 7.10 with all the pretty updates. It is a 64 bit PC, but I am running the 32 bit Ubuntu.   
The sound would NOT work at all. 
I went to [http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html) and downloaded the 
NVIDIA-Linux-x86-169.07.pkg1.run file. 
I saved it to my Documents directory. 
I rebooted the laptop and went into Ubuntu Recovery Mode so that I can run without X Server running.  Log in as root. 
I went into the Documents folder logged in as root. 
Then I ran "sh NVIDIA-Linux-x86-169.07.pkg1.run"
This went thru a bunch of questions ... just leave everything default. 
After rebooting run this command at a prompt as root: 
nvidia-xconfig --mode 1024x768. After a reboot you will have the proper resolution. 
The only issue I have now is that I cannot get my compiz running properly. (But I have sound yay) 
Now for the fight to find the wireless Drivers ... I am using the Encore 802.11g USB adapter for now. The cam probably won't ever work!  lol

---

### Post by platinumblack on 2008-01-13
Hi,
     I recently got a Acer 4520,
     I installed ubuntu on it, using safe graphics mode
     
     Right now graphics works with vesa

     Wifi works partially with ndiswrapper
     (Can detect networks and accesspoints, but cannot connect most of the time)

     Sound doesnot work at all. ( tried using backports and editing alsa-base  file)

     Nvidia drivers also donot work (tried the glx-new driver and also the driver from nvidia site)

     I also have trouble booting as system fails to detect my disks sometimes . Currently fixed this using the
     all_generic_ide option (but this seems to make disk access much slower)

     I think i have tried most of the suggestions in this thread.

Please help

---

### Post by jontan6 on 2008-01-18
**[SIZE="4"]Acer 4520 Ubuntu Guide[/SIZE]**

Hello, Im an owner of Acer 4520, and installing Ubuntu on it was so painful.  It took me so many sleepless nights trying to make everything work.  Im writing this guide to help other newbies like me.  And also as a thank you for all forum users who post solutions to the related problems.

When installing, I assume that internet connection through ethernet (the wired thing/RJ45) is available.  Because wireless does not work out of the box, and you need internet to get all drivers.

Also, when ever you edit a config file (like files in /etc) always backup the original before editing.
E.g.
cp /etc/someconfigfile.conf /etc/someconfigfile.conf.2008_01_18_backup
(i like appending dates as extension so I know what date it is working)

I use pico editor becase it is what Im familiar with.

**[SIZE="4"]Hardware Specs [/SIZE]**

This is my hardware specs for comparison purposes:
AMD Turion 64x2 TL-58 (1.9 Ghz, 2 x 512 KB L2 cache)
2Gb DDR2 Memory
120Gb Toshiba MK1237GSX
Nvidia Gefore 7000M / nForce 610M
Atheros AR5007EG Wireless Network Adapter
Webcam
Sound
etc

**[SIZE="4"]Ubuntu Version[/SIZE]**

As of this time of writing, Ubuntu 7.10 (gutsy) is the latest production version of Ubuntu.  

I find Ubuntu 7.04 (Feisty) 32 bit to be the best fit.  I did not consider 64 bit because they say you don't get any much performance gain, and you might run into incompatibilities.

In my testing, Im having hardisk problem with 7.10 which I will discuss in hardisk section.

**[SIZE="4"]Initial Installation/Live CD[/SIZE]**

When booting from CD for installation, choose boot in Safe Graphics mode.  When Live CD is booted, check right away if your internet connection is working (ethernet not wireless).

If it is not working, like in my case, it is most probable that it is because of wrong MAC address detected for your ethernet card.  I read there are cases where linux can't detect the correct MAC address, and hence some incorrect value was assigned.

What I know is MAC address is unique for each ethernet card and it has several digit of hex value like tis “00:1B:24:86:DB:D9”.  If you know your MAC address, open a terminal (Applications -> Accessories -> Terminal)

Check what interface name your lan was assigned to.  Sometimes it is eth0, or eth1.  To check type the ff:
***ifconfig***

Then type this:
***sudo ifconfig eth0 hw ether 00:1B:24:86:BD:D9***

replace eth0 and 00:1B:24:86:BD:D9 with appropriate values.  And then test if you're connection is ok.  If not, try restart the device by issuing the ff. commands:
***sudo ifconfig eth0 down***
***sudo ifconfig eth0 up***
This means close and then open again.  By this time you will see that Ubuntu is requesting for new ip address from the DHCP server.

If you don't know your correct MAC, then you might need to install and boot with another OS like Windows XP.  If you tried windows type this in a console window to get the value:
ipconfig /all

If internet is ok in Ubuntu Live CD, click the install in the desktop and follow the instructions.

**[SIZE="4"]Hardisk/Booting Issues[/SIZE]**

After installing Ubuntu and booting from the hardisk, it is probable that you will get stuck in the splash screen and then after maybe 5 minutes it will drop you in a console with some word like initramfs.

What you do is while on GRUB (the screen that lets you choose what to boot), choose the first item (the one without the recovery mode) and press 'e' (which means edit).  then you go to another menu screen, choose the second one from the top (the one that has a long line) and press 'e' (again to edit). Scroll to the end of the line and add any of these 2 parameters (experiment which one works for you).
***all_generic_ide***
***libata.ignore_hpa=1***
press enter, then press 'b' to boot.  Hopefully you will be able to boot.

In my case of Ubuntu 7.04 32 bit, I can boot without doing the steps above.  If I use the Ubuntu 7.10 then I need to do those.

In case you have problem and doing above allows you to boot, you need to check right away if your hardisk performance is ok.  In my test, using all_generic_ide is very slow.  To check your speed, in the terminal type the ff.
***sudo hdparm -t /dev/sda***
Replace /dev/sda with appropriate value if hardisk is not /dev/sda.  But most probably it is /dev/sda
The result should be something like 38Mb/second (give or take a little bit).  If it is 8Mb/second then that is very slow.  You will notice with 8mb/s loading of programs is very slow.  Try changing the parameter or consider another version of Ubuntu.

To make the parameter to GRUB permanent, in terminal type
***sudo pico /boot/grub/menu.lst***

Find the line that looks like the one you see in the grub menu and add the appropriate parameter. 

**[SIZE="4"]Ethernet Issues[/SIZE]**

On every boot, it is possible that your eth keeps on incrementing (e.g. eth0, eth1, eth2, etc).  This is a bug.  If you still have internet and you can live with that, then maybe don't bother.  Depending on ubuntu version, this may or may not happen.  In my 7.04 this does not happen.  But just in case it does happen to you and you want to fix, do the ff.

***sudo pico /etc/udev/rules.d/70-persistent-net.rules***
erase all contents and add the ff.
***SUBSYSTEM=="net", DRIVERS=="forcedeth", NAME="eth0"***
this forces that eth0 is always used and does not increment. forcedeth is the nvidia ethernet driver.

When you always need to correct the MAC address at every boot (like discussed above) and you want to make automatic executed for you, do the ff.
***sudo pico /etc/init.d/myboothscript.sh***
and add th ff. lines and save (use appropriate values)
***#!/bin/sh***
***ifconfig eth1 hw ether 00:1B:24:86:BD:D9***

then make the file an executable file by the ff:
***sudo chmod 755 /etc/init.d/myboothscript.sh***
then make your script be automatically executed every boot by doing the ff:
***update-rc.d mybootscript.sh defaults 90***

**[SIZE="4"]Sound driver[/SIZE]**
I find compiling the driver the best solution to make it work. Refer to [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29) for complete guide and more info.  Below are copy paste of same instructions

Install the required tools and kernelheaders
***sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`***
Download the latest version of alsa
  alsa-driver
	[ftp://ftp.alsa-project.org/pub/driver/](ftp://ftp.alsa-project.org/pub/driver/) 
  alsa-lib
		[ftp://ftp.alsa-project.org/pub/lib/](ftp://ftp.alsa-project.org/pub/lib/) 
  alsa-utils
	[ftp://ftp.alsa-project.org/pub/utils/](ftp://ftp.alsa-project.org/pub/utils/) 

Setup installation directories
[B][I]sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
[/I][/B]


Compile and install alsa-driver
[B][I]cd alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
[/I][/B]


Compile and install alsa-lib
[B][I]cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
[/I][/B]


Compile and install alsa-utils
[B][I]cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
[/I][/B]


Edit config
***sudo pico /etc/modprobe.d/alsa-base***
Add the ff. lines at the bottom
***options snd-hda-intel model=acer***
Then reboot

**[SIZE="4"]Video Card[/SIZE]**

Envy is a script/program that does installation of nvidia/ati driver for you.  Google and download envy_0.9.9-0ubuntu6_all.deb (the latest as of this time of writing) then in terminal go to folder where you save the file and install it by
***sudo dpkg -i envy*.deb***
You will get some sort of error saying there is dependences or something.  This is ok, type the ff. to download dependency and complete installation of envy:
***sudo apt-get install -f***
Then run envy by
***sudo envy -t***
Choose manual installation, then choose nvidia, and then choose latest driver (not legacy).  After successful, reboot and check if can still load graphics.  If window system is still ok, you may want to change the resolution from 1024X768 to 1280X800 (maximum resolution).  To do that do this
***sudo pico /etc/X11/xorg.conf***
Look for section that looks like this
[B][I]	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection[/I][/B]
and add “1280X800” which after should look like this
[B][I]	SubSection "Display"
		Depth	24
		Modes		"1280X800"	"1024x768"	"800x600"	"640x480"
	EndSubSection[/I][/B]
Then reboot.

In any case window system won't start and you want to revert to more lousy video driver that works, you can do this.
Reboot and choose recovery mode in GRUB.  Login in the text mode and do this:
***sudo envy --uninstall-all***
Then edit config. 
***sudo pico /etc/X11/xorg.conf***
Look for this:
***Driver		"nvidia"***
Change nvidia to either ***nv*** or ***vesa***.  Usually ***vesa*** works
Also remove the “1280X800” that you added previously.  

Alternative way to install video, just in case you are using ubuntu 7.10.  Go to Applications -> Add/Remove.  Type nvidia in search field, a list will be shown.  Choose the one with something like
nvidia binary x.org driver ('new' driver)
Click apply to download the driver.
Go to System->Administration->Restricted Driver Manager and select/enable the nvidia video driver.
Reboot.  You can also change the resolution like the steps above and then reboot.

**[SIZE="4"]Atheros Wifi[/SIZE]**

Here is the link that I used to resolved wifi [http://learningcomputer.info/2007/11/17/the-solution-for-antheros-wifi-problems-acer-4520-on-ubuntu/](http://learningcomputer.info/2007/11/17/the-solution-for-antheros-wifi-problems-acer-4520-on-ubuntu/)
Install packages
[B][I]sudo apt-get install ndiswrapper-common
sudo apt-get install ndisgtk
sudo apt-get install ndiswrapper-utils-1.9
[/I][/B]
Go to google to search and download for the winxp 
driver ***net5211.inf*** 
In my case the file I was able to download was “***Wireless_XP_071011.zip***”.  Extract the content and in terminal, go to the “ndis5x” folder if you use 32bit ubuntu, or “ndis5x64” for 64 bit (im not sure, im just guessing.  I use the one without 64). Execute in terminal the ff.
[B][I]ndiswrapper -i net5211.inf
ndiswrapper -l
ndiswrapper -m
ndiswrapper -ma
loadndisdriver1.9
[/I][/B]

When wifi is installed and network you connect to has network key, every time you boot ubuntu always ask you for keyring password.  The workaround is discussed in [http://ubuntuforums.org/showpost.php?p=2776815&postcount=1](http://ubuntuforums.org/showpost.php?p=2776815&postcount=1) , which I copy paste below:

Use same password for your login and keyring password must be the same
Go to terminal and type:
***sudo apt-get install libpam-keyring***
Then edit config
***sudo pico /etc/pam.d/gdm***
And add the ff at the bottom
***@include common-pamkeyring***

If login password not same as keyring password, you can delete the keyring by
***rm $HOME/.gnome2/keyrings/default.keyring***
and then re-enter keyring pass later

**[SIZE="4"]Webcam, etc[/SIZE]**

webcam is working out of the box.  just install an application that can use your webcam.  E.g. cheese.
***sudo apt-get install cheese***

I think other device also work out of the box. e.g. card reader.

**[SIZE="4"]Other interesting things you may want to check out[/SIZE]**

13 Must Do things on new Ubuntu 7.04 Feisty Fawn installation ([http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html](http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html)) these are collection of packages you may want to install. e.g. codecs, etc.

Does Ubuntu Linux kill / shorten hard disk life google this topic because it is important. I did not copy paste here the problem and solution because your laptop will work without it.

---

### Post by lamont2k7 on 2008-01-18
Hi jontan6,
Thanks a ton for the guide. I too have aspire 4520 but with Athlon cpu. Managed to get it gutsy up and running with a lot of help from this thread..... time to make eth0 use the correct mac address every boot and make the wifi work.

:)

---

### Post by sgtbug on 2008-01-20
finally!!! a solution that does not go offtopic!!  Will try this today..

Thanks a lot for this.. :)

---

### Post by afterstep13 on 2008-01-20
hi,

   I might be going a little off topic but I wanted to know
   what exactly does the option all_generic_ide do ?
   also what does the option libata.ignore_hpa=1 do ?

   And why does the system fails to boot when I donot use these options ?

---

### Post by datanalytics.com on 2008-01-20
Hello...

I recently purchased a Acer Aspire 4520 and I have had plenty of problems installing the 64 bit version of Gutsy. I have to thank all those in the list for providing hints as to how to solve the problems I faced.

I have still got two issues outstanding. I am going to be very egoist and post questions rather than answers to how I solved my issues. But my problems, I believe, have not been discussed in the list so far and may even help other people with issues with the wireless connection and hard disk performance.

My first problem is related to the **wireless connection**. I have followed all the steps at [the ubuntu wireless troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"), a great reference, and I cannot make my wireless connection work. 

In particular, 

> carlos@kropotkin:~$ ndiswrapper -l
net5211 : driver installed

But no information is provided about the hardware, although if it were properly configured, it would return something like 

> net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

I cannot see the device. In fact, lshw returns (excerpt)
> 
 *-network UNCLAIMED
             description: Ethernet controller
             product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
             vendor: Atheros Communications, Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list
             configuration: latency=0



In some of the troubleshooting guides I saw some comments concerning the wireless button on the computer, the one that looks like a radar antenna. All my other buttons work (bluetooth, etc.), but that one. I guess that there should be a light under it when it is on. But I see none. And I cannot activate it. After I press it, I get the following lines in dmesg:

> [  724.680029] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  724.680034] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  724.749896] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[  724.749902] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

Could it be the reason why my wireless hardware seems disconnected? How could I make it work again? Is there a way to have that key properly working?

Incidentally, in my previous Acer laptop, recently stolen in central London, I had a similar problem: one day, while running windows, I pressed the key and when I rebooted in Ubuntu the wireless card seemed as dead as it is now. At the time I had a windows partition and I could reboot Windows, press the button and activate it. Now I am 100% on Ubuntu.

My second problem has to do with **hard disk performance**. I could never make my system boot without setting the IDE option in the BIOS and adding the all_generic_ide option to grub.

The problem I face now is that the disk performance is appalling.  It seems that these options destroy performance. There is no way I can tune it with hdparm (it seems that it only works with hdX devices, not sdX) and I could not find information about how to use sdparm to tune it.

Has anybody found a solution to be able to boot and, at the same time, have reasonable disk performance?

Any help will be appreciated.

---

### Post by afterstep13 on 2008-01-21
I too faced a lot of problems installing the 64 bit ... finally setteled for 32 bit...
I too have hd-performance issues and wifi light problem....still looking for soln...

Does any one has a clue, what is causing the booting problem ?

---

### Post by ups on 2008-01-21
> **afterstep13 said:**
> Does any one has a clue, what is causing the booting problem ?I don't think there is any certain cause known yet, there is a [bug open about it]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256") though. Please feel free to add any more information you may have.

---

### Post by afterstep13 on 2008-01-22
> **jontan6 said:**
> **[SIZE="4"]Acer 4520 Ubuntu Guide[/SIZE]**

Hello, Im an owner of Acer 4520, and installing Ubuntu on it was so painful.  It took me so many sleepless nights trying to make everything work.  Im writing this guide to help other newbies like me.  And also as a thank you for all forum users who post solutions to the related problems.

When installing, I assume that internet connection through ethernet (the wired thing/RJ45) is available.  Because wireless does not work out of the box, and you need internet to get all drivers.

Also, when ever you edit a config file (like files in /etc) always backup the original before editing.
E.g.
cp /etc/someconfigfile.conf /etc/someconfigfile.conf.2008_01_18_backup
(i like appending dates as extension so I know what date it is working)

I use pico editor becase it is what Im familiar with.

**[SIZE="4"]Hardware Specs [/SIZE]**

This is my hardware specs for comparison purposes:
AMD Turion 64x2 TL-58 (1.9 Ghz, 2 x 512 KB L2 cache)
2Gb DDR2 Memory
120Gb Toshiba MK1237GSX
Nvidia Gefore 7000M / nForce 610M
Atheros AR5007EG Wireless Network Adapter
Webcam
Sound
etc

**[SIZE="4"]Ubuntu Version[/SIZE]**

As of this time of writing, Ubuntu 7.10 (gutsy) is the latest production version of Ubuntu.  

I find Ubuntu 7.04 (Feisty) 32 bit to be the best fit.  I did not consider 64 bit because they say you don't get any much performance gain, and you might run into incompatibilities.

In my testing, Im having hardisk problem with 7.10 which I will discuss in hardisk section.

**[SIZE="4"]Initial Installation/Live CD[/SIZE]**

When booting from CD for installation, choose boot in Safe Graphics mode.  When Live CD is booted, check right away if your internet connection is working (ethernet not wireless).

If it is not working, like in my case, it is most probable that it is because of wrong MAC address detected for your ethernet card.  I read there are cases where linux can't detect the correct MAC address, and hence some incorrect value was assigned.

What I know is MAC address is unique for each ethernet card and it has several digit of hex value like tis “00:1B:24:86:DB:D9”.  If you know your MAC address, open a terminal (Applications -> Accessories -> Terminal)

Check what interface name your lan was assigned to.  Sometimes it is eth0, or eth1.  To check type the ff:
***ifconfig***

Then type this:
***sudo ifconfig eth0 hw ether 00:1B:24:86:BD:D9***

replace eth0 and 00:1B:24:86:BD:D9 with appropriate values.  And then test if you're connection is ok.  If not, try restart the device by issuing the ff. commands:
***sudo ifconfig eth0 down***
***sudo ifconfig eth0 up***
This means close and then open again.  By this time you will see that Ubuntu is requesting for new ip address from the DHCP server.

If you don't know your correct MAC, then you might need to install and boot with another OS like Windows XP.  If you tried windows type this in a console window to get the value:
ipconfig /all

If internet is ok in Ubuntu Live CD, click the install in the desktop and follow the instructions.

**[SIZE="4"]Hardisk/Booting Issues[/SIZE]**

After installing Ubuntu and booting from the hardisk, it is probable that you will get stuck in the splash screen and then after maybe 5 minutes it will drop you in a console with some word like initramfs.

What you do is while on GRUB (the screen that lets you choose what to boot), choose the first item (the one without the recovery mode) and press 'e' (which means edit).  then you go to another menu screen, choose the second one from the top (the one that has a long line) and press 'e' (again to edit). Scroll to the end of the line and add any of these 2 parameters (experiment which one works for you).
***all_generic_ide***
***libata.ignore_hpa=1***
press enter, then press 'b' to boot.  Hopefully you will be able to boot.

In my case of Ubuntu 7.04 32 bit, I can boot without doing the steps above.  If I use the Ubuntu 7.10 then I need to do those.

In case you have problem and doing above allows you to boot, you need to check right away if your hardisk performance is ok.  In my test, using all_generic_ide is very slow.  To check your speed, in the terminal type the ff.
***sudo hdparm -t /dev/sda***
Replace /dev/sda with appropriate value if hardisk is not /dev/sda.  But most probably it is /dev/sda
The result should be something like 38Mb/second (give or take a little bit).  If it is 8Mb/second then that is very slow.  You will notice with 8mb/s loading of programs is very slow.  Try changing the parameter or consider another version of Ubuntu.

To make the parameter to GRUB permanent, in terminal type
***sudo pico /boot/grub/menu.lst***

Find the line that looks like the one you see in the grub menu and add the appropriate parameter. 

**[SIZE="4"]Ethernet Issues[/SIZE]**

On every boot, it is possible that your eth keeps on incrementing (e.g. eth0, eth1, eth2, etc).  This is a bug.  If you still have internet and you can live with that, then maybe don't bother.  Depending on ubuntu version, this may or may not happen.  In my 7.04 this does not happen.  But just in case it does happen to you and you want to fix, do the ff.

***sudo pico /etc/udev/rules.d/70-persistent-net.rules***
erase all contents and add the ff.
***SUBSYSTEM=="net", DRIVERS=="forcedeth", NAME="eth0"***
this forces that eth0 is always used and does not increment. forcedeth is the nvidia ethernet driver.

When you always need to correct the MAC address at every boot (like discussed above) and you want to make automatic executed for you, do the ff.
***sudo pico /etc/init.d/myboothscript.sh***
and add th ff. lines and save (use appropriate values)
***#!/bin/sh***
***ifconfig eth1 hw ether 00:1B:24:86:BD:D9***

then make the file an executable file by the ff:
***sudo chmod 755 /etc/init.d/myboothscript.sh***
then make your script be automatically executed every boot by doing the ff:
***update-rc.d mybootscript.sh defaults 90***

**[SIZE="4"]Sound driver[/SIZE]**
I find compiling the driver the best solution to make it work. Refer to [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29) for complete guide and more info.  Below are copy paste of same instructions

Install the required tools and kernelheaders
***sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`***
Download the latest version of alsa
  alsa-driver
	[ftp://ftp.alsa-project.org/pub/driver/](ftp://ftp.alsa-project.org/pub/driver/) 
  alsa-lib
		[ftp://ftp.alsa-project.org/pub/lib/](ftp://ftp.alsa-project.org/pub/lib/) 
  alsa-utils
	[ftp://ftp.alsa-project.org/pub/utils/](ftp://ftp.alsa-project.org/pub/utils/) 

Setup installation directories
[B][I]sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
[/I][/B]


Compile and install alsa-driver
[B][I]cd alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
[/I][/B]


Compile and install alsa-lib
[B][I]cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
[/I][/B]


Compile and install alsa-utils
[B][I]cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
[/I][/B]


Edit config
***sudo pico /etc/modprobe.d/alsa-base***
Add the ff. lines at the bottom
***options snd-hda-intel model=acer***
Then reboot

**[SIZE="4"]Video Card[/SIZE]**

Envy is a script/program that does installation of nvidia/ati driver for you.  Google and download envy_0.9.9-0ubuntu6_all.deb (the latest as of this time of writing) then in terminal go to folder where you save the file and install it by
***sudo dpkg -i envy*.deb***
You will get some sort of error saying there is dependences or something.  This is ok, type the ff. to download dependency and complete installation of envy:
***sudo apt-get install -f***
Then run envy by
***sudo envy -t***
Choose manual installation, then choose nvidia, and then choose latest driver (not legacy).  After successful, reboot and check if can still load graphics.  If window system is still ok, you may want to change the resolution from 1024X768 to 1280X800 (maximum resolution).  To do that do this
***sudo pico /etc/X11/xorg.conf***
Look for section that looks like this
[B][I]	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection[/I][/B]
and add “1280X800” which after should look like this
[B][I]	SubSection "Display"
		Depth	24
		Modes		"1280X800"	"1024x768"	"800x600"	"640x480"
	EndSubSection[/I][/B]
Then reboot.

In any case window system won't start and you want to revert to more lousy video driver that works, you can do this.
Reboot and choose recovery mode in GRUB.  Login in the text mode and do this:
***sudo envy --uninstall-all***
Then edit config. 
***sudo pico /etc/X11/xorg.conf***
Look for this:
***Driver		"nvidia"***
Change nvidia to either ***nv*** or ***vesa***.  Usually ***vesa*** works
Also remove the “1280X800” that you added previously.  

Alternative way to install video, just in case you are using ubuntu 7.10.  Go to Applications -> Add/Remove.  Type nvidia in search field, a list will be shown.  Choose the one with something like
nvidia binary x.org driver ('new' driver)
Click apply to download the driver.
Go to System->Administration->Restricted Driver Manager and select/enable the nvidia video driver.
Reboot.  You can also change the resolution like the steps above and then reboot.

**[SIZE="4"]Atheros Wifi[/SIZE]**

Here is the link that I used to resolved wifi [http://learningcomputer.info/2007/11/17/the-solution-for-antheros-wifi-problems-acer-4520-on-ubuntu/](http://learningcomputer.info/2007/11/17/the-solution-for-antheros-wifi-problems-acer-4520-on-ubuntu/)
Install packages
[B][I]sudo apt-get install ndiswrapper-common
sudo apt-get install ndisgtk
sudo apt-get install ndiswrapper-utils-1.9
[/I][/B]
Go to google to search and download for the winxp 
driver ***net5211.inf*** 
In my case the file I was able to download was “***Wireless_XP_071011.zip***”.  Extract the content and in terminal, go to the “ndis5x” folder if you use 32bit ubuntu, or “ndis5x64” for 64 bit (im not sure, im just guessing.  I use the one without 64). Execute in terminal the ff.
[B][I]ndiswrapper -i net5211.inf
ndiswrapper -l
ndiswrapper -m
ndiswrapper -ma
loadndisdriver1.9
[/I][/B]

When wifi is installed and network you connect to has network key, every time you boot ubuntu always ask you for keyring password.  The workaround is discussed in [http://ubuntuforums.org/showpost.php?p=2776815&postcount=1](http://ubuntuforums.org/showpost.php?p=2776815&postcount=1) , which I copy paste below:

Use same password for your login and keyring password must be the same
Go to terminal and type:
***sudo apt-get install libpam-keyring***
Then edit config
***sudo pico /etc/pam.d/gdm***
And add the ff at the bottom
***@include common-pamkeyring***

If login password not same as keyring password, you can delete the keyring by
***rm $HOME/.gnome2/keyrings/default.keyring***
and then re-enter keyring pass later

**[SIZE="4"]Webcam, etc[/SIZE]**

webcam is working out of the box.  just install an application that can use your webcam.  E.g. cheese.
***sudo apt-get install cheese***

I think other device also work out of the box. e.g. card reader.

**[SIZE="4"]Other interesting things you may want to check out[/SIZE]**

13 Must Do things on new Ubuntu 7.04 Feisty Fawn installation ([http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html](http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html)) these are collection of packages you may want to install. e.g. codecs, etc.

Does Ubuntu Linux kill / shorten hard disk life google this topic because it is important. I did not copy paste here the problem and solution because your laptop will work without it.


In my case I did the things a bit differently :

0. Get the 32 bit cd (not the 64 bit)

1. Installed in safe mode and restarted
1.1 at grub menu press 'e' to edit the boot parameters.
1.1.1 append all_generic_ide to the 2nd line (root = ...)
1.2 press b to boot    
1.3 login in  X

2. start a terminal, go  to /boot/grub/menu.lst and appended     all_generic_ide     to the lines 
    root = ....
    for both normal and recovery mode.
    (use sudo nano -w /boot/grub/menu.lst)

3. go to the top panel, System -> Administration -> Screens and Graphics
3.1 Then select the resolution and the graphics driver (nvidia)
note :: this gives you an option of testing,  so you can revert back if there are problems. 

4. Install ndiswrapper and obtain 32 bit drivers (64 bit won't work with 32 bit installation)
    (if that didn't work try to download ndiswrapper-1.47 and compile and install it)

Note :: The wifi led doesn't work. So if the drivers were installed and hardware is also detected, and still you can't connect to any network,  try pressing the wifi button to turn it on :)

5.For sound all i did was added 
   options snd_hda_intel model=acer
  to /etc/modprobe.d/alsa-base   

6. Every thing else is working fine tough the disk performance is pathetic, the wifi led is still off and it seems that CPU temps are hovering above 50 C

Note :: I spent several days trying to make 64 bit work, but couldn't. Only thing that 
I could make work was the wifi. Sound and graphics simply didn't work no matter what i tried.

---

### Post by datanalytics.com on 2008-01-25
Hello,

I finally got my AR5006EG card to work with Gutsy 64bit. I followed the [following tutorial]("http://www.madmoose.it/Aspire3684_Linux/") by (almost) the word.

The only difference is that the wget command to download the source code of the ndiswrapper module pointed to an outdated version that did not compile. Download the latest version instead.

I still have this performance issue with the hard disk, though. I am thinking that if the boot process cannot recognise my hard disk it can be because the required modules are not loaded together with the kernel in the initramfs part of the boot. So, what if I recompiled the kernel with support for my disk (to avoid having to use modules)? Do you think it would be a workable approach?

---

### Post by Sean4000 on 2008-01-25
I recently purchased the Acer Aspire 5520-5290 and upon installing Xubuntu 7.10 I get this message:

BusyBox v.1.1.3 (Debian 1:1.1.3-5 ubuntu7) Build-in shell (ash)
Enter 'help' for a list of build-in commands
(initramfs)_

I have no idea how to get my laptop to boot and need it up and running ASAP.  Should I go buy an Apple laptop?

---

### Post by afterstep13 on 2008-01-26
@sean4000
To get your laptop to boot up, do the following...

(i) At the GRUB menu press      e
(ii) Goto the 2nd line and append         all_generic_ide        to it.
(iii) press   b    to boot

This should atleast get your acer to boot. To fix graphics,sound and other issues (if u have any) you might read older posts and other forums.

---

### Post by afterstep13 on 2008-01-26
Ok I tried again and successfully installed ubuntu 64-bit on acer 4520
Here's what i did :

1 Install ubuntu to the system using safe graphics or text mode, then reboot the system
  Note :: It may so happen that the booting may fail. In that case do the follwing :
    (i) at grub boot menu press e
    (ii) goto 2nd l ine (root=...) and and press e
    (iii) at the end of the line add    all_generic_ide    and press enter
    (iv) press b to boot
Note :: You may add the above command (all_generic_ide) to /boot/grub/menu.lst
    then you need not enter manually every time. just append the command to 
    tle line    root=...     for the ubuntu kernel.

2 For installing the nvidia graphics drivers
   (Note you need a working internet connection)

  (i) Goto menu    System->Administration->Synaptic Package Manager
  (ii) click on reload to reload package information (otherwise the package might not appear)
  (iii) install the package nvidia-glx-new
  (iv) goto menu    System->Administration->Restricted Drivers Management    and eneble Nvidia drivers 
  iv) reboot the system, the graphics should be working now
  (vi) goto termnal and run nvidia-settings to configure the display

3 Sound

 (i) using synaptics package manager install      linux-backports-module
 (ii) goto a terminal and do 
              sudo nano -w /etc/modprobe.d/alsa-base
      add the following line to the end
              options snd-hda-intel model=acer
      press Ctrl-X and save the file
 (iii)reboot the system, now sound will be working

4 wifi
  (i) goto   [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)       and  goto the download section
  (ii) click on   "View older releases from the stable package" and dowload  version **1.44**. donot download other versions, for some reason they assign a 00:00... mac address and it can't be changed using ifconfig either
  (iii) extract the archive using   tar xzvf ndiswrapper....
  (iv) download the winxp drivers for your wifi card
  (v)  run the following commands
          sudo modprobe -r ath_pci
          sudo cat > /etc/modprobe.d/blacklist.common
   enter the line    blacklist ath_pci  
   press Ctrl-D
  (vi) run    sudo apt-get install build-essential
  (vii) now reboot the system
  (vii) after reboot, we need to compile ndiswrapper
        cd <the ndiswrapper directory>
        sudo make
        sudo make install
  (viii) extract the wireless drivers to a directory
         tar xzvf <archive name>

   (ix) install the drivers
        cd <the wireless drivers directory>
        sudo ndiswrapper -i net5211.inf

        (now you can do a ndiswrapper -l to see if the drivers were installed)
        
        sudo modprobe ndiswrapper
        sudo ndiswrapper -m
        sudo ndiswrapper -ma
        sudo ndiswrapper -mi
  
  (x)   sometimes it happens that ndiswrapper fails to assign a MAC address to the 
         wifi card, to fix that do the following
         sudo nano -w /etc/network/interfaces
add the line
        pre-up /sbin/ifconfig wlan0 hw ether XX:XX:XX:XX:XX:XX
where XX:XX:XX:XX:XX:XX is the MAC address of the card.

now save the file and reboot.

  (xi) wireless should now be working.

Note:: if you still can't connect then try pressing the wifi button, the wifi led does not seem to work with linux. press the wifi button and then try connecting.

5. The problem of incrementing eth#
    This happens because somehow the MAC address is reported to linux in reverse.
    To fix this do the following :
   (i) dmesg | grep Mac 
 this gives the mac address in reverse ( a line with Invalid Mac ...)
 note that down. that  is the mac address in **reverse**

   (ii) sudo nano /etc/udev/rules.d/70-persistent-net.rules
   delete any line that ends with NAME="eth#"
   add the following line 
   SUBSYSTEM=="net", DRIVERS=="forcedeth", NAME="eth0"
   now save the file
   
   (iii) now do   sudo nano /etc/network/interfaces
   add the line
   pre-up /sbin/ifconfig eth0 hw ether <the mac address>

    (iv) now reboot the system

The system still has a few problems.

One is that of sidk performance. 
Probably because of the all_generic_ide option disk access is terribly  slow.
  ( try sudo hdparm -t /dev/sda (or some other /dev/sd...) to check)

Secoend somewhat less critical is the issue of wifi led. it would be a great help if it would start working.

---

### Post by amitabhishek on 2008-01-28
@jontan6
@afterstep13

Thanks a tonne! This was the solution that I was looking for no jargon just plain English. Thanks to you guys Mint Linux is running like a dream on my 4520. Earlier I wasted a lot of time on cr@ppy solutions.

---

### Post by maxamillion on 2008-01-29
First and foremost, thank you to the jontan6 for the tutorial, it was without doubt the best documentation I had found on installing linux on this laptop, no matter the distro.

Second, on to my reason for posting:
The **all_generic_ide** parameter at boot, while it worked, brought my hdparm performance listing down to 8MB/s and the **libata.ignore_hpa=1** threw a "option not found" error. A friend of mine who happens to be an Ubuntu developer mentioned that I might want to give the **combined_mode=libata** parameter a shot at boot time and sure enough! Not only does it boot but I get 36MB/s from **hdparm -t /dev/sda**

Hopefully this helps other users, enjoy!!!

---

### Post by afterstep13 on 2008-01-29
@maxamillion
Tried **combined_mode=libata** just now. The system didn't boot.
tried all_generic_ide + combined...    booted but it's still at 8MB/s

Am I doing something wrong ?

But I do know that if I boot using the live cd or the alternate cd then I get around 50MB/s

Also please ask your friend on where can I find the docs and info of these commands

---

### Post by maxamillion on 2008-01-29
No, I don't think you are doing anything wrong ... I just kinda slapped it in there and it worked, no magic-fu required.

My friend is not online at the moment, but I will be sure to try and find some documentation. I poked around google for them myself and concluded that the boot parameters are distro specific and I was unable to find ubuntu specific docs on the subject. I will update as soon as I am able to find something out.

---

### Post by afterstep13 on 2008-01-31
I now found another method of booting with reasonable disk speed.

append     **break=top**        to the 2nd line at grub
then the booting pauses at a point and the **(initramfs)** prompt shows up
then do     **modprobe sata_nv**       followed by  **exit**

then the system boots fine and hdparm -t /dev/sda  gives me around 50MB/s.

I also noticed that in place of sata_nv, mant other drivers that are in
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/           also work

I tried to automate it by putting it in a initramfs boot script, but that doesn't seem to work... (can somebody help)

It only works when I do it manually.

I also discovered that there are other boot-scripts at  /usr/share/initramfs-tools/
(all_generic_ide) is one of them. 

So though I have a work-around and it's rather clumsy :)

---

### Post by felipefoz on 2008-02-01
> **afterstep13 said:**
> I now found another method of booting with reasonable disk speed.

append     **break=top**        to the 2nd line at grub
then the booting pauses at a point and the **(initramfs)** prompt shows up
then do     **modprobe sata_nv**       followed by  **exit**

then the system boots fine and hdparm -t /dev/sda  gives me around 50MB/s.

I also noticed that in place of sata_nv, mant other drivers that are in
/lib/modules/2.6.22-14-generic/kernel/drivers/ata/           also work

I tried to automate it by putting it in a initramfs boot script, but that doesn't seem to work... (can somebody help)

It only works when I do it manually.

I also discovered that there are other boot-scripts at  /usr/share/initramfs-tools/
(all_generic_ide) is one of them. 

So though I have a work-around and it's rather clumsy :)

Great One, afterstep13

With these paramaters, now I can boot with the AHCI options Enabled in BIOS, and my hparm is showing the real results from this computer.
Anyway yet to automate this procedure?
I'll also keep looking for an answer, and a easy way to put this laptop working at a full charge.
See ya...

---

### Post by afterstep13 on 2008-02-01
well i tried everything I knew (well how much does a newbie knows anywys :)

I tried to code that into a script and put it in > /etc/initramfs-tools/scripts/init-top/
made sure eXecute permissions were there to the file
then i did a>  update-initramfs -u to generate the initrd image.

then tried to reboot .... and it didn't work !
infact if do > break=top and then just a simple  >  exit    at the **(initramfs)** prompt
then it worked, but it simply wouldn't work it on it's own. (which i find rather spooky)

Tip:  you may edit the file > /usr/share/initramfs-tools/scripts/local 
        go to the lines        > # Default delay is 180s
			                  slumber=180

        edit the 180 to 10 (or something)   then do > update-initramfs -u

        This initrd img would pop into a **(initramfs)**  shell sooner when booting fails,
        rather than make you stare at the computer for a week :)

Right now I upgraded from gutsy to hardy and everything seems to working fine....

Do tell me when you could automate that process

---

### Post by afterstep13 on 2008-02-01
**For those who'd upgrade to hardy**
Upgrade process works fine and computer should boot easily with full features !

However I found a small glitch:
I decided to try the madwifi drivers, to see if that work.
For that i had to remove ndiswrapper.
But unfortunately madwifi didn't work for me :(
So I tried to reinstall ndiswrapper.
And then came the glitch. For some reasons the ndiswrapper sources didn't compile.
Tried fixing it but couldn't make it work. ( I'm new to linux system programming :) 

Finally I located  a  source-package that compiled and worked,
it's ver 1.50 and it seems to be working well.
(Note ver 1.50 is also available as a deb-package but that too didn't work for me)
Put it in as attachment
(Not sure if  it's the same one as at sourceforge, didn't check it, maybe other ver  would work too).
 And yes, the wifi light is still not working

if any one could fix these please let me know

---

### Post by evilghost on 2008-02-05
afterstep, have you tried this?

```

sudo su
pico /etc/initramfs-tools/modules
{add sata_nv to the module list}
update-initramfs -u

```

Or even a hook script?

```

root@a5520:/etc/initramfs-tools/hooks# chmod +x sata_nv
root@a5520:/etc/initramfs-tools/hooks# cat sata_nv
#!/bin/sh
# Hook for loading sata_nv into initramfs.
PREREQ=""
prereqs() { echo "$PREREQ"; }
case $1 in
prereqs)
        prereqs
        exit 0
        ;;
esac

. /usr/share/initramfs-tools/hook-functions

#force_load the sata_nv module
force_load sata_nv

exit 0

root@a5520:/etc/initramfs-tools/hooks# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

```


I'm trying it now and will update.  Using an Acer 5520-5912 with Ubuntu 7.10 AMD64.

---

### Post by afterstep13 on 2008-02-08
No, i didn't try putting it in a hook script, and now i upgraded to 8.04 which works fine.

Will try and see if it works

---

### Post by evilghost on 2008-02-08
Since using the hook script I do not have any issues with sporadic boot failure.  Thanks for doing the leg-work on sata_nv and initramfs.

---

### Post by afterstep13 on 2008-02-09
Great !
One more problem solved !

Right now i'm having two problems :
1. laptop won't wake-up form sleep. Just gives a blank screen and hangs.
2. Couldn't setup a Comp - Comp network on wifi. 
3. (Minor) the wifi led

Is anyone having these problems ? Any suggessions or solutions ?

---

### Post by evilghost on 2008-02-09
Restore from suspend works well on my end.  Occasionally I have to remove/readd the ndiswrapper module.  I'm going to cobble together some Perl code that checks if the interface isn't associated and then will:

```
sudo rmmod ndiswrapper && sudo modprobe ndiswrapper && sudo ifdown wlan0 && sudo ifup wlan0
```

Of course, I'm using a different laptop than you.  Are you using nvidia-glx-new from the repos or did you self-compile?

---

### Post by evilghost on 2008-02-09
Here's the perl code if anyone wants to use it, I'm launching it from rc.local

Standard disclaimer applies, if the code causes your dog to die it's not my fault.

```

#!/usr/bin/perl -w
# Feb 09, 2008
# evilghost
# Perl daemon to perform 'magic' fix on wireless upon sporadic failure.
# Licensed under GNU GPLv3.

#Need these modules
use POSIX qw(setsid);

&daemonize;

#Loop forever.
while(1){
        &checkwifi();
        sleep(2);
}

sub daemonize{
    chdir '/'                 or die "Can't chdir to /: $!";
    open STDIN, '/dev/null'   or die "Can't read /dev/null: $!";
    open STDOUT, '>>/dev/null' or die "Can't write to /dev/null: $!";
    open STDERR, '>>/dev/null' or die "Can't write to /dev/null: $!";
    defined(my $pid = fork)   or die "Can't fork: $!";
    exit if $pid;
    setsid                    or die "Can't start a new session: $!";
    umask 0;
}

sub checkwifi(){
  $wifi = `iwconfig wlan0`;     #Specify your wireless interface.
  if ($wifi =~ m/Access Point: Not-Associated/g || $wifi =~ m/No such device/g){
    #print localtime() . " Fixing wireless, not associated\n";
    system("rmmod ndiswrapper"); 
    sleep(1);
    system("modprobe ndiswrapper"); 
    system("ifdown wlan0"); 
    system("ifup wlan0"); 
    sleep(2);
  #}else{
    #print localtime() . " Wireless is associated.\n";
  }
}

```

---

### Post by afterstep13 on 2008-02-10
I'm using the nvidia-glx-new driver.

I have no clue, what is causing the trouble :(

While the computer is in sleep, I press any key, then
the machine seems to fire up, but then all it gives is a blank screen, and stops responding. I then have to reboot it :(

Does any one know where the logs of the resume process are ?

---

### Post by raaki_88 on 2008-02-10
hello dude i too did face a problem iam having a acer 4520 laptop

ok first of all

what version of ubuntu you are using 

next i prefer you to use 7.04 rather than 7.10

and with your installation should start from "install ubuntu on safe graphics mode"

enough wid this next update your repositories i guess you that then after that download the latest alsa drivers from the below site

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

and after done with this just msg me i'll tell you the next steps

---

### Post by felipefoz on 2008-02-12
> **evilghost said:**
> afterstep, have you tried this?

```

sudo su
pico /etc/initramfs-tools/modules
{add sata_nv to the module list}
update-initramfs -u

```

Or even a hook script?

```

root@a5520:/etc/initramfs-tools/hooks# chmod +x sata_nv
root@a5520:/etc/initramfs-tools/hooks# cat sata_nv
#!/bin/sh
# Hook for loading sata_nv into initramfs.
PREREQ=""
prereqs() { echo "$PREREQ"; }

case $1 in
prereqs)
        prereqs
        exit 0
        ;;
esac

. /usr/share/initramfs-tools/hook-functions

#force_load the sata_nv module
force_load sata_nv

exit 0

root@a5520:/etc/initramfs-tools/hooks# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

```


I'm trying it now and will update.  Using an Acer 5520-5912 with Ubuntu 7.10 AMD64.

Many issues here:
Hook script didn't work by me and neither did the module file. I did a fresh install and update the initramfs with the script, and didn't work. I keep doing it manually, by using break=top in the kernel line and loading manually the sata_nv module. Not a solution yet. I heard recompiling the kernel or using any other kernel, then the boot works fine. 

Does the mic work? anyway to test it? The gnome recorder doesn't work well and after digging a while, it causes the system sound to go crazy. 

Suspend works well, it just take a while, it takes from 30 to 40 seconds to get back to normal screen. I think it's normal this delay. At the beginning the system seems to hang, but as I said, it seems.

Hibernate doesn't work at all, tried to edit many options in the /etc/default/acpi-support, but no way to wake up the computer, I think this issue is related to the sata_nv driver, but, just a suggestion!

Any news? I'll be here trying all the possibilities...
If I don't succeed, I believe I'm gonna move to 8.04, at least with that version the boot works fine.

---

### Post by marslert on 2008-02-18
1. I have made the sound worked by following step,
However, all the sound volume that I adjust (let say I set to no sound). The sound will revert back to maximum level at my next reboot.


2. My screen color will revert to dark color during startup screen. But, it will back to normal color after I login to system. How to get rid on this?

---

### Post by afterstep13 on 2008-02-24
well, I found a sol'n to the boot / hd issue through hit & trial

make a boot script; sudo nano /etc/initramfs-tools/scripts/init-premount/fix

#!/bin/sh

PREREQ=""
prereqs()
{
        echo "$PREREQ"
}
case $1 in
# get pre-requisites
prereqs)
        prereqs
        exit 0
        ;;
esac
sleep 10 

Now save it. and do a sudo chmod +x /etc/initramfs-tools/scripts/init-premount/fix

and then a  sudo update-initramfs -u

It should work.

I don't have a proper explanation why it works.

The script basically make a 10 sec delay at premount. (so boot process is delayed by 10 sec :)
I guess that at boot time some kind of hardware /drivers conflict occurs.
The script introduces a 10 sec delay which prevents the conflict, leading to a successful boot.
I have tried with a 1 sec delay in place of 10, but didn't work.
I guess a specific amount of delay is necessary to ensure that it works.

Please try it and tell me if it works.

Also the hang problem can be reproduced by adding the boot option break at 2nd  line at grub and at the initramfs prompt do a modprobe ahci (do it as soon as the prompt appeares !)

(So I guess my earlier post about break=top and then modprobe sata_nv is irrevelant)

---

### Post by felipefoz on 2008-02-24
afterstep13,

I couldn't be more thankful, now I'm able to boot without typing every time those lines, I was getting pissed off. I'd be this weekend upgrading to 8,.04.
So, after I tried with 10 seconds delay, and seeing how it worked. I decided to do the dirty job, I tried with 1,2,3,4,5 and it finally worked with 6. But, after installing the ndiswrapper driver (next post) stopped working again, so changed to 7 then. So, this time is definitely the time that the system needs to boot. So, changing to 7  the delay time,  it will probably work for most of you. Thank you again.
I'm working now in the hibernate issue, and also in the s-video and vga out, apparently the current solutions for it doesn't work in this laptop
See you...

---

### Post by felipefoz on 2008-02-24
Another problem solved:

The Wifi issue with led!
- Downloading the latest version of ndiswrapper, i used de 1.51
- blacklisting the ath_pci module, by putting the "blacklist ath_pci" line to /etc/modules/blacklist
- uninstalling previous ndiswrapper in system, then compiling it "make, make install" stuff.
- downloading the windows driver from this link 
[http://www.atheros.cz/download.php?atheros=AR5008&system=1]("http://www.atheros.cz/download.php?atheros=AR5008&system=1")
the version is 6.0.3.85, (32 bits on ubuntu 32 bits only tested) the second one in the page (yes, it is the ar5008 driver page) but it also works for the ar5007eg, linux shows as ar5006eg, but it is ar5007eg.
- installing windows drivers by
sudo ndiswrapper-i net5416.inf
- restart the system...

and voilá, wifi is working with led, and better signal than the other driver "net5211.inf", or even madwifi drivers, also tested for me!
The issue now, is the wifi led is always on, it only blinks when there is connection traffic, otherwise is on.
see ya...

Source: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=512828](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=512828) 
and other websites....

---

### Post by felipefoz on 2008-02-27
i could hibernate as well
the problem is with the built-in nvidia drivers from ubuntu, getting the latest version in the web site from nvidia, and manually installing it works everything fine, I did some workaround, but I am not sure what worked and what not. So I'm gonna test a little bit more, to find out what is relevant or not. then i post a reply.
Cheers...

---

### Post by afterstep13 on 2008-02-28
@felipefoz    what are you using 32 bit or 64 bit ubuntu ? And what laptop are u using ?
                   will u kindlu post the output of   uname -a  here ?

I still can't make my system to go suspend or the wifi led to work

---

### Post by felipefoz on 2008-02-28
> **afterstep13 said:**
> @felipefoz    what are you using 32 bit or 64 bit ubuntu ? And what laptop are u using ?
                   will u kindlu post the output of   uname -a  here ?

I still can't make my system to go suspend or the wifi led to work
I'm using now the 32 bits after finding out that hardware works better in this version, I know this post is in the 64-Bits forum, but most of the things works for both of them, by now, only wireless are different, there are no net5416.inf for xp-64. About the suspend thing, I'll research here what were those things that I changed to work. I think I edited the xorg.conf adding "NvAGP"    "1"  to the device section, something in the "/etc/default/acpi-support" and some with the ubuntu restricted drivers. Well, this weekend I'm planning to do everything from beggining! Do you know if compiling alsa-source, we have success in working the mic?
Anyway, I'm not in my computer now, but I'm using the latest 7.10 kernel - 32 bits. I think 2.6.22-14-generic. Later I'll edit the post and change it.
uname -a
Linux 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
Computer: acer 4520 - turion X2 tl-58 2GB Ram 160HDD Nvidia nforce 630/Geforce 7000M
See ya

---

### Post by koffeejv on 2008-03-03
hello everyone
am using 4520 too and the gutsy gibbon installed

everything is ok.

but when i wanna add the 5 dvd of repositories, i got msg: 
                  
           E:failed to mount...

how i have to configure the cdrom device in fstab ?
am n00b & dont know what right code/line i have to write in fstab  ???

sorry for my english
thx :)

---

### Post by grn on 2008-03-04
Thanks for the excellent directions for installation.

But I am not able to make sound work on my Acer 4520.

The OS does not recognise my sound device at all.
I tried to compile the drivers as you suggested. I could compile and install alsa-lib and alsa-utils successfully, but the ./configure command failed, with the following output:

grn@grn-ubuntu:/usr/src/alsa/alsa-driver-1.0.16$ sudo ./configure --with-cards=hda-intelchecking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.16
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
grn@grn-ubuntu:/usr/src/alsa/alsa-driver-1.0.16$ 

I am a newbie. Please guide.

Thanks in advance

---

### Post by igknighted on 2008-03-04
You don't need to compile anything, just install the package "linux-backports-modules-generic" which has the newer Alsa driver backported. After that add this line at the bottom of /etc/modprobe.d/alsa-base: ```
options snd-hda-intel model=acer
``` Then save and reboot, sound should work fine.

---

### Post by grn on 2008-03-04
> **igknighted said:**
> You don't need to compile anything, just install the package "linux-backports-modules-generic" which has the newer Alsa driver backported. After that add this line at the bottom of /etc/modprobe.d/alsa-base: ```
options snd-hda-intel model=acer
``` Then save and reboot, sound should work fine.

I did try the above step. But the sound still does not work. No sound devices detected.

Also, i skipped to mention, that I am on a 32bit version of Ubuntu.

I have installed the linux-backports-modules, the linux-backports-modules-generic as well as the linux-backport-modules-386. Should I keep just one of them to work?

---

### Post by afterstep13 on 2008-03-04
@grn
do           lsmod | grep snd-hda-intel
and see if the module is there.

if not do    sudo modprobe snd-hda-intel model=acer 

if it's successful i.e. no errors then 
do     alsamixer       and change volume settings. (make sure pcm and master are not muted)

if there is an error, post the error and also post the last few lines of     dmesg

@koffeejv
how exactly are u trying to add the DVDs ?
it's quite possible that fstab is correctly configured.

check and add the line   
# cdrom
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Do you fail to mount any cd / dvd or just those DVDs ?
if yes (and assuming fstab is correct) do      groups       and post the output.
if no then do    ls -l /cdrom   and see if  it's linked to  /media/cdrom

---

### Post by felipefoz on 2008-03-05
@afterstep13
check this guide out...
I've made this week...
completely tested by me!
Your name is on it! hehe
Waiting your opinion...
see ya

[http://ubuntuforums.org/showthread.php?t=715187]("http://ubuntuforums.org/showthread.php?t=715187")

---

### Post by grn on 2008-03-05
Thanks a ton, felipefoz

BEEEEAAAAAAUUUUTIFULLLLL Guide


Most of the things worked for me. You are right about the sound. After fiddling enough with the linux-backports-modules, I finally got it to work only by compiling the drivers from scratch. (Step by step from Jontan6's post([[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=510352&page=11")), and now yours ([[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=715187[/COLOR]]("http://ubuntuforums.org/showthread.php?t=715187").)

But I experienced a few hitches here and there.
See if they make any sense to you. (I am on 32 bit)

1. After GRUB, my screen freezes up indefinitely with the text, 'Starting Up ...' .
But after I press the 'Power Button of my lappy(after 7-10 seconds), 'I get three error lines(Cannot allocate source region 7... 8... 9...), and then it boots normally and with good speed. The SATA setting in the BIOS is AHCI. I tried with the IDE setting too, but still the same.
It is extremely strange, isn't it. Yes, I did check the 'fix' script, and rechecked, and rechecked again, . Everything is correct. Can't figure out why that is so.

Also, my GRUB seems to be taking longer to show the menu. It scans my dvd drive before showing the menu. That would not happen earlier. Any clues???


2. My Webcam was working after I installed cheese.
But to get my sound working, I had downloaded the 'linux-backports-modules' - and all of them - generic, 386.
Since then my Display failed and the lappy went sick. Somehow I got the Display working.
And everything else is alright too.
But suddenly cheese  stopped recognizing my webcam. What could be the issue?
Anyone else faced with this???

---

### Post by grn on 2008-03-05
'@afterstep13, thanks

But I recompiled my drivers to make the sound work. It works well now.

---

### Post by afterstep13 on 2008-03-06
@all

also check felipfoz'g guide :

[http://ubuntuforums.org/showthread.php?t=715187](http://ubuntuforums.org/showthread.php?t=715187)

it'll sort out most of the issues you have :)

---

### Post by ups on 2008-04-19
Those having the booting problem can try upgrading to Hardy RC which was just released. I've not seen the hang up during boot since Hardy Beta. Can others also confirm?

One regression which I am seeing though is that the hardware volume control doesn't work anymore. Other things appear mostly the same.

---

### Post by s.jesudasan on 2008-04-29
> **ups said:**
> Those having the booting problem can try upgrading to Hardy RC which was just released. I've not seen the hang up during boot since Hardy Beta. Can others also confirm?

One regression which I am seeing though is that the hardware volume control doesn't work anymore. Other things appear mostly the same.

R u using 32 bit gutsy to upgrade

---

### Post by ups on 2008-04-30
> **s.jesudasan said:**
> R u using 32 bit gutsy to upgrade
I'm running 64-bit Ubuntu (both Gutsy and Hardy ofcourse)

Not a single boot failure in Hardy so far, but there are some other annoyances (battery life is reduced to 2 hours from 2.5 hours)...

---

### Post by tulanh on 2008-05-09
Following the guide, I've successfully installed Ubuntu 7.10 on my Acer aspire 4520 (My laptop has vista pre-installed). The grub show up vista in the list. But when I select Vista/Longhorn for booting. It's show the vista progress bar and then dump with a blue screen and then it restarts. Don't know why.
Any help?
Sorry for my English.

---

### Post by nikolay.dimitrov on 2008-05-11
I have 2 Longhorn points, 1 work good and 1 do not work. I have Aspire 7520. I do not have any troubles with the new (fresh - not update) installation with Hardy Heron (8.04 LTS). Good luck.

---

### Post by amitabhishek on 2008-06-13
Has any one tried Hardy Heron on this Laptop? Its available with various tech. magazines here this month. But I want to be sure before sinking $4 on one of these magazines.

---

