---
title: "Unabe to open Morrowind / add Expansions."
date: 2012-02-01
forum: Wine
---

### Post by kriltos on 2012-02-01
Im having Trouble Installing Elder scrolls 3 Morrowind onto Playonlinix on Ubuntu 11.10

i have the disk for the first game then the two expansions in ISO files.
i can install morrowind with playonlinix no prob just doesnt do anything else with it after! inculding adding on the expansions. at a dead end with this. Also looked though previous threads on here, nothing seems to answer my problem.

---

### Post by kriltos on 2012-02-01
Update. I install Orginal CD and open the game (without expansions) i get an error message saying there is no CD in the cd-drive : /

---

### Post by kriltos on 2012-02-02
Error message i get.

  	 	 	 	 	 	   [pol_wine_setversionEnv] message: setting wine version
 path:1.3.2, x86
[POL_wine_setversionEnv] Message:
 “/home/ross/.playonlinux//wine/linux-x86/1.3.2” exists
 [pol_wine] message:Running wine-1.3.2
 wine: cannot find”
 [pol_wine] message: wine return 87
  

anyone?

---

### Post by kriltos on 2012-02-02
bump** still no reply let alone an answer:popcorn:

---

### Post by Toz on 2012-02-02
To get wine (POL 4.0) to recognize the CD Drive, this should work:
From the main POL window, click on the "Configure" button. In the dialog box that opens, select Morrowind on the left hand side, click on the "Wine" tab on the right side and click on the "Configure Wine" button. This will bring up the wine configuration window (properly linked to the Morrowind virtual drive). Click on the "Drives" tab and click the "Add..." button. Select the drive letter and then in the the "Path" text box, enter **/dev/cdrom** (for a cdrom) or **/dev/dvd** (for a dvd). Click "Ok". Try now and see if it helps.

---------------------------

As for the isos, you can either use a gui tool to mount them (see: [http://www.addictivetips.com/ubuntu-linux-tips/mount-virtual-disc-images-in-ubuntu-linux-with-furius-iso-mount/]("http://www.addictivetips.com/ubuntu-linux-tips/mount-virtual-disc-images-in-ubuntu-linux-with-furius-iso-mount/")) or manually:
```

sudo mount -t iso9660 -oloop <path/to/iso.iso> /mnt
```
...change <path/to/iso.iso> to be the real path and name of the iso.
This will uncompress the iso file into the /mnt directory.

Then, if the expansion packs need to be added to the existing Morrowind install, go back to the POL Configuration dialog and this time select the "Miscellaneous" tab, then click on the "Run an .exe file in this virtual drive" and then navigate to /mnt and select the name of the install file.

Once done installing, you can manually unmount the iso via:
```
sudo umount /mnt
```

---

### Post by kriltos on 2012-02-03
great instructions, easy to follow but it didnt solve the problem. went into wine config selected D for my disk drive and typed in /dev/cdrom, (didnt work) then tried /dev/dvd, again nothing. even tried E drive

Cant say ive tried the mounting yet, still trying to get the first part sorted. any other suggestions? still same error, no cd, please insert etc.

Also which wine version should i use?

1.3.4 / 1.3.2 / 1.3.0 / 1.2.3 / 1.1.14 ? default was 1.2.3.


Mounting error message:
Error mounting image.
OS error(16): Device or resource busy

wtf? its not busy REedit. Never mind, i was trying to mount it twice :) mounting works just the original problem still.

---

### Post by Toz on 2012-02-03
Insert the CD into the drive and have a look at the contents of the /media directory:
```
ls /media
```
You "should" get a directory showing up that is the contents of the Morrowind CD (lets assume its called "Morrowind").

Go back to the configuration where you specify the cd and instead of /dev/cdrom, try /media/Morrowind (or whatever the directory is called).

Wine version 1.2.3 should work fine, but I don't think the CD issue is related to the version of wine that you are using.

---

### Post by kriltos on 2012-02-03
Alright! we got the Disk drive working, /media/MORROWIND worked.

Now i get a program Error Message;

The program morrowind.exe has encountered a serious problem and needs to close blah blah,

This can be caused by a problem in the program or deficiency in Wine. you may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.. :?

From one to another. sounds like i might be missing some files for the start up CGI maybe?

---

### Post by Toz on 2012-02-03
Good news about the drive.

What messages do you get on the terminal if you run the game from the terminal?

According to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1331]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1331"), wine needs to be compiled with mp3 support (which i believe it is) and you need to have libmpg123 installed.

---

### Post by kriltos on 2012-02-03
i dont have libmpg123 installed. i'll download it now. where show i put it after ive done that? i'll open it in terminal now and check.

Edit:


writting log to /home/ross/.playonlinix//tmp/errors_the elder scrolls III - morrowind.log.e

[pol_wine_setversionenv] message: setting wine version path: 1.2.3, x86
[pol_wine_setversionEnv] message: "/home/ross/.playonlinx//wine/linux-x86/1.2.3" exists
[pol_wine] message: running wine-1.2.3 morrowind launcher.exe
wine: cannot find L"c:\\windows\\system32\\winemenubuilder.exe -a -r" (2)

---

### Post by Toz on 2012-02-03
To install libmpg123:
```
sudo apt-get install libmpg123-0
```

Are you using the 64-bit version of ubuntu?
```
uname -m
```

---

### Post by kriltos on 2012-02-03
no. im using Ubuntu 11.10 32bit

Reading package lists... done
building dependency tree
reading state information ...done
libmpg123-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

---

### Post by kriltos on 2012-02-03
AH!!!! done it. tried opening the game again and changed the screen settings put it down to 800X600. seemed to work.

Tried to install Tribunal with POL and directed it to where the image was mounted
/home/ross/TRIBUNAL_ISO but it doesnt recognize that.

Tried to open the setup.exe with wine but it says morrowind is not installed. 
I'm assuming this problem will be the same for Bloodmoon.

Cheers for your continued help. you've put be leeps and bounds in front of where i was! at least i can play the game without expansions.

---

### Post by Toz on 2012-02-03
> **kriltos said:**
> Tried to install Tribunal with POL and directed it to where the image was mounted
/home/ross/TRIBUNAL_ISO but it doesnt recognize that.
Did you specify/select the setup.exe file?

> Tried to open the setup.exe with wine but it says morrowind is not installed. 
Probably because POL is using a custom prefix. What does:
```
ls ~/.PlayOnLinux/wineprefix
```
...return? There might be a directory in there called **TES3_Morrowind** (or something like that). In which case, try:
```
WINEPREFIX=~/.PlayOnLinux/wineprefix/TES3_Morrowind wine /home/ross/TRIBUNAL_ISO/setup.exe
```

If that doesn't work, download the Tribunal install script from playonlinux ([http://www.playonlinux.com/repository/download.php?id=313]("http://www.playonlinux.com/repository/download.php?id=313")) and run it Tools->Run a Local Script.

---

### Post by kriltos on 2012-02-03
You are a god among men. Thanks so much. that final line of code sorted me out, naturally i changed tribunal for bloodmoon and it did both :) Solved !

---

