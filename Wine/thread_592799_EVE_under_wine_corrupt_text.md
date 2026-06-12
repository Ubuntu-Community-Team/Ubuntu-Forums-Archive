---
title: "EVE under wine: corrupt text"
date: 2007-10-26
forum: Wine
---

### Post by NisseKun on 2007-10-26
Hello!
I've been trying to get EVE to work under Ubuntu 7.10 with WINE, and I have, it's running alot better than in win XP.
However, all text fields are corrupted and do not display correctly, which also means I have to copy paste my password to log on.

I've been searching around in the forums to find a soloution for this, but no one seems to have encountered the same problem.

I do the exact same steps as a friend of mine, for whom it works perfectly. Which is: 

Install newest WINE

opened winecfg for it to create the drive_c/windows directories

Added d3dfiles. (others seems to be fine without this, but my friend had to do it, ofc I've tried it w/o doing this too) 

Added arial.ttf to fonts folder, this is using the exact same file as my friend.


also tried adding regkeys manually, which was something I got from the EVE forums. didn't help.

please help me if you can ^^ I would really like to get EVE working under Ubuntu. Runs slow as hell on Vista.. :S

---

### Post by NisseKun on 2007-10-27
If anyone gets the same problem, then there is a temporary solution for this.
The problem seems to lie within wine .45 .46 .47 with gForce4 and gForce5, and also some ATI cards. 
to get this working, you need to overwrite your wined3d.dll.so with the .44 version of it. 
This should make it work. 

See [http://bugs.winehq.org/show_bug.cgi?id=9797](http://bugs.winehq.org/show_bug.cgi?id=9797)

---

### Post by Tuckwoor on 2007-11-04
Next question... How do I get hold of the .44 dll of just that file?

---

### Post by Vitamin-Carrot on 2007-11-04
i thought eve was available for linux

---

### Post by Perfect Storm on 2007-11-06
EVE-Online linux client is available.

---

### Post by Tuckwoor on 2007-11-08
Its cedega based and doesn't support ati officially (crashes my machine after short while). I still want to try getting wine working with it so still need to find out how to get hold of this .44 version of wined3d.dll.

[http://bugs.winehq.org/show_bug.cgi?id=9797]("http://bugs.winehq.org/show_bug.cgi?id=9797")

---

### Post by Tuckwoor on 2007-11-08
Just reading about a tool for regressing wine versions? Something called wine-git? Might be able to use that somehow to get the dll?

[http://wiki.winehq.org/GitWine]("http://wiki.winehq.org/GitWine")

(*Prays someone has the dll somewhere nice and easily downloaded*)

---

