---
title: "Rtl8187 Patched driver issues"
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by JudasReanimated on 2008-05-01
Alright I installed the patched RTL8187 drivers from Aircrack-ng.org, because my original drivers were extremely unstable. Whenever I used anythng that pulled large bandwidth it killed my connection and I could never get more than 70% signal even when sitting in front of my massively powerful router.

Windows in contrast worked flawlessy in this aspect (shocked I´m sure, as was I!) Well I decided to look into getting open source drivers that were patched and apparently far more stable and allowed TX overclocking

Well I followed the instructions on [http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

Installed the drivers and patch, and when I rebooted, since I use Wicd instead of Network Manager or Manual Config, I just opened it up and it detected no wireless networks, so I check Airdriver-ng, and get this,

```
Driver details for: "Realtek rtl8187"

Compiled into kernel:   No
Installed:              YES
Loaded:                 No
Firmware installed:     N/A

Modules:

Modules:
r8187 ieee80211_rtl ieee80211_crypt_rtl ieee80211_crypt_wep_rtl ieee80211_crypt_tkip_rtl ieee80211_crypt_ccmp_rtl 

Files:
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/r8187.ko 2008-05-01 17:06
/lib/modules/2.6.22-14-generic/extra/ieee80211-rtl.ko 2008-05-01 17:04
/lib/modules/2.6.22-14-generic/extra/ieee80211_crypt-rtl.ko 2008-05-01 17:04
/lib/modules/2.6.22-14-generic/extra/ieee80211_crypt_wep-rtl.ko 2008-05-01 17:04
/lib/modules/2.6.22-14-generic/extra/ieee80211_crypt_tkip-rtl.ko 2008-05-01 17:04
/lib/modules/2.6.22-14-generic/extra/ieee80211_crypt_ccmp-rtl.ko 2008-05-01 17:04

version:        V 1.1
depends:        usbcore,mac80211
vermagic:       2.6.22-14-generic SMP mod_unload 

For more information see:
http://www.aircrack-ng.org/doku.php?id=r8187

```

Well I notice it says Loaded = No

So I go and check my Modinfo,

```
filename:       /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/r8187.ko
description:    Linux driver for Realtek RTL8187 WiFi cards
author:         Andrea Merello <andreamrl@tiscali.it>
version:        V 1.1
license:        GPL
srcversion:     09EEC3E8B38955DBB96947E
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore,mac80211
vermagic:       2.6.22-14-generic SMP mod_unload 
parm:           ifname:charp
parm:           devname: Net interface name, wlan%d=default
parm:           channels: Channel bitmask for specific locales. NYI (int)

```

Then I attempt to Modprobe it,

```
FATAL: Error inserting r8187 (/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/r8187.ko): Unknown symbol in module, or unknown param
```

So I again refer to the guide, and follow the solution steps, and then restart my PC and try again with the same result as before.

Any and all help would be greatly appreciated!

---

### Post by hajk on 2008-05-02
The instructions you followed have a patch for the r8187 module contained in the 2.6.24 kernel sources. However, it appears that you're running a 2.6.22 kernel, and that won't necessarily work. One possible way out: upgrade to Hardy which has the 2.6.24 kernel.

---

### Post by JudasReanimated on 2008-05-03
I udapted to Hardy, and still the same issue, anymore ideas?

---

### Post by JudasReanimated on 2008-05-04
bump

Also strangely my WiFi in Windows no longer works either, after the patch update, but running Live CD it works fine. <_< I'm at a loss of how what I do in Linx can effect Windows, but this is a unique coincidence.

---

### Post by JudasReanimated on 2008-05-05
Well I found out that my Windows will connect to other access points, except for my particular router, and that my Live CD of Gutsy 64bit has no trouble with my router V_V, which is odd.

However I messed with the drivers somemore and got it the at least recognise my SSID Broadcast, but it also says I have a Wep security protocol even if I have none set up, or WPA2; It also shows my signal strength at minimum even if directly infront of it.

---

### Post by JudasReanimated on 2008-05-07
Dabump, hopefully someone knows something!

---

### Post by tjwoosta on 2008-05-08
i have this same wireless card, i found a driver from datanorth that works

here is the link to the post
[http://ubuntuforums.org/showthread.php?t=765671]("http://ubuntuforums.org/showthread.php?t=765671")

usually helps to search the forums

---

### Post by JudasReanimated on 2008-05-09
Nope sorry friend, that didn't work either.

---

### Post by Yellow Pasque on 2008-05-09
I'd suggest using the Windows drivers and ndiswrapper
[ftp://210.51.181.211/cn/wlan/X64_1304_1119.zip](ftp://210.51.181.211/cn/wlan/X64_1304_1119.zip)
Let me know if you need further help.

---

### Post by ASULutzy on 2008-05-09
Temüjin

Have you actually gotten these drivers to work or heard confirmation that they do? I'm just about ready to give up, and it's tough to track down the right drivers, since there are several different versions that all go by the same name. I'm currently using
```
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp.
```

I'll give them a shot, but every driver I've tried so far has either not worked, caused a general protection fault that rendered the system unbootable until the driver was removed, or worked for approximately 30 seconds and then hard locked the system.

Wish me luck:guitar:

edit: ah, these are for Rtl8187 not Rtl8187B

Oh well, guess I'll keep looking!

---

### Post by Yellow Pasque on 2008-05-09
ASULutzy,
Realtek does not offer 64-bit drivers for the 8187B :(

---

### Post by JudasReanimated on 2008-05-10
The default Linux Drivers worked fine except they dropped my connection randomly. I prefer if at all possible to use nothing from windows. 

Just because I want everything to be open source If possible

---

### Post by JudasReanimated on 2008-05-11
Bizumpity bump

---

### Post by Yellow Pasque on 2008-05-11
> I prefer if at all possible to use nothing from windows. Just because I want everything to be open source if possible
Yeah, I feel the same way. Don't get your hopes up with Realtek products though...

---

### Post by JudasReanimated on 2008-05-11
Yeah I'm starting to see the futility in it, but I haven't lost hope yet!

---

### Post by srhines on 2008-05-13
I am also having problems with the rtl8187 driver on an amd64 system. It seems that ndiswrapper will not work properly no matter which driver I try to bundle (X64, Win98, WinXP, Vista64, ...). Has anyone else gotten this wifi card to work on an amd64 platform?

---

### Post by Yellow Pasque on 2008-05-13
> **srhines said:**
> I am also having problems with the rtl8187 driver on an amd64 system. It seems that ndiswrapper will not work properly no matter which driver I try to bundle (X64, Win98, WinXP, Vista64, ...). Has anyone else gotten this wifi card to work on an amd64 platform?
I believe ndiswrapper only works with the XP-64 drivers on amd64 builds. Do you know where ndiswrapper is going wrong (i.e. loading the driver kernel module, bringing up the wireless interface, or connecting to the wireless network)?

I've gotten the rtl8180 drivers to work on Gutsy & Hardy64 as well as 64-bit Arch Linux.

---

### Post by srhines on 2008-05-14
> **Temüjin said:**
> I believe ndiswrapper only works with the XP-64 drivers on amd64 builds. Do you know where ndiswrapper is going wrong (i.e. loading the driver kernel module, bringing up the wireless interface, or connecting to the wireless network)?

I've gotten the rtl8180 drivers to work on Gutsy & Hardy64 as well as 64-bit Arch Linux.

I tried the driver you specified on the first page of this thread, but it just locks up my networking if I try to connect. The output of ndiswrapper -l is shown here:
netrtuw_x64 : driver installed
	device (0BDA:8187) present (alternate driver: rtl8187)

I have also tried getting things to work with the X64/ version of net8187b.inf. This file does not even let wlan0 show up when doing an iwconfig. I have tried pretty much every thread's suggestions for getting this card to work, and they all pretty much fail. I then have to resort back to the flaky rtl8187 driver that prevents me from using ssh/scp. Perhaps I am running the wrong commands for installing the module with ndiswrapper, since there are many different threads that talk about using it. I have been doing ndiswrapper -i xyz.inf, then ndiswrapper -m, followed by rmmod my old drivers and ndiswrapper and then modprobe ndiswrapper.

Has anyone else had any success in getting this card to work on an x86-64 system (ASUS P5K Premium wifi-ap motherboard)?

---

### Post by generic_idea_machine on 2008-05-14
> **ASULutzy said:**
> Temüjin

Have you actually gotten these drivers to work or heard confirmation that they do? I'm just about ready to give up, and it's tough to track down the right drivers, since there are several different versions that all go by the same name. I'm currently using
```
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp.
```

I'll give them a shot, but every driver I've tried so far has either not worked, caused a general protection fault that rendered the system unbootable until the driver was removed, or worked for approximately 30 seconds and then hard locked the system.

Wish me luck:guitar:

edit: ah, these are for Rtl8187 not Rtl8187B

Oh well, guess I'll keep looking!

I've got an RTL8185 and havent had much success with the drivers myself. 
 - Tried the linux driver released by Realtek (same symptoms such as GPF @ boot that you mentioned)
 - Tried ndis wrapper = unsuccessful
 
  I think there is a particular update that broke the driver support. I say this because, I upgraded from 7.10 when Hardy Heron was still in a beta mode and the driver was working all this time. Occasionally I would lose the connection to the Wireless AP, but I had a script (cron) to kick the connection every 45 minutes and that did the trick. 

 It was only after I ran a couple of updates (post beta) mode that the driver got borked. Not sure what broke it. 

 Exasperated, I did a quick search and noticed that broken support for RTL8185 was actually classified as a bug 
 [https://bugs.launchpad.net/ubuntu/+bug/152527]("https://bugs.launchpad.net/ubuntu/+bug/152527")

 A bit more Googling resulted into a solution, whereby someone took the driver provided by Realtek and hacked it so it actually works for 64 bit Hardy Heron. I tried that solution as well...but it didn't exactly work for me. (Sorry too lazy to search for the link again...)

Having spent a considerable amount of time trying to get this working. Something that was working up untill Gutsy Gibbon (7.10), I have almost given up trying to get any Realtek device to work with Hardy Heron.

Options:
      # 1 : revert back to 7.10
      # 2 : Fedora 9
      # 3 : Cat 5

---

### Post by JudasReanimated on 2008-05-17
bump

---

### Post by JudasReanimated on 2008-05-18
buzumpity bump.

---

### Post by JudasReanimated on 2008-05-20
bozo bump

---

### Post by Yiftos on 2008-05-21
If you are going to use Window drivers with ndiswrapper, you will need to blacklist the LINUX native (alternate driver: rtl8187)

sudo gedit /etc/modprobe.d/blacklist

 unremark or add the line: blacklist rtl8187
save the file. 
Also, I notice that you are using ndiswrapper -m which should no longer be used. Start over!

Unload sudo modprobe -r ndiswrapper
Remove sudo ndiswrapper -r netrtuw_x64.inf
Just use sudo ndiswrapper -i netrtuw_x64.inf
Then use sudo depmod -a
Then sudo ndiswrapper -l and you should not see the alternative driver listed.
reload sudo modprobe ndiswrapper

You may have to reboot to make sure that the native r8187 driver is gone.

---

