---
title: "Latest update to wine screwed up steam!"
date: 2008-01-13
forum: Wine
---

### Post by EGJason on 2008-01-13
It took me forever to get steam to work previously.  There was an update this morning to wine, and now none of it works.  Any way to rollback this change please? :mad:

It took forever to set it up, words cannot express how pissed I am.

---

### Post by EGJason on 2008-01-13
A bit more detail, excuse my fury...

Steam starts up fine, but when I execute a game, like Team Fortress 2, it says:

Registry in use by another process, timeout expired.

Any help is appreciated...

---

### Post by Joga5000 on 2008-01-13
Same problem here. I actually was able to get into Day of Defeat: Source a minute ago, but after I closed it out and tried again, it gave me that error message (and the same with all my other Steam games).

---

### Post by twright on 2008-01-13
hi,

if you uninstall stream then winedoors ([apt:wine-doors]("apt:wine-doors")) has an automated installer for it :)

---

### Post by aoanla on 2008-01-13
Hi everyone.

No need to uninstall Wine or Steam or anything. This is a fairly common complaint that Steam produces, even in Windows (although patches to Steam have mostly fixed the issue in Windows). It's also not Wine's fault, and certainly not the fault of upgrading to the new Wine - the issue actually, at root, stems from the filesystem not quite syncing at the rate Steam thinks that it should be.

One thing that may help is typing:

chattr -R +S ~/.wine/drive_c/Program\ Files/Steam

This <i>is</i> mentioned in the AppDB write up for Steam, and has been for months! I do wish people would actually check the resources available to them before complaining that things have been broken...

---

### Post by EGJason on 2008-01-14
> **aoanla said:**
> Hi everyone.

No need to uninstall Wine or Steam or anything. This is a fairly common complaint that Steam produces, even in Windows (although patches to Steam have mostly fixed the issue in Windows). It's also not Wine's fault, and certainly not the fault of upgrading to the new Wine - the issue actually, at root, stems from the filesystem not quite syncing at the rate Steam thinks that it should be.

One thing that may help is typing:

chattr -R +S ~/.wine/drive_c/Program\ Files/Steam

This <i>is</i> mentioned in the AppDB write up for Steam, and has been for months! I do wish people would actually check the resources available to them before complaining that things have been broken...

I actually went through the sticky topics at the top and eventually found it lastnight at WineHQ.  It worked perfectly for me!  Thanks for the help!

---

### Post by EGJason on 2008-01-14
BTW, the correct syntax is as follows:

**sudo** chattr -R +S ~/.wine/drive_c/Program\ Files/**Valve/**Steam

---

### Post by jsym on 2008-02-08
Thanks for the discussion.

I had looked elsewhere and seen the **chattr** suggestion and tried it out, but it didn't work--Steam continued to tell me the registry was in use for every game except Portal.

EGJason's suggestion that perhaps the directory should be .../Valve/Steam gave me new hope.  It didn't work either (I don't have a .../Valve/Steam directory on my installation), but the implicit suggestion that the directory matters was inspiring.

I ran:

```
sudo chattr -R +S ~/.wine/drive_c/Program\ Files/
```

thereby setting the synchronous flag for *everything* in the directory and it worked like a charm.

Now, I recognize that there are other things in the directory besides Steam and Valve files, but since I only use wine for Steam I figured that there couldn't be much harm (I've figured stuff like this before and been burned, so fingers crossed).

---

