---
title: "Wine will not install programs"
date: 2008-05-31
forum: Wine
---

### Post by kennster on 2008-05-31
I have world of warcraft installed and just got my old Steam info and go to download steam and it will not let me install steam i dubble click it. nuttin i right click open with WINE. nuttin what might be wrong?

---

### Post by cogadh on 2008-05-31
The Steam installer is an MSI file, you need to run it using the command line. Either run it like this:
```
wine start SteamInstall.msi
```
OR
```
msiexec SteamInstall.msi
```
Needless to say, you need to change directories to wherever you put the Steam installer before running those commands.

---

### Post by kennster on 2008-05-31
> **cogadh said:**
> The Steam installer is an MSI file, you need to run it using the command line. Either run it like this:
```
wine start SteamInstall.msi
```
OR
```
msiexec SteamInstall.msi
```
Needless to say, you need to change directories to wherever you put the Steam installer before running those commands.

i typed in both of thos and neather one worked :(

---

### Post by Horomancer on 2008-06-01
the MSI is a format used by windows that is not supported by wine automatically. You can make it supported though...
Did this just last night, but can't remember how exaclty.

An option is to go and huntdown the Steam.exe files. Those should give you no troubles.


edit: I know that the steps of typing

wine iexplore [http://www.winehq.org/](http://www.winehq.org/)

and hitting yes for the download option and dling the adobe flash.exe files and opening the flash.exe through wine where involved

---

### Post by cogadh on 2008-06-01
> **kennster said:**
> i typed in both of thos and neather one worked :(

They have to, that's how Wine handles .msi files. As I said, you need to change directories to wherever you downloaded the Steam installer first. For example, if you have the installer on your Desktop:
```
cd ~/Desktop
wine start SteamInstall.msi
```

However, as Horomancer mentioned, there are some additional steps required before Steam will work. It is best to do all of them before trying to install Steam. First you need to install the Wine Gecko HTML engine. Run this, then follow the prompts:
```
wine iexplore http://www.winehq.org/
```
You also need to install the Windows version of FlashPlayer in Wine. Go to the Adobe website and download the Windows executable, then install it in Wine:
```
cd /wherever/you/put/the/installer
wine install_flash_player.exe
```
And lastly, you need to install the winbind package:
```
sudo apt-get install winbind
```

---

