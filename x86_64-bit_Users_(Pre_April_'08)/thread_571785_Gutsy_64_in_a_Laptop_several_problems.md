---
title: "Gutsy 64 in a Laptop: several problems"
date: 2007-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by mirix on 2007-10-09
Hi,

I have tried several 64 bit Ubuntu versions in my ASUS A6Tc: 6.06, 6.10; 7.04, and 7.10.

There are some problems that happen with all the Ubuntu versions (but not with Debian Etch):

- First there's a BIOS error on booting regarding the timer not being  connected to IO-APIC. In Debian, just adding acpi=noirq to the boot options solved the issue and no other error messages or problems appeared. This problem appears to arise from a bug in certain ASUS BIOSes (or so they say the Linux developers).

- In Ubuntu, not adding the acpi=noirq boot option causes the system to freeze (sometimes it recovers after a while). In Debian 4.0 it can also happen, but only rarely.

- Another problem concerns to the gnome sound main control. You can scroll the bar until it reaches more or less the middle point and no problem, but if you want to go beyond that point there is a weird noise and no sound anymore for the second half. This happens in Ubuntu 7.04 and 7.10 but not in Debian 4.0.

- A Gutsy-specific problem is that the screen blinks every minute or so. It is a very short blink, but noticeable anyway. 

Otherwise Gutsy is great as it solves some of the Wifi-related issues in previous versions of Ubuntu. It is also great that the installation of the flash player, the restricted drivers and related stuff is now automatic. If the blinking problem is solved I might consider switching from Debian to Ubuntu.

I do not understand, though, how it is possible that Debian 4.0 with an older kernel an all can detect my hardware better that any of the Ubuntu versions.

---

### Post by mirix on 2007-10-10
There's another issue concerning the screens menu. If I try to configure two screens the xorg.conf file becomes a mess and I have to go back to the original file in order to use the computer.

---

### Post by roleta on 2007-10-23
I am using the same laptop but switched to 32 bit version(better apllication support) of ubuntu(from 6.06 to 7.10) and except the sound i have all problems mentioned by you. Without noacpi boot option the system is unusable, randomly freezes. I know that this problem is caused by nvidia driver (using envy to have latest one), because while using old nv driver the system is stable, but with nv i have no succes to get my second monitor working. Use glxgears -info and you will see that this driver has  problems.  Wiith noacpi mode the system is working on higher temperature, because there is no cpu scalling supported and fan start at 60 degrees and without it ofcourse the battery will be empty much soon. I can get you my xorg.conf for dual screen using twinview. On ubuntu 7.10 it is much worst because of randomly flicking of the monitor. I have never try debian on this laptop and it can be stable cause of using the older modules but it is only my personal opinion. 

Has someone solved the problem with nvidia driver(randomly freezes) without switcing off acpi on this notebook?  Please help, i am despered.

---

### Post by joshuapurcell on 2007-10-23
I'm not familiar with this laptop and its components, and I imagine that most other people aren't either (unless they have the laptop themselves). Since I'm running 64-bit gutsy on a T61 with hardly any issues, I have to assume that many of your problems are due to a combination of hardware and software that wasn't tested as heavily as other combinations. It would help us on the forum is we knew what your hardware was (or even a link to the hardware detail page of your laptop) so if someone has worked through issues with something similar they will know.

Although posting a topic titled "Gutsy 64 on a Laptop" got me interested in the thread anyway :D.

---

### Post by roleta on 2007-10-24
root@roleta:/home/rollyboy# lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
root@roleta:/home/rollyboy# uname -a
Linux roleta 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
root@roleta:/home/rollyboy# dmidecode --string bios-version
080012 
root@roleta:/home/rollyboy# dmidecode --string bios-release-date
09/25/2006
root@roleta:/home/rollyboy# dmidecode --string bios-vendor
American Megatrends Inc.
root@roleta:/home/rollyboy# 

 

info from asus page:
[http://www.asus.com/products4.aspx?l1=5&l2=24&l3=134&model=1186&modelmenu=2](http://www.asus.com/products4.aspx?l1=5&l2=24&l3=134&model=1186&modelmenu=2)

I know that with this peace of HW were som bios issues, but i am using new bios. My opinion the whole problem is with the nvidia driver, cause it no depend on architecture (tried 32 or 64 bit) and with standard nv driver the system is stable.

---

### Post by roleta on 2007-10-24
after hours and hours of googling I find something what will stable my system but in other side, it will slow down performane. It is allowing only one cpu core at the boot time with option maxcpus=1 at a boot time. Whole article is at [http://www.nvnews.net/vbulletin/showthread.php?t=58498](http://www.nvnews.net/vbulletin/showthread.php?t=58498) . Look like the system is stable but is using only half power of cpu :-(((. If has someone better idea, please post.

---

### Post by allo2u on 2007-10-24
Hi people,

I'm using an Asus A6T (without 'c') which uses almost the same hardware, and I have just installed Ubuntu gutsy 64bit (compiz-fusion enabled). (I've been running Ubuntu edgy and feisty before but stopped using it because I liked to try vista :( (big mistake, happy to have Linux again)

I just stumbled upon this threat and because I've had exactly the same problems we can share information to get everything working.

I don't have a lot of time right now so here's just a little info, maybe it helps.

Concerning the flashing screen problem: 
It seems to have something to do with the nvidia driver, (see links below for more info).
For*** me*** the following fixed it:
1 In a terminal type:
```
sudo gedit 
```
Then copy/paste the following text into the text editor:
```
#!/bin/bash
#NoFlashingPlease
while true; do glxinfo >/dev/null; sleep 5; done 
```
Save the file as /usr/local bin/NoFlashingPlease.sh (or something/somewere else).
Then make the script executable by typing: 
```
chmod 755 /usr/local/bin/NoFlashingPlease.sh
```
Then finally type 
```
gnome-session-properties
```
 to open the session window, click 'Add' > browse to /usr/local/bin/NoFlashingPlease.sh > give the thing any name and description you like and click 'Ok'
You need to logout and login to complete the process.

For me the following entry in the file /boot/grub/menu.lst appears to result in stable ubuntu (for info see Gentoo A6T wiki further below:

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=77a78a68-94fa-43d8-a542-d8f0111e3502 ro quiet splash  vga=792 pci=assign-busses apicmaintimer idle=poll reboot=cold,hard
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

I haven't done much testing though, please share your results.
Btw I flashed the bios to the latest version which is necessary according to the gentoo a6t wiki, A6Tc bios might have to be flashed too.
Use this command to see CPU-temperature:
```
cat /proc/acpi/thermal_zone/TZ00/temperature
```
You might need it since messing with acpi stuff appears to be dangerous (I haven't got any bad experiences yet though)

Here are some websites I got information from, I hope they're useful for you too.

Lot's of general info (very useful):
[http://gentoo-wiki.com/HARDWARE_Asus_A6T#Hardware](http://gentoo-wiki.com/HARDWARE_Asus_A6T#Hardware)
Some extra general info:
[http://jmuchemb.no-ip.com/~jm/trac/wiki/A6Tc-AP014H](http://jmuchemb.no-ip.com/~jm/trac/wiki/A6Tc-AP014H)

screen flashes:
[http://ubuntuforums.org/showthread.php?t=398821&page=11](http://ubuntuforums.org/showthread.php?t=398821&page=11)

"ACPI & DST" (I think the link at following website might possibly have a solution for the ACPI problems, but haven't read it completely. I just wanted to share it.
[http://gentoo-wiki.com/HARDWARE_Asus_F3T#ACPI](http://gentoo-wiki.com/HARDWARE_Asus_F3T#ACPI)


One question: has anyone of you managed to get the broadcom 4318 wireless to work with the native driver and wpa(1) security or got ndiswrapper working in 64bit gutsy? I've always used ndiswrapper but can't get it to work properly in 64bit gutsy. The native driver also doesn't work well. 

I hope I can find some more time to find some more solutions.

---

### Post by Inxsible on 2007-10-24
I have the same problem of screen flickers and it get annoying as hell after some time. Will try the solutions here and also find out if there are others.

---

### Post by Inxsible on 2007-10-25
allo2u, thanks for the solution that you have provided. I ran it in the terminal and i think it works, i kept running it for about 15 odd minutes.

However, as a programmer I am very wary of an infinite loop which is what the code is.

I hope there are other solutions available. This did not happen in my Feisty 32 bit installation, so i am guessing this is probably either a Gutsy problem or the new nvidia driver problem.

Some posts suggest reverting back to 100.14.09 ...this is what I am going to try  and see if that works.

If not, I think I will have to go back to Feisty 32 bit :(

---

### Post by allo2u on 2007-10-25
Sound/speaker problem:
If you right click the volume-icon and select 'Open Volume Control' you'll see 'PCM' and 'Line In' and some other sliders. If you slide 'Line In' to about half you get the weird noise, if you disable 'Line In' the sound from the speakers gets softer, I haven't tried to figure out what's happening here but its strange.

This weird sound problem can be fixed on my computer by right-clicking the volume-icon on the gnome-panel, choose 'Preferences', in the pop-up window double-click 'PCM'. 
(If you keep the mouse on the volume-icon afterwards the yellow information thingy should say 'PCM: **%'

I hope I can get the wireless to work a little better next since it's really anoying.

---

### Post by roleta on 2007-10-25
->allo2u

I have checked your advices but the system is much more stable only with only one core running (tested with to many glxgear:-),system don't freezy ). Kernel boot option help to stable the system but the infinite loop script will not solve the  nvidia issue.System is still freeizing under heavy load . It is really shame that nvidia does not fully supported users running 64bit dualcore asus notebook. Any other idea?

---

### Post by allo2u on 2007-10-26
Roletta what problems do you mean exactly? I haven't had any issues since I added those lines and the script. Can you tell me how you get the system to crash? What sort of heavy load? I had 8 glxgears running and was still able to use the computer.
I haven't tried the maxcpus=1 option since the system runs smooth without it.
The script is only to solve the flashing screens.

 Strange thing is that the BIOS error on booting regarding the timer not being connected to IO-APIC is back while I didn't change anything. Also when I boot the laptop sometimes freezes at the asus logo, which might have to do with the reboot=cold,hard option.

I have to point out that I've got a slightly different model, a6t:
[http://www.asus.com/products.aspx?l1=5&l2=24&l3=134&l4=0&model=1185&modelmenu=2](http://www.asus.com/products.aspx?l1=5&l2=24&l3=134&l4=0&model=1185&modelmenu=2)

lspci:
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2) [COLOR="Red"]I don't see this one on your lspci output, maybe because I added 1GB ram (2GB now)[/COLOR]
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1) [COLOR="Red"]Different from a6tc![/COLOR]
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08 )
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08 )
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by roleta on 2007-10-27
Our notebooks have different CPU's, i have x2 turion, it should have more power saving features (AMD try to catch intel's dual core2 with this model). My nvidia card is GO 7300.
My problem is, that when i'm using latest nvidia ver. 100.14.19 installed by envy script, system is unstable and it does not matter if the infinity loop script is running or not. System is more stable with use of parameters mention by you at kernel boot. After few minuter second monitor attached to my laptop (twinview in xorg.conf) start to flicking and then monitor on the notebook flicked too and than whole computer freezes. Or if notebook don't freeze, i can not watch videos.I see only many color noise screen but sound play o.k. After restart videos play normaly but after few minutes the freezing again.
I have tested the older nvidia legacy driver 96.43.01and the system looks stable on 32 bit gutsy, but i have tested it only for 2 days now. I can run many glxgears at same time (20) but than the temperature gets realy hign(monitoring it with sensors), but the system don't crash.

---

### Post by John Jason Jordan on 2007-10-27
> **joshuapurcell said:**
> I'm not familiar with this laptop and its components, and I imagine that most other people aren't either (unless they have the laptop themselves). Since I'm running 64-bit gutsy on a T61 with hardly any issues, I have to assume that many of your problems are due to a combination of hardware and software that wasn't tested as heavily as other combinations. It would help us on the forum is we knew what your hardware was (or even a link to the hardware detail page of your laptop) so if someone has worked through issues with something similar they will know.
I also have a T61 (model 6460) and it has the Intel 4965 wireless. I can't get it working reliably with Gutsy. Once in a while I can connect, but usually the drop-down menu in network manager does nothing, that is, it fails to display a list of available networks to connect to. This is a brand new install of Gutsy amd64 as the only OS on a brand new Thinkpad T61. I need to find more owners of T61 Thinkpads with the Intel 4965 wifi in order to see if it is something in my installation or if it is a bug. Anyone?

---

### Post by allo2u on 2007-10-27
Roletta we do have the same processors Turion X2 (mine 1.6GHz)
The only difference I see is the A6Tc having a Geforce 7300 go and A6T having 7600 Go.
Why you have installed the 100.14.19 driver using envy, for the nvidia control panel? I've mine set up  using the Restricted Drivers Manager and it's the same version (package nvidia-glx-new (100.14.19), working without problems.

Maybe there's another A6Tc user or other users with 7300 who experience the same problems, I hope they can help you.

---

### Post by roleta on 2007-10-27
I have experiences with envy in the past so that is the reason. The older legacy driver I have installed using envy too. 

to wifi problem: try wifi-radar, it is really nice utility. Or maybe use ndiswrapper with windows driver.

---

### Post by roleta on 2007-11-10
So, finaly i have tested my system for 2 weeks, and it is stable. Just using these parametres in kernel boot:pci=assign-busses apicmaintimer idle=poll reboot=cold,hard
and nvidia driver is older version: 96.43.01

---

### Post by nicolasdiogo on 2007-11-11
hi,

i have a A6TC, and i am also having trouble with it.
but i am only using on the boot:

nolapic

parameter, with some problems with the graphics flashes, i will try the old driver and see if it improves.

---

### Post by nicolasdiogo on 2007-11-20
hi,

just a quick update:

i have installed the latest BETA driver from nvidia and it seems to have improved dramatically the usability of this laptop.
if you decide to install to install this driver remember to nv to your restricted module file, see here

[http://ubuntuforums.org/showthread.php?t=617594](http://ubuntuforums.org/showthread.php?t=617594)

regards

---

### Post by nicolasdiogo on 2008-01-05
hi,

for those of your interested in having hibernation on this AT6c and probably other laptops with Nvidia graphic card:
have a look at this article:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#How_to_Suspend_with_nVidia_140m.2F570m](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#How_to_Suspend_with_nVidia_140m.2F570m)

i have amended as below:

/etc/default/acpi-support

 # Should we save and restore state using the VESA BIOS Extensions?
 SAVE_VBE_STATE=false
 ...
 # Should we attempt to warm-boot the video hardware on resume?
 POST_VIDEO=false
 ...
 # Set the following to "platform" if you want to use ACPI to shut down
 # your machine on hibernation
 HIBERNATE_MODE=platform


and also added my wireless driver to be reloaded every time i suspend or hybernate my laptop:


/etc/default/acpi-support

 # Add modules to this list to have them removed before suspend and reloaded
 # on resume. An example would be MODULES="em8300 yenta_socket"
 #
 # Note that network cards and USB controllers will automatically be unloaded 
 # unless they're listed in MODULES_WHITELIST
 MODULES="iwl4965 iwlwifi_mac80211 cfg80211"

hope it helps.

---

### Post by roleta on 2008-05-20
Have someone checked the new 8.04 release? I will, but not at this time(little bit busy) so I don't want to spent 3 evenings to get everything working.

---

