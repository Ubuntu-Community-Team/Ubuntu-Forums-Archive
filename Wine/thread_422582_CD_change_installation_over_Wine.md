---
title: "CD change installation over Wine"
date: 2007-04-25
forum: Wine
---

### Post by roadster.eleven on 2007-04-25
Hello everyone,

I'm trying to install Tiger Woods PGA Tour 2006 over Wine on my Ubuntu but some issues came to surface!
The installation procedure requires 3 CD's that I have to change during the process and I'm experience some problems with this CD change because Wine doesn't permit to open the case and don't recognize the second one.

The Crossover Office have a menu that permits the CD ejection instead of unmount, so my question is: When the installation over Wine requires more than 1 CD, how can I change it?  

Thanks in advance.

---

### Post by strixy on 2007-04-25
I don't know if this will work, but have you considered ripping the 3 CD's to ISO's and mounting them? In theory, that should do the trick.

---

### Post by cogadh on 2007-04-25
Instead of changing directories to the CD and "wine"ing the setup,  run the installation like this:
```
wine /media/cdrom0/setup.exe
```
Sometimes, the CD swap is prevented because the terminal is in the CD directory already. Running the install this way will usually allow you to eject and swap CDs normally. If it doesn't, then try:
```
sudo umount -f /media/crdom0
```
If it works, you should be able to eject and swap CDs normally. If it doesn't, try this:
```
sudo umount -l /media/cdrom0
```
You will probably have to manually remount the new CD after swapping and it doesn't always allow the install to continue. If none of these work, then strixy's suggestion is probably the only way to do it.

---

### Post by Naegling23 on 2007-04-25
open another terminal and enter wine eject
that will open your drive without exiting your wine install.  Pop the next disk in, let it mount, then continue.

---

### Post by Naegling23 on 2007-04-25
Another option is to copy the cd's to folders stored on your computer.  Think WoW then subfolders labeled disk1, disk2, disk3 etc.

run the setup program from the first folder, then, when it asks you for the next disk, point it to the disk2 folder and continue.  When the install is finished, just delete all the disk info from your drive to free up space.

Note: both of my posts work fine, I installed WoW using wine eject, and Jedi Academy using the disk copy method.

---

### Post by roadster.eleven on 2007-04-25
Thank you all for the quick replies! I tried the cogadh solutions but it doesn't worked! The **wine /media/cdrom0/setup.exe** produces an error message because of the non existence of some files in the home directory. The other solutions have problems too, I can unmount the drive and eject the CD but the installer of the game doesn't recognize the second CD.

About the Naegling23 solutions, I have one question: How can I point the Wine to the disk2 folder in the middle of the installation? I open another window and point Wine to the folder? I tried this but the installer doesn't proceed.

Thanks.

---

### Post by tk471 on 2008-09-14
Hello, I just had to do this for a four CD game (Blade Runner), pretty much as described above.  After inserting your first CD, and running from terminal
```

wine /media/cdrom0/setup.exe
```

After (in my case) choosing a full install, everytime the installer wanted the next CD, I had opened a second terminal window, to do this:

```
sudo umount -f /media/cdrom0
eject /media/cdrom0
sudo mount -t iso9660 /dev/cdrom1 /media/cdrom0
```

and then go back to the installer, continuing for each CD.  Your device may vary, in my case the actual CD-ROM device is at '/dev/cdrom1'.

---

### Post by Todamont on 2010-08-19
I tried the above methods with "Tiger Woods PGA 2006". None worked. 
wine /media/cdrom0/Autorun.exe

returned error: could not find /home/(username)/AutorunGUI.dll

running from the cd directory worked, and I was able to get the "media" disk mounted, which showed some .mp3 files, but not the "courses" disk, which presumably was "disk 2". 

sudo mount -t iso9660 /media/cdrom1 /media/cdrom0

returned error: mount special drive /media/cdrom1 does not exist

sudo mount -t iso9660 /media/scd0 /media/cdrom0

gave me a warning about being read-only, and appeared to mount the disk, but no files showed up in browser and "insert disk 2" message did not clear. 

Any gurus out there want to tackle this problem? My friend bought this game, but just can't make it run on the new Ubuntu OS I set him up with...

---

### Post by pyrael on 2011-09-11
I just had to do this with a 2CD game. Sometimes, if you look in media, you'll see that instead of mounting the disk to cdrom or cdrom0 or whatever, it will mount as the LABEL_NAME. What I did was this...

(I was installing Vietcong)

cd /media
wine ./VIETCONG_CD1/setup.exe

(at disk change) 

 wine eject <--- no new tab needed because the new wine goes back to the prompt allowing more commands

(after swapping)

sudo ln -sf VIETCONG_CD2 VIETCONG_CD1

then click okay on the GUI

---

