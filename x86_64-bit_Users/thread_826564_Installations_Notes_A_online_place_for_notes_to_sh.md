---
title: "Installations Notes: A online place for notes to share..."
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by VitalBodies on 2008-06-12
**Installations Notes:** An Online place to keep notes...

This is my online place to keep installations notes. Your welcome to keep yours here also, thus others might benefit. Plus if your system is down you have a place to go on another computer to fix yours. 

**MY NOTES:** (a work in process, somewhat brief but working on them) 

XXXXXXXXXXXXXXXXXXXXX GETTING READY: XXXXXXXXXXXXXXXXXXXXX
**BACKUP:** 
Export Bookmarks. 
Screen capture Passwords. 
Export Mail Address Book. 
Write down or Screen capture  Mail Account Settings and Passwords. 
Mail. 
FTP addresses, passwords and settings. 
Fonts. 
Critical settings for certain programs like online MYSQL databases, 3D graphic card drivers and such. 
A screen capture of tabs or passwords can be helpful, like for Firefox. 
Desktop stuff. 
All of my files.

XXXXXXXXXXXXXXXXXXXXX INSTALL: XXXXXXXXXXXXXXXXXXXXX
Boot to the CD and install. 
XXXXXXXXXXXXXXXXXXXXX SETUP: XXXXXXXXXXXXXXXXXXXXX

**SETTING UP UBUNTU:** 

Change Software Sources to MAIN SERVER.
System > Administration > 
Run Update Manager to make Ubuntu up to date. 
If you have no connect then connect using the little double monitor icons in the upper right corner of the default Ubuntu screen. 
If your driver does not work then see below NO INTERNET? 
 

**Install Firewall:** 
Applications > Add/remove... > add firestarter

Setup fire to start at login:
Open Nautilus: ```
gksudo nautilus
```
Edit your /etc/sudoers
Change from read only. 
Add this Line TO THE END: ```
your_login_name ALL= NOPASSWD: /usr/sbin/firestarter
```
Change to read only.

System > Preferences > Sessions: 
Startup Tab > 
Name: FireStarter FireWall
Add command: ```
sudo firestarter --start-hidden
``` 
Comment: Start the Firewall at login



**AntiVirus:**
Applications > Add/remove... >  Add CalmTk
```
sudo freshclam -v
```

**MAIL**: 
Import Email
Import Address book. 
download dictionary

**FTP:** 
Load Bookmarks:
For FileZilla: [http://wiki.filezilla-project.org/FAQ](http://wiki.filezilla-project.org/FAQ)
Home Folder > Show Hidden Files > .Filezilla
Rename sitemanager.xml to sitemanager.xml_old in case you have to go back.
Basically you have to replace the sitemanager.xml with your one from back up.

**BROWSER: **
Bookmarks
Gnash: If you use gnash add/remove add Gstreamer-ffmpeg plugin 
Flash: sudo aptitude install flashplugin-nonfree
Java: 
Applications > Add/remove... >  add icetea and OpenJdk

**XAMPP: Apache, PHP, MySQL etc in one easy to install package.**
Download: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
INSTALL:
```
cd /to where XAMPP is...
```
Begin the install: 
```
sudo tar xvfz xampp-linux-1.6.6.tar.gz -C /opt
cd /opt/lampp/
```

START: ```
sudo /opt/lampp/lampp start
```
STOP: ```
sudo /opt/lampp/lampp stop
```
TEST: [http://localhost](http://localhost) or [http://localhost/index_global.shtml](http://localhost/index_global.shtml)
SECURITY: ```
/opt/lampp/lampp security
```
PW: your_password
Username: lampp
CONFIGURE: [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
TRANSFER FILES TO HTDOCS: ```
gksudo nautilus
```

**FONTS:** 
gksu nautilus /usr/share/fonts/truetype
Make a directory and add fonts...
 
```
sudo fc-cache -f -v
```

**Resource Monitor:** 
```
sudo apt-get install htop
htop
```

XXXXXXXXXXXXXXXXXXXXX WIRELESS: XXXXXXXXXXXXXXXXXXXXX

**Connecting Using :** 
Applications > Add/remove... >  Add RutilT (for serialmonkey drivers)

Build this so you can build the legacy drivers. 
```
sudo apt-get install build-essential
```

**Getting Connected: **
Applications > Add/remove... >  Add RutilT
Ralink RT2570 chipsets based wireless 802.11g devices like my 
Download Driver: [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)
INFO: [http://ralink.rapla.net/](http://ralink.rapla.net/)
XXXXXXXXXXXXXXXXXXXXXXX
Re: Installing the ra2570 driver...
Here is how I got the wusb56gv4 working:

**SHORTENED INSTRUCTIONS:**
Download to desktop: [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)
Extract the driver (right click on its icon on your desktop and select "Extract Here.")
sudo apt-get install build-essential
cd ~/Desktop/rt2570-cvs-2008061613/Module (must = Folder Name)
make
sudo make install
sudo gedit /etc/modprobe.d/blacklist
#Added these entries to the blacklist to replace rt2500usb with rt2570usb:
blacklist rt2500usb
blacklist RT2500USB

sudo modprobe rt2570
sudo ifconfig rausb0 up
REBOOTED then set networking to manual (used my routers setting SSID etc) rather than roaming and REBOOTED
sudo ifconfig rausb0 up
REBOOTED
Connected!

**SHORT REINSTALL INSTRUCTIONS:**
1.) Download to desktop: [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)
--> If you did not do this before updating the kernel you still might be fine. 
--> Use the latest driver you have. 
2.) Extract the driver (right click on its icon on your desktop and select "Extract Here.")
3.) cd ~/Desktop/rt2570-cvs-2008061613/Module (must = Folder Name)
4.) make
5.) sudo make install
6.) sudo modprobe rt2570
7.) sudo ifconfig rausb0 up
8.) Bring up RutilT and connect as needed...
9.) You should be Connected!


