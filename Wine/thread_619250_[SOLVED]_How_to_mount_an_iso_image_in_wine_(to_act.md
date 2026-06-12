---
title: "[SOLVED] How to mount an iso image in wine (to act as a cd)"
date: 2007-11-21
forum: Wine
---

### Post by Tyke91 on 2007-11-21
I've made an iso of my SC broodwar CD, and I'd like to be able to mount that as a CD and play SC broodwar without the disk (i often lose the disk AND I need two disks so that i can play on a lan network with my friend)

I've tried mounting it to the point /media/cdrom0 (my cdrom drive)[which was probably dangerous]   and mounting it to /mnt/isos (a directory I created)

I know there is a way in wine to mount an iso to a virtual "D/:" drive in order to play without a disk, but I don't know exactly how to do that.

any help would be most appreciated.

---

### Post by Sukarn on 2007-11-21
From what you've said, I assume that you know how to loop mount the iso file to the location /media/cdrom.

Open wine configuration (winecfg) and go to the Drives tab (I don't have wine installed at the moment so the actual tab name might be different).

If /media/cdrom (or where ever you are mounting the iso file) is not present in the list of drives, then add it.

---

### Post by baqai on 2007-11-21
what a coincidence i had the same querry regarding virtual drives, i even posted regarding the same question in one of the above FAQ's. I am using AcetoneISO2 by the way

What you can try to do is to go to **Configure Wine** and in **drives** add the path to the virtual drive (in my case its /home/me/virtual-drives/1 ) and than go in advance and set it as CDROM, maybe this will work for you?

I read these instructions in a thread related to oblivion, how ever it hasn't worked for me

i was trying to install Swat 4 which is on two cd's i mounted the image and setup ran fine till it asks for the second cd, no matter what i do i can't manage to make it read the second cd

here is what i have tried

wine eject e: (the path to virtual cd)
mounting and unmounting the drive several times

I even tried installing Daemon Tools in wine but setup refused to run for me so back to square one for me :)

---

### Post by Sukarn on 2007-11-21
> **baqai said:**
> what a coincidence i had the same querry regarding virtual drives, i even posted regarding the same question in one of the above FAQ's. I am using AcetoneISO2 by the way

What you can try to do is to go to **Configure Wine** and in **drives** add the path to the virtual drive (in my case its /home/me/virtual-drives/1 ) and than go in advance and set it as CDROM, maybe this will work for you?

I read these instructions in a thread related to oblivion, how ever it hasn't worked for me

i was trying to install Swat 4 which is on two cd's i mounted the image and setup ran fine till it asks for the second cd, no matter what i do i can't manage to make it read the second cd

here is what i have tried

wine eject e: (the path to virtual cd)
mounting and unmounting the drive several times

I even tried installing Daemon Tools in wine but setup refused to run for me so back to square one for me :)

Maybe you can try copying the contents of the two cds to one folder on your hard drive and then run the setup from there?

---

### Post by Tyke91 on 2007-11-21
My problem is solved :)

it turns out that I couldn't get it to mount in wineconfig because of a spelling mistake 

I typed
```

/home/mykola/virtualdrive/drive0

```
when i should have typed
```

/home/mykola/virtualdrive/Drive0

```


anyway, here are the steps I used to attain this, you may be able to install via the disk images, but I used the CDs so I'm writing what I did. I am assuming that you have WINE 0.9.46 (the latest version as of Nov 21 2007) installed.

1. install starcraft and broodwar via your cds and WINE

