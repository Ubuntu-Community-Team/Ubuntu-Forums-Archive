---
title: "Exact steps to getting Airport Extreme working in Dapper..."
date: 2006-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by spaceballl on 2006-03-11
**Update: I have been getting some positive IMs/ emails/ responses about this working fairly well. For those who cannot get it working well, make sure you are trying this on a FRESH INSTALL (i.e. don't mess w/ any network/wireless settings before you try this) of Ubuntu Linux, flight 5. Maybe it's worth making this a *sticky?* Also, since I just updated this, if anyone sees any glaring mistakes, please let me know so I can change them! Good luck!!!**
[UBUNTU LINUX FLIGHT 5 DOWNLOAD]("http://cdimage.ubuntu.com/releases/dapper/flight-5/")

*Note: If anyone can help me out on how to get this thing fully working w/ all the gnome gui utils, etc, let me know. I think this a crucial element for PPC users, and we should try to get a very detailed howto going.*

Do exactly this, and you should get some success with 802.11G in Ubuntu Linux, Dapper Flight 5 PPC.

1. Hook your computer up to an ethernet connection. We need to download a few files through your landline before we can get wireless up and running. Ubuntu should be able to detect this network at installation. If not, go to *System, Administration, Networking*, and set it up real quick.

2. Launch Synaptic Package Manager. To do this, go to to *System, Administration, Synaptic Package Manager*. In order to get 802.11g working we need a few files. Click search and look for the following files: *gcc, g++, subversion, and make*. Check the boxes next to these files to get them ready to be installed. If, while you're doing this, another window pops up and lists dependencies to be installed, don't worry about. It needs these files too. Once it's all done, click *Apply*. Wait for everything to finish and close Synaptic.

3. Then open up a terminal window by clicking *Applications, Accessories, Terminal*. Then type the following, hitting enter at the end of each line (if it asks for your password in the end, make sure to enter it):
```
svn checkout svn://svn.berlios.de/bcm43xx/trunk/fwcutter
cd fwcutter
make
wget [http://www.ghostcorp.net/AppleAirPort2](http://www.ghostcorp.net/AppleAirPort2)
./bcm43xx-fwcutter AppleAirPort2
sudo make installfw
```

4. At this point, everything should be good to go, functionality wise. Now you just need to set it up. To do that, we'll make a script that prepares your internet. Don't close your terminal window, but open the gnome text editor by clicking *Applications*, *Accessories*, *Text Editor*. The standard text editor should open up, and it will be familiar to anyone who has used windows before. Paste the following lines into the blank document:
```
#!/bin/bash
interface=eth0 # interface of your wireless card
# Turning off wired network...
ifconfig eth1 down
modprobe bcm43xx
# Starting up wireless network...
ifconfig $interface up
iwconfig $interface essid MY_ESSID
iwconfig $interface mode managed
iwconfig $interface key off
dhclient $interface
```
[SIZE="1"]**Note: I believe that all iBooks / Powerbooks have eth1 = ethernet, eth0 = wifi. Mine does. you'll need to verify yours. The original script more or less taken from the ubuntu wiki (not trying to claim its mine)**[/SIZE]

**802.11B network only?**If you have an 802.11B network, add the following text on its own line, in between the lines, "ifconfig $interface up" and "iwconfig $interface essid MY_ESSID."```
iwconfig $interface rate 11M
```

5. In the text, change "MY_ESSID" to the name of your wireless network. Then click *File, Save As*. Name the file "wirelessup" and don't give it any sort of extension. Save it in the default location. Close the text editor.

6. Go back into your open terminal window and type the following lines, hitting enter after each one:
```
cd
chmod +x wirelessup
sudo ./wirelessup

```

7. Fire up firefox and surf that sweet net wirelessly! Either that... or get some errors and then come back here for more help! ](*,)

Every time you boot up the computer, you'll have to enter the terminal and type the following:
```
sudo ./wirelessup
```

...but people are working on there being better ways...

---

### Post by Bonjourmate on 2006-03-12
Tried it and got this at the end.

```

bonjourmate@Wookie:~$ sudo ./myscript
eth1: ERROR while getting interface flags: No such device
FATAL: Module bcm43xx not found.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; Operation not supported.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; Operation not supported.
./myscript: line 11: Setting up dhcp: command not found
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:0d:93:37:d7:cc
Sending on   LPF/eth0/00:0d:93:37:d7:cc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
ip length 576 disagrees with bytes received 580.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 576 disagrees with bytes received 580.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.17 -- renewal in 1005302120 seconds.

```

---

### Post by spaceballl on 2006-03-12
what output do you get if you just type "iwconfig"?

---

### Post by aimislame15 on 2006-03-12
I followed these exact steps and got it working on my iBook after 3 try's. I was also reading some other threads at the same time to get it working and might have incorperated some other stuff into it but it works.
All I have to do now on bootup is set the channel rate mode and connect. I'm in the process of writing a perl script to automate the connection as well. Just keep trying this stuff over and over. Go ahead and try to rmmod all the mods you added, then re-download them all and start over. I had to try it a few times btu it worked ;-) P.S. this is from my ibook in linux ;-)

---

