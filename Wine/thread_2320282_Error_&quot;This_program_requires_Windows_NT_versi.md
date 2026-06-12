---
title: "Error &quot;This program requires Windows NT version 6.0 or later&quot;"
date: 2016-04-12
forum: Wine
---

### Post by asb3 on 2016-04-12
I'm trying to install MusicNotes.  The latest version of MusicNotes is for Windows 10.  (Will WINE rune Windows 10 apps?) I was unable to download the Windows 10 app because the web page autodetects the OS, and since I'm running LINUX, the "Download" button is not active.  I was able to download an older version of the software that supposedly runs under windows XP, VISTA and 8.  When I used WINE to run the installer, the installation failed and returned the error message "This program requires Windows NT version 6.0 or later".  Any ideas?

---

### Post by yoshii on 2016-04-12
If you run Mozilla Firefox, you can temporarily install an addon called TotalSpoof.  It will fool the websites into thinking you are running Windows, and then you can download the program you want.  [https://addons.mozilla.org/en-US/firefox/addon/totalspoof/?src=search](https://addons.mozilla.org/en-US/firefox/addon/totalspoof/?src=search)

You can disable or remove TotalSpoof when you are done with it.  

Also, check Wine Configuration:  (winecfg from within a terminal) from the Ubuntu application menu.  
There is a tab within Wine Configuration which let's you choose the Windows version for compatibility issues like what you are experiencing.  
It doesn't change the behavior of Wine, it just reports to software a (fake) operating system version.  By the way, WinNT v6 = Vista.  

Good luck.

---

### Post by asb3 on 2016-04-13
I tried running InstallMusicnotes.exe with the operating system set in WINE Config to Windows 8 and to Vista.  Same error.

---

### Post by kurt18947 on 2016-04-13
Wine will not run all or even most Windows programs. Here is one database:

[https://appdb.winehq.org/](https://appdb.winehq.org/)

You could also look at playonlinux.com or codeweavers.com

If you can find your program listed, you might find tweaks to Wine that will allow installation and at least limited functionality.

---

