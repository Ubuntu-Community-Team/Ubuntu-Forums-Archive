---
title: "WoW won't save settings"
date: 2008-05-27
forum: Wine
---

### Post by RealEyez on 2008-05-27
Whenever I start WoW, I have to reconfigure my video and interface settings.
My World of Warcraft Folder and all the .exe's all have read and write permissions.

GeForce 8800 GT
AMD X64 2.5 GHz Processor
2 GB DDR2 SD RAM

Also, I am prompted to accept the Terms of Use and End User License Agreement upon starting the program. 

My config.wtf file looks like this:

SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET ffxDeath "0"
SET ffxGlow "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"

Any help would be appreciated.

---

### Post by RealEyez on 2008-05-28
Bump

---

### Post by MemoryDump on 2008-05-28
seems like a permission issue to me. 
can you open your config.wtf manually and still make changes to it?

my permissions are set to this:
ls -al /home/memdmp/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf 
-rw-r--r-- 1 memdmp memdmp 2764 2008-05-28 06:59 /home/memdmp/.wine/drive_c/Program Files/World of Warcraft/WTF/Config.wtf

---

### Post by RealEyez on 2008-05-28
I'm a Linux noob right now, do I just copy+paste that into Terminal?

Also, is there something that you can put into your config.wtf files that will remember your settings?

---

### Post by RealEyez on 2008-05-28
Bump again. It also plays the opening movie whenever opened.

---

### Post by MemoryDump on 2008-05-29
open up a terminal and type this:

```
ls -al ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf 
```

it should give you the details of that file.
What I'd try is backup Config.wtf to Config.wtf.bak:

```
cp ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf.bak
```

then delete your Config.wtf file:

```
del ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf
```

Start WoW like you normally do. This "should" re-create your Config.wtf for you. You might notice that your performance is sluggish as it's missing some variables to run properly under Wine.
Now exit WoW.
check your Config.wtf again to see if there's more lines in it now. If it does then it's saving your WoW settings now. I'd recommend adding the lines you have in your Config.wtf.bak to your new Config.wtf file.

try that and see what happens.

---

### Post by Zorael on 2008-05-29
I got this when I didn't have permissions to write to the config.wtf file as well as my own account directory (for ingame settings; keybinds, addons, etc). I chowned them properly and it worked.

I can't remember the directory structure so I can't give a proper terminal command for it. :>

---

### Post by Frippera on 2008-07-13
I had the same issue, all the rights where ok.

I found that a second "Config.wtf" file is created in the WTF directory (located in my Wow install dir).

I just backed up and then deleted my main "Config.wtf" and then everything was fine. 

I no longer had to: 
- watch the intro movie every time
- accept all the agreements every time
- change all my settings every time

Maybe this is a change to how Wow handle the "Config.wtf". Hope it helps someone.

---

### Post by Dpaulson on 2008-07-18
> **MemoryDump said:**
> open up a terminal and type this:

```
ls -al ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf 
```

it should give you the details of that file.
What I'd try is backup Config.wtf to Config.wtf.bak:

```
cp ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf.bak
```

then delete your Config.wtf file:

```
del ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf
```

Start WoW like you normally do. This "should" re-create your Config.wtf for you. You might notice that your performance is sluggish as it's missing some variables to run properly under Wine.
Now exit WoW.
check your Config.wtf again to see if there's more lines in it now. If it does then it's saving your WoW settings now. I'd recommend adding the lines you have in your Config.wtf.bak to your new Config.wtf file.

try that and see what happens.

thank you so much

---

### Post by traemccombs on 2011-07-03
Yeah, I nuked my WTF dir, and then started with a fresh Config.wtf  The problem is, it (WoW) starts up as 3360x1050 resolution, and there are NO other options.  So I have to manually go into the Config.wtf and put in:  SET gxResolution "1152x864"  

The above resolution is for me when I run it in Windowed mode.  (I'm one of those crazy Multiboxers and I have to have 2x WoW windows running)  :)

I've never had any issues like this until 4.2 just came out.  I've been playing WoW under WINE for what, 4+ years now?

:/

What I do now is, I have a file called:  good.wtf  and it has all the settings I want.  I simply copy  good.wtf -> Config.wtf before starting WoW and I'm able to play.

Kind of a pain in the ***, but it works.

All files are chowned to me.  And as I stated, I nuked the whole WTF dir and started over and well... the name of the DIR is appropriate.

---

