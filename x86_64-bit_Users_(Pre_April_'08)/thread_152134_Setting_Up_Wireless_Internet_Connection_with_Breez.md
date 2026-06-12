---
title: "Setting Up Wireless Internet Connection with Breezy + Airport Extreme"
date: 2006-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by plush on 2006-03-29
First of all, I have been using Ubuntu Breezy, the live cd, on my powerpc64 G5 for a few weeks and I'm thoroughly impressed.  I prefer it over Aqua any day.  However since I'm relatively new to Linux, and since Airport Extreme support on Breezy is a bit more complicated to set up, I need help with doing so.

Also, in Breezy, I've tried setting up wireless internet with a Linksys Wireless G USB device I have handy, to no avail.  My router is Linksys, 192.168.1.1 is the internal IP, and the SSID is linksys.  I don't use any encryption like WEP or WPA.

Any help or direction as to where I can find help would be greatly appreciated.

---

### Post by OfficeLinebacker on 2006-03-29
[https://wiki.ubuntu.com/WiFiHowto]("https://wiki.ubuntu.com/WiFiHowto")

---

### Post by plush on 2006-03-29
Thanks a bunch!  I didn't even notice the Wiki area.  I've read a ton of old posts about setting up the airport extreme card but they're a bit confusing and outdated...  Does the latest Dapper release readily support this card?

For a powerpc mac user, would you suggest installing Breezy or Dapper?

---

### Post by OfficeLinebacker on 2006-03-30
No problem, I'd say over half the things people start threads about have been documented in the the WiKi.
 
Good job being a responsible citizen with the searching first and whatnot, and welcome!

---

### Post by plush on 2006-03-30
**[COLOR="DarkRed"]IGNORE THE THREAD TITLE, THIS IS A DAPPER, NOT BREEZY POST.[/COLOR]**

Success!  I've been able to get online, and I'm currently using Ubuntu Dapper Flight 5.  

Here are the problems I've experienced:  
-"Airport Extreme" can refer to either to Apple's base station OR the wireless card. 
-Many posts are outdated, providing unnecessary or possibly crippling info. 
-Differentiating between steps in Apple Unix Terminal vs Umbuntu's Linux Terminal. 
-Apple's Darwin has many small nuances that can trick its users switching to Linux. 
-Countless cross-references and links about the exact same things (ha, like this one)!

Anyway, the trick to getting the _Airport Extreme card _to work was:

[COLOR="Blue"]A)[/COLOR] Using the fwcutter (on the firmware taken from [http://www.ghostcorp.net/AppleAirPort2](http://www.ghostcorp.net/AppleAirPort2); remember it's case-sensitive if you're using "wget") and then placing the many *.fw files I got in /lib/firmware (on my Ubuntu partition of course).  [COLOR="black"][COLOR="Red"]No need to download SoftMac, the BCM43xx snapshot, or anything like that!  There is a lot of confusion about this![/COLOR][/COLOR]

[COLOR="Blue"]B) [/COLOR] Setting up a static IP for my router (Linksys WRT54G), either manually with "iwconfig" or through the Networks GUI in the Administration menu.
[COLOR="Blue"]
C) [/COLOR]And finally running "dhclient" for my adapter interface from a script that sets the rate to 11M (SEE BOTTOM LINKS).

Notes:  This is on a **Power Mac G5** circa 2004,  dual-booting **Ubuntu Dapper Flight 5** and **Mac OS X Tiger**.  A **Linksys WRT54G** router is the wireless access point. 

_Important installation information:_

I followed the instructions in the thread below to shrink my partition.  The two new necessary partitions were then created from the Ubuntu installer CD (which only worked when I burned it with disk utility rather than Toast), by choosing "Guided Partitioning" and "Use Largest Block of Free Space".  Attempting to create an "Apple_Bootstrap" partition on my own caused problems and subsequently I realized choosing the latter "Guided" option was idiot-proof.

_Easily mount your Macintosh HD Partition:_

Go to "/dev/disk/by-label", and see what your OSX HFS+ volume is labeled as by typing "ls".  Make a directory where you want to mount your partition, for example "sudo mkdir /mnt/macosx".  Then type  "sudo mount /dev/disk/by-label/YOURDISKLABEL  /mnt/macosx -t hfsplus" to mount it there.  To link to it from your desktop go to ~/Deskop, and type "ln -s /mnt/macosx".  If this works, put the necessary info into your "/etc/fstab" file to have it boot up that way.

Very Helpful Posts:
[http://ubuntuforums.org/showthread.php?t=142727](http://ubuntuforums.org/showthread.php?t=142727)  [COLOR="DeepSkyBlue"]-Airport Extreme card firmware issues + script[/COLOR]
[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)  [COLOR="DeepSkyBlue"] -Fast repartition w/o deletion[/COLOR]
[http://www.ubuntuforums.org/showthread.php?t=14922&highlight=mounting+mac+os+partition](http://www.ubuntuforums.org/showthread.php?t=14922&highlight=mounting+mac+os+partition)[COLOR="DeepSkyBlue"]-Mount your OS X HFS+ Partition[/COLOR]
[http://www.ubuntuforums.org/showthread.php?t=85720&highlight=mounting+mac+os+partition](http://www.ubuntuforums.org/showthread.php?t=85720&highlight=mounting+mac+os+partition)

THERE WERE NO OTHER STEPS, CONFIGURATIONS, OR DOWNLOADS!

---

### Post by CSMatt on 2006-04-21
I apologize for bringing up such an old thread, but I'm finding myself in the same situation.  I have an iBook G4 (12 inch 800 MHz model) and installed Breezy Badger but can't use the AirPort Extreme card.  The wiki didn't help me, iwconfig did not show any wlan setups, and the wireless tools are already installed.

I would appreciate some assistance.

---

### Post by AlphaMack on 2006-04-21
You guys need to be using Dapper.

This is how it worked for me.  Use fwcutter to extract the firmware components from AppleAirPort2.  Modprobe it and reboot.

Use a program like Wi-Fi Radar to find your base station to obtain an IP.  Ditto entering a location into System->Admin->Networking.  You **can** use DHCP and WEP as well, so as long as your passphrase includes **s:** at the beginning.  So if your WEP key is "sugar123" you would enter "s:sugar123" into the fields.  Select the location and also be sure that you can connect to your base station.  Then reboot again.  You should now be connected and have a working connection.

The caveat?  You have to reboot every time you switch networks or if you sleep your machine.

---

### Post by plush on 2006-04-21
I am using Dapper.  Matt, I would also highly recommend you switch to Dapper.  Although there is a bug in the PPC kernel which affects systems with +1GB of Ram from using their Airport Extreme cards, if you don't have that much RAM you're good to go.  BTW the bug's been filed, and there is a patch for it, but unfortunately I haven't been able to implement it (it's a patch for the 2.6.16 kernel, and I can't seem to compile it ](*,) ).

[http://www.ubuntuforums.org/showthread.php?t=155824](http://www.ubuntuforums.org/showthread.php?t=155824)
[https://launchpad.net/distros/ubuntu/+bug/38912](https://launchpad.net/distros/ubuntu/+bug/38912)

Matt, if this isn't your case, then I suggest you download bcm43xx-fwcutter, cut the airport .fw files from the AppleAirport file I linked to above, and put those in your /lib/firmware folder.  Then run modrpobe bcm43xx and you should be good to go.  Remember to set your rate to 11M if you're still having problems.  These instructions are for Dapper, if you have Breezy use to wiki to find instructions;  they are quite a bit more involved so I simply suggest you use Dapper.  If you need more help just private message me :)  I've had my fair share of tinkering with the Airport.

---

### Post by CSMatt on 2006-04-21
Is there any chance that this driver will come with the next version of Ubuntu?

---

### Post by plush on 2006-04-22
Listen, it IS included in the new Dapper version.  However the firmware files needed by the drivers are NOT, because they are proprietary Apple hardware files.  Thus the fw-cutter (firmware-cutter) tool for extracting the files out of Apple's driver file, and then placing these into the Linux /lib/firmware directory for the driver to work :)

---