### Post by Bonjourmate on 2006-03-12
[QUOTE=spaceballl]what output do you get if you just type "iwconfig"?[/QUOTE]

```
bonjourmate@Wookie:~/Desktop/openrpg1$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

---

### Post by Madman68 on 2006-03-12
Are you sure you are using the newest release "Dapper". That output looks to me to be the output I got when trying to configure my Airport extreme in the previous release of Ubuuntu. Also, are you shure your wireless card in working right if the above is not the case.

---

### Post by spaceballl on 2006-03-12
Yah something is wrong w/ that iwconfig. Even if we don't do anything that I wrote above, we should get some wireless extensions... what version of dapper are you using

---

### Post by spaceballl on 2006-03-13
```

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
ip length 576 disagrees with bytes received 580.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 576 disagrees with bytes received 580.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.17 -- renewal in 1005302120 seconds.

```
Bonjourmate, are you sure your internet isn't working at this point? It looks like you're on an access point...

---

### Post by Bonjourmate on 2006-03-13
Well :D it may be.  I made a very stupid mistake though, I wasn't even using Dapper.  I didn't figure out what Dapper was till a few replies into this whole thing.  Just moved to Linux and am using Breezy.  

If Airport Extreme works in Dapper, cool, or at least it will be when it's released.  But for now I need something stable and so I'll stick with Breezy and keep working on madwifi.

---

### Post by spaceballl on 2006-03-13
[QUOTE=Bonjourmate]Well :D it may be.  I made a very stupid mistake though, I wasn't even using Dapper.  I didn't figure out what Dapper was till a few replies into this whole thing.  Just moved to Linux and am using Breezy.  

If Airport Extreme works in Dapper, cool, or at least it will be when it's released.  But for now I need something stable and so I'll stick with Breezy and keep working on madwifi.[/QUOTE]
Download Dapper Flight 5! The newest CD is reeeeeeeally stable. I have it, and plus, Ubuntu's new default theme is way sexier than Breezy. Honestly, Dapper is leaps ahead of Breezy, especially in mac support :-). I'd check it out if I were you...

---

### Post by Bonjourmate on 2006-03-13
I suppose I'll give it a shot.

---

### Post by pitr on 2006-03-14
I got this working on my ibook following other peoples info found on the net and even managed to get wpa working but there is one thing I'm having problem with. Sometimes when I boot my wireless interface is called eth2 othertimes eth1. Anyone have any ideas what is wrong and how to fix it?

---

### Post by Bonjourmate on 2006-03-14
I burned the Dapper ISO onto a CD and booted from it, but when I did I got a picture of a folder in the middle of screen that flashed a question mark and something else (can't remember the second image).  Anyways, it didn't seem to go any further than that and I had to restart and boot into breezy.  Any ideas what may be happening?

---

### Post by spaceballl on 2006-03-14
it means the ISO can't be booted off. Probably a bad burn i think. Try burning it at a different speed?

---

### Post by Bonjourmate on 2006-03-14
heh, that was my last blank disc.  I'll pick up some more after class.

---

### Post by AlphaMack on 2006-03-23
I'm getting the same error as Bonjourmate and I'm on Dapper.  The first time I got it to work (meaning the card was recognized but no valid access point), then I tried something else that completely borked it all.  And now doing these same steps I too get the "fatal bcm43xx not found" message and the same dump as quoted above.

---

### Post by slooksterpsv on 2006-03-23
Below this thread is a thread of mine, it tells you how to get and install everything you need. If someone does this and thinks I need to reword it, please let me know, or type up a summary of what you did. Thanks. Its below this thread, I got internet on it working great using my method.

---

### Post by AlphaMack on 2006-03-23
I still get the same error.

I wonder if something to do with [this method](http://www.fisica.unipa.it/~lavaget/ubuntuae/) borked bcm43xx all together for me.

---

### Post by slooksterpsv on 2006-03-24
Actually, bcm43xx isn't installed with Dapper Drake, found that one out, at least not the firmware version. If you do dmesg, that'll show you an error saying the module can't be found. So just follow those steps on the one thing, I uploaded the file, and it should work. I have had others have success


Also, WPA and WEP passwords are accepted if you follow my method. see HOW-TO in this part of the forum.

---

### Post by papyromancer on 2006-03-27
Rock! 8) 54 Mbps :-D -- everyting else I tried only allowed 11Mbps. I might add that I did this on a clean (networking at leat) flight 5 install.

Just make sure you modify the script to YOUR essid.

```
eth0      IEEE 802.11b/g  ESSID:"rublev"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:14:BF:E0:08:D7
          Bit Rate:54 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
```

---

### Post by spaceballl on 2006-03-27
[QUOTE=papyromancer]Rock! 8) 54 Mbps :-D -- everyting else I tried only allowed 11Mbps. I might add that I did this on a clean (networking at leat) flight 5 install.[/QUOTE]
Glad you got it up and running!!! I updated the instructions to hopefully make them a bit more user friendly. The steps go into a bit more detail and now I write the script w/ a GUI text editor rather than w/ VI. So I hope this helps everyone. Best of luck!!!

---

### Post by Richard on 2006-03-27
Hi,

This method only works with WEP authentification, not with WPA ? :-k

---

### Post by Seq on 2006-04-07
I modified your script a bit. It is a little light on the error reporting as it only reports module errors. I'm a little rusty on my shell scripting, so I'll add proper error handling/notification later (or if anybody else does, that would be good too).

Basically it does the same configuration as before, but now it will run itself through gksudo when you run it as your user. So make a file on your desktop, make it executable (same steps as before), but now you can just click this and type your password.

```

