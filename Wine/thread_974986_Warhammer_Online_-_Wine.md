---
title: "Warhammer Online - Wine"
date: 2008-11-08
forum: Wine
---

### Post by Zypher on 2008-11-08
I'm not one for GUI's but most of this should be easy to do anyways!

**Warhammer Online: Age of Reckoning** - Via Wine
First off the performance of the game isn't the greatest on Windows so don't be expecting too much on Linux. That being said, it isn't too hard to get it up and running on Linux via wine.

Let me go ahead and put this out there, I'm not going to teach anyone how to compile wine from source, if you can't do it then I apologise for wasting you're time.

**[1]** -- Grab Source
```
git clone git://source.winehq.org/git/wine.git wine
```

**[2]** -- Choose you're poison
You need to open up wine/dlls/d3d9/device.c

find:
```
TRACE("Returning %p %p\n", This, pCaps); 
```
add below:
```
pCaps->MaxVertexBlendMatrices=0x4; 
```

result:
```

     filter_caps(pCaps);

     TRACE("Returning %p %p\n", This, pCaps);
     pCaps->MaxVertexBlendMatrices=0x4;
     return hrc;
 }

```

**[3]** -- Compile Wine
Go ahead and compile it now, its such a small little fix :D
```
./configure
make depend && make
sudo make install
```

**[4]** -- winhttp.dll go get it
use google to find winhttp.dll and download
```
mv winhttp.dll  ~/.wine/drive_c/windows/system32/winhttp.dll
```

**[5]** -- teach winecfg 
run winecfg from either alt-f2 or from command line
-> switch to the libraries tab
-> choose winhttp.dll from the dropdown menu and add it to the list
-> choose edit on the right, set it to native
-> apply 
-> exit

**[6]** -- winetricks
download winetricks
```
wget  www.kegel.com/wine/winetricks
```
grant ability to execute
```
chmod +x winetricks
```
download / install directx9
```
./winetricks directx9
```

**[7]** -- getting the game
I had a readily available windows hard drive, I haven't tested any other means of installing the game.
```
 cp /media/windows/Games/Warhammer/* ~/wine/drive_c/Program\ Files/Warhammer/* 
```

**[8]** -- run this sucka
I don't know how you kids do it these days, but I just fired off
```
WINEDEBUG=-all wine warpatch.bin
```
from inside the warhammer directory, now the patcher looks terrible but it works. Now you may think the game has frozen or whatever when it sits at hand shacking it isn't frozen just let it sit for a bit. 

*misc
I haven't really figured out any way to improve performance yet, but I'll continue to work on it.

---

### Post by thirdoculus on 2008-11-08
> **Zypher said:**
> I'm not one for GUI's but most of this should be easy to do anyways!

**Warhammer Online: Age of Reckoning** - Via Wine
First off the performance of the game isn't the greatest on Windows so don't be expecting too much on Linux. That being said, it isn't too hard to get it up and running on Linux via wine.

Let me go ahead and put this out there, I'm not going to teach anyone how to compile wine from source, if you can't do it then I apologise for wasting you're time.

**[1]** -- Grab Source
```
git clone git://source.winehq.org/git/wine.git wine
```

**[2]** -- Choose you're poison
You need to open up wine/dlls/d3d9/device.c

find:
```
TRACE("Returning %p %p\n", This, pCaps); 
```
add below:
```
pCaps->MaxVertexBlendMatrices=0x4; 
```

result:
```

     filter_caps(pCaps);

     TRACE("Returning %p %p\n", This, pCaps);
     pCaps->MaxVertexBlendMatrices=0x4;
     return hrc;
 }

```

**[3]** -- Compile Wine
Go ahead and compile it now, its such a small little fix :D
```
./configure
make depend && make
sudo make install
```

**[4]** -- winhttp.dll go get it
use google to find winhttp.dll and download
```
mv winhttp.dll  ~/.wine/drive_c/windows/system32/winhttp.dll
```

**[5]** -- teach winecfg 
run winecfg from either alt-f2 or from command line
-> switch to the libraries tab
-> choose winhttp.dll from the dropdown menu and add it to the list
-> choose edit on the right, set it to native
-> apply 
-> exit

**[6]** -- winetricks
download winetricks
```
wget  www.kegel.com/wine/winetricks
```
grant ability to execute
```
chmod +x winetricks
```
download / install directx9
```
./winetricks directx9
```

**[7]** -- getting the game
I had a readily available windows hard drive, I haven't tested any other means of installing the game.
```
 cp /media/windows/Games/Warhammer/* ~/wine/drive_c/Program\ Files/Warhammer/* 
```

**[8]** -- run this sucka
I don't know how you kids do it these days, but I just fired off
```
WINEDEBUG=-all wine warpatch.bin
```
from inside the warhammer directory, now the patcher looks terrible but it works. Now you may think the game has frozen or whatever when it sits at hand shacking it isn't frozen just let it sit for a bit. 

*misc
I haven't really figured out any way to improve performance yet, but I'll continue to work on it.

Hey man, thanks! I just got Warhammer, and don't use or own a Windows copy; so I'll try this out.

---

### Post by nicesocks on 2009-02-05
I've picked up a copy of this game, and would love to play it.

I've followed everything as detailed above, but run into an issue with the patcher starts running.  It downloads, then disappears, never to return.  I've left this up for hours, no change...

If I close WINE I get an error.  It informs me that "it was unable to patch" and that I should either "check for other versions of the game running" or "ensure I have enough disk space."

I know I don't have another version running.  And I have more than enough disk space available for this game.  What can I do?

---

### Post by nicesocks on 2009-02-19
nothing on this, huh?

WoW gets all the love, WAR neglect.  /sigh

---

### Post by ajackson on 2009-02-20
WoW, because of it having a Mac version, is more OpenGL friendly. Warhammer isn't and one of the sticking points (the rendering of chars) looks fairly complex without resorting to an out and out hack which the wine devs try to avoid.

The fix posted does work but it is a dirty hack so doesn't stand any chance of being brought into wine officially.

---

### Post by nicesocks on 2009-02-21
thanks ajackson.  i figured that had something to do with it (the mac port, that is).

i think i'll just shelve this game for now, uninstall wine, and reinstall it for other applications.  mainly, sketchup.

hopefully wine will get the support for WAR in the future.  maybe i'll see it on the gold list and try again.

---

