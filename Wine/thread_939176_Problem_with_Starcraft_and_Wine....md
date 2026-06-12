---
title: "Problem with Starcraft and Wine..."
date: 2008-10-05
forum: Wine
---

### Post by NCarlson on 2008-10-05
I must say this must be an extremely common, generic topic...but I have a problem with starcraft on Wine 1.1.5 recognizing the CD to run.  When I try to run starcraft I get an error that the CD is not in the drive, but the darn thing is IS in the drive.

Funny thing is, an older version of wine (0.9.59) worked almost perfectly.

What is the problem with this?  Open-source software is expected to get better each release.

Anyway, some suggestions appreciated.

---

### Post by dfreer on 2008-10-05
> **NCarlson said:**
> I must say this must be an extremely common, generic topic...but I have a problem with starcraft on Wine 1.1.5 recognizing the CD to run.  When I try to run starcraft I get an error that the CD is not in the drive, but the darn thing is IS in the drive.

Funny thing is, an older version of wine (0.9.59) worked almost perfectly.

What is the problem with this?  Open-source software is expected to get better each release.

Anyway, some suggestions appreciated.

Regressions happen. And it's a bit naive to think that open-source software is somehow immune to feature-creep, bugs and regressions.

Anyways, did you set up your winecfg correctly to map a drive letter to the CD drive? Are you trying just to play starcraft and it's not recognizing the CD, or are you trying to install it? If the former is the case, you can also install patch 1.15.2 I believe, which lets you play without a CD.

---

### Post by NCarlson on 2008-10-06
Patience, then, I must have.

I ran the command 'wine regedit.exe', pressed Ctrl + F, typed in the query 'starcraft' and found no registry entries related to starcraft.

In addition, I went into winecfg, to the drives tab, set the drives to automatically config.  This set the cd-rom drive to E:.
I even viewed the advanced settings of the drive and made sure it was set to cd-rom, not a hard drive or a floppy.  Perhaps this is because 1.1.5 is not a stable release.  Any more suggestions?

---

### Post by lehvrhon on 2008-10-07
try to view this maybe this could help, 
```
http://ubuntuforums.org/showthread.php?t=929576
```

or maybe you can check this site
```
http://appdb.winehq.org/objectManager.php?sClass=version&iId=149
```

---

### Post by dfreer on 2008-10-07
> **NCarlson said:**
> Patience, then, I must have.

I ran the command 'wine regedit.exe', pressed Ctrl + F, typed in the query 'starcraft' and found no registry entries related to starcraft.

In addition, I went into winecfg, to the drives tab, set the drives to automatically config.  This set the cd-rom drive to E:.
I even viewed the advanced settings of the drive and made sure it was set to cd-rom, not a hard drive or a floppy.  Perhaps this is because 1.1.5 is not a stable release.  Any more suggestions?

Still don't know if you are trying to install starcraft from scratch, or if you already have it installed and are just trying to play it.

If you are trying to install it, try creating a new wine directory like so:
```
WINEPREFIX="$HOME/.starcraft/" winecfg
```
Run autodetect on your drives, set up your sound. Then run the install:
```
WINEPREFIX-"$HOME/.starcraft/" wine setup.exe
```
See if it lets you install it that way.

If you already have it installed, I'd try reinstalling it, make sure to use a new wine directory when you do like above. If that's not an option, try upgrading starcraft to patch 1.15.2 like previously mentioned, reading the notes on how to copy the install.exe to your hard drive, so that you can play without CD.

It could be an issue with wine version 1.1.5, I only have wine 1.1.1 in Debian Lenny but the CD works fine for me. I do know that whenever I fiddle with my virtual CD drives with a starcraft already installed, it doesn't ever seem to recognize the CD in the drive even if I change things back. That's why I recommend reinstalling fresh.

---

### Post by jimmah6786 on 2008-10-14
Blizzard recently released a No CD update for StarCraft. Yes, this is official not some sort of illegal patch.

[http://www.blizzard.com/support/?id=msc01694p]("http://www.blizzard.com/support/?id=msc01694p")

Try it, the people over at winehq.com seem to like it.

Cheers!

---

### Post by NCarlson on 2008-10-15
Thanks for the help!  Yes, I am aware of blizzard's no cd patch.  I don't really want to use it, because in order to run starcraft w/o the cd it requires a 500-MB file copy and rename...which I'm trying to avoid.

@lehvrhon:  Thanks for the link to the thread.  I've made sure that /media/cdrom0 is set to type cd-rom.  I even checked that registry entry suggested in the thread, and set it to the right drive letter, but still no love.

@dfreer:  I will try your suggestion.

I've actually googled around a bit and found that this is a registered bug.  If nothing for me works, I'll just switch over to the latest stable version of wine.

---