#!/bin/bash

interface=eth0
ssid=ci-ap

if [ `/usr/bin/whoami` != 'root' ]
then
  gksudo $0
else
  modprobe bcm43xx || zenity --error --title="Error" --text="Error loading bcm43xx module"
  iwconfig $interface up
  iwconfig $interface rate 11M
  iwconfig $interface essid $ssid
  iwconfig $interface mode managed
  iwconfig $interface key off
  dhclient $interface | zenity --progress --pulsate --auto-close --text="Connecting to Network..."
fi

```

Also, there appear to be only two problems I can see stopping NetworkManager from working with an Airport Extreme bcm43xx.
[LIST=1]
[*]NM tries to bring the interface up at full speed. To resolve this, edit this file:
```
'/etc/network/if-pre-up.d/wireless-tools
```
Add this to the file right after the iwconfig check at the top:
```
ifconfig $IFACE up
$IWCONFIG "$IFACE" rate 11M
```
Also, comment out the block referencing $IF_WIRELESS_RATE, just incase.

[*]ifup apparently now tries to configure all wireless through wpa_supplicant? It seems to run automagically, and investigating the files in /etc/network/*.d/ seems to confirm this. I do not know how to disable this yet (I've spent all of about five minutes on it so far). After fixing this, though, NetworkManager and other tools *should* work for us. 
[/LIST]

---

### Post by Abandon on 2006-04-08
I' m using Ubuntu 6.06 flight 6 PPC version and there is no "svn" command there. What is svn, why is is not there (anymore)?

---

### Post by spaceballl on 2006-04-08
Hmmm... I think you need the package "subversion." try getting that and then trying the svn command.
-Kevin

---

### Post by n00bWillingToLearn on 2006-04-09
I followed your instructions and my wifi was working but because I am new to linux I broke X trying to get XGL working and because I don't yet have anything important on my Ubuntu partition I just re-installed. I then tried just running your sh script ( or is it called a bash script? ) because I seemed like fwcutter stood for firmware and that that sould not have changed by reinstalling Ubuntu. When that didn't work I followed your instructions completely once more ( I changed the eth0 to eth1 and eth1 to eth0 in the script because my wireless is eth1 according to 'Networking', and it worked the first time ). My wireless still does not work and I hope that doing whatever was done with the firmware twice didn't hurt anything. I am willing to re-install again and will probably end up needing to anyways. I am running dapper on a 17'' powerbook in case that matters.

edit: Also when wireless was working it would only connect when very close to the router and failed to connect even when I had three bars in OSx.

---

### Post by jjb on 2006-04-09
[QUOTE=spaceballl]**Update: I have been getting some positive IMs/ emails/ responses about this working fairly well. For those who cannot get it working well, make sure you are trying this on a FRESH INSTALL (i.e. don't mess w/ any network/wireless settings before you try this) of Ubuntu Linux, flight 5. Maybe it's worth making this a *sticky?* Also, since I just updated this, if anyone sees any glaring mistakes, please let me know so I can change them! Good luck!!!**
[UBUNTU LINUX FLIGHT 5 DOWNLOAD]("http://cdimage.ubuntu.com/releases/dapper/flight-5/")

*Note: If anyone can help me out on how to get this thing fully working w/ all the gnome gui utils, etc, let me know. I think this a crucial element for PPC users, and we should try to get a very detailed howto going.*

Do exactly this, and you should get some success with 802.11G in Ubuntu Linux, Dapper Flight 5 PPC.

1. Hook your computer up to an ethernet connection. We need to download a few files through your landline before we can get wireless up and running. Ubuntu should be able to detect this network at installation. If not, go to *System, Administration, Networking*, and set it up real quick.

2. Launch Synaptic Package Manager. To do this, go to to *System, Administration, Synaptic Package Manager*. In order to get 802.11g working we need a few files. Click search and look for the following files: *gcc, g++, subversion, and make*. Check the boxes next to these files to get them ready to be installed. If, while you're doing this, another window pops up and lists dependencies to be installed, don't worry about. It needs these files too. Once it's all done, click *Apply*. Wait for everything to finish and close Synaptic.

3. Then open up a terminal window by clicking *Applications, Accessories, Terminal*. Then type the following, hitting enter at the end of each line (if it asks for your password in the end, make sure to enter it):
```
svn checkout svn://svn.berlios.de/bcm43xx/trunk/fwcutter
cd fwcutter
make
wget [http://www.ghostcorp.net/AppleAirPort2](http://www.ghostcorp.net/AppleAirPort2)
./bcm43xx-fwcutter AppleAirPort2
sudo make installfw
```

4. At this point, everything should be good to go, functionality wise. Now you just need to set it up. To do that, we'll make a script that prepares your internet. Don't close your terminal window, but open the gnome text editor by clicking *Applications*, *Accessories*, *Text Editor*. The standard text editor should open up, and it will be familiar to anyone who has used windows before. Paste the following lines into the blank document:
```
#!/bin/bash
interface=eth0 # interface of your wireless card
# Turning off wired network...
ifconfig eth1 down
modprobe bcm43xx
# Starting up wireless network...
ifconfig $interface up
iwconfig $interface essid MY_ESSID
iwconfig $interface mode managed
iwconfig $interface key off
dhclient $interface
```
[SIZE="1"]**Note: I believe that all iBooks / Powerbooks have eth1 = ethernet, eth0 = wifi. Mine does. you'll need to verify yours. The original script more or less taken from the ubuntu wiki (not trying to claim its mine)**[/SIZE]

**802.11B network only?**If you have an 802.11B network, add the following text on its own line, in between the lines, "ifconfig $interface up" and "iwconfig $interface essid MY_ESSID."```
iwconfig $interface rate 11M
```

5. In the text, change "MY_ESSID" to the name of your wireless network. Then click *File, Save As*. Name the file "wirelessup" and don't give it any sort of extension. Save it in the default location. Close the text editor.

6. Go back into your open terminal window and type the following lines, hitting enter after each one:
```
cd
chmod +x wirelessup
sudo ./wirelessup

```

7. Fire up firefox and surf that sweet net wirelessly! Either that... or get some errors and then come back here for more help! ](*,)

Every time you boot up the computer, you'll have to enter the terminal and type the following:
```
sudo ./wirelessup
```

...but people are working on there being better ways...[/QUOTE]

---

Thank you. Close, so close, but airport is not working yet. Here is the problem:
I did *exactly* what you wrote and there was a big wake up on the machine (Dapper flight 6 on a Apple PB alu 1.5), a lot of noise and the explicit presence of the Airport card via iwconfig.
But when I try to connect via eth2 (this is what iwconfig shows I thought it would be eth0), I receveive this answer:

"Listening on LPF/eth2/00:11:24:90:78:9d
Sending on   LPF/eth2/00:11:24:90:78:9d
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping."

What is 255.255.255.255 by the way? the router? does it have to show off as I'm using DHCP (Scuze, I'm a novice).

If you have any solution to this problem - close, so close ...

jjb

---

### Post by jjb on 2006-04-09
Yep, I think ethx is the main problem. In my case it "should" be eth0 and iwconfig shows eth2 - and cascading the ethx in the script doesn't resolve the problem (by the way, is there a different ethx on ibooks, powerbooks etc?) . I actually wonder if the stable version of dapper will fix the problem, and help connecting via wifi without having to trigger a script each time. jjb

---

### Post by shorty0927 on 2006-04-11
((Newly installed Dapper on my dual-boot G4 PB 15", 1.5GHz))

I think I'm having problems with WPA.  You said that your instructions ought to get the wireless working with WPA, but I haven't seen a spot in the instructions (or network settings) that would have me to enter my WPA password.

I THINK everything else is ok--iwconfig gives me this:
[COLOR="Gray"]
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"WhatNoPie?"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate:54 Mb/s   Tx-Power=15 dBm
          RTS thr: off   Fragment thr: off

eth1      no wireless extensions.
[/COLOR]
I tried installing wpa_supplicant, as recommended in [these]("http://www.fisica.unipa.it/~lavaget/ubuntuae/") instructions that someone else posted, but I'm having trouble accessing the configuration file to make some changes.

I'm curious about something else--during install, it appeared that the Airport card and ethernet were identified during hardware detection and I was given the option of choosing wireless or wired at that point.  Did anyone else encounter this, too?  I tried selecting the wireless option, but it didn't seem to make the connection, so I chose the ethernet option instead.  Would that have an effect on whether or not these instructions work for me?

---

### Post by humina on 2006-04-14
I followed this how to with flight 6.  I have my iwconfig all set up but I also cannot get an IP address from dhclient.  Any clue why this is?  My dmesg output it:
 SoftMAC: Can't perform deauthentication, network is not authenticated.
could that be the problem?

---

### Post by AlphaMack on 2006-04-15
I finally got my Airport working.

Use wifi-radar to create a profile:

Network Name:  Your ESSID
Under WiFi options:
Mode: auto
Channel: auto
Key:  Your password **prefixed by 's:'** without the quotes.  So if your key is "sugar123" you would enter "s:sugar123"
Security:  Restricted

Connection should be DHCP.

Now try to connect and you should obtain a working IP.  You might get kicked off, so the next thing to do is head over to System->Administration->Networking.  Enter the same information about your network for the eth1 (or eth0) wireless card.  You might even want to create different locations (where is that promised hot-WiFi switching a la the Airport menu?).

You'll definitely need to reboot.  I know I had to.

YMMV, but here I am posting while connected to a WEP-protected network.


Caveats:
1.  Sleeping the machine and waking it will cause network loss.  You won't be able to reconnect at all and you'll need to reboot.

2.  Sleep is a little flaky in Flight 6 anyway. ;)

---

### Post by jaboit on 2006-04-21
hello thanks for all the good info --

however, I can't seem to find the subversion package. sudo apt-get install subversion tells me the package is missing, and it doesn't appear with a Synaptic Manager search.

Any ideas?

Im on a G4 with Dapper flight 6

EDIT:

Sorry, I found it:   [http://ubuntuforums.org/showthread.php?t=96787&highlight=subversion+missing](http://ubuntuforums.org/showthread.php?t=96787&highlight=subversion+missing)

---

### Post by shorty0927 on 2006-04-23
Can anyone confirm that they have wireless functioning on a powerbook (or ibook, I suppose) running Dapper?  If so, which versions of the kernel and drivers are you using?

I'm wondering because I've been trying to get wireless working on my powerbook with Dapper/2.6.15-18ppc kernel and the latest bcm43xx driver, fwcutter and softmac, but not having much luck.  I'm picking up wireless networks (according to Networking), but haven't been able to get my wireless network to see my powerbook.

On the bcm43xx website, they say that you need to be using a 2.6.16+ kernel, but I haven't found a source on the internet that says a 2.6.16+ kernel is stable on a powerbook...so I'm just wondering what worked for all you unwired PB users.  

Thanks!

---

### Post by AlphaMack on 2006-04-23
[QUOTE=shorty0927]Can anyone confirm that they have wireless functioning on a powerbook (or ibook, I suppose) running Dapper?  If so, which versions of the kernel and drivers are you using?

I'm wondering because I've been trying to get wireless working on my powerbook with Dapper/2.6.15-18ppc kernel and the latest bcm43xx driver, fwcutter and softmac, but not having much luck.  I'm picking up wireless networks (according to Networking), but haven't been able to get my wireless network to see my powerbook.

On the bcm43xx website, they say that you need to be using a 2.6.16+ kernel, but I haven't found a source on the internet that says a 2.6.16+ kernel is stable on a powerbook...so I'm just wondering what worked for all you unwired PB users.  

Thanks![/QUOTE]

I had Wireless working with Dapper Flt 5 (then 6 and now the beta) using the latest driver on a Rev A 15" Al PowerBook G4.  You'll need to use Wi-Fi Radar to connect to the network.  If using WEP, be sure your passphrase includes a "s:" at the beginning (without quotes).  Also add a profile in System->Admin->Networking.  Then reboot.

---

### Post by shorty0927 on 2006-04-23
> You'll need to use Wi-Fi Radar to connect to the network.

With something like kismet?  How is that done?

> Also add a profile in System->Admin->Networking.

Do you mean add a location?  eth0 has been showing up in my Networking window automatically, but I haven't tried adding a location.

Should I be using the Config panel in Networking to config the connection, or would it be better to do adjust it all with command line in iwconfig?

Keep the suggestions coming...after a couple of weeks of trying, I'm still determined to get this wireless working!

---

### Post by jackoverfull on 2006-04-24
i'm on dapper flight 6 and it works for me. anyway it sometimes dont work and i need to reboot or to sleep and try againm almost randomly.

subversion was missing for me too but after a **sudo apt-get update** all was ok.

nice work anyway, i almost lost all hopes! :-D

---

### Post by jackoverfull on 2006-04-25
a strange thing appened after dist'upgrade: my airport cart was eth0, now it's eth1 and eth0 is the ethernet card!:-k 

when i noticed that i modified the script wirelessup replacing eth0 with eth1 and i'm connected again.
any idea on how it's possible?:-k

---

### Post by shorty0927 on 2006-04-25
I don't know for sure (because I'm a Linux noob) but it might have something to do with udev, which is some kind of dynamic device management thing.  I only know about it because I was reading through the first post of the [self-help]("http://www.ubuntuforums.org/showthread.php?t=142716") forum (see #11-f) and saw something about it.  The post just directs you to the man pages to learn how to make those devices have static numbers.  Sorry I can't help with specific coding...

---

### Post by Seq on 2006-04-25
[QUOTE=jackoverfull]a strange thing appened after dist'upgrade: my airport cart was eth0, now it's eth1 and eth0 is the ethernet card!:-k 

when i noticed that i modified the script wirelessup replacing eth0 with eth1 and i'm connected again.
any idea on how it's possible?:-k[/QUOTE]
I noticed ifrename was removed from my system a few days ago during an update. Perhaps it was for you as well, and your NICs are loaded in a different order.

Put "bcm43xx" in your /etc/modules on it's own line, and your cards should be loaded in the original order again.

Or re-install ifrename :p

---

### Post by macluvjay on 2006-04-26
[writting this from withing Ubuntu (1GHz iBook G4 Dual-Boot OS X/Ubuntu)]

Thank you to everyone for the tutorial.  If anyone is interested...
Everything went smoothly, except, the script.  All I did was setup profiles in Network Settings for eth0.  It is currently working at work with WEP.  I'll see how it likes my home setup tonight.  Will report back then.

---

### Post by donovan1983 on 2006-04-27
I followed just through step 3 and then put bcm43xx in my /etc/modules file and it all works great. I just use Wifi-radar to connect to an access point, no extra scripts or disconnection from the ethernet network needed. On my system the wifi card is eth1. I'm using an iBook G4 12" 1.2GHz if that helps any.

---

### Post by CSMatt on 2006-05-06
[QUOTE=spaceballl]2. Launch Synaptic Package Manager. To do this, go to to *System, Administration, Synaptic Package Manager*. In order to get 802.11g working we need a few files. Click search and look for the following files: *gcc, g++, subversion, and make*. Check the boxes next to these files to get them ready to be installed. If, while you're doing this, another window pops up and lists dependencies to be installed, don't worry about. It needs these files too. Once it's all done, click *Apply*. Wait for everything to finish and close Synaptic.[/QUOTE]
None of these packages show up in the Synaptic Package Manager in the Beta version.

---

### Post by spaceballl on 2006-05-06
[QUOTE=CSMatt]None of these packages show up in the Synaptic Package Manager in the Beta version.[/QUOTE]
you probably need to enable all the repositories.

---

### Post by CSMatt on 2006-05-08
How would I do that?  The wiki doesn't help (there seems to be a different method in Dapper) and the last time I enabled all packages and downloaded updates for these new packages, my iBook was rendered useless.

---

### Post by littlephil on 2006-05-17
Looks like ghostcorp.net has disappeared, does anyone know an alternate download location for the AppleAirPort2 driver?

Thanks in advance.

---

### Post by slooksterpsv on 2006-05-17
Give me a few minutes to alter my configuration for my Trackpad and I'll upload my version of it. I'll even ZIP the fw files so if you don't want to extract the ones, you don't have to.

---

### Post by slooksterpsv on 2006-05-17
Here you go, already extracted

---

### Post by littlephil on 2006-05-18
Now berlios.de seems to be down, nightmare. Thanks for the other files though, I can't seem to figure out how I use them though. Any information would be appreciated.

---

### Post by bluemonki on 2006-05-18
[QUOTE=alphasubzero949]
Caveats:
1.  Sleeping the machine and waking it will cause network loss.  You won't be able to reconnect at all and you'll need to reboot.

2.  Sleep is a little flaky in Flight 6 anyway. ;)[/QUOTE]

if you 're-modprobe' the bcm43xx driver it should come back up without a reboot :)

Try this:

```

# sudo modprobe -r bcm43xx

# sudo modprobe bcm43xx

```

I don't think the sleep is that bad really....

---

### Post by slooksterpsv on 2006-05-18
[QUOTE=littlephil]Now berlios.de seems to be down, nightmare. Thanks for the other files though, I can't seem to figure out how I use them though. Any information would be appreciated.[/QUOTE]
You need to go to a Terminal (under Applications->Accessories) and cd to the directory where the bcm43xx files are. So lets say you extracted them to your desktop, then type in:
cd ~/Desktop/bcm43xx[PRESS TAB KEY] -- pressing tab will fill in the rest for you.
sudo cp *.fw /lib/firmware -- Type in your password, it won't show up, but its  there and that will copy all the fw files to there.
modprobe bcm43xx -- this probes the driver so you can use it. Then in a thread I have setup I tell you how to get it working under Dapper Drake.

---

### Post by littlephil on 2006-05-21
Thanks for all the help, after my router decided to take some time out I've now got this all up and running. Finally I can walk round the house and listen to Radio 4 over the internet again. Praise be:)

---

### Post by Uta on 2006-05-25
First thank you to all the people who have posted useful info on this issue. I actually got my iBook working wireless off the Live CD. I wasn't sure it was possible but here I am posting from the Live CD on my iBook via the Airport Extreme card. I can't wait for June 1st to get the full install disc of Dapper for PPC. Cheers!

---

### Post by spaceballl on 2006-05-26
Glad you got it working!

---

### Post by tuggy on 2006-05-26
really? it works with the livecd? i wanted to give it a try before wiping out OS X :)
we just have to follow the same steps, right??

---

### Post by Uta on 2006-05-26
Yes you need to follow 'some' of the steps.
I had no way of using an ethernet cable to download the files to my laptop so I previously downloaded the needed files and put them on an external USB drive. Booted the Live CD, the USB drive mounted on the desktop, I dragged the required files on to Ubuntu's desktop,I used Ubuntu's Networking(GUI) to put in my info for my card (name, WEP settings, etc) and proceeded with the install of the files. .
After the install, I did  'ifup eth1'  and I was on--

---

### Post by tuggy on 2006-05-26
thanks everyone, its working perfectly!!
wireless is very stable and fast, im running with the livecd, so everything will be lost when i restart :(

i used wifi-radar to help me out, and installed network-manager. its strange because the network manager applet displays a warning sign, and says it cannot detect any network devices...

---

### Post by areitze on 2006-05-26
Hey All,

Thx for all the info posted, I finally got the airport card on my iBook working.  but i do find that the strength of the conection is not that good.  It worked pretty well in my room before under os x, but now it's been very hard to get connected in my room, but when I'm Closer to the router, of course it works a lot better.

One other problem I've found with the conection is the sleep.  When my iBook went to sleep, or when the screensaver activated and left the laptop for a couple of hours un touched, I had to reboot the computer complete to be able to conect back to the wifi conection.  I've been using wifi radar, but not sure if it is the correct app to use, plus I can't see any signal strength while I'm conected... how can I fix this???

Thx again for all your help
ARV.-

---

### Post by aimislame15 on 2006-05-29
I haven't had that problem and I sleep and restart my computer all the time. Maybe you should do a 

```

apt-get update
apt-get dist-upgrade

```

---

### Post by areitze on 2006-05-29
Thx for the tip, but no can do...  upgraded all I needed, rebooted, still can't login with wep... only while I have the router open... with no wep and for everyone around to freely navigate in my wifi conection..  :D  I'd like to keep it like that, but I still have to get conected to wifi networks that do use wep...

Sleep issue is still there though... Signal is very week, and waking up the iBook, makes me reboo the whole system...

mmmm
ARV.-

---

### Post by AlphaMack on 2006-05-29
[QUOTE=bluemonki]if you 're-modprobe' the bcm43xx driver it should come back up without a reboot :)

Try this:

```

# sudo modprobe -r bcm43xx

# sudo modprobe bcm43xx

```

I don't think the sleep is that bad really....[/QUOTE]

I'll have to try that when I get back to my Mac.

My other Achille's heel for the time being is NetworkManager.  It won't accept my WEP passwords, both with or without the 's:' prefix.  And yes, I selected the 64/128 ASCII option (at least on the PC side, this does work and without the need for 's:' in the WEP passphrase).  I really wish that there is some kind of way to make it work because changing profiles in Networking (or even using Wifi-Radar) can be a PITA.

---

### Post by spaceballl on 2006-05-30
[QUOTE=alphasubzero949]My other Achille's heel for the time being is NetworkManager.[/QUOTE]
Yeah can't stand that...

---

### Post by acorn22 on 2006-05-30
Does this work in Kubuntu? Or when will it? It should, right? All it is is Ubuntu with KDE.

And if it does, does it work with the lastest LiveCD? That is the what I am currently using.

EDIT: Nevermind. 

[http://www.ubuntu.com/testing/flight5#head-f14bdc0c107b0a5328378706008230328700f68b](http://www.ubuntu.com/testing/flight5#head-f14bdc0c107b0a5328378706008230328700f68b)

but the links are dead :(

---

### Post by spaceballl on 2006-05-30
[QUOTE=acorn22]Does this work in Kubuntu? Or when will it? It should, right? All it is is Ubuntu with KDE.[/QUOTE]
Yeah, for better or worse, this solution doesn't rely on any GUI based stuff so it will work w/ ubuntu, kubuntu, xubuntu, etc

---

### Post by h.ornstein on 2006-05-31
Hallo ,

I have followed the posts on the Airport Extreme, though it is possible to get it working, it is quite difficult for a newbie. Most of the stuff that is written about the Broadcom chip is meant for Ubuntu on pc. That raises another question: Why can a laptop with a common wireless card, get on the internet by using the Airport Extreme? It may be stupid, but I don't understand the necessity of the Broadcom chip now.
I think I take anethernet cable to connect Ubuntu. If you think I'm stupid feel free to answer and help me.

---

### Post by acorn22 on 2006-05-31
[QUOTE=h.ornstein]
That raises another question: Why can a laptop with a common wireless card, get on the internet by using the Airport Extreme? [/QUOTE]

If I understand your question, It is becasue Broadcom won't release the drivers for the AirPoret Extreme.

But Airport cards are only in iBooks/Powerbooks, or so I beleive.

---

### Post by h.ornstein on 2006-06-01
Hallo,

I'll be more specific about my problem. I have a mac g4, with the Belkin F5D7000 wireless pci card inserted. This card needs a driver for the ralink rt2500 chipset. With macosx I can reach the internet. A laptop with winxp an a common wireless card gives no problem. So the airport extreme basestation is working with two os's without a broadcom driver. My question is : why refuses Ubuntu to get connected ?

Any help or suggestions are welcome !

---

### Post by acorn22 on 2006-06-02
At what point can I unplug? Right after dling from synaptic?

h.ornsein: I can't help you there. :( Sorry

---

### Post by dtm693 on 2006-06-02
Hi all,

I'm using Kubuntu (Dapper) and it appears that my Airport card is picking up my wireless network; however, my network is WPA, and being new to Linux, I am confused as to what to do.

In the "Wireless Assistant," I can see my network, but it is unable to connect (obstensibly because there isn't WPA support?).  Can someone help me out with this?

I lack a tremendous amount of Linux knowledge, so if anyone who replies could assume I know nothing, it would be much appreciated.  Thanks in advance.

--Dan

---

### Post by James_M on 2006-06-04
Mine's not really working.  this is the output of my iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```
andbefore that, this is what came up:
```
Listening on LPF/eth0/00:11:24:80:7b:da
Sending on   LPF/eth0/00:11:24:80:7b:da
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
ip length 328 disagrees with bytes received 332.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 333 disagrees with bytes received 337.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.254
bound to 192.168.1.65 -- renewal in 42808 seconds.

```
What did I do wrong?  I'm using a Xubuntu live CD.

---

### Post by veebis on 2006-06-07
Finished step 2 (Synaptic package installs), system notified requiring restart. On restart, yaboot freaks out, won't boot... "Invalid memory access" message, then an infinite loop of non-starting. Did a re-install, just in case, same thing.

HELP!

---

### Post by veebis on 2006-06-07
Just in case, nevermind.
Reinstalled, followed different guide, voila! Airport. Extreme? Can't tell yet (b wireless)...

---

### Post by bennyp on 2006-06-14
Hey all. I have a very strange problem.
I installed the firmware from a downloaded driver. The driver file (the latest one from 10.4.6) that came from my partition would not work with fwcutter, so i was forced to download one.

My problem is that I can connect to the network, but the ip address I receive is bad, it's 70.x.x.254, which is clearly no good. What can I do here?

---

### Post by perl_user on 2006-06-17
*wget [http://www.ghostcorp.net/AppleAirPort2](http://www.ghostcorp.net/AppleAirPort2)*

the url doesnt work :(

is there a other download location how knows anybody ?

and is this the best solution at the moment to get Airport work?

---

### Post by dombleu on 2006-06-25
You know, I might be redundant, but I can't stand to remain silent when I still see all this struggle around the ae card.

For already a few times installing dapper on my powerbook G4, that is really all I need to do:

get, unpack and build fwcutter
./fwcutter AppleAirPort2
sudo cp *.fw /lib/firmware

and configure my network with the usual Ubuntu gui tools.

No need to get dirty with scripts and iwconfig anymore...

Hope it helps.

Dom

---

### Post by draculr on 2006-06-26
[QUOTE=perl_user]*wget [http://www.ghostcorp.net/AppleAirPort2](http://www.ghostcorp.net/AppleAirPort2)*

the url doesnt work :(

is there a other download location how knows anybody ?

and is this the best solution at the moment to get Airport work?[/QUOTE]


Yes, the link is broken, anyone have another??

---

### Post by spy1325 on 2006-06-30
[QUOTE=draculr]Yes, the link is broken, anyone have another??[/QUOTE]

i also desperatly  need this file also, i hadn't bothered to read through the whole thread before i started the process.. i was so excited about Airport support.. now my dreams have been shot down by the "ERROR 404" man....:(

---

### Post by spy1325 on 2006-06-30
I got the AppleAirPort2 File from "/System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2"
from a mac, but now i need a place to store it so i can wget it, becuase manually placing it at / is not working for me. anyone willing to host the file?
or anyone willing to tell me where to store the file so the rest of the commands will work?

---

### Post by spy1325 on 2006-06-30
SUCCESS!!!!

i had to extract the AppleAirPort2 firmware from the .kext file on a diffrent mac, and followed all your insntructions untill the text file batch file. 

the only way i can get it to work, is every time i boot up, i run these commands
```

sudo ifconfig eth1 up
sudo iwlist eth1 scan
sudo iwconfig eth1 channel <CHANNEL>
sudo iwconfig eth1 enc <MYKEY>
sudo iwconfig eth1 essid <MYESSID>
```

and that works to find any wireless access points around, and then i can connect, works great. 

anyone who cant find the AppleAirPort2 File can Pm me if they need it, if people are still using this method and are reading this thread.

im going to write a batch file to automaticly connect to my home network, but with this i am able to connect to other networks...
woohoo airport extreme WORKS!

---

### Post by Strohmy on 2006-09-10
.

---

### Post by string on 2006-09-10
I managed to scan for networks but how do I set a WEP key ? thanks

---

### Post by jackoverfull on 2006-09-13
i'm on edgy now, works perfectly here!:) 
only a difference: the mod bcm43xx is already loaded and need a reload so install the driver then do:

```
modprobe -r bcm43xx
modprobe bcm43xx
```

also the gnome network tool can't find the essid automatically, inserting it manually works.

---

### Post by sokkles on 2006-11-27
Just wanted to say thank you! I followed the original instructions in this thread, on a G4 iBook (w/ Dapper, heard that Edgy might be a bit too edgy on a mac..), with the exception of extracting "AppleAirPort2" from my OS X partition. Ten minutes of work, now I'm posting this over a wireless connection.

So thanks again!

---

### Post by sirhandel on 2006-12-04
Hey...I don't have an apple partition (wiped entire drive clean...) can anybody send me the file that was hosted on ghostcorp.net, as well as EXPLICIT instructions on what to do with it? This is my second day on linux, and I have no idea what I'm doing. My e-mail address is [email]dashboardbuddha@gmail.com[/email]

Thanks!

---

### Post by lws1984 on 2006-12-12
Slight issue here, instead of downloading from that site I got the AppleAirPort2 file off my OS X partition, but when I try to do the "./bcm43xx-fwcutter AppleAirPort2" bit, I get a "command not found" error. What's going on?

---

### Post by aimislame15 on 2007-02-14
Are you in the same directory as the bcm43xx-fwcutter file?

---

### Post by sylvielouise on 2007-02-20
hey, "[http://www.ghostcorp.net/AppleAirPort2]("http://www.ghostcorp.net/AppleAirPort2")" i don't think it exists anymore...

is there an alternative to this command in step 3.

[INDENT]svn checkout svn://svn.berlios.de/bcm43xx/trunk/fwcutter
cd fwcutter
make
wget [http://www.ghostcorp.net/AppleAirPort2](http://www.ghostcorp.net/AppleAirPort2)
./bcm43xx-fwcutter AppleAirPort2
sudo make installfw[/INDENT]


cheers.

---

