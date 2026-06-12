---
title: "The actual solution to broadcom 43XX on iBooks wanted!"
date: 2006-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by N'Jal on 2006-03-31
Ok i have spent all night scouring the forums for how to make the broadcom 43xx driver work under dapper, no luck, i tried wiki's howto's, firmware.debs everything, and nothing has worked currently i am using this thread [http://www.ubuntuforums.org/showthread.php?t=89960](http://www.ubuntuforums.org/showthread.php?t=89960), 
To allow me to duel boot without constantly installing operating systems, now if you have no idea how to fix this problem please do not post, even good luck messeges, i appriciate you hope we will find our solution, but it just means more posts to sort through to get to the solution. I mean no disrespect but we need a solution asap.

I know other people have G4 iBook's and ain't got this working so guys this is for you and me, once we get one iBook working theoretically we should get them all working. 

I need a iBook to be able to connect to a router we decided to name W00T3R, it's bad but better than MSHOME, and W00T3R uses 128-WEP, so if we get that working unencrypted networks should be a cinch.

What i have personally discovered: -

1) The airport card in G4 iBooks is 4318 or 4306 both are supported [http://openfacts.berlios.de/index-en.phtml?title=Bcm43xxDevices](http://openfacts.berlios.de/index-en.phtml?title=Bcm43xxDevices)

2) The fwcutter can be used to extract tiger drivers, and with a Tiger installation it can be retrived from /System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2

3) It's a catch 22, you need an internet connection to install this bloody thing, you need an ethernet cable idealy, sorry dude's but that's the way it has to be, it's either wire it up or spend all night downloading dependancies on another computer, not reccomended, been there and done that. 

4) The driver is in the 2.6.15 =< kernel tree, Dapper has a such kernel, so upgrading to dapper is a much easier way to go, Now it's certinly possible to install breezy and them use a flight cd to upgrade to breezy that way. Or just install Breezy and dist upgrade with that handy internet connection.

5) Using NDISwrapper tutorials are to be avoided as they are for the X86 platform only, no good to us.

If anyone has some more fundamental things to know i shall add them, now if anyone who got it working could post i would appriciate it.


EDIT: I have gotten the duel boot set up, and at some point today when my housemate isn't asleep i shall invade his room and update to Dapper.

EDIT: Upgraded to dapper used fwcutter to install driver, nothing, tried the live cd, told it to connect to W00T3R with the password it just looped asking me for the password every few seconds. This was with flight 5.

---

### Post by ceratophyllum on 2006-04-01
I have a G4 and I got it working. But it is not ready yet for the general public, as in people who are unable or unwilling to use the command-line. Sorry about the catch-22 you mention, but you are running bleeding-edge, alpha quality software.

Are you using DHCP or do you have a static IP set for your interface? It sounds like you have done all the hard stuff.  Unfortunately, even with the latest version of Dapper, the GUI network config utility still does not work.  You have to do it manually and then write a script to automate the process.

I am using DHCP and have a router to share my connection with my wife's windows PC.

Check that the modules are loaded: lsmod | grep bcm43xx

Before you try to bring up the interface, look through the output of dmesg to make sure the softmac and broadcom modules loaded w/o errors.


Once you're sure the modules are loaded and the interface exists, run the following script as root (use sudo) to bring it up:

modprobe bcm43xx
# make sure module is loaded

ifconfig eth0 down
ifconfig eth0 up
# bring up interface. use iwlist to check if your wireless interface is
# eth0 or eth1

iwlist eth0 scan
#show user what's giong on

iwconfig eth0 channel 6
iwconfig eth0 rate 11M
iwconfig eth0 essid "default"
#these settings above will vary depending on your network!
#use iwlist to find what your settings are

dhclient3 eth0
# start dhcp client to
# get IP, gateway, DNS servers from router


I have a 1.2 GHz 12" ibook G4 and wireless is working pretty reliably. But when I wake the ibook from sleep, the wireless connection stops working even though it looks like the interface is still up. Just run the script again when you wake the iBook.

---

### Post by N'Jal on 2006-04-01
```

njal@serenity:~$ lsmod | grep bcm43xx
bcm43xx               128812  0
ieee80211softmac       32384  1 bcm43xx
ieee80211              38248  2 bcm43xx,ieee80211softmac

njal@serenity:~$ dmesg
[   63.930938] ieee80211_crypt: registered algorithm 'NULL'
[   63.933429] ieee80211: 802.11 data/management/control stack, git-1.1.7
[   63.933437] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@li nux.intel.com>
[   63.996431] bcm43xx:  driver

```
Those seem to be the relevent parts of dmesg
```

njal@serenity:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"W00T3R"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off

eth0      no wireless extensions.

sit0      no wireless extensions.


njal@serenity:~$ sudo ./internet.sh
SIOCSIFFLAGS: No such file or directory
eth0      Interface doesn't support scanning.

Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth0 ; Operation not supported.
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device eth0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; Operation not supported.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:11:24:8a:d7:c0
Sending on   LPF/eth0/00:11:24:8a:d7:c0
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
i think that eth0 is not my wireless device im sure it's eth1 from iwconfig and the output of the script so i changed the script to eth1 and re-ran it, this is it's output.
```

