---
title: "LibSDL too old"
date: 2007-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Doctor J on 2007-09-22
I'm trying to compile a game [UFO:Alien Invasion].  The compile isn't succeeding because it needs libSDL > v1.2.10; i only have version 1.2.9 even though i have turned on all channels [backports, etc.].  This is on Dapper_64.  Am i likely to break anything by getting the package from: [http://packages.debian.org/stable/libs/libsdl1.2debian](http://packages.debian.org/stable/libs/libsdl1.2debian) ?  They have v1.2.11.  Other than that i would have to compile the source from [http://www.libsdl.org/download-1.2.php](http://www.libsdl.org/download-1.2.php) , which is v1.2.12.  What is the recommended way to handle this?

---

### Post by Sockerdrickan on 2007-09-22
Uninstall sdl then compile latest and sudo make install :)
edit: or change the way the game is compiled

---

### Post by Doctor J on 2007-09-24
Okeh, i've now got SDL and all its splitoffs compiled, and UFO compiled okay.  What i hadn't expected was that Synaptic removed 30 other packages that [directly or indirectly] depended upon SDL.  Is there a way to install a 'placeholder' for the manually installed SDL, or am i now doomed to have to manually compile all SDL needing software?

---

