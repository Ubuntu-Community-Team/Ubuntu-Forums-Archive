---
title: "Counter-strike: source problem"
date: 2007-10-14
forum: Wine
---

### Post by Colro on 2007-10-14
So I've finally gotten CS:S downloaded and installed, but it's not wanting to open. HL1 mods work fine, though. When I open css, it seems to work fine at first, going to the game's loading screen. After about 5-10 seconds, though, it crashes me back to my desktop at a lower resolution and I have to ctrl+alt+backspace to fix it. Has anyone else ever had this problem? Is it fixable?

---

### Post by Colro on 2007-10-15
bump

---

### Post by Colro on 2007-10-15
bump

---

### Post by iNPUt- on 2007-10-15
Just play cs 1.6, its a much better game ;)

Its a sign..

---

### Post by dfreer on 2007-10-16
CS pretty much always starts in a lower resolution on first run, until you go in and change the resolution manually. The problem you have sounds like it could be fixed by running it in a virtual desktop (winecfg), changing the resolution, and then running it regularly.

---

### Post by Colro on 2007-10-16
> **dfreer said:**
> CS pretty much always starts in a lower resolution on first run, until you go in and change the resolution manually. The problem you have sounds like it could be fixed by running it in a virtual desktop (winecfg), changing the resolution, and then running it regularly.

Same crash in a virtual desktop =(

I'm trying to use this script to start it to pre-set the resolution, but no dice, still starts in 640x480 and crashes me back to my desktop without changing my resolution back.

DISPLAY=:0 WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen \
    -width 1024 -height 768 -applaunch 240 \
    -heapsize 512000 +map_background none "$@"

Edit: just tried to change the resolution in regedit -- no dice, still starts in 640x480 and crashes.

---

### Post by Colro on 2007-10-16
Someone in IRC suggested that I try around with different versions of WINE; with 0.9.43 my screen goes black and eventually I can hear my mouse going over the buttons -- but I can't see anything.

---

### Post by dfreer on 2007-10-16
Are your video card drivers installed correctly, and do other 3D games work correctly?

---

### Post by Colro on 2007-10-16
Yes and yes. Half-life, Counter-Strike, Natural Selection and Warcraft 3 all run flawlessly.

---

### Post by frodon on 2007-10-17
Try also the windows 98 mode in winecfg there's some cases where it solves this kind of issue.
Also be sure to have read thoroughly the following page :
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

---

### Post by coldguy on 2007-10-21
Using Win 98 mode Steam says it doesn't support your OS.

---

### Post by frodon on 2007-10-22
> **coldguy said:**
> Using Win 98 mode Steam says it doesn't support your OS.I know but you can ignore this warning, it won't prevent your game from running as expected.

---

### Post by Colro on 2007-10-22
> **frodon said:**
> I know but you can ignore this warning, it won't prevent your game from running as expected.

You can't ignore it, it refuses to open the game if it doesn't like your OS.

---

### Post by frodon on 2007-10-22
> **Colro said:**
> You can't ignore it, it refuses to open the game if it doesn't like your OS.It don't prevent to start the game for me and other users i've met on UF who use this option to solve crash issues so if it does for you maybe you have another problem.

---

### Post by berserker on 2007-10-22
To launch CS:S in Win98 mode try this:

Go to the "Applications" tab, "Add application" and drill down to the Steam folder and select "Steam.exe". Choose "Windows XP" as the version of Windows to run. Then "Add application" again and select "hl2.exe". Choose "Windows 98" as the version of Windows. Click OK and then launch the game again.

Essentially, you're running Steam.exe in XP mode to allow the game to launch and then hl2.exe in 98 mode to avoid the crashes.

Steam.exe is located in ~/.wine/drive_c/Program Files/Steam/ on my machine.
hl2.exe is located in ~/.wine/drive_c/Program Files/Steam/steamapps/[user_name]/counter-strike source/

---

### Post by stueyboy on 2008-01-25
Just a quickie. I had exactly the same issue at the start of this thread and will try the above fix. But can anyone let me know if this worked for them? I have exactly the same symptoms. HL, CS and other mods work fine but CSS and HL2 get to the graphics screen then crash back after 5 seconds.

Any info would really help as other than that I am well impressed with Wines ability to emulate Steam

---

### Post by Tim0miT on 2008-04-02
update your wine app, worked for me:guitar:

---

### Post by Ntweat on 2008-04-02
well i m able to run CS2 no problems but only in single player i want to play it in multiplayer mode... it asked for Gecko i installed now it connects to multiplayer but then it hangs i have to restat the xserver... any help?? i have even updated my wine

---

