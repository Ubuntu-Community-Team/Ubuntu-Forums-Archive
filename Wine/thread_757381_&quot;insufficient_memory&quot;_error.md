---
title: "&quot;insufficient memory&quot; error"
date: 2008-04-16
forum: Wine
---

### Post by kgriff on 2008-04-16
I am running Wine 0.9.59 on Ubuntu 7.10.
I'm trying to get Nova Development's Photo Explosion Deluxe running and have run into some issues.

Here's where I'm at so far:  Tried to install the program from Wine, but it didn't work.  Installed in Windows and copied program and all registry entries to Wine.  During the windows install, I found out that the program requires Internet Explorer in order to install.  Still didn't work, and I had a terminal full of errors about missing dll's.  Traced this problem back to missing mfc42.dll and msvpc60.dll.  Moved both from the Windows\System32 directory to the Wine Windows/System32 directory.
Installed Wine Gecko.
When I attempt to run the program I get a pop-up error box with the following error:  "Unable to read version information from file C:\Program Files\Nova Development\Photo Explosion Deluxe\Ipe40.exe, insufficient memory or low system resources"

Since the first time I tried to run the program and got this error, I have again tried to install the program from Wine, since I installed Gecko.  This time the install completed without error.  However, when I run the program I still have the same error.

I don't believe this is actually a memory or resource issue.  Running System Monitor when I'm trying to run this program reveals the following:

User memory:  223 MB of 440MB
Used swap:  34MB of 1.2GB
CPU usage barely blips.

User memory immediately prior to running the program was 216 MB of 440MB

I am running an Athlon 3700+ at 2.4GHz

I've posted this to the Wine forum and had a few suggestions, but nothing that helped.  Any assistance would be appreciated.

---

### Post by thefishki345 on 2008-04-16
I had this happen to me when I was installing steam on wine.
copy the install/setup file and everything in it to your desktop and run the setup/run the program from there. If that doesn´t work, I´m not sure what you should do next. sorry I cant be of more assistance.

---

### Post by kgriff on 2008-04-16
Are you saying I should copy the entire installation CD to the desktop and run the installation from there?  Then, presumably, run the program from the desktop as well, once it is installed?

---

### Post by thefishki345 on 2008-04-16
Yes, copy the files from the cd to your desktop and install it from there, then try and run it, if you still need the files keep them, if you dont, delete them.

---

