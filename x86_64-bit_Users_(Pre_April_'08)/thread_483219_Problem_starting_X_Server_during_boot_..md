---
title: "Problem starting X Server during boot ."
date: 2007-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by ub-noob on 2007-06-24
Hi,

I had installed Feisty Fawn on my Acer PC (AMD-64) in parallel with windows vista.  Everything was working fine until I decided to use windows true type fonts.

Here is what I did (suggestion taken from a thread here):
```
sudo mkdir /usr/share/fonts/truetype

Copy your windows fonts to this directory:

sudo cp /media/hda1/windows/Fonts/*.ttf /usr/share/fonts/truetype/windows

Fix the permissions:

sudo chmod 644 /usr/share/fonts/truetype/*

Tell the system about the new fonts

sudo fc-cache /usr/share/fonts/
```
Then I logged out for changes to take effect and then logged in again.. only problem is I was not able to.  I just got a black screen with a mouse icon swirling.. forever.

I did a hard reboot... selected Ubuntu in Grub, but came to a halt at the same point as before.  I did a CTRL+ALT+F2 and logged in to the terminal as admin privilege user.  Then when I started X Server (startx at the prompt) and I see the following error

```
Fatal server error:
Server is already active for display 0
       If this server is no longer running, remove /tmp/.X0-lock and start again.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 KEY
giving up

xinit: unable to connect to X server
xinit: No such process (errno 3): Server error
```

I removed the lock by typing
```
sudo rm /tmp/.X0-lock
```
and stared X Server.  It starts but my fonts are all messed up.  All I see is little squares in place of characters (Everywhere.. menu items, desktop icon names, window headers... all are squares).

Now I did CTRL+ALT+F2 again, here is what I see on the screen:

```
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

I did a CTRL-C, typed "su - root" and started X Server as root.  Now everything works fine.

But booting into Ubuntu is still a problem.

I have gone through a lot of threads on all error messages.  I don't seem to find the solution.  I do not want to re-install Ubuntu.  Any help to fix this will be greatly appreciated.

Thanks in advance guys.

Sriram.

---

### Post by incubus on 2007-06-24
Hi, 

I don't have any experience with installing these fonts, so it's better to wait for somebody more knowledgeable to help you.  But if you could survive without those fonts, I would remove them, run fc-cache again, and see if that fixes it.

It would help if you could post your complete xorg log.  I don't think that part you posted actually shows the relevant error (wacom is something else).  The file would be:
```

/var/log/Xorg.0.log

```

incubus

---

### Post by Cappy on 2007-06-24
```

sudo chmod 755 /usr/share/fonts/truetype/*
sudo chmod -R 755 /usr/share/fonts/truetype/windows

```
Try that .. that's what I have for my permissions there.

If all else fails you can remove them:
```
sudo mv /usr/share/fonts/truetype/windows /tmp
sudo fc-cache /usr/share/fonts/

```

---

### Post by avik on 2007-06-24
Another thing is that all my fonts seem to have a permission of 700 (-rwx------), not 644.  Next time, there's no need to change the permissions.

Whether that helps with your problem or not, I wanted to put the information out there.

---

### Post by ub-noob on 2007-06-25
Cappy and Avik,

Thanks for your suggestions.  It, indeed, fixed the problem.  I changed the font permissions to 755 and I was able to login again.

Thank you guys for helping me out.

Sriram.

---