NOTES:
```
lshw -C network
```
Gets this:
```
*-network
description: Wireless interface
physical id: 1
logical name: rausb0
serial: 00:12:17:83:ff:47
capabilities: ethernet physical wireless
configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=RT2500USB WLAN
```


**SHORTENED RT2500 INSTRUCTIONS:** 
Download to desktop: [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
Extract the driver (right click on its icon on your desktop and select "Extract Here.")
sudo apt-get install build-essential
cd ~/Desktop/rt2500-cvs-2008052413/Module
make
sudo make install
sudo -s
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist 
sudo modprobe rt2500
sudo ifconfig rausb0 up
lshw -C network

XXXXXXXXXXXXXXXXXXXXX NO INTERNET?: XXXXXXXXXXXXXXXXXXXXX
**NO INTERNET?:**
What if you can not connect to the internet? 
I got it going! I had a LOT of help. 
Ideally you would install a Linux driver. If you only have a Windows driver this will get you going until you find a Linux driver. 
Here is what is needed: 
You need to get Ndiswrapper going. 
If you had a connection to the net all the above would be easy. 
With the Ubuntu CD in the drive try this: 
System > Administration > Software Sources: 
Choose the CDROM with UBUNTU check box. 
Close. 
Applications > Add/remove... >  
Select all open source applications. 
Search for wireless drivers
Check the check box for Windows Wireless Drivers
Click the enable button. 
That should install Windows Wireless Drivers
Go to  System > Administration > Windows Wireless Drivers
See if you can load your driver. 

If not...
Just go to Synaptic Package Manager, that is in System > Administration and search the Synaptic Package Manager for **Ndis** and you will find three things to load:
ndisgtk
ndiswrapper-common
ndiswrapper-utils. 

If that fails:
But with no connection you will have to use another computer and connect and get these: (Example: this is for the 64-bit version) 
Mirrors for 64 ndisgtk:
[http://packages.ubuntu.com/hardy/amd64/ndisgtk/download](http://packages.ubuntu.com/hardy/amd64/ndisgtk/download)

Mirrors for [all architecture] ndiswrapper-common: 
[http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download](http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download)

Mirrors for 64 ndiswrapper-utils 1.9:
[http://packages.ubuntu.com/hardy/amd64/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/hardy/amd64/ndiswrapper-utils-1.9/download)

Download all 3 and install them in this order: commons, utils and then ndisgtk.
NOTE: They will answer with dependency error if one or the other has to go first. 

Once these are installed then use this driver: 
[http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

Once you have installed that driver setup your wireless in Network Settings. 
Note: Be sure to reboot if you have problems. 

I wrote his message using the 64-bit Ubuntu Hardy and my Atheros based Abit wireless card! 

Please add your helpful notes to those who follow our foot steps....
Did this post help?

XXXXXXXXXXXXXXXXXXXXX COMMANDS: XXXXXXXXXXXXXXXXXXXXX
**COMMANDS:This is just a reference that I saw in another thread. **
lspci -v | less - What chipset does the card have? 
ifconfig - lists IP address (similar to ipconfig in Windows)
iwlist scan - shows wireless networks that are available in the area along with basic encryption information
lshw -C network - Shows interface and driver associated with each networking device
lspci -nn - Shows hardware connected to the pci bus
lsusb - Shows USB connected hardware
lshw -C usb - Additional info on USB related hardware (good for USB dongles)
cat /etc/modprobe.d/blacklist - List modules that will not be loaded by the Operating System at boot time
lsmod - lists currently loaded kernel modules. (Example usage - lsmod | grep ndiswrapper)
route -n - Lists kernel IP routing table -- Good for troubleshooting problems with the gateway (netstat -rn = equivalent command)
sudo route add default gw 192.168.1.1 - Example of how to set the default gateway to 192.168.1.1
sudo route del default gw 192.168.1.1 - Example of how to delete the default gateway setting
sudo modprobe ***** - Loads the kernel module **** . (Example usage - sudo modprobe ndiswrapper, sudo modprobe r818x, sudo modprobe ath_pci)
sudo modprobe -r **** - Unloades the kernel module ****. (Example usage - sudo modprobe -r ndiswrapper)
sudo ifup/ifdown <interface> - Brings up/down the interface and clears the routing table for the specified interface
sudo ifconfig <interface> up/down - Brings up/down the interface for the specified interface
sudo dhclient <interface> - Request IP address from DNS server for specified interface
sudo dhclient -r <interface> - Release IP address associated with specified interface
sudo iptables -L - Lists firewall rules
dmesg | more - Lists boot log -- good for troubleshooting problems with modules/drivers not being loaded
uname -r - Displays kernel version
/etc/iftab (Feisty and pre-releases (Edgy, etc)) - /etc/udev/rules.d/70-persistent-net.rules (Gutsy) - File which assigns logical names (eth0, wlan0, etc) to MAC addresses
cat /etc/resolv.conf - Lists DNS servers associated with network connections (Network Manager)
/etc/dhcp3/dhclient.conf - File which sets or modifies dns (domain name servers) settings

---

