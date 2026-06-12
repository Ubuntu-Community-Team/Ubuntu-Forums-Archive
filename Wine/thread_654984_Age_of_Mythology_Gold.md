---
title: "Age of Mythology Gold"
date: 2007-12-31
forum: Wine
---

### Post by SecretSnack on 2007-12-31
Hi,

I'm running Wine 0.9.43 and I managed to get AOM installed.  But now it won't run: when I select the program OR insert the CD OR click on the .exe on the CD, nothing happens.  Any ideas?

---

### Post by Pathfinder_ on 2007-12-31
I think you need a no-cd loader or a fixed executable to run it. Just place it in your AoM directory and run it. (make sure the version of no cd loader matches your AoM version)
 I won't list the links to those as that might be against the forum rules. Use google to find them. There are plenty.

---

### Post by raddellee on 2008-01-02
to get age of mythology gold working follow this guide from wine-wiki.org

Before installation mfc42.dll must be placed in ~/.wine/drive_c/windows/system32, which can be obtained from C:\WINDOWS\system32 if you have a Windows partition. Without this file the product key will fail to verify.

To begin installation the following must be typed at the command line:

wine /mnt/cdrom0/AOMSetup.Exe

Where /mnt/cdrom0/ is your CD drive.

Either Express Install or Install can be chosen, both work without any issues.

Setup will stop at 35% and ask for the second CD, insert the second CD into the same drive the first was in and once it is mounted click OK and the installation will continue as normal.
[edit] Running the application


This game works the best under wine 0.9.18, in 0.9.17 all the textures are black making it unplayable, and in 0.9.16 the water flickers if the graphics are set to high.

To run the game 4 files must be copied to ~/.wine/drive_c/windows/system32, ntoskrnl.exe, bootvid.dll, hal.dll, and kdcom.dll, all of which can be found in C:\WINDOWS\system32.

Before player the 1.03 patch must be installed, then a No-CD patch must be installed or the game will not run.

To launch the game this must be types at the command line:

wine "/home/[username]/.wine/drive_c/Program Files/Microsoft Games/Age of Mythology/aomx.exe" +noIntroCinematics

It is recommended to use the +noIntroCinematics as the title videos do not display properly. (this step is not needed in later versions of wine)

In-game, the campaigns do not work, the game crashes after the intro videos. Single player works fine. Multiplayer over a LAN between a Windows computer and a Linux computer does not work, With the Windows one as the host the Linux one sees the game but cannot connect, the other way around, the Windows one does not even see the Linux one. 


If you wanted to view this page visit [http://wine-wiki.org/](http://wine-wiki.org/) 
search for age of mythology and it is titled Age of Mythology: The Titans (3,191 bytes) the second 1 down
this includes the links for the crack and patch]

---

### Post by tlf30 on 2010-05-18
I'm having a bit of trouble when it comes to the second disk, it tells me to put it in to drive E: but i tried all 3 of my CD drives and it doesn't like any of them. *Please* help.:confused:

---

### Post by tlf30 on 2010-05-19
I got the drives working but now when I run the program it tells me font error and then the game loads and there's no words. I have the updated version and the no-CD patch installed. I'm also running Wine 1.1.42.

---

