---
title: "Problem with Steam and Wine"
date: 2008-05-19
forum: Wine
---

### Post by ogisdan on 2008-05-19
I have been checking guides and how to's but I have still yet to get it running. I begin by puting > wine iexplore into the terminal and i get wine's virtual desktop up with internet explorer. I then head over to steampowered.com and download the only installer i see which gives me the steaminstall.msi file. I then type in the terminal > msiexec -i SteamInstall.msi and i get this error:
> danny@danny-desktop:~$ wine msiexec /i SteamInstall.msi
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:msi:copy_package_to_temp failed to copy package L"SteamInstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"SteamInstall.msi"


i am using the latest version of wine which is 1.0 and i have everything in it the same way i got it minus the virtual desktop size which is 1024x768. i have been using this guide, [http://wine-review.blogspot.com/2007/11/steam-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/11/steam-on-linux-with-wine.html)

Thanks for the help!

---

### Post by Sleaka J on 2008-05-20
You need to type in "wine" before that. The guide is wrong.

ie. $ wine msiexec /i SteamInstall.msi

However, I did it this way:

$ wine start SteamInstall.msi

Try the WineHQ AppDB on Steam

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554)

---

### Post by ogisdan on 2008-05-20
> **Sleaka J said:**
> You need to type in "wine" before that. The guide is wrong.

ie. $ wine msiexec /i SteamInstall.msi

However, I did it this way:

$ wine start SteamInstall.msi

Try the WineHQ AppDB on Steam

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554)

i tried those and it gave me this:


> danny@danny-desktop:~$ wine msiexec /i SteamInstall.msi
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:msi:copy_package_to_temp failed to copy package L"SteamInstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"SteamInstall.msi"
danny@danny-desktop:~$ 



edit: am i supposed to save it to the desktop?

---

### Post by Sleaka J on 2008-05-20
It doesn't matter where you save it, just as long as you have write permission. However you might want to download it again if you're getting those errors (specifically the error about it being unable to open). It could be a bad download.

---

### Post by OpposingForce on 2008-05-20
I had a hard time with the msi file too.  While I'm sure it's possible to install msi files in WINE, I couldn't figure it out.  It's easier to get .exe files to run in WINE so here's the steaminstall.exe that valve used to use before they replaced the installer with msi for some reason.  I used this to set up steam on my comp (ubuntu 8.04)

[http://www.ausgamers.com/files/details/html/10694](http://www.ausgamers.com/files/details/html/10694)

[http://developer.valvesoftware.com/wiki/Steam_under_Linux#Ubuntu](http://developer.valvesoftware.com/wiki/Steam_under_Linux#Ubuntu)

^^ There's a guide on how to do it.  But all you should have to really do is put that .exe on your desktop and run

```
wine SteamInstall.exe
```

Then it should go through a whole bunch of crap and install, then it'll automatically update itself to the latest version.

---

### Post by ogisdan on 2008-05-20
> **OpposingForce said:**
> I had a hard time with the msi file too.  While I'm sure it's possible to install msi files in WINE, I couldn't figure it out.  It's easier to get .exe files to run in WINE so here's the steaminstall.exe that valve used to use before they replaced the installer with msi for some reason.  I used this to set up steam on my comp (ubuntu 8.04)

[http://www.ausgamers.com/files/details/html/10694](http://www.ausgamers.com/files/details/html/10694)

[http://developer.valvesoftware.com/wiki/Steam_under_Linux#Ubuntu](http://developer.valvesoftware.com/wiki/Steam_under_Linux#Ubuntu)

^^ There's a guide on how to do it.  But all you should have to really do is put that .exe on your desktop and run

```
wine SteamInstall.exe
```

Then it should go through a whole bunch of crap and install, then it'll automatically update itself to the latest version.

thanks, that worked out.

edit: i installed the fonts into the wine/cdrive/fonts and i still can't see what im typing should i reinstall steam?

---

### Post by OpposingForce on 2008-05-20
Check again to make sure its in ~/.wine/drive_c/windows/fonts 

If that doesn't work try restarting steam, I think it worked right off the bat for me.  So if restarting the program doesn't work try rebooting your computer.  If that fails then try reinstalling.

---

