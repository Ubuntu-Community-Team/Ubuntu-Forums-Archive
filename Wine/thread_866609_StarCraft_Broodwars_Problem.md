---
title: "StarCraft Broodwars Problem"
date: 2008-07-21
forum: Wine
---

### Post by fp2007 on 2008-07-21
Ok here it goes, this is what i've done, using Cedega i've installed StarCraft the original game using the disk, I lost my Broodwars expansion except I have backup images of most my games (including that expansion), Now what im trying to do is play Broodwars mounted through AcetoneISO (I've already installed the Broodwars Expansion and get the choice from the menu), the original game plays fine (Since I have the disk mounted in the drive), but to play Broodwars it asks that that particular disk be in the drive as well,. Is there a way to mount the .iso as I did before, and edit a .cfg type file to direct Starcraft to the AcetoneISO mounted Broodwar Expansion Image? Perhaps confusing, but I was nearly there, something perhaps im doing wrong. Any help is appreciated.                  
                                 -Fp2oo7

---

### Post by eragon100 on 2008-07-22
Why not just burn the .ISO to an empty cd with brasero disc buring?

I "got" my starcraft and starcraft: broodwar a few days ago, as ISO's.

I burned them to cd-roms and they both play fine from there :wink:

---

### Post by dfreer on 2008-07-22
Hmmm, well if you install the latest patch you can play either of these games without the CD's, although it does take another 1 GB of space or so.

Beyond that, if you can mount the expansion ISO, you should be able to point Cedega to it as a virtual CD Drive (at least wine lets you do this, Cedega should to).

---

### Post by disturbedite on 2008-07-22
update to the lastest version of starcraft/bw. one of the things they did was remove the need to have the disc in to play.

same with diablo 2.

---

### Post by evets25 on 2008-07-22
You can actually mount an ISO in linux straight from the commandline, without any other programs. This is built right into the kernel, so it should be universal across most distros too. Ok, so, to mount an iso, first open up a commandline, cd to the directory that the iso is stored in, and then use the following command: 
```
sudo mount -o loop imagename.iso directory 
```

Just replace "imagename.iso" with the filename of the iso you are trying to mount, and replace "directory" with the name of the directory you wish to mount the iso to. So, for example, I run this command to mount the starcraft iso on my own computer:

```
sudo mount -o loop starcraft.iso /mnt/iso
```

By the way, you should make the directory to mount ISOs to in the /mnt directory. This is the proper place for it on a linux system, and this conforms to the UNIX standard way of doing things. The /mnt directory is there specifically for this kind of thing, so use it. :D

I use this command all the time when installing games, I find it quite helpful. 

If you're interested in learning more about the powerful mount command, run this from terminal: 
```
man mount
``` 
and then grab a drink and settle in for a nice long read. 

Enjoy.

---

### Post by fp2007 on 2008-07-22
thanks the command line mounting and having cedega point to that directory worked wonders, you guys are awesome, thanks again (And btw, my cd burner crapped out, picking up a new one friday, thats why I setup my question in this specific direction).

-Fp2007

---

### Post by MeTylerDurden on 2008-07-23
I never understood the directions for playing without the cd  ,  I did get the patch and read it.   Said to install a file from the cd and rename it. (which I couldn't figure out to do as my cd only installs the game and lets you play)

---

### Post by dfreer on 2008-07-23
> **MeTylerDurden said:**
> I never understood the directions for playing without the cd  ,  I did get the patch and read it.   Said to install a file from the cd and rename it. (which I couldn't figure out to do as my cd only installs the game and lets you play)

You don't install the file, you manually copy the file. Just browse the contents of your CD with nautilus and drag 'n' drop, then rename.

```
---------------------
- patch 1.15.2
---------------------
  Feature Changes

- StarCraft and StarCraft: BroodWar no longer require the CD while playing the game.  To play without the CD, please follow the following instructions:

Windows Users:
- Make sure you have "Hide extensions for known types" unchecked. To do this please use the following steps:
    - Click Start -> Programs -> Accessories -> Windows Explorer
    - Click on Tools -> Folder options (Windows Vista users may have to press the Alt key to see the tools option at the top of the window)
    - Click on the View Tab In the list, look for the "Hide extensions for known file types" option, and make sure that it is unchecked.
    - Click OK to save the changes.
    - Now you will need to copy some files from the Game CDs

- If you own only StarCraft, copy "INSTALL.EXE" from the StarCraft CD to your StarCraft folder and rename it to "StarCraft.mpq".

- If you own StarCraft: Brood War, copy "INSTALL.EXE" from the StarCraft: Brood War CD to your StarCraft folder and rename it to "BroodWar.mpq".  If you wish to play the StarCraft original missions then please copy and rename the install file from the original StarCraft CD as well, as listed directly above.
```

---

