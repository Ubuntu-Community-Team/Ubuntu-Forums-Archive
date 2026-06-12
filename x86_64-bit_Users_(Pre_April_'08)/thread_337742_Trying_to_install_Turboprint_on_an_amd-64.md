---
title: "Trying to install Turboprint on an amd-64"
date: 2007-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by ve6ani on 2007-01-13
I downloaded Turboprint-1.95-1_i386.deb and tried to install it using linux32.
Here's what happened:
walter@ubuntu:~/Desktop$ sudo linux32 dpkg -i turboprint_1.95-1_i386.deb
dpkg: error processing turboprint_1.95-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 turboprint_1.95-1_i386.deb
I have the 32 bit libraries installed. I'm running Dapper Drake
Does anyone know of an amd64 build for Turboprint,? or any other suggestion,
?
Walter

---

### Post by kleeman on 2007-01-13
You need the 64bit version. There are no debs for 1.9.5 I notice. My suggestion: Download the 1.9.4 version for 64bit and manually install following the instructions. I did this and it was very simple.

---

### Post by John Jason Jordan on 2007-01-13
> **kleeman said:**
> You need the 64bit version. There are no debs for 1.9.5 I notice. My suggestion: Download the 1.9.4 version for 64bit and manually install following the instructions. I did this and it was very simple.
I've been looking for a way to access all the features of my printers (Laserjet 8000DN) from Linux, so I installed Turboprint per your instructions. 

Installation went fine, but what does it do? When I select a Turboprint "printer" the print options are not even all the ones that are available if I print to the regular driver installed via CUPS. What's the point of Turboprint?

And since it doesn't seem to do anything, how do I uninstall it?

---

### Post by kleeman on 2007-01-13
> **John Jason Jordan said:**
> I've been looking for a way to access all the features of my printers (Laserjet 8000DN) from Linux, so I installed Turboprint per your instructions. 

Installation went fine, but what does it do? When I select a Turboprint "printer" the print options are not even all the ones that are available if I print to the regular driver installed via CUPS. What's the point of Turboprint?

And since it doesn't seem to do anything, how do I uninstall it?

You should get an icon on your desktop called Turboprint-Config. This enables you to configure options for the printer. For my two printers (HP laserjet 1200 and Photosmart 7660) it gives better resolution and for the Photosmart the photo prints are outstanding as it has special photopaper options...

---

### Post by John Jason Jordan on 2007-01-13
> **kleeman said:**
> You should get an icon on your desktop called Turboprint-Config. This enables you to configure options for the printer. For my two printers (HP laserjet 1200 and Photosmart 7660) it gives better resolution and for the Photosmart the photo prints are outstanding as it has special photopaper options...
Didn't get any icons. No menu entries either.

From reading about it my printer is supported, but from looking at the list of other printers it appears it is designed to enhance output on color printers. My printer is a high-speed black and white laser and I don't have any problem with the print quality. What I have a problem with is getting print dialog boxes in applications to offer all the features of the printer (duplex, output stacker, input trays 1-4, and so on.) Xtpsetup doesn't give me any options at all.

I also read the online manual and man turboprint, but not a word about how to uninstall it. It's not listed in Add/Remove Programs or in Synaptic. Any ideas how to uninstall it? Thanks.

---

### Post by kleeman on 2007-01-13
You can access the config by typing
xtpconfig

at a terminal prompt.

To uninstall go into the installation subdirectory and type

./uninstall

---

### Post by ve6ani on 2007-01-14
I had downloaded  turboprint-1.94-4.x86_64.tgz before Christmas and had no luck installing it (failed dependencies). Tried to find and install the library files it was looking for. Spent a few days trying and then put it aside.
I installed Mandriva 2007 on one my old computers a couple of days ago  and installed Turboprint on it. Turboprint installed smoothly.
I downloaded and tried the .deb file on my Ubuntu box and it didn't fly..
On a hunch, I deleted all traces of Turboprint on my Ubuntu box and downloaded 1.94-4.x86_64.tgz again.  This time Turboprint installed ok.
Who knows? Maybe I downloaded a corrupted file last time, or the file got corrupted in downloading.
A month ago I ran into all kinds of problems with Turboprint. This time it works.
Now I'll try to share one printer between 2 computers, I hope.

Walter

---

### Post by John Jason Jordan on 2007-01-14
> **kleeman said:**
> To uninstall go into the installation subdirectory and type
./uninstall
Thanks.

It said it would delete a bunch of stuff. But all it deleted was the config file. Nevertheless it is gone now. I just searched for TurboPrint and manually deleted everything. And even then the printers it installed in CUPS were still there.

---

