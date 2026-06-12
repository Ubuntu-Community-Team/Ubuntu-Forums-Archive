---
title: "X server automatically disabled?"
date: 2005-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Compwiz on 2005-01-22
install went smooth, however, when the boot screen comes up and says
```
**starting gnome desktop
```
screen flashes, then a blue screen that says:
> "I have disabled the Xserver: restart GDM when it is configured correctly" appears and shows some error information about Xfree86, then returns to
```
debian login:
```
is this a bug in Xfree86 or is my resolution just not set correctly?

thanks in advance
-compwiz

---

### Post by valadil on 2005-01-22
That's what happens to me when I install ubuntu for amd64.  Login as normal (if it hasn't given you a chance to create users yet log in as root with a blank pw) and apt-get yourself some xorg (or xfree86 if you're in warty).  I strongly dislike the installer for amd64 because it seems so inconsistent.  On the other hand it's never been any worse than debian, so you won't see me bitching about how unusable it is...

---

### Post by Compwiz on 2005-01-22
ok, so apt get installs from the internet, or the CD? i will try using apt-get,... thanks for the support- like to see im not the only one  8-[ wow, i dont kno hoe to use apt-get! damn!

---

### Post by s_p_a_r_k_y on 2005-01-22
to use apt...

apt-cache search packagename will list packages which are dependant on it or similar to the package you are looking for

apt-cache search xfree86 will list several x packages. try using it with
 apt-cache search package | less 
so you can actually see all of the packages.

To install, then
apt-get install package1 package2... as many as you want

Apt will then fix all the dependancies for you.

In regards to X not working check the log file in /var/log/XFree86.0.log, go all the way to the bottom usually to see what the error was. If it was No screens Found then there is a problem with your resolution or screen section of the X config.

---

### Post by Compwiz on 2005-01-22
alright, so i do not have to be in the graphic user interface to do this, right, cuz thats whats not working 

"error: xfree86 not configured "... this is my biggest problem ... how am i supposed to configure it when it wont work?

---

### Post by Dylanby on 2005-01-22
From the command line:```
sudo dpkg-reconfigure xserver-xfree86
```

---

### Post by Compwiz on 2005-01-22
```
error: xserver-xfree86 is broken or not fully installed
```
i am sorry for th inconvenience ...  but i really want the GUI.

---

### Post by Dylanby on 2005-01-24
Did you sort it out?
What happens if you type:
```
sudo apt-get update
sudo apt-get install xserver-xfree86
``` 

I'm assuming you're trying to install Warty.
Hoary doesn't use XFree86.

---

### Post by Compwiz on 2005-01-24
yah, its warty ... its jut that it keeps saying that it is broken ... that probly not a good thing right? ne way, ill try those commands,then if that doesnt workill just wait for my other copies, maybe. (i orderd it)

if i type ```
sudo apt-get install xserver-xfree
``` it comes up with the error message in my previous post ... i havent tried the```
sudo apt-get update
``` yet ...  but i have a feeling its a bug with the CD.  :-(

---

### Post by valadil on 2005-01-24
Edit your /etc/apt/sources.list file to get rid of the cd.  It should look something like this:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security universe

Unless of course if you've added some of your own repositories.  Then run sudo apt-get update.  This will tell ubuntu that it should get packages from the sources listed above rather than from the cd you don't trust.  After that try running sudo apt-get upgrade.  This will have ubuntu look at what packages are on your system and download any newer versions that may have come out since then.  

Then try going through this thread again and installing the suggested packages.

---

### Post by Compwiz on 2005-01-24
[QUOTE=valadil]Edit your /etc/apt/sources.list file to get rid of the cd.  It should look something like this:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security universe

Unless of course if you've added some of your own repositories.  Then run sudo apt-get update.  This will tell ubuntu that it should get packages from the sources listed above rather than from the cd you don't trust.  After that try running sudo apt-get upgrade.  This will have ubuntu look at what packages are on your system and download any newer versions that may have come out since then.  

Then try going through this thread again and installing the suggested packages.[/QUOTE]
 i am not connected to the internet on that machine yet

---

### Post by quackking on 2005-01-24
I've got the same problem on a Shuttle barebones SK83G system with 512MB of 400Mhz DDR RAM and a 200MB Seagate SATA drive, with the AMD-64 3000+ CPU. This system has a VIA chipset for video and for LAN. I get the system to come up in text mode, and I am connected to the internet (I did a network install using the Ubuntu Warty mini-iso from the 'current' branch.)

The installer automatically selects the vesa xfree86 driver, but it does not start the x server. I have done apt-get update and also apt-get install xserver-xfree86 - apt-get tells me:

$ sudo apt-get install xserver-xfree86
Reading Package Lists... Done
Building Dependency Tree... Done
xserver-xfree86 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
 
The error log in /var/log/XFree86.0.log contains this output:

<begin log output>
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 720x400@88Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@87Hz (interlaced)
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 110.0 MHz   Image Size:  300 x 225 mm
(II) VESA(0): h_active: 1280  h_sync: 1320  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) VESA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1060 v_border: 0
(II) VESA(0): Searching for matching VESA mode(s):

(II) VESA(0): Total Memory: 512 64KB banks (32768kB)
(EE) VESA(0): No matching modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "ddc"
(II) UnloadModule: "int10"
(II) UnloadModule: "vbe"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

<end of log output>

What am I doing wrong? Or what should I do to fix this? Thanks in advance.

---

### Post by Dylanby on 2005-01-24
So with your cd in your drive type:
```
sudo apt-get update
sudo apt-get install aptitude
```

"aptitude" is a frontend for apt which may help you resolve some broken packages.
Perhaps you have some packages which aren't completely installed properly?

So now type:```
sudo aptitude
``` 

Arrow down to installed packages & hit enter.
Type "/" & type "xserver".

Do you see "xserver-common" & "xserver-xfree86"?

You can type "?" in aptitude for the help screen.

---

### Post by quackking on 2005-01-24
Yes, I have both xserver-common and xserver-xfree86 (version 4.3.0-dfsg) installed (that is,  there is a letter "i" next to them)

One more thing: I have installed webmin and now can read my email (sorry, newbie, not so familiar with debian and command-line utilities..) At config time, root sent this email to root:

Subject 	Debconf: Configuring xserver-xfree86 -- No X server known for your video hardware.

Either you have no video hardware installed on this machine (serial
console only?), or the "discover" program was unable to determine which X
server is appropriate for your video hardware.	This could be due to
incomplete information in discover's hardware database, or it could be
that your video hardware is simply not supported by any available X
servers.
-- 
Debconf, running at localhost.localdomain
[ Debconf was not configured to display this note, so it mailed it to you. ]
-- 

Obviously something is not working here. What did I do that was wrong? For what it is worth, I can run the stock Knoppix 3.7 download (a 32 bit distro) on this machine in vesa-based Xfree sessions with no problem.

---

