---
title: "Problem with .msi files with Wine 0.9.48"
date: 2007-10-30
forum: Wine
---

### Post by rookshop on 2007-10-30
Hi, 

I installed the latest version of Wine from WineHQ. Since I wanted to install Steam, I downloaded the Steam client from steampowered.com. It is a .msi file.

I changed into the directory where the installer was downloaded and tried to open it with "wine msiexec"

But I get the following message:

[INDENT]buzzy@Buzzy-ThinkPad:~/Desktop$ wine msiexec SteamInstall.msi
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
[/INDENT]

What do I do?? :(

---

### Post by misfitpierce on 2007-10-30
you can google for steam.exe download and find older one to install.

---

### Post by rookshop on 2007-10-30
Will do it right now...

But the problem is still not solved. It is the latest version of Wine. I googled it and found that "wine msiexec" should do the trick.

But no luck for me..

---

### Post by cogadh on 2007-10-30
Don't use msiexec, just do "wine start SteamInstall.msi", that will install it correctly by calling msiexec and applying the appropriate flags. If you use msiexec directly, you need to specify the /i flag, so the command should be "wine msiexec /i SteamInstall.msi"

---

