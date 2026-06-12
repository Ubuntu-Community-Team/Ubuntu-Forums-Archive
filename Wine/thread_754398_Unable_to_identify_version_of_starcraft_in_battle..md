---
title: "Unable to identify version of starcraft in battle.net"
date: 2008-04-13
forum: Wine
---

### Post by Amranu on 2008-04-13
Sometimes I can access battle.net and log on and everything, but more often than not I am told that my version cannot be identified and I may have a virus or whatnot.

I have used a windows partition install, installed, and reinstalled in wine, and even imported the registry from my windows partition to wine. None have fixed it.

---

### Post by rocky5051 on 2008-04-13
Firstly, look at this to see if there is anything you may have done wrong or missed.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149)

Also, it says on the AppDB that there was a patch made that would allow it to play online without a No-CD crack. (I don't own this game, but it has been to my experience that any game run with a No-CD crack will have network problems because it appears to the server as an old or unsupported version of the game).

---

### Post by Kilz on 2008-04-13
No CD patches with Blizzard games a a bad idea. One thing that helps with Blizzard Games is setting up a node link.
```

It helps to add a device node symlink, so do the following. If your cd-rom drive letter in winecfg is d: and the corresponding device node to your mount point is /dev/hdc then run the following command:
$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
Note, you *must* have two colons! You can tell what your device node is in /etc/fstab or viewing your boot-log.
```

Also run wine in win2k mode.

---

### Post by tym2die on 2009-04-17
go to wine configuration/graphics/uncheck allow the window manager to control the windows. then update game

---

### Post by CharmyBee on 2009-04-17
The version number can be viewed in the bottom right corner in the main menu. If it isn't there, then it's the initial version. Patch up.

The latest official patch has no CD check.

---

### Post by FrozenFox on 2009-04-18
Unholy mother of thread resurrections, lol. The above two posts (and this :p) were made after a post from a *year* ago.

There probably aren't any legitimate (read: lots of malicious "patches" probably floating around) nocd patches for the latest versions for the reasons given in the post above this one.

I wouldn't have even bothered replying were it not for this being just a few posts down on p1. Let it die in peace! ;P

---

### Post by dhaus111 on 2009-09-17
Going to go ahead and disagree with ya amranu.  This problem is still alive and well.  A couple of years ago I was able to install and run battle net with SC, now that's not the case.  I'm up to date with the latest patch (confirmed in the bottom right of the initial window, 1.16.1 i think is what it is), still investigating options but would love to hear it if anybody knows what's causing this.

---

### Post by donkyhotay on 2009-09-18
I've never run into this problem and I play on B.net quite often. I always make certain that I'm up to date before connecting (don't patch over B.net) and don't use CD-cracks. Fortunately the most recent versions of starcraft have no-CD built into them and it works just fine.

---

### Post by Azrael3000 on 2009-11-02
The solution, at least for me, was to run winecfg and in the graphics tab unselect 'Allow the window manager to control the windows' et. voila. 
Apparently a problem with gnome or so.
Happy gaming

---

### Post by TheBuzzSaw on 2009-11-02
Also, the latest patches remove the need to have the CD. No one should be using cracks anyway. ;)

---

### Post by Jepic Phail on 2009-11-02
Don't you have to copy and paste install.exe from the CDs to your Starcraft directory and rename it StarCraft.mpq and BroodWar.mpq or something for no-CD?

EDIT: Battle.net is not working for me. I can't even get to the login page. :(

---

### Post by TheBuzzSaw on 2009-11-02
> **Jepic Phail said:**
> Don't you have to copy and paste install.exe from the CDs to your Starcraft directory and rename it StarCraft.mpq and BroodWar.mpq or something for no-CD?
The details are in the patch notes, but yes, something like that.

---

