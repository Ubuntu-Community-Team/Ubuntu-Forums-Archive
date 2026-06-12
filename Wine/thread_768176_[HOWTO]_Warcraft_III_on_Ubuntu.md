---
title: "[HOWTO] Warcraft III on Ubuntu"
date: 2008-04-26
forum: Wine
---

### Post by spamoom on 2008-04-26
This works with every version of ubuntu that I've installed (including hardy).

1. Install wine-doors using a .deb - [direct link]("http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb") - [download page]("http://www.wine-doors.org/wordpress/?page_id=3") -
2. Run WineDoors from Applications >>System Tools >> Wine-Doors and let it configure wine
3. Once the main wine-doors window comes up search down the list for DCOM 98 and press install followed by Apply
4. Close winedoors once that has completed and insert your warcraft III ROC cd. Browse to your cd and double click on install.exe, follow the installation as you would on windows.
5. Then do the same for the frozen throne if you want.
6. To run it manually, you can put this command in console, the first for ROC and the second for TFT. Opengl is added to stop it using directx which dramatically increased performance.
```
wine "/home/[COLOR="Red"]username[/COLOR]/.wine/drive_c/Program Files/Warcraft III/Warcraft III.exe" -opengl
wine "/home/[COLOR="Red"]username[/COLOR]/.wine/drive_c/Program Files/Warcraft III/Frozen Throne.exe" -opengl
```
7. The installers automatically make the correct launchers for you on the desktop that run through wine. You can delete the .lnk files however as they are not used.

This is my first proper post, so give me feedback if it is/isn't right. :)

---

### Post by unicorn_2003_1 on 2008-05-24
Yeah, I just did a normal install of Warcraft TFT in wine. and tweaked the registry with the opengl entry, works great, even faster than on Windows:)

one problem though, the screen is stretched as my LCD's native resolution is 1280*800, and warcraft only supports 4/3 resolution. you know how to make it run full screen with black strips on the sides like it would on Windows?

I know I can use virtual desktop to restrict the desktop to 4/3, but that was just not the fun experience I'd get from a full screen view, still good for replay watching though.

---

### Post by zalberico on 2008-06-21
I followed your instructions, and it installed successfully however when I try and run it, it says that the disk is not in the drive. 

 The disk is a store bought copy and the serial number is real. I think its the copy protection on it that's doing this. 

 I've read in different places that you need a nocd hack, but I've also read that that doesn't work.  If you had this problem how do you fix it? 
    Thanks

---

### Post by Mikerlord on 2008-06-21
Umm my retail wc3 frozen throne cd is scratched rlly badly soo if anyone could do me a BIG favor could anyone upload their "setup.mpq" file from their cd to a website or send it to [email]hiddintacos@yahoo.com[/email] please thanks becuz i really wann a play badly and my setup.mpq is corrupted becuz of the scratches on it besides i bought the cd like 3 years ago and i cant get another replacement soo... ya.

---

### Post by zalberico on 2008-06-21
Ok, so now I've installed frozen throne and updated to patch 1.21b, but I'm still getting the same 'Please put disc into drive' error as before.  It seems that no one else is having this problem so here are my specs maybe its my hardware.

Lenovo T61
2.4 ghz Intel 64bit
Intel x3100 integrated (This should be enough for warcraft)
4 gigabytes RAM

Running Hardy 

Would my integrated card be causing this problem?

---

### Post by SBFC on 2008-06-21
To avoid headaches I always get a nocd patch for games that do checks, like Warcraft III.

---

### Post by shae on 2008-06-21
With the latest patch Warcraft III does not check for the CD anymore.

---

### Post by zalberico on 2008-06-21
I believe patch 1.21b is the latest patch, but I'm still being asked for a cd.  Could you point me in the direction of a nocd patch?  Maybe that would help me finally get this thing running.

Thanks

---

### Post by dmn_clown on 2008-06-22
> **spamoom said:**
> This works with every version of ubuntu that I've installed (including hardy).

1. Install wine-doors using a .deb - [direct link]("http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb") - [download page]("http://www.wine-doors.org/wordpress/?page_id=3") -
2. Run WineDoors from Applications >>System Tools >> Wine-Doors and let it configure wine
3. Once the main wine-doors window comes up search down the list for DCOM 98 and press install followed by Apply
4. Close winedoors once that has completed and insert your warcraft III ROC cd. Browse to your cd and double click on install.exe, follow the installation as you would on windows.
5. Then do the same for the frozen throne if you want.
6. To run it manually, you can put this command in console, the first for ROC and the second for TFT. Opengl is added to stop it using directx which dramatically increased performance.
```
wine "/home/[COLOR="Red"]username[/COLOR]/.wine/drive_c/Program Files/Warcraft III/Warcraft III.exe" -opengl
wine "/home/[COLOR="Red"]username[/COLOR]/.wine/drive_c/Program Files/Warcraft III/Frozen Throne.exe" -opengl
```
7. The installers automatically make the correct launchers for you on the desktop that run through wine. You can delete the .lnk files however as they are not used.

This is my first proper post, so give me feedback if it is/isn't right. :)

You don't need winedoors or dcom98 to install or play WCIII:RoC or TFT, you only need to mount the cd and run the installer via wine in any terminal.  ```
wine /media/cdrom/install.exe
``` The copy protection (if you aren't using 1.21b) should work fine in Wine >=1.0.

---

### Post by jjk7288 on 2008-06-22
> one problem though, the screen is stretched as my LCD's native resolution is 1280*800, and warcraft only supports 4/3 resolution. you know how to make it run full screen with black strips on the sides like it would on Windows?

If you are using the latest NVidia drivers, there is a setting in the control panel for aspect ratio scaling. Otherwise, what I would recommend is opening the registry ("regedit" in terminal) then...

HKEY_CURRENT_USER > Software > Blizzard Entertainment > Warcraft III > Video

Change "resheight" and "reswidth" to match your resolution. It's not 100% perfect, but it looks WAY better than it would otherwise.

Hope that helps.

---

