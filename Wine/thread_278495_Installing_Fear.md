---
title: "Installing Fear"
date: 2006-10-16
forum: Wine
---

### Post by EntenduEtOublie on 2006-10-16
So I feel like i post a lot of "Newbie" questions on here... but anyways I've always been into that game Fear, while I was playing online I saw that most of the servers were linux... and now I can get fear to install right even using Wine... can somebody help me?

---

### Post by Niko_Thien on 2006-10-16
At First: Yeah, a lot of Gamingservers are running under linux. But they are not running the game itself, but only a special server program. 

Referring to winehq.com F.E.A.R. it is not possible to run it using wine. But Cedega might be able to handle this game. But you'll have to pay for Cedega. There's also an entry of Cedega in the Wiki, you might want to check it out.

greetz Niko

---

### Post by K.Mandla on 2006-10-16
(I'm just going to shift this into the gaming area, where it will get better attention. ... ;) )

---

### Post by OffHand on 2006-10-16
> **EntenduEtOublie said:**
> So I feel like i post a lot of "Newbie" questions on here... but anyways I've always been into that game Fear, while I was playing online I saw that most of the servers were linux... and now I can get fear to install right even using Wine... can somebody help me?

FEAR is not playable on Linux... yet.

[http://transgaming.org/gamesdb/games/alphabrowse.mhtml?letter=F](http://transgaming.org/gamesdb/games/alphabrowse.mhtml?letter=F)

---

### Post by Polygon on 2006-10-17
it needs the .NET framework, and since wine does not support this the game will not run at all.

---

### Post by justin whitaker on 2006-10-17
I've got discs, and Cedega. Let me see if I can get this to run. Maybe there is a mono hack we can use.

---

### Post by Anonymo on 2008-10-02
Sorry to bring up an old thread, but has anyone got this to work yet?  I want to play F.E.A.R. combat but it doesn't work.

---

### Post by Anonymo on 2009-02-06
I was able to get F.E.A.R. Combat working on Arch Linux, getting low FPS at the moment, but overall still playable.  Going to try to run it on Ubuntu 8.10 later today.

Followed this guide:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5159](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5159)

```
Get wine 1.0.1/1.1.5 or later

1. Put native d3dx9_36.dll to your game or system32 folder
2. Apply 1.08 patch(if you don't want to enjoy all the game bugs...)
3. Install WMFADist.exe
4. Change
HKEY_CURRENT_USER\Software\Wine\Direct3D\OffscreenRenderingMode
to "fbo" to get better fps and Pixel Doubling/Soft Shadows working
```

---

