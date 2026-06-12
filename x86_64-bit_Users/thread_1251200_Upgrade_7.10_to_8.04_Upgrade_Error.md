---
title: "Upgrade 7.10 to 8.04 Upgrade Error"
date: 2009-08-27
forum: x86 64-bit Users
---

### Post by thespleen on 2009-08-27
Hi
 
I have a problem upgrading from 7.10 to 8.04 64 bit server edition.
 
The upgrade (and any updates) fail with the following error.
 
acpid : can't open /proc/acpi/event. Device or resource busy.
 
I have come across other posts that suggest stopping acpid, killing hald and then updating but when I use the command 'killall hald' I get a message saying that there is 'hald : no process killed' and the upgrade still fails with the same error.
 
I have copied an example of the output below.
 
Can anybody help with this problem.
 
Thanks.
 
sudo apt-get install ubuntu-artwork
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-artwork is already the newest version.
The following packages were automatically installed and are no longer required:
tomboy ekiga gedit-common gcalctool libkpathsea4 gnome-volume-manager
gucharmap gnome-games rhythmbox gedit seahorse guile-1.6-libs whois
libgmime2.2-cil libsdl1.2debian-alsa gnome-cards-data libguile-ltdl-1
gnome-nettool gconf-editor finger libsdl1.2debian gnome-system-tools eog
bug-buddy sound-juicer vino evince ghostscript-x libopal-2.2
libgnomevfs2-bin gtk2-engines-pixbuf gnome-screensaver zip gnome-games-data
libmusicbrainz4c2a fast-user-switch-applet totem gnome-themes file-roller
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 77 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu9.3) ...
* Loading ACPI modules... [ OK ]
* Starting ACPI services... acpid: can't open /proc/acpi/event: Device or resource busy
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Yellow Pasque on 2009-08-27
Instead of killing it, try stopping hal with:
```
sudo /etc/init.d/hal stop
```

..or just remove acpid. IIRC, only laptops still use it (HAL deprecates it).

---

### Post by thespleen on 2009-08-27
I removed acpid and everything is fine now.
 
Thanks very much.

---

