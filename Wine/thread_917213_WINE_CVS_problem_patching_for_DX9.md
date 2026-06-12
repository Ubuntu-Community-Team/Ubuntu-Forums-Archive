---
title: "WINE CVS problem patching for DX9"
date: 2008-09-11
forum: Wine
---

### Post by killguta on 2008-09-11
So I saw that my WoW is having poor frame rate and that TF2 is practicly unplayable with ~10fps with the lowest settings possible. I heard about this Wine with DX9 through CVS so I gave it a shot but I have this problem.

> WineCVS.sh - Progress(u) : Green is current

   0 = Uninstall
   1 = Cleanup
   2 = CVS checkout
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Checking out CVS ... May take a while

   CVS checkout done...
    Did you know Cedega is made by Transgaming?
    They have a binary version that works better than CVS,
    since it has better support for Installshield and copy
    protected games. Go to [www.transgaming.com](www.transgaming.com) for more info




WineCVS.sh - Progress(u) : Green is current

   0 = Uninstall
   1 = Cleanup
   2 = CVS checkout
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Configuring ...




--------- Error log - file /home/john/.WineCVS/sources/dx9wine/ErrorLog : ---------
patching file dlls/wined3d/drawprim.c
Hunk #1 FAILED at 1725.
Hunk #2 FAILED at 1784.
Hunk #3 FAILED at 1966.
3 out of 3 hunks FAILED -- saving rejects to file dlls/wined3d/drawprim.c.rej
patching file dlls/wined3d/stateblock.c
Hunk #1 FAILED at 64.
Hunk #2 FAILED at 379.
Hunk #3 FAILED at 402.
3 out of 3 hunks FAILED -- saving rejects to file dlls/wined3d/stateblock.c.rej
patching file dlls/wined3d/surface.c
Hunk #1 FAILED at 202.
Hunk #2 FAILED at 897.
2 out of 2 hunks FAILED -- saving rejects to file dlls/wined3d/surface.c.rej
patching file dlls/wined3d/swapchain.c
Hunk #1 succeeded at 29 with fuzz 2 (offset -24 lines).
Hunk #2 FAILED at 87.
Hunk #3 FAILED at 110.
Hunk #4 FAILED at 230.
Hunk #5 FAILED at 438.
4 out of 5 hunks FAILED -- saving rejects to file dlls/wined3d/swapchain.c.rej
patching file dlls/wined3d/utils.c
Hunk #1 succeeded at 26 with fuzz 1 (offset 2 lines).
Hunk #2 FAILED at 370.
Hunk #3 FAILED at 418.
Hunk #4 FAILED at 1668.
3 out of 4 hunks FAILED -- saving rejects to file dlls/wined3d/utils.c.rej
patching file dlls/wined3d/wined3d_private.h
Hunk #1 FAILED at 231.
Hunk #2 succeeded at 926 with fuzz 2 (offset 385 lines).
Hunk #3 FAILED at 1269.
Hunk #4 FAILED at 1303.
Hunk #5 succeeded at 2362 with fuzz 2 (offset 1215 lines).
Hunk #6 FAILED at 2384.
4 out of 6 hunks FAILED -- saving rejects to file dlls/wined3d/wined3d_private.h.rej
patching file include/wine/wined3d_interface.h
Hunk #1 FAILED at 282.
Hunk #2 FAILED at 383.
Hunk #3 FAILED at 413.
Hunk #4 FAILED at 514.
Hunk #5 FAILED at 1256.
Hunk #6 FAILED at 1278.
6 out of 6 hunks FAILED -- saving rejects to file include/wine/wined3d_interface.h.rej
patching file include/wine/wined3d_types.h
Hunk #1 FAILED at 427.
1 out of 1 hunk FAILED -- saving rejects to file include/wine/wined3d_types.h.rej

Patching FAILED
Try running the script with refresh:
WineCVS.sh refresh


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


john@john-desktop:~/Desktop$ WineCVS.sh refresh
bash: WineCVS.sh: command not found


As you can see the refresh command isn't working :( . Any ideas?

---

### Post by DoktorSeven on 2008-09-12
If you have a good computer and WoW/TF2 has low frame rates, it is likely you do not have proper 3d drivers for your video card, since plain Wine can run those games just fine.  What kind of video card do you have?  What does

```

glxinfo | grep direct

``` 

return?  (Should say "direct rendering: Yes")  Also note that onboard graphics cards in laptops and cheaper desktops by Intel will not work well at all thanks to a lack of proper 3d accelerated drivers for that chipset; you'll need something from ATi or nvidia to make it work properly.

In other words, don't bother with Wine CVS; the prepackaged Wine versions will work just fine, though you do need your system properly set up to use it with 3d games.

---

### Post by killguta on 2008-09-12
> **DoktorSeven said:**
> If you have a good computer and WoW/TF2 has low frame rates, it is likely you do not have proper 3d drivers for your video card, since plain Wine can run those games just fine.  What kind of video card do you have?  What does

```

glxinfo | grep direct

``` 

return?  (Should say "direct rendering: Yes")  Also note that onboard graphics cards in laptops and cheaper desktops by Intel will not work well at all thanks to a lack of proper 3d accelerated drivers for that chipset; you'll need something from ATi or nvidia to make it work properly.

In other words, don't bother with Wine CVS; the prepackaged Wine versions will work just fine, though you do need your system properly set up to use it with 3d games.

It says yes to the direct rendering, I have a decent tower 1GB ram, 8400GS, Dual Core 1,60GHz. With this system I get ~60fps all the time in TF2 with all settings high (no AA or stuff like that :( ) , but in linux I have ~20fps at lowest settings. I want it to become like this [http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/](http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/) . :(

---

### Post by aoanla on 2008-09-13
> **DoktorSeven said:**
> If you have a good computer and WoW/TF2 has low frame rates, it is likely you do not have proper 3d drivers for your video card, since plain Wine can run those games just fine.  

False.

It is a well-known fact that no Wine version runs TF2 at reasonable frame rates in DX9 mode with the native Wine DirectX dlls.
Apparently, some people have managed to get good performance by doing the "copying Microsoft directX dlls from an XP install" approach, and, of course, everyone can get TF2 to run happily in DX8.1 mode. 
This appears to be due to deficiencies in Wine's implementation of certain DX9 functions (probably shader related, judging from the "black box" issues that people using vanilla Wine also get on the game HUD in DX9 mode).

---

### Post by killguta on 2008-09-13
> **aoanla said:**
> False.

It is a well-known fact that no Wine version runs TF2 at reasonable frame rates in DX9 mode with the native Wine DirectX dlls.
Apparently, some people have managed to get good performance by doing the "copying Microsoft directX dlls from an XP install" approach, and, of course, everyone can get TF2 to run happily in DX8.1 mode. 
This appears to be due to deficiencies in Wine's implementation of certain DX9 functions (probably shader related, judging from the "black box" issues that people using vanilla Wine also get on the game HUD in DX9 mode).

Could you somehow give me a list of what to copy? :D

---