2. restart the computer (I've tried 'not restarting' and going on to the next steps, but something was broken and I got an error telling me that it was unable to change my screen size.)

3. go to your wineconfig>Audio page make sure that you have unchecked "OSS driver" and checked "ALSA". 

4. go to your wineconfig>Graphics page and make sure that you have checked these boxes: 
[LIST]
[*]Allow DirectX apps to stop the mouse leaving their window[/LIST][LIST]
[*]Allow the window manager to control the windows[/LIST][LIST]
[*]Allow Pixel Shader (if supported by hardware)[/LIST][LIST]
[*]Screen Resolution 120 dpi[/LIST]5. create an iso of the broodwar disk in your home folder by typing this command
```
dd if=/dev/cdrom of=$HOME/BROODWAR.iso bs=64k

```

6. create the directory that you want to mount the iso in (i chose virtualdrive/Drive0
```
mkdir ~/virtualdrive/Drive0
```

7. mount the iso to that directory
```

sudo mount -o loop BROODWAR.iso ~/virtualdrive/Drive0

```

8. go back to wineconfig and click on the "Drives" tab.  add a new drive (probably drive E) and write the path to virtualdrive/Drive0 into the drive mapping box (I wrote /home/mykola/virtualdrive/Drive0 )

9. select "Show Advanced" and set the "Type" to CD-ROM. then select the "Show dot files" box.

10. run starcraft from your WINE programs list without the CD!

---

### Post by baqai on 2007-11-21
Well copying both the cd's in one folder and than installing the game worked for me, in the end the wine window wasn't automatically closing and when i tried to run the game it gave this error

```

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
---------------------------
 Havok - Build (20031208)
err:ntdll:RtlpWaitForCriticalSection section 0x7e4d35a0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000f, blocked by 0009, retrying (60 sec)
wine: Critical section 7e4d35a0 wait failed at address 0x7bc39c10 (thread 000f), starting debugger...
Unhandled exception: wait failed on critical section 0x7e4d35a0 thread_data_tls_index+0x40
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc39c10
baqai@baqai-desktop:~/.wine/drive_c/Program Files/Sierra/SWAT 4/Content/System$ Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
No process loaded, cannot execute 'detach'

```

and in the window i get a error dialgoue box with following message 

```
No Label

Crash Time: 11/21/07 22:56:22

OS: Windows XP 5.1 (Build: 2600)
CPU: GenuineIntel Unknown processor @ 2997 MHz with 2009MB RAM
Video: Direct3D HAL (10014)

UserName: baqai
ComputerName: baqaidesktop
Application location: C:\Program Files\Sierra\SWAT 4\Content\System\

SWAT Build Number: 31973

Access Violation caused General protection fault!

History: UGameEngine::Draw <- UWindowsViewport::Repaint <- UWindowsClient::Tick <- ClientTick <- UGameEngine::Tick <- UpdateWorld <- MainLoop->GenerateExtraCrashInfo [(GLevel: 'myLevel' PendingLevel: '(NULL)' NetMode: 'NM_Standalone'] <- MainLoop

```

I will try the manual mount method instead of using a front end and see if i can succeed

---

### Post by piepolitb on 2007-11-30
> **baqai said:**
> Well copying both the cd's in one folder and than installing the game worked for me, in the end the wine window wasn't automatically closing and when i tried to run the game it gave this error

```

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
---------------------------
 Havok - Build (20031208)
err:ntdll:RtlpWaitForCriticalSection section 0x7e4d35a0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000f, blocked by 0009, retrying (60 sec)
wine: Critical section 7e4d35a0 wait failed at address 0x7bc39c10 (thread 000f), starting debugger...
Unhandled exception: wait failed on critical section 0x7e4d35a0 thread_data_tls_index+0x40
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc39c10
baqai@baqai-desktop:~/.wine/drive_c/Program Files/Sierra/SWAT 4/Content/System$ Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
No process loaded, cannot execute 'detach'

```

and in the window i get a error dialgoue box with following message 

```
No Label

Crash Time: 11/21/07 22:56:22

OS: Windows XP 5.1 (Build: 2600)
CPU: GenuineIntel Unknown processor @ 2997 MHz with 2009MB RAM
Video: Direct3D HAL (10014)

UserName: baqai
ComputerName: baqaidesktop
Application location: C:\Program Files\Sierra\SWAT 4\Content\System\

SWAT Build Number: 31973

Access Violation caused General protection fault!

History: UGameEngine::Draw <- UWindowsViewport::Repaint <- UWindowsClient::Tick <- ClientTick <- UGameEngine::Tick <- UpdateWorld <- MainLoop->GenerateExtraCrashInfo [(GLevel: 'myLevel' PendingLevel: '(NULL)' NetMode: 'NM_Standalone'] <- MainLoop

```

I will try the manual mount method instead of using a front end and see if i can succeed

got same problem with swat4...! Same message error in dialog box and I tried two ways to install: 
1. as you guys said, copying both cds in a folder and start installation via wine
2. installed via windows (I'm still a dual booter...sigh) and tried to launch it in ubuntu with wine
Anyway I've got that error (if you're asking, in windows it works)

can you help me?

---

### Post by piepolitb on 2007-12-02
great! it works! :guitar:

just upgrading wine this morning:lolflag:

hope this can help someone

---

### Post by Ascendaeus on 2009-07-23
it's not solved. i go into cnfg, click add, and it picks random letter, for the names of random new drives and doesn't do anything with any of that, i exit, click on the exe and it says i need a cd. i tried to install deamon tools lite and it said you got error 256, i tried to install deamon tools and it said you got error 256, i can't figure out how to get files out of my virtual drives on gmount how do you mount a drive in wine it seems like there is no solution i don't know what you mean by add the drive i added twenty seven drives and they all disappeared as soon as i left the config, i've got c: and z: and neither of them are accepting an iso i've got, morrowind, fallout three and halo, halo doesn't work online, morrowind doesn't have a disk (i downloaded only an iso,.. how is it that i don't have the cd?) and fallout crashes on startup. i click browse and the iso is invisible in the file i put it in and my virtual cd roms are stuffed with morrowind and i can't get them out of there without restarting my computer. battlefield 2142 is apparently the most popular and compatible game for wine but there is apparently nobody playing it bcuz there is only 7 seeds how do i get past the halo update? why does fallout crash and how do i Mount a ******* ISO!?

---

### Post by matts31415 on 2010-06-19
I was trying to get rosetta stone to work in wine and could not get the ISO of the language disk to be recognized by the rosetta stone program or by wine in general.

mkdir /mnt/virtual

mount -o loop /path/to/languageCD.iso /mnt/virtual

go to the wine configuration window (Applications > Wine > Configure Wine)

Go to the Drives tab

Click Add...

Set the path to /mnt/virtual

click Show Advanced button

set Type: cdrom

thats it. launch your app and it should recognize your mounted iso as a cd

for me the key was setting that drive type to cdrom in the wine cfg

---

### Post by axelsvag on 2010-06-29
Thank you it worked perfectly, the only thing I have left to solve is the sound. Wine sounds works perfectly on spotify, but not in rosetta stone

---

### Post by elvinatom on 2010-07-05
what would be nice would be a script that mounts an iso and then launches the game - all without root/sudo/gksu authentication.  And when you exit the game the images gets unmounted automatically too.  So you can make a .desktop file for the menu: Just click and play! :)

---

### Post by tiger74 on 2010-08-02
You guys are very naughty!! :D

---

### Post by IanW on 2010-08-02
> **elvinatom said:**
> what would be nice would be a script that mounts an iso and then launches the game - all without root/sudo/gksu authentication.  And when you exit the game the images gets unmounted automatically too.  So you can make a .desktop file for the menu: Just click and play! :)

I suggest you investigate "wisotool". It seems to be a "winetricks" for games.

---

### Post by Dudutzu on 2011-03-26
> **matts31415 said:**
> I was trying to get rosetta stone to work in wine and could not get the ISO of the language disk to be recognized by the rosetta stone program or by wine in general.

mkdir /mnt/virtual

mount -o loop /path/to/languageCD.iso /mnt/virtual

go to the wine configuration window (Applications > Wine > Configure Wine)

Go to the Drives tab

Click Add...

Set the path to /mnt/virtual

click Show Advanced button

set Type: cdrom

thats it. launch your app and it should recognize your mounted iso as a cd

for me the key was setting that drive type to cdrom in the wine cfg

It was just what I needed! 
(even the application)

---

### Post by shaggydavid on 2012-11-23
why not use the "no cd patch" provided by blizzard? all you would have to do is install sc and bw then patch.  copy "install.exe" from sc cd to the install directory renaming it starcraft.mpq , then copy "install.exe" from bw cd to to the install directory renaming it broodwar.mpq
if you do this there will be no need to mount the cd immage.

---

### Post by undrline on 2013-06-19
For those who might still be having issues with certain finicky CDs, the only thing that worked for me with one particular game was gcdemu (cdemu.sourceforge.net, they have a launchpad ppa).

---

