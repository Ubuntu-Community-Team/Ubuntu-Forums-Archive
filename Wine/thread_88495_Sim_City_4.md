---
title: "Sim City 4"
date: 2005-11-10
forum: Wine
---

### Post by Nu-Buntu on 2005-11-10
Hi all,

I have Sim City 4 Deluxe for Windows (one of the reasons I still dual boot). Anyway, I tried to install on Breezy using WINE. Disk 1 works fine, then it asks for Disk 2. The problem is, Disk 1 will not eject so I can put Disk 2 in the drive. The only way to open it is to abort the install. I have also tried copying both disks to a common directory, but that didn't work either.

Has anyone found a way to successfully install this game under WINE in Breezy?

Thanks!

---

### Post by janz84 on 2005-11-10
try copying both cds to the hd (in the same dir) and then installing

---

### Post by Nu-Buntu on 2005-11-10
[QUOTE=janz84]try copying both cds to the hd (in the same dir) and then installing[/QUOTE]
I tried this, and it didn't work either. Curious, eh?

---

### Post by souled on 2005-11-10
Have you tried unmounting the cd via command line? sudo umount /media/cdrom0

---

### Post by Nu-Buntu on 2005-11-10
[QUOTE=souled]Have you tried unmounting the cd via command line? sudo umount /media/cdrom0[/QUOTE]
Yep

---

### Post by SickTwist on 2005-11-10
There is a built-in command in wine to simulate Windows ejecting a CD. Sorry, I don't remember the exact syntax but it is somthing like:

wine eject

Perhaps that is what you need?

PS I'm a huge SimCity fan myself but have not tried running it in Wine. (I dual boot with W2K for SC4 & Roller Coaster Tycoon.) Maybe I should also try to install SimCity with Wine. (I have SimCity4 + Rush Hour add-on). Please keep us posted on how your adventure goes. Also, I'm curious: What version of Wine are you running and did you install anything special (DirectX, native DLLs, DCOM98, IE, fonts, etc.) before you tried SimCity?

---

### Post by janz84 on 2005-11-10
[quote=Nu-Buntu]I tried this, and it didn't work either. Curious, eh?[/quote]

Hmmm, that must mean that the installer expects the files to on 2 seperate cds as opposed to asking only when the nessary files are missing...

sorry my advise didnt turn any results

---

### Post by testcees on 2006-01-12
Apply a no-CD crack and copy the C:\Program Files\Maxis\ to .wine/drive_c/Program Files. Start Simcity:

wine .wine/drive_c/Program\ Files/Maxis/SimCity\ 4\ Deluxe/Apps/SimCity\ 4.exe -- -opengl

With winecfg I set the version to windows98, and I use the ALSA driver for sound (emulation).

---

### Post by akurashy on 2006-01-12
also this is supported by cedega but I don't know if it for wine

---

### Post by alpopel on 2006-01-15
what about "eject" in bash?? that will eject the cd. 

alpopel

---

### Post by akurashy on 2006-01-15
i installed simcity4 using cedega and it works perfectly... i have to try using wine

---

### Post by vargas.lucas on 2006-09-25
how to configure cedega to run sim city 4??

hey -> sorry for my english ;]

---

### Post by U5tabil on 2007-03-12
Im having some big problems instaling this game even with cedega. the problem is when it comes to asking for the CD2....

Anyone having a step by step how to install this game?

---

### Post by darksidedude on 2007-07-02
what I noticed was that when it asks for cd 2, wait about a minute and the cd should auto eject, then just pop in the second, haven't found out how to get it to run, it freezes at the splash screen =(

---

### Post by darksidedude on 2007-07-02
For those who use cedega I have figured out the fix to this issue, 

1. after the install right click on the shortcut in cedega (this was done in 6.0.2) and go to "edit property's"

2. at the bottom there is a box that says  edit settings" open it up

3. go to scheduler and select "NO" 

4. two check boxes should light up un select "accelerated interprocess communication"

5. click apply and enjoy:popcorn:

---

### Post by RockTonic3 on 2007-12-03
Hello!

I've tried waiting for the cd tray to open, and also tried copying the folders to the hard drive.  I've read elsewhere that if you copy the cd's as two folders, you can switch the name of the second folder to the original name of the first folder.  This is supposed to trick the installer into thinking the disc was changed, but it doesn't work for me.  I change the folder names and push 'OK' in the switch cd prompt, but nothing happens.  

The same thing happens if i push a paper clip into my cd drive to switch the cd's without having to push the button...  

Am I doing something wrong?

---

### Post by Catalyst2Death on 2007-12-14
if your installing from a cd, you have to use "wine eject D:\"  I think, I'm not sure, but I know you have issue the eject command from wine... ubuntu won't respond to umount, it will return device busy errors...

---

### Post by lucasbarton on 2007-12-28
I am certainly new, but with some reading I've found a solution, at least for me, to this problem. If you copy the first disc to a folder, then place the second in the drive, and use wine to run setup.exe, you can just select OK when the dialog box comes up. No ejecting.

Anyway, I've got an in-game issue. I can't seem to load jpg custom terrains. I can get to the open screen using Ctrl+Alt+Shift+R, but double clicking on the jpg or selecting OK doesn't seem to work. Any suggestions there?

Lucas

---

