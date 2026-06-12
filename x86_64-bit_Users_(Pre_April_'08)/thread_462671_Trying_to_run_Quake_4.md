---
title: "Trying to run Quake 4"
date: 2007-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tdraket on 2007-06-02
I've been trying to run Quake 4 on my laptop, but every time I try to load it I get:

Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
found interface lo - loopback
found interface eth0:avahi - 169.254.5.246/255.255.0.0
found interface eth1 - 192.168.1.13/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x6f346a2
Loaded pk4 /usr/local/games/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /usr/local/games/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /usr/local/games/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /usr/local/games/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /usr/local/games/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /usr/local/games/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /usr/local/games/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /usr/local/games/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /usr/local/games/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /usr/local/games/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /usr/local/games/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /usr/local/games/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Current search path:
/home/tdraket/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/usr/local/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/usr/local/games/quake4/q4base/zpak_french.pk4 (3462 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
/usr/local/games/quake4/q4base/pak012.pk4 (1081 files)
/usr/local/games/quake4/q4base/pak011.pk4 (5620 files)
/usr/local/games/quake4/q4base/pak010.pk4 (5539 files)
/usr/local/games/quake4/q4base/pak009.pk4 (1284 files)
/usr/local/games/quake4/q4base/pak008.pk4 (1289 files)
/usr/local/games/quake4/q4base/pak007.pk4 (1330 files)
/usr/local/games/quake4/q4base/pak006.pk4 (1343 files)
/usr/local/games/quake4/q4base/pak005.pk4 (1395 files)
/usr/local/games/quake4/q4base/pak004.pk4 (2249 files)
/usr/local/games/quake4/q4base/pak003.pk4 (1281 files)
/usr/local/games/quake4/q4base/pak002.pk4 (313 files)
/usr/local/games/quake4/q4base/pak001.pk4 (5837 files)
/usr/local/games/quake4/q4base/game100.pk4 (2 files)
/usr/local/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 59 loaded
244ms to load 1071k of material
79ms to load 43k of skin
158ms to load 716k of sound
4ms to load 1k of materialType
283ms to load 2078k of lipSync
67ms to load 105k of playback
1102ms to load 1665k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
632 strings read from strings/english_code.lang
1654 strings read from strings/english_guis.lang
5616 strings read from strings/english_lips.lang
6085 strings read from strings/english_maps.lang
632 strings read from strings/french_code.lang
1654 strings read from strings/french_guis.lang
5616 strings read from strings/french_lips.lang
6085 strings read from strings/french_maps.lang
632 strings read from strings/italian_code.lang
1654 strings read from strings/italian_guis.lang
5616 strings read from strings/italian_lips.lang
6085 strings read from strings/italian_maps.lang
632 strings read from strings/spanish_code.lang
1654 strings read from strings/spanish_guis.lang
5616 strings read from strings/spanish_lips.lang
6085 strings read from strings/spanish_maps.lang
Couldn't open journal files
execing default.cfg
"ALT" isn't a valid key
"CTRL" isn't a valid key
couldn't exec editor.cfg
couldn't exec Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
TODO: Sys_SetClipboardData
********************
ERROR: SDL_SetVideoMode failed: Couldn't find matching GLX visual
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: SDL_SetVideoMode failed: Couldn't find matching GLX visual


I have an ATI video card if that helps any.  Anyone know what I can do?

---

### Post by vinnn on 2007-06-03
This bit...

```
Loading GL driver 'libGL.so.1' through SDL
TODO: Sys_SetClipboardData
********************
ERROR: SDL_SetVideoMode failed: Couldn't find matching GLX visual
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: SDL_SetVideoMode failed: Couldn't find matching GLX visual
```

...is saying that there is no 3D acceleration found.

Which ATI graphics card to you have?
Have you installed the ATI binary driver or are you using the default open source driver?

Open up a terminal, What is the output of..
```
grep Driver /etc/X11/xorg.conf
```

---

### Post by Tdraket on 2007-06-03
It says
> tdraket@ShadowLover:~$ grep Driver /etc/X11/xorg.conf
        Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "ati"


I have an ATI RADEON Xpress1150 with 256MB HyperMemory.  It's what came in my laptop.

Since I haven't installed any drivers for my video card I'm assuming I have the default one.  Where would I go to get this driver?

---

### Post by vinnn on 2007-06-03
The...```
Driver "ati"
``` bit shows us that you're using the open source driver.
The open source driver does support 3D acceleration on 9x00 cards and older but not the newer GPUs, therefore you have to install ATI's non-free driver.
Now I'm not a 64bit user so I'm not sure if the following will work, if it doesn't you'll have to manually download the driver from [http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html") and follow their instructions.
But usually in Ubuntu Feisty it's as simple as opening up the '**Add/Remove...**' app...

Make sure '**All available applications**' is picked in the **Show** box & type **fglrx** in the search box.

Select to install the '**ATI Binary X.Org driver**' and click **OK**.

Type in your root password and watch it install.

Reboot. (You can get it going without a reboot but as you're new we won't go there)

If all is well, doing a... ```
grep Driver /etc/X11/xorg.conf | tail -1
``` in a terminal should show the **fglrx** driver instead of **ati**.

---

### Post by Tdraket on 2007-06-03
The ATI site doesn't have linux drivers for my card, and the install didn't work, probably because the site doesn't have drivers, thus it won't support it.  I did install it and restart, but it still says ati.

---

### Post by vinnn on 2007-06-04
Check to see if the fglrx driver is installed open up a terminal and type...```
sudo modprobe fglrx
```... and type in your root password if prompted.
If you get "FATAL: Module fglrx not found." then fglrx is not installed, bad luck, ATI sucks.

If you get no message then that's good, carry on with editing your xorg.conf file. But not before you back it up!
To do that, in your terminal do...
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.original
```
...and type in your root password if prompted.

Bring up the "Run Application" box in Gnome by hitting [Alt] + [F2].

Type in the following; ```
gksudo gedit /etc/X11/xorg.conf
``` and press the Enter key or click on the **Run** button.

Then in gedit change the line...
```
Driver "ati"
```
to...
```
Driver "fglrx"
```

**Make sure there are no typing errors**, then save the file.


Once you're sure it's correct, simply hit **[Ctrl] + [Alt] + [Backspace]** to restart the X server and return you to the login prompt (or you could reboot).

---

### Post by Tdraket on 2007-06-04
Before I try that could you tell me how to return it back to the original if it doesn't work.  I mean if it doesn't work then would it like not allow me to log on or something of that sort because it keeps trying to load the wrong drivers?  Then how would I put it back to normal?  Oh I typed in "sudo modprobe fglrx"  and I got "Not loading fglrx module; not used in /etc/X11/xorg.conf".  I'm not sure what to do with that.  That makes it sound like it's there.

---

### Post by vinnn on 2007-06-05
Sounds good to go...

Just in case, if the X server doesn't work after your change you can drop down to a terminal by hitting [Ctrl] + [Alt] + [F1 - F6]
Login and restore your backup xorg.conf (that you made earlier) as the main xorg.conf file...
```
cd /etc/X11
sudo cp -f xorg.original xorg.conf
sudo reboot
```
done

---

