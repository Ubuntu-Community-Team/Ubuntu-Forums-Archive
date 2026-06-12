---
title: "RPG Maker XP RTP"
date: 2008-11-28
forum: Wine
---

### Post by Izek on 2008-11-28
RPG Maker XP RTP 1.02 won't install, I tried it on Hardy and now Intrepid.

The following occurs when I try to run Setup.Exe in the resulting RPGXP_RTP102 dir...

```
ian@ian-desktop:~/Desktop/RPGXP_RTP102$ dir
InstMsiA.Exe  readme.txt	    Setup.Exe
InstMsiW.Exe  RTP_Standard_102.msi  Setup.Ini
ian@ian-desktop:~/Desktop/RPGXP_RTP102$ wine Setup.Exe
Usage:
  Install a product:
    msiexec {package|productcode} [property]
    msiexec /i {package|productcode} [property]
    msiexec /a package [property]
  Repair an installation:
    msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
  Uninstall a product:
    msiexec /x {package|productcode} [property]
  Advertise a product:
    msiexec /j[u|m] package [/t transform] [/g languageid]
    msiexec {u|m} package [/t transform] [/g languageid]
  Apply a patch:
    msiexec /p patchpackage [property]
    msiexec /p patchpackage /a package [property]
  Modifiers for above operations:
    msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
    msiexec /q{|n|b|r|f|n+|b+|b-}
  Register a module:
    msiexec /y module
  Unregister a module:
    msiexec /z module
  Display usage and copyright:
    msiexec {/h|/?}
NOTE: Product code on commandline unimplemented as of yet

Copyright 2004 Vincent B&#65533;ron
ian@ian-desktop:~/Desktop/RPGXP_RTP102$ msiexec Setup.Exe
Usage:
  Install a product:
    msiexec {package|productcode} [property]
    msiexec /i {package|productcode} [property]
    msiexec /a package [property]
  Repair an installation:
    msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
  Uninstall a product:
    msiexec /x {package|productcode} [property]
  Advertise a product:
    msiexec /j[u|m] package [/t transform] [/g languageid]
    msiexec {u|m} package [/t transform] [/g languageid]
  Apply a patch:
    msiexec /p patchpackage [property]
    msiexec /p patchpackage /a package [property]
  Modifiers for above operations:
    msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
    msiexec /q{|n|b|r|f|n+|b+|b-}
  Register a module:
    msiexec /y module
  Unregister a module:
    msiexec /z module
  Display usage and copyright:
    msiexec {/h|/?}
NOTE: Product code on commandline unimplemented as of yet

Copyright 2004 Vincent B&#65533;ron
ian@ian-desktop:~/Desktop/RPGXP_RTP102$ msiexec /a Setup.Exe
fixme:msi:MSI_OpenDatabaseW open failed r = 80030050 for L"C:\\windows\\temp\\msi1a8.tmp"
ian@ian-desktop:~/Desktop/RPGXP_RTP102$ msiexec /i Setup.Exe
fixme:msi:MSI_OpenDatabaseW open failed r = 80030050 for L"C:\\windows\\temp\\msi1ca.tmp"
```

---

### Post by cogadh on 2008-11-28
What are the contents of that Setuup.ini? Sometimes you can find info on what the setup is supposed to be doing in those and it may help point you in a direction of a solution.

---

### Post by Izek on 2008-11-29
> **cogadh said:**
> What are the contents of that Setuup.ini? Sometimes you can find info on what the setup is supposed to be doing in those and it may help point you in a direction of a solution.

It's as follows:
```
[MSILoader]
MSIFileName=RTP_Standard_102.msi
```

---

