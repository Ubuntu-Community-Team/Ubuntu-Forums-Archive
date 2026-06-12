---
title: "Garry's Mod Issue/DirectX 9?"
date: 2007-07-18
forum: Wine
---

### Post by BlahMan_of.Doom on 2007-07-18
:) I got DirectX 9 running. Thank you for all your help :)

And also, in wine, Garry's Mod 10 does not show up in the game list. I copied the steamapps/gcf file to the steam directory from my Windows partition, and it does not work. If I remove the file, it does not show up at all. It works perfectly fine in windows, so I don't know what's going wrong there. Thanks. This is the 1st priority issue, I can wait on the graphics problem a bit.

:popcorn: Thanks.

---

### Post by BlahMan_of.Doom on 2007-07-19
Anyone?

---

### Post by Hottshot3312 on 2007-07-21
bump?  I love Directx 9 too.

---

### Post by dfreer on 2007-07-21
there is a commandline argument for wine where you can specify which direct x level you want your specific app to run in, as always check wine appdb for questions about using wine:
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)
This is a link for Counter Strike Source, here's the relevent info:
>  All things going well, this game will work in current versions of wine (wine-0.9.15 and up) if you:

   1. Install steam and Counter Strike Source from the DVD or via the steam download.
   2. Select only "OSS" sound driver in winecfg (others will lag or won't work at all).
   3. Start Steam with the following command:

cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 240

Note: Your path might differ, depending on language and installation directory. This is default for English install.
Note2: Additional command line options go after -applaunch * not before. Ex: -applaunch 240 -dxlevel 80 -console
[B]
For better graphics quality you might want to use -dxlevel 90 command option and enable GLSL shaders via registry[/B] (save this to a "file.reg" then import with 'wine regedit file.reg'):

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"UseGLSL"="enabled"

For better performance use -dxlevel 80 or even 70 and the following game settings:

cl_drawmonitors 0
r_WaterDrawRefraction 0
r_WaterDrawReflection 0


Best thing to try with gary's mod would be to remove the .gcf and redownload it using steam, to make sure everything gets installed that needs to be (although I don't know if it requires anything more than the .gcf, there wasn't any information at appdb).

---

### Post by BlahMan_of.Doom on 2007-07-22
Garry's Mod doesn't even show up on the list at all, so I don't see how I can download it :\. And for the rare times that it does, it says that I'm not subscribed to Garry's Mod o.O

And I already got my DirectX9 Issue solved.

EDIT: You're almost at 1000 posts :P

---

### Post by BlahMan_of.Doom on 2007-07-23
Are all of my issues that I've had with Ubuntu unsolvable? I mean seriously..

---

### Post by dfreer on 2007-07-23
> **BlahMan_of.Doom said:**
> Are all of my issues that I've had with Ubuntu unsolvable? I mean seriously..

If you can wait a week or so, I'm planning on buying Garry's Mod 10 and I will be able to help you with your problem better.

---

### Post by cogadh on 2007-07-23
I'm not sure this is really an Ubuntu/Wine issue, it sounds like it might be a Steam issue. 

One question though, have you tried to do the "move Steam install" trick? You can copy your entire Steam installation from Windows into the Wine directory (make a backup copy of your original Steam install in Wine, just in case), then delete the ClientRegistry.blob file and start Steam. It should re-build the blob and after doing a scan of all installed games, they should work normally (if they already work with Wine, of course).

---

### Post by BlahMan_of.Doom on 2007-07-29
I copied the folder from my Windoze install, but I didn't delete the ClientRegistry.BLOB.

I'll try that in a second. Thanks.

---

### Post by dfreer on 2007-07-30
Getting back to you, I purchased GM10 from steam on my windows account, installed and ran it fine. I then went to my ubuntu AMD64 and installed wine/steam fresh, and Garry's Mod 10 appears in my game list. It is currently downloading, so I'd have to get back to you on whether it runs or not (I don't see any reason why it wouldn't).

---

### Post by BlahMan_of.Doom on 2007-07-30
Okay..maybe the steam update fixed it. Thanks.

---

### Post by BlahMan_of.Doom on 2007-08-02
I see it now in the Steam games list. Cool. Thanks...I think the Wine update fixed it.

EDIT: Oh nevermind. It still says "You're not subscribed to garrysmod."

---

### Post by robindegen on 2008-06-04
I can confirm it works fine. I couldn't run the msi installer over the new wine for some reason so i installed on windows and copied the files over to my wine program files. Garry's mod shows up in the list, downloaded fine and it runs.

---

### Post by Sammi on 2008-06-04
> **robindegen said:**
> I can confirm it works fine. I couldn't run the msi installer over the new wine for some reason so i installed on windows and copied the files over to my wine program files. Garry's mod shows up in the list, downloaded fine and it runs.
Great.

It's also got a gold rating on appdb.winehq.org, so it should really be fine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10990](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10990)

---

### Post by cogadh on 2008-06-05
More necromancing... where's a mod when you need 'em?

---

### Post by Kekk0 on 2008-06-06
> **dfreer said:**
> All things going well, this game will work in current versions of wine (wine-0.9.15 and up) if you:

1. Install steam and Counter Strike Source from the DVD or via the steam download.
2. Select only "OSS" sound driver in winecfg (others will lag or won't work at all).
3. Start Steam with the following command:

cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 240

Note: Your path might differ, depending on language and installation directory. This is default for English install.
Note2: Additional command line options go after -applaunch * not before. Ex: -applaunch 240 -dxlevel 80 -console

For better graphics quality you might want to use -dxlevel 90 command option and enable GLSL shaders via registry (save this to a "file.reg" then import with 'wine regedit file.reg'):

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"UseGLSL"="enabled"

For better performance use -dxlevel 80 or even 70 and the following game settings:

cl_drawmonitors 0
r_WaterDrawRefraction 0
r_WaterDrawReflection 0 
Thank you so much! :D

---

