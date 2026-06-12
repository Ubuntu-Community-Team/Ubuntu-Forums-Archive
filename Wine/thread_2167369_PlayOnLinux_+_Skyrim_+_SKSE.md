---
title: "PlayOnLinux + Skyrim + SKSE"
date: 2013-08-13
forum: Wine
---

### Post by Daliz on 2013-08-13
Hi all,

I have Skyrim running in Xubuntu 12.04 quite nicely, but since the UI in the game is absolutely horrible, I would like to use the SkyUI mod. It requires the Skyrim Script Extender (SKSE).

The game doesn't work with SKSE under Wine for some reason. I can see the menu but if I try to start a new game, it goes to the loading screen and nothing happens. If I try to load a game (played in Windows) it says that some content used in this save is not available. I have never used any other mods than SkyUI and TrueCompass, and I have those installed in the Wine setup.

I have tried Wine 1.5.20 and 1.7.0 (newest) under PlayOnLinux. I don't really know how can I see the Wine output when the game is started via the POL program.

Has anyone played Skyrim with SKSE under Wine? I haven't really found anything about SKSE in Wine.

Thanks

---

### Post by xREDEMPTIONx on 2013-08-13
Have you tried setting an override for d3d9.dll in the libraries tab in winecfg? Should be native,builtin.

---

### Post by texaswriter on 2013-08-14
I play Skyrim on Steam. I use the Steam Workshop to install mods, but I steer clear of SKSE or any mods requiring it. 

From what I understand, you have to use a different launcher to launch the game with SKSE.

---

### Post by Daliz on 2013-08-15
> **xREDEMPTIONx said:**
> Have you tried setting an override for d3d9.dll in the libraries tab in winecfg? Should be native,builtin.

No, but I'll try that once I have the time, thanks.

> **texaswriter said:**
> I play Skyrim on Steam. I use the Steam Workshop to install mods, but I steer clear of SKSE or any mods requiring it. 
From what I understand, you have to use a different launcher to launch the game with SKSE.

Yeah, I don't like messing with the SKSE myself either but the vanilla inventory screen is so crappy, especially when you have a lot of stuff in there. I haven't found any other UI mods.

SKSE has it's own launcher yes. I've tried to use it via the Playonlinux option "Run an exe file in this virtual drive" (the one where Skyrim is installed obviously).

---

### Post by texaswriter on 2013-08-15
> **Daliz said:**
> 
Yeah, I don't like messing with the SKSE myself either but the vanilla inventory screen is so crappy, especially when you have a lot of stuff in there. I haven't found any other UI mods.

SKSE has it's own launcher yes. I've tried to use it via the Playonlinux option "Run an exe file in this virtual drive" (the one where Skyrim is installed obviously).

I completely agree with you about the UI. The only UI that was ever done well was the XBOX version of Morrowind. Every other UI for a TES game has been absolutely atrocious. 

Yeah, sorry for stating the obvious, just had to make sure. 

This is the closest thing I can find to what you need. Double check with this post to see if you missed something: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=26626&iTestingId=73822](http://appdb.winehq.org/objectManager.php?sClass=version&iId=26626&iTestingId=73822)
 
Let us know how it goes.

---

### Post by loomy-man on 2013-08-19
I was having problems running Skyrim with SKSE (and no problems without it). It would load the game but trying to load a game or start a new one resulted in a 'hang' on the load screen when sounds played normally and the smoke animated but nothing was responsive.

What fixed it for me was changing into the Skyrim directory before running it from a terminal. ( cd .wine/drive_c/<path2Skyrim> && wine skse_loader.exe )

Hope this helps.

---

### Post by Daliz on 2013-08-19
> **loomy-man said:**
> I was having problems running Skyrim with SKSE (and no problems without it). It would load the game but trying to load a game or start a new one resulted in a 'hang' on the load screen when sounds played normally and the smoke animated but nothing was responsive.

What fixed it for me was changing into the Skyrim directory before running it from a terminal. ( cd .wine/drive_c/<path2Skyrim> && wine skse_loader.exe )

Hope this helps.

Yes! That's it! Thanks!

This is how you do it in PlayOnLinux, in case someones wondering:
1. Choose Skyrim, click Configure, click "Make a new shortcut from this virtual drive"
2. Browse to Skyrim folder and choose skse_loader.exe
3. When you have created the shortcut, choose it from the left side menu in the configuration window, and go to Miscellaneous tab
4. In the "Command to exec before running the program" box, type (replace yourusername with your username): cd /home/yourusername/.PlayOnLinux/wineprefix/Skyrim/drive_c/Program Files/Steam/SteamApps/common/Skyrim
5. Run the game from the shortcut you just created

---

