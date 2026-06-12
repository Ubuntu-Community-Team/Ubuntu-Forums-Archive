---
title: "Steam Won't Open"
date: 2012-10-04
forum: Wine
---

### Post by guthriearmstrong on 2012-10-04
Hey all,

Here's my situation:
I installed wine 1.5.14, then installed Steam via PlayOnLinux
When I attempt to run it, a message pops up: "connecting to account," and then Steam shuts off.
If I open Steam with the command "/usr/share/playonlinux/playonlinux --run "Steam" -no-dwrite" the following appears:

> [POL_Wine] Message: Running wine- Steam.exe -no-dwrite
rm: cannot remove `*': No such file or directory
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
p11-kit:  couldn't load module:  /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so:  /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open  shared object file: No such file or directory
[1004/205306:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8
Assert( Assertion Failed: bRet ):hardware_win32.cpp:576
The same message pops up, and then Steam shuts off.

Could someone translate that for me, give me an idea of what to do?

---

### Post by regor210 on 2012-10-06
If your using Ubuntu 12.04 64bit you could try getting these 32bit lib's.

Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following command into the terminal window minus the $.

$ sudo apt-get install libc6:i386 libgcc1:i386 gcc-4.6-base:i386 libstdc++5:i386 libstdc++6:i386

Then restart your computer.

Let us know if this helps please.

---

### Post by bratherlui on 2012-10-07
Same here. Ubuntu 1204 64 bit. 
For me Steam used to work all time since 12.04 until yesterday. 
Either the Steam-update, the Ubuntu-upgrade or using the computer-janitor caused Steam not to work anymore.
In the morning I played Counterstrike - then I installed some upgrades proposed - used the computer-janitor - Steam-upgrade - Steam not working anymore.

Janitor's syslog entries (cat /var/log/syslog.1 | grep jani) where the following and let me think that isn't causing the problem:

Oct  6 09:53:37 monster computerjanitord:INFO: cleaning cruft[Y]: file:/etc/ca-certificates.conf.dpkg-old
Oct  6 09:53:37 monster computerjanitord:INFO: cleaning cruft[Y]: file:/etc/init/mysql.conf.dpkg-old
Oct  6 09:53:37 monster computerjanitord:INFO: cleaning cruft[Y]: deb:qt-faststart
Oct  6 09:53:37 monster computerjanitord:INFO: cleaning cruft[Y]: deb:cdda2wav
Oct  6 09:53:37 monster computerjanitord:INFO: cleaning cruft[Y]: file:/etc/ssl/certs/ValiCert_Class_2_VA.pem.dpkg-new
Oct  6 09:53:37 monster computerjanitord:INFO: cleaning cruft[Y]: deb:libdee-1.0-1
Oct  6 09:53:37 monster computerjanitord:INFO: cleaning cruft[Y]: file:/etc/ssl/certs/java/cacerts.dpkg-old

Added a screenshot of software center which actions were performed before Steam stopped working.

I don't have a solution getting back Steam.

---

### Post by guthriearmstrong on 2012-10-08
Thanks, I'm trying that now.

---

### Post by guthriearmstrong on 2012-10-08
Nope, I'm still getting the exact same error.

---

### Post by P-I H on 2012-10-12
I had also problem to open Steam.
I'm using Ubuntu 12.04.1 (64 bit) and Wine 1.5.14.
The message "connect to Steam account" was shown, but there after noting happened.
I had not used Steam for some days, so I suppose this is caused by an update of either Ubuntu or Steam.
The same happened on two installations on different computers.
The error messages are different on the two computers. On the 2:nd one these are the last lines in the terminal.

```
err:ole:create_server class {dff32fea-3331-48da-a272-ccfc238695be} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {dff32fea-3331-48da-a272-ccfc238695be} could be created for context 0x17
```

I fixed it on the 1:st computer by completly removing Wine and Winetrics. I also deleted the .wine folder. Then installed Wine and Winetricks. Installed Steam with Winetricks. Started Steam and downloaded Civ 5 again, which is the game I am playing.
The local saves in the "My Games" folder was available when I started Civ 5.

---

### Post by bratherlui on 2012-10-20
Hi!

My problems are fixed now. It seems at the Steam-update made the SteamUI.dll corrupted.
I installed Steam over the nice winetricks GUI. This new Steam seem to work, but no text readable in the Login Window.
 I tried copying Steam.exe of the newly installed Steam to the directory where Steam.exe was used to be for years :D
Nothing changed, old steam.exe not startable.  I saw that SteamUI.dll filesize in the newly installed and the old one differ. I copied the new dll to the old installation, renaming the original before.
Surprise! It worked.
But the Steam-login window was blank, nothing to read, just buttons and text-boxes. My typed login was not shown. Keypresses just changed nothing.
I tried to reinstall tahoma.ttf (or how this font was named, don't remember exactly) through winetricks. Nothing changed.
Then I found in ArchLinux wiki, that starting steam with extra parameter " -no-dwrite" might help.
Surprise! It worked.
the command was "wine path/to/steam/Steam.exe -no-dwrite".

---

### Post by lite1979 on 2012-10-20
I'd you'd like to stop using the "-no-dwrite" option, you can go into winecfg, libraries tab, and add "dwrite.dll", then edit, and disable it.

---

