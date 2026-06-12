---
title: "Need help, sound drivers doesn't work?"
date: 2008-06-20
forum: x86 64-bit Users
---

### Post by Prohib on 2008-06-20
I have MSI k9n Neo V3 motherboard, and my sound drivers don't work? I can't open any mp3 file and any video file!

Please help!

---

### Post by Sef on 2008-06-20
Read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by Pjotr123 on 2008-06-20
Apply this simple how-to:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

Easy, simple and fast. For 100 % multimedia support.  :-)

---

### Post by nikgare on 2008-06-21
Can you play the sound and video files in the "Examples" folder?

---

### Post by Prohib on 2008-06-21
I follow instructions from
> Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)


at Step 2, item 5, and I enter this (sudo apt-get update) and press enter. 
This is what is written.
```
nemanja@ubuntu:~$ gksudo gedit /etc/apt/sources.list
nemanja@ubuntu:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
OK
nemanja@ubuntu:~$ sudo apt-get update
Hit http://rs.archive.ubuntu.com hardy Release.gpg
Ign http://rs.archive.ubuntu.com hardy/main Translation-en_US
Ign http://rs.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://rs.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://rs.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://rs.archive.ubuntu.com hardy-updates Release.gpg
Ign http://rs.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://rs.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://rs.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://rs.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Get:1 http://packages.medibuntu.org hardy Release.gpg [189B]
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Hit http://rs.archive.ubuntu.com hardy Release 
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US  
Hit http://rs.archive.ubuntu.com hardy-updates Release
Get:2 http://packages.medibuntu.org hardy Release [5590B]           
Hit http://rs.archive.ubuntu.com hardy/main Packages
Hit http://rs.archive.ubuntu.com hardy/restricted Packages
Hit http://rs.archive.ubuntu.com hardy/main Sources 
Hit http://rs.archive.ubuntu.com hardy/restricted Sources
Hit http://rs.archive.ubuntu.com hardy/universe Packages
Hit http://rs.archive.ubuntu.com hardy/universe Sources
Hit http://rs.archive.ubuntu.com hardy/multiverse Packages
Hit http://rs.archive.ubuntu.com hardy/multiverse Sources
Hit http://rs.archive.ubuntu.com hardy-updates/main Packages
Hit http://rs.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://rs.archive.ubuntu.com hardy-updates/main Sources
Hit http://rs.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://rs.archive.ubuntu.com hardy-updates/universe Packages
Hit http://rs.archive.ubuntu.com hardy-updates/universe Sources
Hit http://rs.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://rs.archive.ubuntu.com hardy-updates/multiverse Sources
Get:3 http://packages.medibuntu.org hardy/free Packages [5721B]
Get:4 http://packages.medibuntu.org hardy/non-free Packages [7726B]
Fetched 19.2kB in 1s (16.9kB/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
nemanja@ubuntu:~$ 

```

Then I go to item 6, and when I have searched in Synaptic Package Manager for libdvdcss2 and for w64codecs and I found nothing.

What to do?
Big thanks for help, I'm new in Linux world so I'm not handling well.

---

### Post by Nepherte on 2008-06-21
> **Prohib said:**
> 
```

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
nemanja@ubuntu:~$ 

```
Then I go to item 6, and when I have searched in Synaptic Package Manager for libdvdcss2 and for w64codecs and I found nothing.

Be sure you have only one installation application open, in casu your terminal. Close instances of Synaptic if you have them. Otherwise I'd just wait a sec and try again until the lock has been released. One way to force the lock release is to restart your computer. The fact that it can't find libdvdcss2 and w64codecs is because the update command you entered before didn't work (the lock remember). That means the medibuntu repository you added, is not in the list yet. You need to have this repository for the programs to install.

---

### Post by Prohib on 2008-06-21
I have done all that, everything paste fine, but sound still doesn't work?

I use w64codecs, libdvdcss2 and install them, then apply, then do the rest, still nothing?

Need help!

---

### Post by bijeeshvs on 2008-06-21
do you have the onboard audio enabled in bios????????????//
can you play any sample videos or music??????????????????
do you have "restricted extras" installed in "system=> administration=> synaptic package manager " ????????????????????????????????????
can you see and change the volume on the panel???????????????
is you " PCM" in the mixer device muted????????????????
double click on the panel's volume icon to get mixer!!!!!!!!!!!!
check all these!!!!!!!!!!!!!!!!!!!


and reply

---

### Post by Prohib on 2008-06-21
1. HD audio controls are Enabled in bios. 
2. No
3. I didn't have restricted extras installed, but now it's installed.
4. No
5. No
6. When I click on Volume control, it's written this:[http://i30.tinypic.com/ei096s.gif](http://i30.tinypic.com/ei096s.gif)



What next?

---

### Post by Nepherte on 2008-06-21
This should get you started figuring out the problem in dept: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

