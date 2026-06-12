---
title: "Heroes of Might and Magic 3 on Wine"
date: 2014-03-04
forum: Wine
---

### Post by riffeth on 2014-03-04
Hello guys,

I am extremely new to Ubuntu, been using it for a couple years but I'm not too versed on the technical side at all.
I've tried to install games on Vine a couple times but never got anything to work properly, so I always kept Win7 on dual boot to switch over for gaming.

Now I've decided I want to play Heroes of Might and Magic 3 again. This is what I did:
I have Wine and Winetricks installed.
I got the GOG.com version of HOMM3.
I executed the install.exe file. Installation with Wine went fine.
I got the widescreen HD patch ([https://sites.google.com/site/heroes3hd/](https://sites.google.com/site/heroes3hd/))

I started the patch - a window appears. I hit Launch. I get a black screen and I see the HOMM3 cursor - but Wine freezes and must be forcefully terminated. I am using Ubuntu 12.04.

Can anyone give me a hint on what to do? I really don't have any idea.

---

### Post by Jake_Paine on 2014-03-04
Have you tried launching the game via the terminal?

```
wine game.exe
```

Will give you output so should help diagnose better!

Good ratings on WineHQ straight out of the box so maybe you can post back some output?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=24425](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24425)

---

### Post by riffeth on 2014-03-04
Hello Jake!

I've done as you've said and started the HD Launcher via the terminal, then started HOMM3 via the launcher. This is the output in the terminal:

fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f700,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f700,0x00000000), stub!
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1

---

### Post by Jake_Paine on 2014-03-04
Hi riffeth! :)

Try un-checking 'allow the window manager to control windows' option in winecfg. Off the top of my head it's under the graphics tab.

Failing that have you tried running it within a virtual desktop in wine? This can be enabled as above.

---

### Post by riffeth on 2014-03-04
Hello Jake, and again thanks for your answer.

I've tried turning off and on both the virtual desktop and the "allow the window manager to control windows" option, but unfortunately to no avail.

---

### Post by AbtZ on 2014-03-04
I'm sorry to hear about your problems. I installed HOMM3 for my girlfriend to play a couple of years ago, with the HD patch, and as far as I can remember it worked without a problem. In fact, it worked a lot better than the Linux version, which I couldn't even get to run.

I was using the CDROM version of the game, however. There might be something different with the GOG version. I would suggest you get an older copy via, ahem, *alternative* channels, and see if it works better for you.

---

### Post by Jake_Paine on 2014-03-04
Hmm have you tried the latest version of Wine from their PPA?

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

Edit: AbtZ might have the best soulution there! Though apparently the GOG version works fine on the WineHQ

---

### Post by oldrocker99 on 2014-03-04
PlayOnlinux has a script specifically for the GOG.com version of HOMM3, and it works like a champ for me.

---

### Post by mastablasta on 2014-03-05
I too would like to propose Play on linux in this case. Play on linux is a GUI frontend for wine and often comes with various scripts and such to help you install and setup the programs. additionally you can select Wine version and install using for exampel older version if game works better in the older version.

---

### Post by sffvba[e0rt on 2014-03-05
*Thread moved to **Wine**.*

---

### Post by riffeth on 2014-03-06
Oh my god, thank you for directing me towards PlayOnLinux, this program is incredible! It works like a charm! And it's available for almost ALL of my favorite childhood games (Fallout, Deus Ex, Diablo II, Black and White, Dungeon Keeper, Broken Sword, Sam and Max, Simon the Sorcerer).

Absolutely fantastic. Sorry that it took me so long to reply, but as soon as it worked, I was consumed by Erathia and have not left it since. I need to go to sleep, badly. Thank y'all.

---

### Post by oldrocker99 on 2014-03-14
Glad to have been of some small help; the Ubuntu community is here just for that reason. One day, you'll be able to answer someone else's question. Pay it forward!

---

