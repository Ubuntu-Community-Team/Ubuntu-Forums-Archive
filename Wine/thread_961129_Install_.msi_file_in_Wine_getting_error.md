---
title: "Install .msi file in Wine getting error"
date: 2008-10-28
forum: Wine
---

### Post by iampriteshdesai on 2008-10-28
I want to install Java kept in file system folder. How to run it in wine?
The file is J2SE Development Kit 5.0 Update 6.msi

If I use the msiexec trick I get the error.
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:msi:copy_package_to_temp failed to copy package L"J2SE"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"J2SE"
iampriteshdesai@iampriteshdesai-desktop:~$ wine msiexec /i J2SE Development Kit 5.0 Update 6.msi
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:msi:copy_package_to_temp failed to copy package L"J2SE"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"J2SE"
iampriteshdesai@iampriteshdesai-desktop:~$

---

### Post by YokoZar on 2008-10-28
The error you're getting (preloader: Warning: failed to reserve range 00000000-60000000) can be fixed by either following the instructions here:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

Or by upgrading to Ubuntu Intrepid (8.10), which includes a fix that works automatically.

---

### Post by YokoZar on 2008-10-28
oops if you're using the Wine beta packages this may still be a problem in Intrepid.

Hopefully I'll fix that tonight.

---

### Post by iampriteshdesai on 2008-10-28
I tried doing the first 2 commands
$ sudo gedit /etc/sysctl.conf

I get error saying command not found.
Also how do you guys know what to do for problems? I am new.

---

### Post by YokoZar on 2008-10-28
> **iampriteshdesai said:**
> I tried doing the first 2 commands
$ sudo gedit /etc/sysctl.conf

I get error saying command not found.
Also how do you guys know what to do for problems? I am new.

Are you using Kubuntu?  Try sudo kate /etc/sysctl.conf

---

### Post by iampriteshdesai on 2008-10-28
No.
I am using Ubuntu Hardy.

---

### Post by YokoZar on 2008-10-28
> **iampriteshdesai said:**
> No.
I am using Ubuntu Hardy.

Then you must have typed it wrong:

sudo gedit /etc/sysctl.conf

Don't include the $ sign by the way, that just means it's something you enter at a terminal.

---

### Post by iampriteshdesai on 2008-10-28
Cool another error:
err:msi:copy_package_to_temp failed to copy package L"J2SE"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"J2SE"
0

---

### Post by YokoZar on 2008-10-28
> **iampriteshdesai said:**
> Cool another error:
err:msi:copy_package_to_temp failed to copy package L"J2SE"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"J2SE"
0

Is your program on Wine's AppDB?

---

### Post by jacksaff on 2008-10-28
The name of the file you are trying to install has spaces in it. 

wine msiexec /i J2SE Development Kit 5.0 Update 6.msi

When you type your command into the terminal the shell thinks that you are listing separate files, ie. J2SE, Development, Kit, 5.0 and 6.msi. Of course none of these actually exist.
You need to put the file name in quotes or escape the spaces (put a \ before them) for the file name to be read properly.

---

### Post by iampriteshdesai on 2008-10-28
no it isn't in App Db

---

### Post by iampriteshdesai on 2008-10-28
I tried quotes too:
iampriteshdesai@iampriteshdesai-desktop:~$ wine msiexec "J2SE Development Kit 5.0 Update 6.msi"
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
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

---

### Post by jacksaff on 2008-10-30
Have you tried 
wine msiexec **/i** "J2SE Development Kit 5.0 Update 6.msi"

---

### Post by iampriteshdesai on 2008-10-30
Still get the same error.

---

### Post by jacksaff on 2008-10-30
Ok, we had two problems, one that you were entering an invalid command, and one the wine bug discussed on this page

[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

Follow the instructions there again about editing /etc/sysctl.conf and see how we go.

They really should write their java development kit in java! Then you wouldn't need wine...

---

