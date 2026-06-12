---
title: "need a good guide for installing steam"
date: 2007-12-29
forum: Wine
---

### Post by uwishurockedthishxc on 2007-12-29
preferably in baby steps because im pretty new.  thanks ahead

---

### Post by Can+~ on 2007-12-29
[http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/](http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/)

---

### Post by crapgar on 2007-12-30
> **uwishurockedthishxc said:**
> preferably in baby steps because im pretty new.  thanks ahead
I installed steam today, here is what I did that seemed to work. Steam is now installed, although trying to install games crashes the program so maybe this is worthless. Regardless, here is my "guide".

I assume you already know this but in case you dont...Applications->Accessories->Terminal. I would drag terminal to your desktop so you can easily open it up. Any time you see code you need to put it in there and press enter.

   1. Install Wine 0.9.46 or newer
   2. For pre wine-0.9.47 versions only: Install tahoma.ttf from either a Windows installation, or download from the net. Copy it to '~/.wine/drive_c/windows/fonts' or install it into your system.(a replacement is included in 0.9.47)
   3. Install Gecko Engine by running

```
      wine iexplore http://winehq.org
```

      and clicking on Install button.

   4. THIS STEP MAY NOT BE NECESSARY. Download Steam installer from [http://www.steampowered.com](http://www.steampowered.com) and run it with

```
       wine msiexec /i/[COLOR="Red"]home/bobcat/desktop/[/COLOR]steaminstall.msi
```

Change the stuff in red to where you saved the file.

This should start the installation process. If it doesnt finish, then do this next step. 

     4.5 I cant find the installer on the internet. I clicked a link to get to it and I don't know which guide I found it on. Download the attached file and save it to your desktop.Extract the exe.

5.
```
wine [COLOR="Red"]home/bobcat/desktop/[/COLOR]SteamInstall.exe
```
Run the installer. 

   5. Start steam using the icon that should be on your desktop. If there is no icon I don't know what to tell you.

---

### Post by darksidedude on 2007-12-30
WINE DOORS nuff said

---

### Post by r41nz0r on 2007-12-30
Thanks for the help and support!

-Rain-

---

