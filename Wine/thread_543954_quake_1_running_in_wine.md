---
title: "quake 1 running in wine?"
date: 2007-09-05
forum: Wine
---

### Post by stalefist on 2007-09-05
hey everyone. i'm trying to get quake 1 to install using wine, but i've gotten nowhere. the old install is a batch file (.bat) and each time i try to run it in wine it doesn't work. has anyone gotten quake 1 to run using ubuntu? btw, im using edgy 6.10 if that makes a difference.

---

### Post by shynko on 2007-09-05
im not sure if wine can install from .bat files I may be wrong though

---

### Post by DoktorSeven on 2007-09-05
If I recall, Q1 extractor is a DOS program. Try using DOSBox.

After that, you don't even need DOSBox or wine.  Go grab a native Quake source port such as DarkPlaces and place the data files you extracted in the resulting directory.

---

### Post by homerhomer on 2007-09-06
Forget wine

download ezquake!

or you can grab gzip file that I setup that is using the pak0 from shareware
let me know if it works
[http://www.mediafire.com/?9o1cmwkznnd](http://www.mediafire.com/?9o1cmwkznnd)

---

### Post by Dalem50 on 2009-04-27
DOSBox actually works for me.

1. Download and Install DOSBox via APT:

```
sudo apt-get install dosbox
```

2. Download Quake 1 from id Software's website:

[ftp://ftp.idsoftware.com/idstuff/quake/quake106.zip]("ftp://ftp.idsoftware.com/idstuff/quake/quake106.zip")

3. Extract to a directory (any)

4. Open DOSBox (In Gnome, on the menu go to Applications, Games, DOSBox Emulator), and mount the directory so you can access it:

```
mount c *directory*
C:
```

5. Once there, extract Quake (Leave everything default and press enter).

```
install.bat
```

6. Once the extraction is done, Quake should load!


I haven't managed to get sound to work. To load it again, repeat step 4 and do:

```
cd QUAKE_SW
QUAKE
```

Hope that helps! :)

---

### Post by asdfoo on 2009-04-27
Although Wine can run dos programs, it doesn't have as much support as dosbox, the support is mainly there to help with Windows applications that use DOS stuff.

---

### Post by CodyK46 on 2009-04-27
> **DoktorSeven said:**
> If I recall, Q1 extractor is a DOS program. Try using DOSBox.

After that, you don't even need DOSBox or wine.  Go grab a native Quake source port such as DarkPlaces and place the data files you extracted in the resulting directory.

DarkPlaces is a great tool. You can download a pack to make Quake look so much better.

---

