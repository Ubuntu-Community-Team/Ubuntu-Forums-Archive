---
title: "linux32 needs to remove essential pacakges?"
date: 2008-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by or1on on 2008-01-17
im trying to install linux32 and its telling me it needs to remove essential packages such as ubuntu-minimal  util-linux  and util-linux-locales what gives?

---

### Post by Cappy on 2008-01-17
linux32 comes with gutsy. You already have it.

---

### Post by or1on on 2008-01-17
odd its not wrking, and apt tells me when i tried to install it that 1 new program will be installed and 3 essential ones will be removed if its already installed dosent it say upgrade instead of install?i found this page its what im running into
[https://bugs.launchpad.net/ubuntu/+source/linux32/+bug/141607](https://bugs.launchpad.net/ubuntu/+source/linux32/+bug/141607)......hmm i should read more :P it seems the problem lies in that linux32 is built into the util-linux program..but how then am i to issue the cmd im trying to install q3a and its not working like this sudo linux32 sh linuxq3apoint-1.32b.x86.run or like this sudo util-linux sh linuxq3apoint-1.32b.x86.run ?

---

### Post by Cappy on 2008-01-17
You already have it; don't install it.

If you need more help you need to post the error from running
```
sudo linux32 ./linuxq3apoint-1.32b.x86.run
```

Make sure you are in the directory of the file and that the file is named linuxq3apoint-1.32b.x86.run

---

### Post by or1on on 2008-01-18
this is the error code
sudo linux32 ./linuxq3apoint-1.32b.x86.run
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
An embedded MD5 sum of the archive exists but no md5sum program was found in /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
If you have md5sum on your system, you should try :
env GUESS_MD5_PATH="FirstDirectory:SecondDirectory:..." ./linuxq3apoint-1.32b.x86.run -check
 All good.
Uncompressing Quake III Arena Point Release 1.32b tail: Warning: "+number" syntax is deprecated, please use "-n +number"
...................................................................................................................................................
./setup.sh: 20: source: not found
The setup program seems to have failed on x86/glibc-2.0

Fatal error, no tech support email configured in this setup
The program returned an error code (1)
ive tried with and without the linux32 same result

---

### Post by Cappy on 2008-01-18
I made a new guide for loki installers like this one recently: [http://ubuntuforums.org/showthread.php?t=667771](http://ubuntuforums.org/showthread.php?t=667771)

This should be the solution:
```

./linuxq3apoint-1.32b.x86.run --target new_loki_dir
cd new_loki_dir
mv setup.sh setupold.sh
sed 's/`DetectLIBC`/"glibc-2.1"/' setupold.sh | sed 's/`DetectARCH`/"x86"/' > setup.sh
chmod +x setup.sh
./setup.sh

```

---

### Post by or1on on 2008-01-18
well the install part went great..then when i type quake 3 in the terminal i get this
and i did run the last part as sudo ./setup.sh

or1on@Darkside: quake3
Q3 1.32c linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/or1on/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Segmentation fault (core dumped)

thanx for your help

---

### Post by Cappy on 2008-01-18
The only thing I can suggest is installing the Nvidia restricted drivers if you haven't done so. The restricted driver is required.

---

### Post by chrisccoulson on 2008-01-18
This may seem like an obvious suggestion, but do you have the ia32-libs package installed?

---

### Post by or1on on 2008-01-18
> **chrisccoulson said:**
> This may seem like an obvious suggestion, but do you have the ia32-libs package installed?
ya i have that installed but thanx anyway :P
and cappy the restricted manager said there was no drivers for my hardware or something to that effect so i installed the driver from nvidias site, my card is an OC BFG 8800GT
thanx again for your help

---

### Post by Kilz on 2008-01-18
> **chrisccoulson said:**
> This may seem like an obvious suggestion, but do you have the ia32-libs package installed?

ia32-libs will not contain the proprietary libGL.so.1 from nvidia that the application requires.

---

### Post by chrisccoulson on 2008-01-18
> **Kilz said:**
> ia32-libs will not contain the proprietary libGL.so.1 from nvidia that the application requires.

Yes, my bad.

or1on: Is this still an issue with the NVIDIA driver installed?

---

### Post by or1on on 2008-01-18
ya chris ive had the nvidia driver installed b4 attempting any game installations, so far ut2k4 is the only one working and im sure its because it has 64 bit binaries. my pc dosent seem to want to run 32 bit games :/   ofcourse it may be the operator and not the machine :) bah i suck at q3a anyway :P

---

