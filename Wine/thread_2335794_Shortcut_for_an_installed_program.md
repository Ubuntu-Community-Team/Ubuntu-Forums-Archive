---
title: "Shortcut for an installed program"
date: 2016-09-01
forum: Wine
---

### Post by prusakjakub on 2016-09-01
Hello,
I installed a program in wine and I have tried to create a shortcut which will launch it, but I haven't been successful. The command I want to run is:
```
WINEPREFIX=/home/kuba/.PlayOnLinux/wineprefix/SC4 wine C:\\Program\ Files\\Maxis\\SimCity\ 4\ Deluxe\\Apps\\SimCity\ 4.exe -intro:off -d:hardware -CPUCount:1 -CustomResolution:enabled -r1280x720x32 -w
```

In the .desktop file I have tried many different ways of running this command in the Exec field but I only see a brief terminal window flash and the program doesn't launch.
Here is the desktop file:
```
[Desktop Entry]

Name=SimCity 4 Deluxe
Exec=env WINEDEBUG="-all" WINEPREFIX="/home/kuba/.PlayOnLinux/wineprefix/SC" wine "C:\\Program Files\\Maxis\\SimCity 4 Deluxe\\Apps\\SimCity 4.exe" -intro:off -d:hardware -CPUCount:1 -CustomResolution:enabled -r1280x720x32 -w
Type=Application
StartupNotify=true
Terminal=true
Comment=SimCity 4 Deluxe
Icon=28C0_SimCity 4.0



```

Thanks for any help

---

### Post by prusakjakub on 2016-09-02
Nevermind I found a solution:

Exec=env WINEDEBUG="-all" WINEPREFIX="/home/kuba/.PlayOnLinux/wineprefix/SC4" wine C:\\\\windows\\\\command\\\\start.exe "C:\\Program Files\\Maxis\\SimCity 4 Deluxe\\Apps\\SimCity 4.exe" -intro:off -d:hardware -CPUCount:1 -CustomResolution:enabled -r1280x720x32 -w

---

