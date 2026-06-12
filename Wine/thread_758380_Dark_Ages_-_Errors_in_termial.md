---
title: "Dark Ages - Errors in termial"
date: 2008-04-17
forum: Wine
---

### Post by Spoken on 2008-04-17
**MY UPDATED SITUATION IS ON THIS POST!!!**I

I'm trying to get one of my favorite windows games to work through wine.  when i try to run it through wine i get this error.  THE WINE DATABASE HAS NOTHING ABOUT THIS GAME!  IS THERE ANYTHING IN THE CODE SPECIFIALLY THAT TELLS ME WHATS WRONG?  I'm a noob.

NOTICE: These are the error messages i get with compiz fusion turned OFF!!

[Dark Ages (the game i want to get to work)]("http://www.darkages.com")


======================================
Here is the OUTPUT i get after i try to LAUNCH
======================================
```

fixme:win:EnumDisplayDevicesW ((null),0,0x32f290,0x00000000), stub!

```

A error box pops up and says:

----------------
LOD Error
----------------
::
main data file not found

---

### Post by Spoken on 2008-04-18
:confused:

---

### Post by happyhamster on 2008-04-19
> 
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\KRU\\Dark Ages\\thidchk.dll") not found
fixme:shell:DllCanUnloadNow stub
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\KRU\\Dark Ages\\Launch.dll") not found

The program needs a few native windows dll files: MFC42.DLL and MSVBVM60.DLL (and perhaps more). An easy way of getting those is using the winetricks script. Download the script from:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

- Navigate to where you downloaded the script:
cd /path/to/where/you/downloaded/the/script

- Run winetricks to install vcrun6 and vb6run (visual basic)::
sh winetricks vcrun6 vb6run

- Or just run winetricks to see all options:
sh winetricks

- Perhaps you'll need cabextract to get things to install, in that case:
sudo apt-get install cabextract

Good luck.

---

### Post by Spoken on 2008-04-20
kk, i did what you instructed me to do, and yet, i still have the same output in terminal.

---

### Post by happyhamster on 2008-04-20
> **Spoken said:**
> kk, i did what you instructed me to do, and yet, i still have the same output in terminal.
The exact same output? Both MFC42.DLL and MSVBVM60.DLL should be located in wine's system32 folder now.

- Try searching the filesystem.  First update the search-database:

sudo updatedb

- Then look for those files:

locate -i MFC42.DLL

locate -i MSVBVM60.DLL

- If it doesn't find anything, try running the script again. If you still have trouble, could you show the output of:

sh winetricks vcrun6 vb6run

---

### Post by Spoken on 2008-04-20
kk i will try this now.

---

### Post by Spoken on 2008-04-20
ok, both dll's are in the wine > system32 folder where they should be at.  here is the output im getting now

======================
OUTPUT DURING INSTALL
======================
```

fixme:spoolsv:serv_main (0 (nil))
fixme:shell:IShellLinkA_fnGetPath (0x179268): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:IShellLinkA_fnGetPath (0x179268): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
admin@dell:~$ fixme:shell:DllCanUnloadNow stub

```

==========================
OUTPUT WHEN LAUNCHING
==========================
```

fixme:spoolsv:serv_main (0 (nil))
err:module:import_dll Library SCSKAppLink.dll (which is needed by L"C:\\Program Files\\KRU\\Dark Ages\\Darkages.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\KRU\\Dark Ages\\Darkages.exe" failed, status c0000135

```

---

### Post by happyhamster on 2008-04-20
> fixme:spoolsv:serv_main (0 (nil))
err:module:import_dll Library SCSKAppLink.dll (which is needed by L"C:\\Program Files\\KRU\\Dark Ages\\Darkages.exe") not found
Ok, now it's complaining it can't find SCSKAppLink.dll. This is no regular windows dll file though, which means the file should have been installed when installing the game. Try searching for it on your system:

sudo updatedb

locate -i SCSKAppLink

- If it doesn't find anything, take a look at the installer you used: perhaps it has unpacked archives or such.

- Alternatively, search the web for a copy of that file and put it in the system32 folder.

- I did a quick search for info on that file and found this:
[http://www.planetda.net/index.php?showtopic=15827](http://www.planetda.net/index.php?showtopic=15827)

- Basically, what they're saying is that the file is part of keylogger-protection software. I would say, take your time to read the info on that page, it's pretty interesting I think. The page also offers an "empty" SCSKAppLink.dll, use at your own risk only.

---

### Post by Spoken on 2008-05-05
omg im so close to making this game work!!!

---

### Post by wirelessmonkey on 2008-05-05
It worked for me by default, though there were some warnings thrown. 
I've attached a screenshot with it running.

The game appears to be playing properly for me, though I can't honestly say I have ever played it.

This is my wine output:
rr:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f230,0x00000000), stub!
fixme:imm:ImmGetDefaultIMEWnd (0x30026 - (nil) 0x7f025270 ): semi-stub
fixme:imm:ImmSetConversionStatus (0x7f0f46e0, 1, 0): stub







I hope this helps.

---

