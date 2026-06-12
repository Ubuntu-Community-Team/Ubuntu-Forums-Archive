---
title: "Baldur's Gate 2"
date: 2008-08-11
forum: Wine
---

### Post by ykcirt on 2008-08-11
I have a small problem.. and surprisingly enough also the solution to it.

The installer won't progress beyond 95%, where it asks for a CD but doesn't recognize it. I'm sure some of you have heard of it. I had the same problem on my windows 98 machine. Anyway, the solution in an MSDOS environment would be this:

> Installer stuck at 95% and asking for CD1 (Back to Known Issues list)

    If you are installing BG2 and the installer gets stuck when it reaches 95% complete and begins to ask for CD1, but never recognizes it, we have a possible solution for you. Please note: It is normal for the installer to ask for CD1 at 95%; the problem is when the installer doesn't recognize CD1 in the drive. The problem seems to be occurring because of an arbitrary assignment of the phrase "CD1" to the CD ROM drive, conflicting with a file name that is on CD1 called CD1.ifo. This problem only affects a small number of people who happen to have a device name for their CDROM's called CD1.

    1) Open your config.sys file (usually found on C:\) in notepad and look for a line that looks similar to, but not necessarily exactly like, "devicehigh=C:\cdrom\taisatap.sys /d:cd1". The key portion of the command to look for are the "devicehigh" and the "cd1". This is a command that will load a CDROM driver called CD1 into high memory. This may be present if you play DOS games that require CDs or have upgraded from DOS to Win95 to Win98. If you do have such a line, change the "CD1" portion of the line to "CDROM01" (note this device label is arbitrary - it's what your CDROM drive name was initially installed as. CD1.ifo is a file on the BG2 CD#1 and the overlap of the names appears to cause problems reading the CD1.ifo file). If you have any other lines similar that load drivers for a second CD (i.e. CD2) you will need to change them as well.

    2) Open your autoexec.bat file (usually found on C:\) in notepad and look for a line that looks similar to but not necessarily exactly like "c:\windows\command\mscdex.exe /d:cd1". Modify the "cd1" portion of this line to "CDROM01". It's important that the exact same name change is made in both config.sys and autoexec.bat (to "CDROM01") for this to work. (note your CDROM will work exactly as before after making these 2 changes but the device name will now be changed to CDROM01 in memory - this won't affect anything that you should be able to detect).

    3) Reboot your machine after making both changes above. Then try the install again and see if that fixes the problem. 

Can someone show me how to fix this in Ubuntu?

---

### Post by Djunky11 on 2008-08-21
I had the same problem until I did a little playing with it. Copy all of your discs data to 1 location on your hard drive, once they're all there run the setup.exe.  It should pause at 95% and ask for CD1 again, except this time it should recognize the CD 1 when you put it in your CD-Rom drive.

Hope that helps :)

---

### Post by edmicman on 2008-09-11
I'm getting this same error, but I've got all of the files copied to the hard drive.  I'm not putting anything in the CD drive; it's all local and it's still giving me this exact error.  How else can you fix it?  Is all the data supposed to be copied into the same directory?  My structure is like this:

Main CD data and setup.exe in bg2/
CD2 is in bg2/CD2/
CD3 is in bg2/CD3, etc for CD4.

Do I need to copy the data from CD2, 3, etc. into the main install directory?

---

### Post by Caedis on 2008-09-12
> **edmicman said:**
> Do I need to copy the data from CD2, 3, etc. into the main install directory?

I have and use BG2 on Herty, and yes, I think that's what I had to do. It will work you just gotta fight with it. Also, I think i had my first install disk in the drive at some point in time.

---

### Post by MaT0 on 2011-01-12
Hey guys,

I know I'm a bit late, but I have been able to install and play the game. I am using the DVD version and I was also asked to insert CD 1 at 95%. This is what I've done:

[LIST=1]
[*] put the game in a single folder or mount the dvd iso (in my case)
[*] run setup.exe
[*] the game stops at 95% and asks for CD 1
[*] make sure you have the CD1 or DVD mounted (my case - /media/virtualDVD)
[*] go to wine configuration (applications>wine>configure wine)
[*] in the drives tab, click to add a new drive (X: for example)
[*] in the path field, type in the path, where you have the CD1 or DVD mounted (in my case /media/virtualDVD)
[*] next, click the show advanced button and in the type field select "CD-ROM"
[*] submit and close wine config
[*] return to the installation of BG2, and browse for the CD. Select the newly created X: drive and submit
[*] now the game will continue to install
[/LIST]
It seems, that the the installation has problems recognizing the CD when it is mounted to a folder. Wine has, thankfully, ways to work around this (as was described above) :) .

Hope this helps.

P.S.: This was done on Ubuntu 10.10 (Maverick Meerkat) using wine 1.2.1 with Gmount-iso for mounting the DVD.

---

### Post by Cardale on 2011-12-27
This is also late, but just thought I would let everyone know that GemRB exists and runs native on linux.

You can play all the original BG awesomeness.  I don't believe the online component is created, but if your a developer feel free :D

---

