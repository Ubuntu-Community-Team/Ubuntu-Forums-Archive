---
title: "Missing GRUB Editor menu entry (8.10)"
date: 2008-12-12
forum: x86 64-bit Users
---

### Post by brad_uk on 2008-12-12
Hi,

I've got a 64 bit 8.10 install that dual boots with XP. I wanted to change the boot order but couldn't find the admin menu entry for grub boot loader.

I looked at some docs here:

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#GRUB_boot_manager_settings](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#GRUB_boot_manager_settings)

It talks about being able to do this under System -> Administration -> Advanced -> GRUB Editor .

I don't have the Advanced menu entry or a GRUB Editor entry anywhere under the system menu. Is it there for anyone else?

I've made the required change by manually editing the config file under /boot/grub but I'm interested to see if I'm missing something (i seem to remember the menu entry from previous versions).

Cheers,
brad.

---

### Post by caljohnsmith on 2008-12-12
To my knowledge there isn't an "Advanced" application under System > Administration, so I'm not sure what that guide is talking about. You could look at using "startupmanager", which is available in the repositories. That's about the best GUI Grub menu editor I'm aware of, but that's only because there aren't many choices. :)

---

### Post by ajgreeny on 2008-12-12
To be honest the easiest way is simply to edit the grub menu file by using ```
gksudo gedit /boot/grub/menu.lst
```
Now you can change the default boot number or time etc etc.  Tell us exactly what you want to do and we'll be able to help in much more detail.

---

### Post by skern03 on 2008-12-19
Intrepid seems to have a slimmed-down administrative menu in both Ubuntu and Kubuntu. In Kubuntu, the System Settings menu might be more aptly called "System Settings Lite!"

'Course, having said that, I had to revert to U8.04 because U8.10 wasn't stable on my leaky system of cobbled together ancient drives, so I'm going on my similarly leaky memory of it... But I can tell you the Advanced menu items are also not in 8.04.

In Kubuntu, there is a Grub GUI.

I wish the two systems had closer parity (outside the differences between KDE and Gnome). Each has things I like that are missing in the other. :(

> **brad_uk said:**
> Hi,
It talks about being able to do this under System -> Administration -> Advanced -> GRUB Editor .

I don't have the Advanced menu entry or a GRUB Editor entry anywhere under the system menu. Is it there for anyone else?

...I'm interested to see if I'm missing something (i seem to remember the menu entry from previous versions).


---

### Post by philinux on 2008-12-19
As mentioned. Installing startupmanager or kgrubeditor are the gui choices.

---

### Post by Elzigzag on 2009-11-07
> **caljohnsmith said:**
> To my knowledge there isn't an "Advanced" application under System > Administration, so I'm not sure what that guide is talking about. You could look at using "startupmanager", which is available in the repositories. That's about the best GUI Grub menu editor I'm aware of, but that's only because there aren't many choices. :)
Sorry to insist on this issue, but according to Ubuntu 9.10 Documentation actually there is (or there should be) a System > Advanced > blah blah blah menu <http://ubuntuguide.org/wiki/Ubuntu:Karmic#Ubuntu_System_Administration> And even a System > Advanced > Grub Editor <http://ubuntuguide.org/wiki/Ubuntu:Karmic#GRUB_boot_manager_settings> Is there any reason explaining why these options are not available in my newly-born Koala? Any clue?

---

