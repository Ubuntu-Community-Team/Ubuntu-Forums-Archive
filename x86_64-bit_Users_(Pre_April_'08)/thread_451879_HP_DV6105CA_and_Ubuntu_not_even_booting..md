---
title: "HP DV6105CA and Ubuntu not even booting."
date: 2007-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Wes.Green on 2007-05-22
Hello all

I've recently decided to move my laptop (was running Vista, currently Sabayon) to Ubuntu

I've gotten the x64 version of Ubuntu to install.  

Ok to start here is a spec sheet of my laptop [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00777624&cc=ca&dlc=en&lc=en&jumpid=reg_R1002_CAEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00777624&cc=ca&dlc=en&lc=en&jumpid=reg_R1002_CAEN)

When I put the CD into the drive it gives my the Ubuntu LiveCD Boot screen.  Asking what I'd like to do.

So I tell it to run Ubuntu off the CD so I can at least sort of make sure that its going to work.

It starts to boot, looks to be loading some drivers and then it gives about 4 or 5 errors that go by to fast to read.
Continues loading some more drivers then it gives another couple of errors and just goes to a black screen and does nothing at all.  Now I'm new to Linux, been a Winblows person forever, but I'd really like to switch over my laptop.

Anyone have any ideas whats going wrong here?  

Thanks in advance

Wes

---

### Post by scrooge_74 on 2007-05-22
It would be good if you could write down the error messages.  It does not sound like the CD is  bad.

It could be issues with Linux and your SATA drives.  Search the forum for SATA issues I have seen a few, but since my drives are not SATA I have no experience with them

---

### Post by ATAQ on 2007-05-22
I was talking to him earlier on an IRC channel, I think it may be to do with drivers, but SATA sounds more reasonable

---

### Post by scrooge_74 on 2007-05-22
> **ATAQ said:**
> I was talking to him earlier on an IRC channel, I think it may be to do with drivers, but SATA sounds more reasonable

Cool picture you have...we will have to wait until he replies

---

### Post by Wes.Green on 2007-05-23
OK I couldn't get the full error, but I got some of it.

> 
[97.380000] bcm43xx : Error : Microcode "bcm43xx_microcode5.fw" not available or load failed.
Firmware_helper[6050]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
[97.424000} bcm43xx : Error : Microcode "bcm43_microcode5.fw" not available or load failed.
Firmware_helper[6053] : main : error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'


Does that help at all?

---

### Post by jcaveman on 2007-05-23
Try booting with the kernel boot option noapic.  The HP BIOS and this chipset seem to have problems without  turning off apic.  The BCM43XX driver doesn't work well with the Broadcom 4311 wireless cards.  You need to put blacklist the bcm43xx driver and load ndiswrapper instead.

---

### Post by Wes.Green on 2007-05-23
Ok, how do I do that?

Sorry, Linux n00b here

---

### Post by jcaveman on 2007-05-23
When the install CD boot screen comes up hit F6 and enter noapic at the end of the line

---

### Post by Wes.Green on 2007-05-23
Ok it seems to be installing.  Once its installed how do I use ndiswrapper ?

Thanks for all the help :D

---

### Post by Wes.Green on 2007-05-23
OK I have Ubuntu installed now.  Just need to get the wireless working.

this is what my lspci says

> 
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)


I've gotten NDISwrapper downloaded and extracted on my desktop.  I'm currently looking at the list_b on the NDISwrapper site but I'm not seeing my specific wireless card.  

should I use a different one?:confused:



EDIT

Nevermind I found the driver I need I think.

---

### Post by Wes.Green on 2007-05-23
Hmm

Alright...I've got Ubuntu loaded and running, seems most stuff is working fine.

I'm having problems with getting the wireless to work though.
Could someone please give me a step by step from downloading the ndiswrapper to installing the windows drivers on this unit?

I believe that I have the correct drivers but I'm not 100% sure. 

Here's what I have.
> 
NDISwrapper     stable  	1.44  	May 17, 2007

> 
#
Card:Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card rev 01

    *
      PCIID: 03:00.0 0280 14e:4311 rev 01
    *
      PC: HP pavilion dv6000 series ‘DV6105US’
    *
      OS: Slackware 11.0
    *
      Driver Used: Win32 Driver from HP
    *
      [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=sg&dlc=en&product=3245619&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=sg&dlc=en&product=3245619&os=228&lang=en) HP Driver
    *
      Other: Kernel version 2.6.19 Slackware 11.0 Ndis 1.33 newest windows driver, absolutely no issues!


Both NDISwrapper and the HP driver are on my desktop (ndiswrapper is a .tar.gz file and the HP driver is a .exe)

Sorry for being such a bug.

---

### Post by jcaveman on 2007-05-24
This link has some instructions on the page for setting up ndiswrapper with DV6000 series computers:

[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by Wes.Green on 2007-05-24
Man this is a pain.

Ok, I've follow the instructions [http://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-f744e28e6c78eb83d22be77819b130016a8e51f3]("http://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-f744e28e6c78eb83d22be77819b130016a8e51f3")
and had no apparent luck.

I got to step 7 (I think) where it says to run iwconfig to make sure your essid and access point fields have been filled 
> 
 user@ubuntu:~bcm4311$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"My_Essid"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:08:74:02:01:FC
          Bit Rate:11 Mb/s
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Its suppose to look like that, or at least somewhat.  this is what mine looks like

> 
root@wesside-laptop:/home/wesside/bcm4311# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I commented out the eth1 line and ndiswrapper says its using wlan0 but for whatever reason I cant get it to see my network.
:(

---

### Post by jcaveman on 2007-05-25
I probably would have left it alone. Mine comes up as eth1 anyway and works just fine.  Do you have network manager installed?  Does your network have security set?

---

### Post by Wes.Green on 2007-05-25
My router has a WEP security password (which i setup long ago)

Um as for network manager, not unless there is a default one installed with Ubuntu?

---

### Post by jcaveman on 2007-05-30
Wireless can be real easy under Ubuntu if you have a card that is directly supported by the kernel. That of course implies vendor support.  Unfortunately, most notebook manufacturers cut cost by using this cheap Broadcom wireless chip and Broadcom won't release their specs so the kernel developers can write a driver.  As a result your left with this ndiswrapper work around.  Try loading network-manager from the repository, if its not already installed.  That should make life easier for you.  It will certainly make setting up the WEP encryption easier.

---

