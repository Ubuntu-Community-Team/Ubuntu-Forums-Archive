---
title: "Wine: Putting everything from my Windows XP CD into it"
date: 2011-09-24
forum: Wine
---

### Post by bigdee973 on 2011-09-24
hey. i tried installing itunes 7 and 10 but i keep getting errors, it said it may be some dependency issues.  so i just wanna install all the xp files.  everything on my cd for wine to use, that way i dont get anymore issues.  how do i do this?

---

### Post by oldos2er on 2011-09-24
Moved to Wine subforum.

---

### Post by Tweak42 on 2011-09-27
> **bigdee973 said:**
> hey. i tried installing itunes 7 and 10 but i keep getting errors, it said it may be some dependency issues.  so i just wanna install all the xp files.  everything on my cd for wine to use, that way i dont get anymore issues.  how do i do this?

Wine doesn't work that way.  Wine is a [compatibility layer]("http://wiki.winehq.org/FAQ#head-c9e6502ad636315e905d07f7e44594757a6738e3") so does not use actual windows system files, just acts as translator.

Unfortunately according to the wine appdb [iTunes]("http://appdb.winehq.org/appview.php?iAppId=1347") has a terrible track record running on wine.  There are several alternative programs to iTunes that run natively on linux, such as Rhythmbox and Banshee.  If you absolutely must have a functionally stable iTunes, look into running it inside a windows [virtual machine]("https://help.ubuntu.com/community/VirtualBox").

---

### Post by bigdee973 on 2011-09-28
> **Tweak42 said:**
> Wine doesn't work that way.  Wine is a [compatibility layer]("http://wiki.winehq.org/FAQ#head-c9e6502ad636315e905d07f7e44594757a6738e3") so does not use actual windows system files, just acts as translator.

Unfortunately according to the wine appdb [iTunes]("http://appdb.winehq.org/appview.php?iAppId=1347") has a terrible track record running on wine.  There are several alternative programs to iTunes that run natively on linux, such as Rhythmbox and Banshee.  If you absolutely must have a functionally stable iTunes, look into running it inside a windows [virtual machine]("https://help.ubuntu.com/community/VirtualBox").


THANKS TWEAK, but what i really really need is the ability to easily edit artists, albums etc.  itunes is very easy with this... say i have a bunch of songs that have unknown artist or songs that belong to one album...in itunes i highlight all of the songs rightclick and get info and just change artist and/or album and all the songs get the same artist/album etc.. this is so much faster and easier than changing each one individually.  unfortunately my harddrive is too small to install windows.  Plus i dont see banshee having this feature..seems to work on a one by one basis when changing artists

---

### Post by Tweak42 on 2011-09-28
> **bigdee973 said:**
> THANKS TWEAK, but what i really really need is the ability to easily edit artists, albums etc.  itunes is very easy with this... say i have a bunch of songs that have unknown artist or songs that belong to one album...in itunes i highlight all of the songs rightclick and get info and just change artist and/or album and all the songs get the same artist/album etc.. this is so much faster and easier than changing each one individually.  unfortunately my harddrive is too small to install windows.  Plus i dont see banshee having this feature..seems to work on a one by one basis when changing artists

Banshee does editing exact how you describe.  Select multiple tracks, right click - Edit Track Information (or hit E).  Mouseover the various buttons in the editor and a tooltip will tell you what they do.

Note: this is using Banshee 2.01, it might be different  in earlier versions.

---

### Post by bigdee973 on 2011-10-16
i upgraded to banshee 2.2 when i right click all i see is properties, when i click properties i see a tab that says basic detail but i cant edit it...wont let me type nothing in.  i tried pressing E when i select a track but it doesnt do nothing.
NOTE: im trying to change the metadata to my music files that are on my android

---

### Post by Tweak42 on 2011-10-17
> **bigdee973 said:**
> i upgraded to banshee 2.2 when i right click all i see is properties, when i click properties i see a tab that says basic detail but i cant edit it...wont let me type nothing in.  i tried pressing E when i select a track but it doesnt do nothing.
NOTE: im trying to change the metadata to my music files that are on my android

I'm not sure but it's possible that tracks cannot be edited on external devices. Does the same thing happen for tracks on your local hard drive?

Here's the context menu you should get on right click:
[IMG]http://banshee-media-player.2283330.n4.nabble.com/file/n2986247/Unbenannt.png[/IMG]

Here's the track editor.
[IMG]http://download.banshee-project.org/shots/1.4.1/track-editor-basic.png[/IMG]

---

