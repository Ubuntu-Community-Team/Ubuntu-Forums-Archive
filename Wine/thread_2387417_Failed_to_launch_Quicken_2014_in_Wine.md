---
title: "Failed to launch Quicken 2014 in Wine"
date: 2018-03-19
forum: Wine
---

### Post by shauking on 2018-03-19
After switched from Windows to ubuntu 16.04, I have to make Quicken 2014 Business & Home work in Wine. After the installation is done, I tried to start the Quicken with the command:

env WINEARCH=win32 WINEPREFIX=~/.wine32 wine ./qw.exe

I saw it launched a black window then crash after a few seconds. The error log shows like:

0039:err:wgl:X11DRV_wglCreateContextAttribsARB Context creation failed (error 1)
0039:fixme:win:EnumDisplayDevicesW ((null),0,0x7a3f904,0x00000000), stub!
0039:fixme:win:EnumDisplayDevicesW ((null),0,0x7a3fa10,0x00000000), stub!
0039:fixme:win:EnumDisplayDevicesW ((null),1,0x7a3fa10,0x00000000), stub!
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  149 ()
  Minor opcode of failed request:  4
  Value in failed request:  0x660253a
  Serial number of failed request:  26676
  Current serial number in output stream:  26676

The wine version is "winehq-stable 3.0". I'd appreciate if anyone can share your experience how to fix the above problem.

---

### Post by ajgreeny on 2018-03-19
If you look at the wine apps db at [https://appdb.winehq.org/objectManager.php?sClass=application&iId=107](https://appdb.winehq.org/objectManager.php?sClass=application&iId=107) you will unfortunately see that **Quicken 2014 Home & Business** is listed as Garbage, basically meaning that it is not worth trying.

Admittedly that was using wine v1.6.1, so your wine v. 3 may be better, but it is far too long since I tried any wine so I can't help further.

---

### Post by kc1di on 2018-03-19
You may have better luck using Playonlinux it's in the repository.  PlayonLinux (POL) allows you to try any wine version up to 3.x something and you can try them without them being directly installed on the machine.  good luck, but as I remember Quicken books would not work in wine.  
Best bet would be to install Virtualbox and install a windows version that  quicken will support.

---

### Post by shauking on 2018-03-20
I tried Playonlinux and no luck. I guess the "garbage" rating on Quicken has its reason. I can always run it in virutalbox or vmware player as workaround :)

---

