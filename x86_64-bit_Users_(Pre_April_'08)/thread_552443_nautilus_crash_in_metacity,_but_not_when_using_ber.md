---
title: "nautilus crash in metacity, but not when using beryl"
date: 2007-09-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by mistlur1 on 2007-09-16
Hi

I recently ran into a problem with nautilus. It freezes and I have to force quit when opening a specific folder every time. Sometimes I can open the folder when using beryl if that's any help.
Right after nautilus crashing, it dumps a debug-file in my home directory with this information:
```
0x75fe50 2007/09/12 20:47:37.6919 (GLog): failed to load session from /home/christian/.nautilus/saved-session-7L8TYT
0x75fe50 2007/09/12 20:47:38.4970 (GLog): Can not caclulate _NET_NUMBER_OF_DESKTOPS
0x75fe50 2007/09/12 20:47:38.4972 (GLog): Can not calculate _NET_NUMBER_OF_DESKTOPS
0x75fe50 2007/09/12 20:47:38.4972 (GLog): Can not get _NET_WORKAREA
0x75fe50 2007/09/12 20:47:38.4972 (GLog): Can not determine workarea, guessing at layout
0x75fe50 2007/09/12 20:47:39.9263 (GLog): Can not get _NET_WORKAREA
0x75fe50 2007/09/12 20:47:39.9272 (GLog): Can not determine workarea, guessing at layout
0x75fe50 2007/09/12 21:01:15.3523 (GLog): nautilus_file_get_uri: assertion `NAUTILUS_IS_FILE (file)' failed
0x75fe50 2007/09/12 21:01:15.3523 (GLog): nautilus_file_get_mime_type: assertion `NAUTILUS_IS_FILE (file)' failed
0x75fe50 2007/09/12 21:01:15.3544 (USER): debug log dumped due to signal 11
```

System info:
Feisty x86_64 fresh install

Any help is appreciated

/mistlur

---

### Post by vinchi007 on 2008-02-14
I'm actually getting same problem the other way around.

When I use compiz, my windows border frames are not visible and file/edit menus show up the the Applications/Places/System menus should be - but window manager does not freeze.

Here is the dump file nautilus-debug-log.txt :
```

===== BEGIN MILESTONES =====
0x8177510 2008/02/14 03:18:29.4013 (GLog): Can not calculate _NET_NUMBER_OF_DESKTOPS
0x8177510 2008/02/14 03:18:29.4014 (GLog): Can not calculate _NET_NUMBER_OF_DESKTOPS
0x8177510 2008/02/14 03:18:29.4014 (GLog): Can not get _NET_WORKAREA
0x8177510 2008/02/14 03:18:29.4014 (GLog): Can not determine workarea, guessing at layout
0x8177510 2008/02/14 03:19:57.2500 (USER): debug log dumped due to signal 11
0x8177510 2008/02/14 03:19:57.2505 (USER): debug log dumped due to signal 11
0x8177510 2008/02/14 03:19:57.2506 (USER): debug log dumped due to signal 11
.......
0x8177510 2008/02/14 03:20:01.8033 (USER): debug log dumped due to signal 11
===== END MILESTONES =====

```

The only workable way I can make my Ubuntu 7.10 is by running "metacity --replace".

Any time I switch back to "compiz --replace" I get the same problem with windows frames.

Anyone got idea which meta file is currept here in home directory?

---

