---
title: "Problems in Vector NTI for wine"
date: 2013-05-07
forum: Wine
---

### Post by lhac on 2013-05-07
I'm trying to wine Vector NTI following [this instruction]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=27578"), but there are some problems:
1.this setup needs reboot, when I clicked the button and the setup killed. what should I do to continue?
2.the instruction indicate after setup crashes, should run rundll32, but there a err on my machine:
```

lhac@lhac-Inspiron-N5110:~$ wine rundll32 '/home/lhac/.wine/drive_c/Program Files/Informax Installations/ime.dll',InstallHelper2 '/home/lhac/.wine/drive_c/Program Files/Informax Installations/f_{9876E8C6-F8D7-4F43-84D3-B97D177F9466}.ini' 
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:process:SetProcessDEPPolicy (1): stub
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: [COLOR=#333333][FONT=Arial]cannot open shared object file: No such file or directory[/FONT][/COLOR]
err:rundll32:wWinMain Unable to find the entry point L"InstallHelper2" in L"/home/lhac/.wine/drive_c/Program Files/Informax Installations/ime.dll"
```

what should I do?

---

