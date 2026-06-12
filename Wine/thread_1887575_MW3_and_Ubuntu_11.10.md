---
title: "MW3 and Ubuntu 11.10"
date: 2011-11-27
forum: Wine
---

### Post by Macrotus on 2011-11-27
Hello

I just bought a new computer and I got Modern Warfare 3 for free. I'm not intrested to install Windows alongside Ubuntu but I hope that MW3 would work (especially the multiplayer) in Ubuntu. Has anyone tested it yet (the multiplayer)?

---

### Post by WienerWuerstel on 2011-11-27
It seems like Modern Warfare 3 works just [fine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=24738&iTestingId=67679") with the newest Wine Versions. 

I for myself tested Black Ops once when it was free for a Weekend and it worked great so it's not surprising that MW3 also plays with Wine.

---

### Post by Version Dependency on 2011-11-27
I got MW3 to work through the latest version of wine...but I had to do the following to make it work: [http://ubuntuforums.org/showpost.php?p=8313625&postcount=2](http://ubuntuforums.org/showpost.php?p=8313625&postcount=2)

---

### Post by Macrotus on 2011-11-28
What about the multiplayer? There's no information about that, only singleplayer.

---

### Post by Macrotus on 2011-11-28
I tried to install Steam, but it freezes when it's trying to create desktop icons.

---

### Post by Macrotus on 2011-11-29
Well, I installed XP so no problem.

---

### Post by frankyboy1211 on 2011-12-23
I have the problem that the system during installation with steam keeps asking for cd 2. Does anyone know how to solve this?

---

### Post by frankyboy1211 on 2011-12-26
ok, so I seemed to have been able to install the entire game, but now I am stuck with the fact that I cannot install directx because I have an ATI Radeon grafix card. Does anyone know how to solve this?

Thanx in advance, Frank

---

### Post by Corn Flake on 2012-01-08
> **frankyboy1211 said:**
> I have the problem that the system during installation with steam keeps asking for cd 2. Does anyone know how to solve this?

You can either unmount disc 1 and mount disc 2 in the same directory where disc 1 was mounted OR you can create a symlink from the disc 2 mount point to where the disc 1 mount point used to be.  In my Kubuntu box, when Steam asked for disc 2, I swapped the discs, mounted disc 2, and ran:
```
sudo ln -s /media/MW3_DVD2 /media/MW3_DVD1
```

---

