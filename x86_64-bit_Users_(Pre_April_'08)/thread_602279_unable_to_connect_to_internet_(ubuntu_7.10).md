---
title: "unable to connect to internet (ubuntu 7.10)"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by d00by on 2007-11-04
I have installed ubuntu gutsy using alternate install CD AMD 64 bit.

I am having problem accessing my wifi on my compaq v3228au laptop.

I posted about this including screenshots here

[http://broadbandforum.in/linux/18449-unable-connect-internet-ubuntu-7-10-a/](http://broadbandforum.in/linux/18449-unable-connect-internet-ubuntu-7-10-a/)

What I tried to did was extract te broadcom firmware so that my wifi would work.

Any idea what I am doing wrong? How do I verify If I have correctly installed the firmware?

Am I entering wrong info in network manager.

I have open WEP wifi with password and SSID broadcast set to off.

EDIT: here is my system config

> System Manufacturer	Hewlett-Packard	
System Model	Presario V3000 (RZ819PA#ACJ)	
System Type	X86-based PC	
Processor	x86 Family 15 Model 76 Stepping 2 AuthenticAMD ~2009 Mhz	
BIOS Version/Date	Hewlett-Packard F.34, 02/06/2007	
SMBIOS Version	2.4	
Windows Directory	C:\WINDOWS	
System Directory	C:\WINDOWS\system32	
Boot Device	\Device\HarddiskVolume1	
Total Physical Memory	1,024.00 MB	
Available Physical Memory	438.90 MB	
Total Virtual Memory	2.00 GB	
Available Virtual Memory	1.96 GB	
Page File Space	1.56 GB	
Page File	C:\pagefile.sys	

results of my firmware extract thingy in ubuntu terminal window

> user@ubuntu:~$ sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/BCMWL564.SYS
[sudo] password for user:
fwcutter can cut the firmware out of /home/user/Desktop/BCMWL564.SYS
  filename :  bcmwl564.sys
  version  :  3.70.17.5
  MD5      :  f5590c8784b91dfd9ee092d3040b6e40

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.
*****: But this can be added in the future...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...
user@ubuntu:~$ sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/BCMWL564.SYS
fwcutter can cut the firmware out of /home/user/Desktop/BCMWL564.SYS
  filename :  bcmwl564.sys
  version  :  3.70.17.5
  MD5      :  f5590c8784b91dfd9ee092d3040b6e40

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.
*****: But this can be added in the future...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...
user@ubuntu:~$ 

---

### Post by dirkmegabyte on 2007-11-04
I absolutely could not get wireless to work with broadcast SSID set to 'off' on my wireless access point. I had to turn the sid broadcast on to connect and let the network manager 'find' the connection. No matter what I did, it would not work until I did that. Beyond that, wireless works flawlessly. Its not a big deal since I'm using wep-psk and doing mac filtering. My laptop is a Compaq Presario F730US with 7.10 x86_64 and the built-in broadcom wireless:

root@craptop:~# lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02) 

...I followed this forum post which works solid 100%:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

...and I had to use step 2a in that forum post.

Good luck!

---

### Post by Cappy on 2007-11-04
Open WEP didn't work for me in Feisty.

First of all try using the HEX password instead of the ASCII.
[http://centricle.com/tools/ascii-hex/](http://centricle.com/tools/ascii-hex/)


Here is the bug report of this problem:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/50214)

In it it says there is a patch for Gutsy here:
[http://ppa.launchpad.net/asac/ubuntu/pool/main/n/network-manager/](http://ppa.launchpad.net/asac/ubuntu/pool/main/n/network-manager/)

If all else fails I previously had to remove the network-manager and install a program that supported WEP called WICD. I'm still using WICD in Gutsy after upgrading from Feisty and it is working.

---

### Post by d00by on 2007-11-04
Thanks.

I followed step 2b.

It worked like magic! All is well. :)

---

### Post by studo77 on 2007-11-04
Internet Connection is less stable in Gutsy, according to my experience.

I sometime lose http, and mostly all net contact.

In my settings Gutsy adds two other DNS addresses. I tried removing them, and only let my router be in there. It was stable for some time, but then got lost, and then i found out, Gutsy added those addresses again. So something is being done automaticcally to net configuration.

Most of the time it works perfectly, but it is annoying. And i am using a wired connection.

---

### Post by d00by on 2007-11-04
I am having problem with my wifi on my Windows XP boot. It loses connection to wifi every few minutes and I have to repair the connection to make it work again.

No such problems on my Ubuntu boot. Go figure! :(

Did my wifi install on Ubuntu mess up my wifi setup in windows??

---

### Post by brunoscunha on 2008-02-21
I find it hard to affect your windows install unless you may have tampered with the wireless chipset

---

