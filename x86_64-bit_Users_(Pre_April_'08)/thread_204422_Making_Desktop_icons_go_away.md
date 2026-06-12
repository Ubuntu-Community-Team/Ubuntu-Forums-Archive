---
title: "Making Desktop icons go away"
date: 2006-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-06-27
First I installed a brand new Dapper-64 on an unused space on my hard drive as a test installation to see if everything that I needed worked. It did, so I tried to do "sudo apt-get dist upgrade," but that hopelessly borked my old Breezy-64 installation. I finally bit the bullet and wiped it out, reformatted it, and installed Dapper-64 on it, which will now be the main installation. I'll keep the test installation as a rescue version.

When I was playing with the test installation I found an option to make the icons for files located in /home/jjj/Desktop not appear on the desktop. I've spent the last hour trying to find that option again. Where is it?

Also, none of the screensavers are working, although they are working fine in the test installation. This leads me to suspect that my problem above is that some configuration file did not get installed. Has this happened to anyone else? Where are the screensaver files kept?

---

### Post by christoffer on 2006-06-27
I have yet to discover any other way to do the icon-visible-on-the-desktop thing, but there might be. Here's how I do it.

Launch gconf-editor.

Extend the "apps"-folder,
Extend the "nautilus"-folder,
Click the "desktop"-folder,
Uncheck/check the icons you want/don't want visible on the desktop.

Quit gconf-editor. Done.

As for screensavers? The only thing I can think of is that I used to have had a problem with that when I hadn't installed the drivers for my graphics card. None of the OpenGL-savers would work (and they were plenty). Perhaps it's something related?

---

### Post by John Jason Jordan on 2006-06-27
[QUOTE=christoffer]I have yet to discover any other way to do the icon-visible-on-the-desktop thing, but there might be. Here's how I do it.[/QUOTE]
As it turns out, the installation I was trying to do that with got so screwed up that I had to reformat and reinstall, which I will do tomorrow. I am currently using my test installation of Dapper-64, where I have the icons hidden. I still can't figure out how I did it though. If I remember while poking around in here I'll post back. I hate icons all over my desktop. I think it's Nautilus that makes them appear, because once I uninstalled Nautilus a long time ago with Breezy and afterwards no icons ever appeared on the desktop.

[QUOTE=christoffer]As for screensavers? The only thing I can think of is that I used to have had a problem with that when I hadn't installed the drivers for my graphics card. None of the OpenGL-savers would work (and they were plenty). Perhaps it's something related?[/QUOTE]
I just fixed that. Followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=195557]("http://ubuntuforums.org/showthread.php?t=195557")
Now I have real screensavers!

---