njal@serenity:~$ sudo ./internet.sh
SIOCSIFFLAGS: No such file or directory
eth1      Interface doesn't support scanning : No such device

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:11:24:9b:af:20
Sending on   LPF/eth1/00:11:24:9b:af:20
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

And even for someone like me who doesn't know so much about the working's of linux knows that the network was detected but the packets were not tx/rx, i beleive this has something to do with our network being WEP protected, i do not have the authority to deactivate the password. 
If there was a way of specifying the password in the script i do however know the password.

Thank you for your help so far, at least i know the drivers and firmware and present and working. My idea is to get wireless working then writing a shell script that should do it automatically for the user, i was thinking of creating a iso image for mac users to install but i would have nowhere to post it. But even then, could i use mkisofs to create an installable image of my mac system to overwrite the existing duel-boot installation and be ready to go wirelessly? 

If you just wanna focus on this one step at a time, that's cool, i would like to get wireless working first, if push came to the shove i could redo what i did previously. But again thank you.

---

### Post by dombleu on 2006-04-02
I fought for days trying to install mine on my powerbook G4.

Always ended up like this: I can see the hotspot, but can not talk to it in no way.

But!

I came accross a post on this very forum with a nice little script to start the thing. 

[http://ubuntuforums.org/showthread.php?t=142727&highlight=howto+airport](http://ubuntuforums.org/showthread.php?t=142727&highlight=howto+airport)

But that was not enough. I just found that fwcutter was putting the firmware files in the wrong place! Just copied them where they should, and if I recall well, it's in /lib/firmware, and excuted that litte script and it was all done!

No real magics since I got to run a script at every boot to get it working. But I guess It could be linked somehow to the boot process in /etc/rc.d/.

Anyway It works really f***g great ever since. Great driver really. Just a little complicated to get it up and running for the first time.

I should try it with the network tool of ubuntu. It might be just working from there as well now...

Edit: It is. I just reset everything in the ubuntu network tool, reconfigured my wl card and rebooted. Wifi is still working! So I guess I would just need to extract the firmware in the right place and activate the card with ubuntu setup stuff. But then again, i'm not on a Ibook, i'm on powerbook. Don't know if that makes much a difference...

P.S.: One thing that is definately cool with Linux is that I can really see things getting better and better, and when something is going wrong, most often there's a trick to get things somehow working the way I want. There is always at least hope! Just to much comps running onto hopeless OSes.

---

### Post by N'Jal on 2006-04-02
Ok nothing worked, the firmware is in two places now, /lib/firmware and /lib/hotplug/firmware. But when scripts are run, i beleive that Linux detects the ESSID, but because our connection is WEP protected and since i have had no chance to enter the password at any point it's a given that i am not going to get online. Unless i manually connect to the router, which is curious since shouldn't i have to enter the password there too?


But what i know about my system thus far

1) My wireless connection resides on eth1
2) The scripts can detect the ESSID
3) I still cannot get online
4) Everytime i run the scripts i get a messege about no leases avalible, or something like that. But i am sure we use DHCP, because we just set up the router and didn't assign static IP's so unless the router is defaulted to static IP's we should be on DHCP.

EDIT: This is the terminal output from the screen when i run the script
```

njal@serenity:~$ sudo ./wirelessup
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:11:24:9b:af:20
Sending on   LPF/eth1/00:11:24:9b:af:20
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

And i can confirm DHCP is being used, manually jacking into the router and checking my settings shows me i am indeed using DHCP and am getting online being plugged into the router.

However what's curious is when i did iwconfig after running the scripts i got this 
```

njal@serenity:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"MY_ESSID"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate:54 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off

eth0      no wireless extensions.

sit0      no wireless extensions.

```

EDIT: Ok i was on #ubuntu+1 was told to install network-manager, i installed that, it's applet and the gnome bit, and it magically worked, without the need for entering the WEP password. Strange.

EDIT2: Also i can only seem to get a wireless connection after starting connected to the router with a wire in the first place, i can then disconnect the cable and DHCP over wireless kicks in.

EDIT3: After learning how NetworkManager works, i have a greater understanding of what might be going on inside my machine, however I've managed to get wireless for a while, but when i reboot it's totally gone, and i can't seem to keep the applet in the tray nor open the gui for it to run any of the scans.

I also added bcm43xx to my /etc/modules file but alas this has not had the desired effect. Tomorow i will however start putting a script together that got me to where i am for any mac users that are in the same boat.

Thanks
Njal

---

