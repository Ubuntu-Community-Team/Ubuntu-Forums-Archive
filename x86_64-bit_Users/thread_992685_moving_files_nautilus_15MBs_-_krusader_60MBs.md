---
title: "moving files: nautilus 15MB/s - krusader 60MB/s"
date: 2008-11-25
forum: x86 64-bit Users
---

### Post by nexxus07 on 2008-11-25
Hi,

I'm running ubuntu hardy desktop x64. I had some lager files (total ~500GB) to transfer. Nautilus would start moving files at 25MB/s and degrade to 13MB/s which seemed to slow for my 7200U/min Seagate harddrives. (I was coping from hd1 to hd2). Testing the drive's speed by creating a 1 GB testfile via dd from /dev/null revealed 100MB/s for hd1 and 180MB/s for hd2.

I then installed Krusader as an alternative filemanager under Gnome and repeated the procedure. To my surprise I'm at least getting now transfer speeds between 40-70 MB/s on the same drives!

Anyone else experienced these kind of slowdowns with nautilus? What do you think?

Cheers,
Thomas

---

### Post by cariboo on 2008-11-25
This problem has been around since Hardy was released, it is a little better in Intrepid, but still not good. I use mc to do a lot of administration and it works well for me. MC has a text based interface, but you can use a mouse with it. MC is available in the repositories and you can use the usualy ways to install it.

Jim

---

### Post by nexxus07 on 2008-11-26
After further testing and coping files with krusader and nautilus I'm not sure Krusader is a better solution for high file transfer speeds. I'm just copieng a 7 GB file (DVD image) from hd0 to hd1 at speeds around 5MB/s with Krusader. That's like a play street zone on what's supposed to be the autobahn!

I used MC before but it crashed badly on me when using with remote connections. I guess there is never the perfect solution but I might want to give it a try to see whether I can achieve higher speeds. 

Do you guys think this is only an issue when using graphical interfaces to copy files?

[Edit]
I just copied the same 7GB file accross my LAN in about 12 Minutes. Before the speed was about 5 MB/s which is around 40MBits transfer rate. My LAN is a 100MBit connection and I calculated 80MBit/s transfer rate for the 12 Minutes it took to transfer the file across the LAN. 

If I'm doing the calculation right (with rounding and 3 Hoegaarden) I copied the same file faster across the LAN than internally between hd0 and hd1!!!

---

### Post by vanadium on 2008-11-26
How would the performance be copying using the command line?

---

