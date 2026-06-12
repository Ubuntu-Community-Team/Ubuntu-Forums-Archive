---
title: "Has anyone figured out how to get PokerEdge to run under wine?"
date: 2008-07-04
forum: Wine
---

### Post by tdb1001 on 2008-07-04
I Downloaded the PokerEdge install from [www.poker-edge.com/download.php](www.poker-edge.com/download.php).
Ran it under wine and it successfully installed PokerEdge.
However when I attempt to run the app it fails completely. Running it in a terminal window gives the following dump:

[COLOR="RoyalBlue"]tim@tim-desktop:~$ env WINEPREFIX="/home/tim/.wine" wine "C:\Program Files\PE\iexplore.exe"
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
install the Windows version of Mono to run .NET executables
tim@tim-desktop:~$[/COLOR]

I do not know what this Mono app is. Has anyone managed to get PokerEdge to run under wine? Any help would be much appreciated!

Tim

---

### Post by brazemcee on 2008-07-04
Hi there.

I believe it has something to do with:
- NOT installing IE6
- NOT installing Mono

You should install Mono. I don't know exactly what it is but I guess it's like .net framework.
You can use PlayOnLinux or Wine-Doors to install it.

About IE6... Try installing it on the same wineprefix as Pokeredge. It might do the trick.

But don't expect much. The way I see it, it uses Internet Explorer and this is NOT good.:(

---

### Post by stinger30au on 2008-07-04
copy and paste this line to a shell prompt

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)


it will load a script that will help copy files from MS to make wine run different apps

now copy paste this

sh winetricks


scroll down the list of programs and put a tick in the box that mentions "mono"
mono is an open source version of the .net application for windows.
it is not perfect not will it run everything. but have a go

---

### Post by tdb1001 on 2008-07-05
OK, installed winetricks and using it installed mono. Now when I try running PokerEdge I get the following dump:

[COLOR="RoyalBlue"]tim@tim-desktop:~$ env WINEPREFIX="/home/tim/.wine" wine "C:\Program Files\PE\iexplore.exe"
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

** (C:\Program Files\PE\iexplore.exe:22): WARNING **: The following assembly referenced from C:\Program Files\PE\iexplore.exe could not be loaded:
     Assembly:   Infragistics.Win.UltraWinToolbars.v3.2    (assemblyref_index=5)
     Version:    3.2.20042.18
     Public Key: 7dd5c3163f2cd0cb
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (C:\Program Files\PE).


** (C:\Program Files\PE\iexplore.exe:22): WARNING **: Could not load file or assembly 'Infragistics.Win.UltraWinToolbars.v3.2, Version=3.2.20042.18, Culture=neutral, PublicKeyToken=7dd5c3163f2cd0cb' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'PokerEDGE.MainForm' from assembly 'iexplore, Version=4.3.8183.10262, Culture=neutral'.
tim@tim-desktop:~$ [/COLOR]

Any additional ideas would be much appreciated!

---

