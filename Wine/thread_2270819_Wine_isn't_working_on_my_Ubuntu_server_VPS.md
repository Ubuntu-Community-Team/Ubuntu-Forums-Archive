---
title: "Wine isn't working on my Ubuntu server VPS"
date: 2015-03-25
forum: Wine
---

### Post by slayer6662 on 2015-03-25
Hello,
I have bought a linux vps from ovh . The VPS has 2 vCore , 2 GB RAM & 64-BIT openvz Virtualization . I have installed ubuntu server 12 64bit on this vps . I want to run windows applications so I installed wine , but I encounter errors when trying to that . When I type winecfg or type wine name.exe in terminal I get this error : 

sometimes : wine: socket : Cannot allocate memory

or : 
err:wineboot:start_services_process Couldn't start services.exe: error 4 p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory err:winecfg:WinMain failed to restart 64-bit L"C:\\windows\\system32\\winecfg.exe", err 4 Application tried to create a window, but no driver could be loaded. The explorer process failed to start.


I've searched the net for hours but couldn't find any solution . So how can I deal with this issue , and thanks in advance

---

### Post by TheFu on 2015-03-26
Why not get a Windows VPS if you want to mainly run Windows programs?

Under WINE, most applications have extremely specific setup requirements. Find those for your apps at [https://appdb.winehq.org/](https://appdb.winehq.org/) . Every Windows app setup is different, so you'll need to post the exact name, version, subversion of the app here to get any help. If they are video-heavy apps, forget the VPS.

Oh - and trying to run 32-bit Windows on a 64-bit Linux has been known to cause complexities. Do you have the 32bit Linux core libraries installed?  I don't use WINE much anymore, but I recall there was some issue with WINE on 64-bit Linux.

---

### Post by slayer6662 on 2015-03-26
> **TheFu said:**
> Why not get a Windows VPS if you want to mainly run Windows programs?

Under WINE, most applications have extremely specific setup requirements. Find those for your apps at [https://appdb.winehq.org/](https://appdb.winehq.org/) . Every Windows app setup is different, so you'll need to post the exact name, version, subversion of the app here to get any help. If they are video-heavy apps, forget the VPS.

Oh - and trying to run 32-bit Windows on a 64-bit Linux has been known to cause complexities. Do you have the 32bit Linux core libraries installed?  I don't use WINE much anymore, but I recall there was some issue with WINE on 64-bit Linux.

As for rating of the application I want to use is "GOLDEN" but the problem that WINE doesn't work (winecfg for example) . I can install another version than ubuntu 64bit . I'll consider that . Thanks very much

---

### Post by TheFu on 2015-03-26
I don't see "GOLDEN" as an app name in the DB.

Anyway, try reinstalling wine and get the latest winetricks, then follow the setup instructions for the app in the appdb. Applications with heavy video or audio requirements may not work.  For example, I was able to get videoredo to install, but running it was next to useless over the network. It may work if I sat behind the directly connected mouse, but where I installed it was a KVM VM to a headless machine.

---

