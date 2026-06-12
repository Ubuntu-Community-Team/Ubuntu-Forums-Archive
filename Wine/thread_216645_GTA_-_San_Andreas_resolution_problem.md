---
title: "GTA - San Andreas resolution problem"
date: 2006-07-15
forum: Wine
---

### Post by Greeface on 2006-07-15
I tried installing GTA from the DVD, but it didn't work so I installed it on a Windows machine and copied it over.  When I try to open it with WINE it says that it "Cannot find 800x600x32 video mode."  How do I fix this?  CS runs fine under WINE, also.

Thanks a bunch

---

### Post by stimpack on 2006-07-15
There is a .set file usually in My Documents save game folder, this is the settings file and can be deleted to fix problems, how this translates to your Wine setup I dont know.

---

### Post by Greeface on 2006-07-16
Okay, i will look for this file and post back.  I am now using Cedega, and I still get the same problem

Thanks

---

### Post by Greeface on 2006-07-16
EDIT:  Woops, nevermind, what i said before in this post wouldn't work.

---

### Post by Greeface on 2006-07-17
> **stimpack said:**
> There is a .set file usually in My Documents save game folder, this is the settings file and can be deleted to fix problems, how this translates to your Wine setup I dont know.

Ah, I think you are getting close.  I have done some more reasearch, and I think that it's generated once you rn the game.  I ran it on my windows machine and changed the settings to 800x600x16 and placed the gta_sa.set file in the my documents folder.  Still doesn't work, but it doesn't bring up that error anymore, it just doesnt start.

EDIT: When I try to open it with straight WINE it still says "Cannot find 800x600x32 video mode."
EDIT 2: It does the same as above when I usse the command "cedega gta_sa.exe"

Hmm...

---

### Post by Greeface on 2006-07-21
Alright, I have 3 monitors so my xorg.conf file is tweaked.  I replaced the current xorg.conf file with the original for 1 monitor that I had backed up, but it still does the same thing.  So I am ruling out TwinView or Xinerama as the problem.  Any advice is greatly appreciated!  ~Greg

---

### Post by sha on 2007-10-16
> **Greeface said:**
> EDIT: When I try to open it with straight WINE it still says "Cannot find 800x600x32 video mode."
EDIT 2: It does the same as above when I usse the command "cedega gta_sa.exe"

Hmm...

My solution was running winecfg and setting a virtual wine desktop and "Allow the windows manager to control the windows" on the Graphics tab. Now, it works in windowed mode, but it works... :)

EDIT: No problem with TwinView and 2 cloned monitors.

---

