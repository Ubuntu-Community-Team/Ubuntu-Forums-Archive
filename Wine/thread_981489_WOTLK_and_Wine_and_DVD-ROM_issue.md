---
title: "WOTLK and Wine and DVD-ROM issue"
date: 2008-11-13
forum: Wine
---

### Post by Starmartyr on 2008-11-13
Well, I found the easy button.  So, stop making the install of WOTLK much harder than it needs to be. Stop trying to mount the media, and pulling your hair out.

I am running Ubuntu 8.04, Wine 1.18, and an nVidia grafx card.

My solution (after 6 hours of failed installs and surfing for answers):

1. Make sure your DVD-ROM drive is setup in /etc/fstab correctly:

   in terminal:
```
sudo gedit /etc/fstab
```

   this is my setup of my DVD-ROM in my fstab, so may work for you on your system:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

2. Go upgrade your account at [https://upgrade.worldofwarcraft.com/installer/]("https://upgrade.worldofwarcraft.com/installer/") using your WOTLK CD Key.

3. Once you have upgraded, download the installer that follows (installer will work on WOTLK.)

4. Run the installer (double-click worked for me for Wine to pickup and run.)  

5. Watch the installer work, and enjoy the install graphics and music (LOL)

6. Download patch 3.01 to 3.02, or wait longer for the WOW Downloader to install it.  Got my patch from [http://www.strategyinformer.com/pc/worldofwarcraft/patch/27078.html]("http://www.strategyinformer.com/pc/worldofwarcraft/patch/27078.html")

7. Patch your WOW install.

8. Enjoy WOTLK! :popcorn: (try to keep the butter from getting all over your mouse and keyboard)

---

### Post by spaceghoti on 2008-11-15
Unfortunately, I already upgraded my account online and didn't try to run the downloader because I already had the DVD installer.  Thus, when I went back to try to get the installer what they offered was the Burning Crusade, and when I tried re-upgrading my account my key was already in use.

---

