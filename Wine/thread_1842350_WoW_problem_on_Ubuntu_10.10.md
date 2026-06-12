---
title: "WoW problem on Ubuntu 10.10"
date: 2011-09-11
forum: Wine
---

### Post by Wildtrax on 2011-09-11
Hey guys I am trying to run WoW on Ubuntu and and since windows is completely screwed, I have tried to install WoW on this system.

So here's the deal I am running Ubuntu 10.10, and I currently have Wine 1.3 installed. I installed all the patches of WoW through the Wine Tricks installer and it will not launch. No matter what I try, it will not launch and I am at a lost to what to do about it now...

Could you help a gal out?

---

### Post by Perfect Storm on 2011-09-11
Try go to where WoW is installed and launch the game manually via the terminal.
Something like this:
```
wine <path>/wow.exe
```

---

### Post by lbeavisc on 2011-09-11
also you can try launching it by browsing to where it is installed and right clicking on it and selecting windows program launcher

---

### Post by Wildtrax on 2011-09-11
Okay so
 World of Warcraft is installing it is currently on the 1/2/3 screen setup/available/playable. So right now it is in the yellow bar... 

The blizzard background downloader is also up but it says "waiting" and nothing is happening..

Further more I Have Wine 1.2 installed with the package etc and it is working properly.

So here is the problem... and I am going to refer to this thread here

[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

I am trying to click "PLAY" and it crashes.  
I looked else where on the ubuntu forum and the person says to run this in the terminal

Winecfg  okay did that

Then they say to run this in the terminal

[SIZE=2]gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/wtf/Config.wtf
[/SIZE]
Okay got that too, so then they say to paste this code in there [SIZE=2]SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
[/SIZE]

Did that and then it tells you to SAVE, well I click on SAVE and it does not save there is an error message telling me this...

**Could not find the file /home/wildtrax/.wine/dri…f Warcraft/wtf/Config.wtf.**

Is that because I didn't finish downloading the game all the way? because it is still playable just wont run well I assume...


My last option is to go and buy the WoWCD and manually install them on WINDOWS... even though the drive is corrupt and the internet will not let me download anything it should work... any ideas guys?  I've been trying to get this to work all night long.

thanks so much for your help

---

### Post by Wildtrax on 2011-09-11
> **Artificial Intelligence said:**
> Try go to where WoW is installed and launch the game manually via the terminal.
Something like this:
```
wine <path>/wow.exe
```


no such directory =/  thanks though

---

### Post by Wildtrax on 2011-09-11
Omg! I tried the regedit tweak too, added the folder and everything and it still did not work! This is so frustrating!!! Dammit..

---

### Post by _d_ on 2011-09-11
What kind of outputs do you get if you execute Launcher.exe or WoW.exe via terminal with the wine command?

---

### Post by Tweak42 on 2011-09-12
What video hardware and drivers are you using?

When asking for help please try to follow tips in the sticky post [Things to include when asking for help]("http://ubuntuforums.org/showthread.php?t=885111") heading at the top of the wine forum.  It will save us and yourself much frustration and response time.

---

