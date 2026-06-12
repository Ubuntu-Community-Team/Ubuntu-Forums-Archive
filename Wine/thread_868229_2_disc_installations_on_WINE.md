---
title: "2 disc installations on WINE"
date: 2008-07-23
forum: Wine
---

### Post by Bnosidda on 2008-07-23
I need help with that, specific impossible creatures, a download guide would be nice

---

### Post by mad_golfer on 2008-07-23
Did you check the wine forums about it?

- Anthony
[Found some discounts on PC Magazines !!!]("http://www.magazinesusa.com/pc-magazine-subscription.cfm")

---

### Post by LinuxRocks713 on 2008-08-03
> **Bnosidda said:**
> I need help with that, specific impossible creatures, a download guide would be nice

Do the same procedure as you would do with Windows; Insert Disk 1 of your game and run the setup program. Then eject and insert Disk 2 of your game.

---

### Post by donotbugme on 2008-10-19
Alternatively, copy the contents of disc 1 to a new directory; then copy the contents of disc 2 to the same directory (select 'merge all' if prompted). 

You may need to change the permissions of the newly copied discs too: open a terminal, cd to the directory containing the contents of the discs and change the permissions thus:

```
sudo chmod -R 777 *
```

(The -R is recursive, so all the sub-folders and their contents will be changed too; the 777 sets RW permissions for owner, group and world, and the asterisk is a wild card which denotes all files in the selected directories).

Locate the installation file (probably something like setup.exe) and run it from Nautilus (right click and select open with Wine, or 'open with ...' and browse to Wine), or tell Wine to run the setup file from a terminal window by changing to the directory containing the setup.exe and type:

```
Wine setup
```

You won't be prompted for cd 2 because all the files are in the installation directory.

---

