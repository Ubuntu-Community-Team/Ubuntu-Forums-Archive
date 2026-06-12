---
title: "Xserver is not installed?!?"
date: 2007-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by vincister on 2007-02-04
I had to reinstall ubuntu, first time(almost year ago) I installed it, there was that problem with xserver - graphic interface was kinda messed up, but there was solution: to reconfigure xserver to think that it has VESA video (instead of nvidia) and it worked...
But now - here is my problem: when I type
```
sudo dpkg-reconfigure xserver-xorg
```
I got an error that xserver-xorg is not installed !!! (why is this? last time this reconfigure worked :confused: )

---

### Post by amohanty on 2007-02-04
Did you install the server version??

Try:
> sudo apt-get install ubuntu-desktop

If that is already installed try:

> sudo apt-get install xserver-xorg

If thats installed too reinstall xserver-xorg.

HTH
AM

---

### Post by vincister on 2007-02-04
I installed with default settings (i think that desktop, cause I did exactly the same like first time and that was with graphical interface)

I'll try to install / reintsall that xserver

---

### Post by Kilz on 2007-02-04
> **vincister said:**
> I installed with default settings (i think that desktop, cause I did exactly the same like first time and that was with graphical interface)

I'll try to install / reintsall that xserver

The question is, did you download the server install disk and install that. The server install disk does not install a desktop/xserver. Servers dont need them most of the time.

---

### Post by vincister on 2007-02-04
hmm when i type```
sudo apt-get install xserver-xorg
```
first time I see that it installs the xserver, but there is an error, then I type the same second time I get this:
```
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
    xserver-xorg
1 upgraded, 0 newly installed, 0 to remove and 202 not upgraded.
Need to get 0B/274kB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
dpkg: parse error, in file '/var/lib/dpkg/available' near line 2 package 'aspell
-en':
value for 'status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an eror code (2) 
```

about the installation: I have CDs from ship-it (v 5.10 for 64-bit) and last time I installed it, everything was alright, though now somethings weird

---

### Post by kuja on 2007-02-04
You also need to install the "xorg" package.

---

### Post by amohanty on 2007-02-04
Can you post the output of:

sudo apt-get check


AM

---

### Post by vincister on 2007-02-06
heh, never mind!

I decided to re-install ubuntu completely, This time 6.06 64-bit, and solved all the xserver problems like I did year ago :D

---

