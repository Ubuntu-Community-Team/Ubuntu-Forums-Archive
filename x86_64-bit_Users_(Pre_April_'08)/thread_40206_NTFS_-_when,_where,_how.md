---
title: "NTFS - when, where, how ???"
date: 2005-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ::DoGG:: on 2005-06-08
Hello guys!
I was just wondering... There are couple linux project that try to enable full access to ntfs partiotions, making a drivers etc..
But why it`s so hard ? Is the NTFS filesystem specification closed, or it`s just hard to implement it into kernel ?
I have 2 ntfs partitions and don`t want to mount them for writing since a heard that a lot of people got screwed after this and endup with broken partition tables etc..
So do you gus think that we will have to wait a long time for a driver for ntfs that couls work as stable and good as a actuall driver for fat32 partiotions ?

P.S. Beeing a slave of microsoft from 1 day now. Well, GTA:SA is even more addictive :D

---

### Post by Markrian on 2005-06-08
NTFS is not openly documented, no. It has to be reverse engineered. It may never be fully safe to write to it using reverse engineered drivers.

However, there is something you could try (but I'd still not do it myself, just in case.) Read about it here: [http://slashdot.org/article.pl?sid=03/12/02/1536227](http://slashdot.org/article.pl?sid=03/12/02/1536227)

It is also expressedly prohibited to reverse-engineer it.  As well, The Microsoft company seemingly changes the specifications every now and then to throw off development of a free ntfs driver.

---

### Post by FluffyElmo on 2005-06-08
Captive-ntfs is probably the best option available right now. It's slow and may not be perfect, but if you just need to move files to ntfs now and then it'll do the job.

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

---

### Post by Markrian on 2005-06-09
[QUOTE=azz, apparently]
It is also expressedly prohibited to reverse-engineer it.  As well, The Microsoft company seemingly changes the specifications every now and then to throw off development of a free ntfs driver.[/QUOTE]

First of all, it seems a bit odd that a (I assume) moderator edited my post instead of just adding his own.

Second of all, reverse-engineering, in general, is certainly not prohibited. In America perhaps it is (though I don't know much about that), but in general, worldwide? Certainly not. The SourceForge page [http://linux-ntfs.sourceforge.net/](http://linux-ntfs.sourceforge.net/) would have been shut down years ago if that was the case.

---

### Post by desdinova on 2005-06-09
If its prohibited somewhere in the world, it makes it difficult to distribute globally... MS are not exactly keen to give Linux any footholds...

---

