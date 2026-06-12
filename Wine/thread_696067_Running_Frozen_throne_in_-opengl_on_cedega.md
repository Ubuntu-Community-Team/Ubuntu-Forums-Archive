---
title: "Running Frozen throne in -opengl on cedega"
date: 2008-02-13
forum: Wine
---

### Post by dethsqurl86 on 2008-02-13
cedega war3.exe -opengl


i have tried this comman in terminal and this is my reply

/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
/home/m3phy/.cedega/.winex_ver/winex-6.0.5/winex/bin/wine: cannot find 'war3.exe'

im running gutsy can anyone help?

---

### Post by FrozenFox on 2008-02-13
The problem is likely just as it says: it cannot find warcraft 3 in the current directory, which I'm betting you are running that command from the home directory.

cd into the directory where warcraft 3 is installed first, and add a ./ before war3.exe and then that will work (ie cd "/path/to/warcraft3/folder/containing/war3.exe/lol/" then cedega ./war3exe -opengl. look around for the folder, its going to be somewhere in /home/m3phy/.cedega/ perhaps /home/m3phy/.cedega/Warcraft III/drive_c/Program Files/Warcraft III or something like that. 

I don't know why you're running it in cedega though, it's slow and wine 0.9.55 runs wc3 fine including battlenet, i just tested it an hour ago.

[http://www.mepislovers.org/forums/showthread.php?t=13883](http://www.mepislovers.org/forums/showthread.php?t=13883)

The .deb for wine 0.9.55 is at the end of the first post to dl and double click. It doesn't have a gui like cedega, but you're not doing stuff through a gui anyway, so i don't see what the problem would be. Wine-doors has a deb also, it can install wc3 from a graphical interface as well [http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3). After that, all you need to do is edit your start menu entry that is made for wc3 to add the -opengl part.

---

