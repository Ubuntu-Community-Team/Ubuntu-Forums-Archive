---
title: "Problems Installing D-Link DWA-130..."
date: 2008-08-29
forum: x86 64-bit Users
---

### Post by Atticus_Starr on 2008-08-29
So I'm trying to install my d-link dwa-130 usb device and I got as far as installing ndiswrapper but if I go to MainMenu -> System -> Administration -> Windows wireless drivers and click on configure network there is no wireless connection in the list. 

My gui looks like this [http://filesmelt.com/Imagehosting/pics/bfe317a8d586fa1e96f7c53c2d65ada8.png.]("http://filesmelt.com/Imagehosting/pics/bfe317a8d586fa1e96f7c53c2d65ada8.png") 

my device is found under code: 

ndiswrapper -l. 

but when i do code: 

sudo iwconfig 

it says there are no wireless anything. 

I tried the code on this post [http://ubuntuforums.org/showthread.php?t=892252&highlight=dwa-130]("http://ubuntuforums.org/showthread.php?t=892252&highlight=dwa-130"), but when i get to code: 

sudo ndiswrapper -m 
sudo echo ndiswrapper >> /etc/modules 


it says access is denied. please help.

---

### Post by yoman on 2008-08-29
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Yellow Pasque on 2008-08-29
Err, sorry about that. Try this:
```
gksudo gedit /etc/modules/
```
Add a line that says:
```
ndiswrapper
```
Save and quit. Now:
```
gksudo gedit /etc/network/interfaces
```
Make sure you have at least the first two lines to create a wireless interface. Mine looks like:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid *name_of_your_wireless_network*
```

---

### Post by Crafty Kisses on 2008-08-29
Try as stated above, if that doesn't work, can you please post the output of:```
lshw -C network
```

---

### Post by Atticus_Starr on 2008-08-30
that didn't work. when I put in code:

gksudo gedit /etc/network/interfaces

it tells me that the directory does not exist. 
Oh, and the output to lshw -C network


Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

don't really know what to do now :(

---

### Post by Yellow Pasque on 2008-08-30
> that didn't work. when I put in code:
gksudo gedit /etc/network/interfaces
it tells me that the directory does not exist. 
What directory? We're trying to edit a file, and if the file does not exist, it should be created. I can't imagine if/how you could axe your /etc/network directory.
Try it again. To paste a command in the terminal, use Ctrl+Shift+v

For lshw, open up Synaptic (System -> Administration -> Synaptic..) and install lshw-gtk. Then you can access your hardware list with:
```
gksudo lshw-gtk
```

---

### Post by Atticus_Starr on 2008-08-31
ok... so back to what you were saying earlier. i tried code:

gksudo gedit /etc/modules/

and got...

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
ndiswrapper

then i did code:

gksudo gedit /etc/network/interfaces

and got...

auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1

should i just place in text like the one you showed me yours should look like?
Also, how do u put code into that little box, I'd like to know to make things more clear :)

---

### Post by Atticus_Starr on 2008-09-01
bump...

---

### Post by Yellow Pasque on 2008-09-01
> should i just place in text like the one you showed me yours should look like?As long as your ISP uses dhcp and not static IP addresses, then yes.

> Also, how do u put code into that little box, I'd like to know to make things more clear
with [ CODE ][ /CODE ] tags (no spaces between the brackets)

---

### Post by Atticus_Starr on 2008-09-01
can you tell me exactly what code i should put in if im connecting to a netgear router?

---

### Post by Yellow Pasque on 2008-09-01
> **Atticus_Starr said:**
> can you tell me exactly what code i should put in if im connecting to a netgear router?
Try the example I used at the end of post #2. i.e:
```
auto wlan0
iface wlan0 inet dhcp
```
This should at least get you to the point where you can configure your ESSID and encryption with the NetworkManager GUI. If you didn't log in to the router and change the name of the network, it'll probably be "Netgear" as the default. 

If you can't get an IP, then your ISP probably uses static IP addresses, and you'll need to check with them on what yours is (and write it down for future reference).

---

