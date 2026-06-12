---
title: "WoW Error"
date: 2008-04-14
forum: Wine
---

### Post by X3zh on 2008-04-14
Hello.

I have just installed WoW and it won't run because I am getting an error every time I tr to start it. The error looks like this.

==============================================================================
World of WarCraft (build 8125)

Exe:      C:\spel\World of Warcraft\Wow.exe
Time:     Apr 14, 2008  8:04:05.229 PM
User:     xlv
Computer: xlv-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\spel\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7DDF4321

The instruction at "0x7DDF4321" referenced memory at "0x00000000".
The memory could not be "read".

I have no clue what I should do to correct this. I am thankful for any possible solution.

Thank you.

---

### Post by tparker on 2008-04-14
I am getting this same error. Everything worked great in game previous to this. I just loaded up and it downloaded the 2.4 patch. Download went fine, application of patch said it went fine, but when I tried to start WoW again after the patch all I get is that error.

I went into my WoW folder and re-ran the installer from there to try again, it re-downloaded then told me it didn't need to apply because I already had that version.

Looking in my World of  Warcraft folder I do see that all the previous patches have two items, one is a 'downloader.exe' and the other is a 'patch.exe;' but for moving from version 2.3.3.7799 to 2.4.0.8089 the only item is the downloader, no 'patch.exe'. I do not know how to tell if that is related to the error though.

I have checked the wine appdb and a couple of posts refer to a 'memory error' in passing but I haven't found enough to know if it's this same error or how to fix it if so.

Just to see if this was a Wine or a WoW issue I tried to run City of Heroes, which also worked with no problems the last time I used it (about a month ago). For that I get the loading screen but when it moves on from there I get an error box that says 'Failed to Create OpenGL Rendering Context' and the program goes away when I click 'okay' (the only option).  CoH says it's an OpenGL problem and WoW says memory, but I included the CoH info here in case the problems are somehow related and having it helps.

Any ideas on the WoW error would be greatly appreciated, thanks.


Running Dapper AMD 64, Wine 0.9.57, Nvidia 7600gs.

---

### Post by tparker on 2008-04-14
Okay, I went into my WoW directory again and ran 'Launcher.exe', even though I normally bypass the launcher. The launcher window opened and started up a download from 2.4.0.8089 to 2.4.1.8125. Once again the download and application both went fine, and the new version shows both a 'downloader.exe' and a 'patch.exe' in the WoW folder, although there is still no 'patch.exe' for the 2.4.0.8089 version. I tried starting WoW again and still get the same memory error as the original poster.

---

### Post by X3zh on 2008-04-14
I am running the same graph card as you. I have searched a lill and found out that it could be the drivers ******* things up. Maybe it is, it is worth a try updating 'em.

---

### Post by tparker on 2008-04-14
Got it, just logged in, no problems so far. Here is what I did (adding extra info in case someone comes to the thread later and needs it):

(in a terminal) 

1) sudo apt-get install nvidia-glx nvidia-kernel-common
(this didn't do anything on mine, said I already had the newest, but it's worth running just to be sure)
2) sudo nvidia-glx-config enable
(this did make some changes for me)
3) sudo gedit /etc/X11/xorg.conf
and be sure that the video sections say nvidia instead of nv, mine did but again, good to check.

At this point I did restart x, not sure if it is needed though (I just used ctrl-alt-backspace).

Tried WoW from the same desktop short cut I have always used and it worked just dandy. So somehow from one use of the program to another without doing anything graphical that I can think of it looks like some of my graphics got hosed, but just the 'glx' stuff. No clue how it happened, but glad it was fixable and I hope it helps you.

---

### Post by X3zh on 2008-04-14
Im getting pretty annoyed that my ubuntu won't work properly. Im frustrated of all error messages lmfao.


xlv@xlv-desktop:~$ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

---

