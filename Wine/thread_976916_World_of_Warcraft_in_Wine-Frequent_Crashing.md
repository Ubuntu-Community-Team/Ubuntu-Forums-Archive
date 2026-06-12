---
title: "World of Warcraft in Wine-Frequent Crashing?"
date: 2008-11-09
forum: Wine
---

### Post by evilwombat on 2008-11-09
Okay, so after a pretty long week without WoW, I got it up and running with the steps from the Ubuntu site. It runs very well, but tonight when I went into kara, it started crashing. Its crashed about 5 times now, is there anything I can do?
I'm usually turning or just walking and it will crash.
Are there any special ways that you run it that let you go into raids without crashing?
It did not do this in windows, I'm running this in Intrepid Ibex.

---

### Post by mavicus on 2008-12-02
I am also having frequent Wow crashing in wine on Intrepid. Happens at least hourly, usually more often.
The crash is not instantaneous, it begins with some type of video corruption that resembles clipping. Odd lines/polygons are drawn from the center of the screen to the edges, and I am able to play for another 5 seconds or so before freezing. Just enough time to type "crashing" in chat.

Also, more rarely, I will respawn at the graveyard as a ghost but the screen will be completely black except for the HUD. Restarting the game fixes this but not every restart. Sometimes I log back in with a black screen and must restart again.

I have an nVidia 8800 GT and have tried both 177 and 173 version drivers. I have also tried various versions of wine: 1.1.9, 1.1.8, 1.1.7, 1.1.5, and 1.0.1 which is the version I used before I switched to Intrepid from Gutsy.

I have not copied the error msg generated, but will do so on next crash and post here.

---

### Post by mavicus on 2008-12-02
Error given by Wow is:

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	Z:\home\administrator\World of Warcraft\c_drive\Program Files\World of Warcraft\wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0023:7E1DE0E0

The instruction at "0x7E1DE0E0" referenced memory at "0x786EB4E0".
The memory could not be "read".

---

### Post by mavicus on 2008-12-03
I found this post:

[http://ubuntuforums.org/showthread.php?t=579378]("http://ubuntuforums.org/showthread.php?t=579378")


Which contained a registry tweak that fixed my problem.

Here is the registry portion of that post, reiterated for convenience.

> Almost mandatory reg tweak
This is a simple registry edit for Wine. For some it will dramatically increase the framerate in-game, for others it will fix graphical glitches, but for a few it will make WoW run worse or even crash. Even so it's always worth a try because you can always just delete it again after you try it. No harm done.

Open a terminal window, type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

Notice: the guide below is case sensitive!

1. Find this key HKEY_CURRENT_USER\Software\Wine\
2. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
3. Right-click on the wine folder and select [NEW][KEY]
4. Replace the text New Key #1 with OpenGL
5. Right-click in the right hand pane and select [NEW] then [String Value]
6. Replace New Value #1 with DisabledExtensions
7. Then double click anywhere on the line, a dialog box will open.
8. In the value field type GL_ARB_vertex_buffer_object

---

### Post by mavicus on 2008-12-11
After the previous tweak I experienced a long period with no crashing. The graphics glitch has not happened again. However in certain newly traveled zones (in wotlk expansion) I began experiencing even MORE frequent crashes that were seemingly fixed by forcing wine to run on a single processor of my quad core. This was done by adding the following to the beginning of the command line in my command line to start wow.

```
schedtool -a 0x2 -e
```

On my machine it now looks like:
```

schedtool -a 0x2 -e env WINEPREFIX="/home/administrator/.wine" wine "/home/administrator/World of Warcraft\wow.exe"
```

---

