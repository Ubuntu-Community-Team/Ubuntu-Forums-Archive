---
title: "FAT32 &amp; Airport Extreme"
date: 2006-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by aethiolas on 2006-03-22
I just installed Breezy on 12in powerbook g4 and so far I'll be honest, its getting no use @ all.  I'm running a dual boot system and when I set up it I setup one partition as a shared and it formatted it fat32, too bad now it doesn't show up on OSX.  I've searched for posts here and I've found a couple other people with this exact question but no one seems to answer how to mount that partition, but they answer how to mount your hfs partition on linux.  I don't want to do that b/c it doens't have writing capabilites.  I've already got this partition, can anyone let me know how to make it work?  Also, are there any updates on whether the airport extreme will @ any future point be supported?  I would upgrade to a beta if it had support.  Where could I watch for updates also?

---

### Post by pitr on 2006-03-22
Airport Extreme are supported in Dapper but it requires some tinkering before it is working. I used a couple of different guides posted on the web and managed to get it working on my ibook g4. Try searching the forum and the web for airport extreme and I'm sure you will find some usefull information.

---

### Post by ssam on 2006-03-22
see [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions) and [https://wiki.ubuntu.com/AutomaticallyMountPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions) for mounting fat32 partitions.

---

### Post by aethiolas on 2006-03-22
Def excited about the airport working.  Gonna download the iso tonight for flight 5 and get to work on that.  As for the FAT32, maybe I wasn't very clear.  I can see the partition on linux no prob.  Mounts just perfectly, I can't read the paritition in OSX.  Any help?

---

### Post by ssam on 2006-03-22
gosh linux easier to use than mac os x these days :-)

does it show in disktool (or is it called disk utility) in /applications/utilities. maybe you can mount it with that.

---

### Post by aethiolas on 2006-03-24
I got Dapper installed and its showing my airport extreme, just haven't gotten time so far to got through all the setup.  I still don't understand this partition thing.  It doesn't show up in disk utility but it shows up fun in ubuntu and when I done the reinstall it said it was still fat32.  I dunno...strange but yes I will go with linux being easier than mac! :)

---

### Post by dombleu on 2006-03-24
I got that fat32 problem as well...

I might be wrong, but what I understamd of this is that OSX doesn't give a s**t about partitions that were created using something else than itself. I can see them in the disk utility, but i'm unable to do any operation on them. Not even a plain delete or format.

And since all my partitions but the OSX hfs+ one were formatted under linux... too bad for me i guess.

But i'm sure someone will pop out with a nice workaround...

A third party OSX app maybe?

---

### Post by aethiolas on 2006-03-24
My hopes are not getting up very high.   I have seen multiple threads on this and never a useful answer unfortunately.  Everyone seems to avoid how to get this working.  Never thought that I would prefer running windows dual boot to mac but it was a lto easier to set something like this up thats for sure.

---

