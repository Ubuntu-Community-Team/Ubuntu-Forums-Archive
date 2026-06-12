---
title: "how to test the speed of a tmpfs ramdisk?"
date: 2008-09-23
forum: x86 64-bit Users
---

### Post by phdmybest on 2008-09-23
i am a newbie here.
could anyone so kind to tell me how to test the speed of a tmpfs ramdisk.
i want to compare the speed between tmpfs ramdisk and a normal hard disk.
thanks in advanced.

---

### Post by Jouke74 on 2008-09-24
Well the speed of your memory will definitely be much faster than the harddisk and will depend on your memory speed. The easiest is to copy a large file on your ramdisk, and then make a copy of this file on the same ramdisk. This will give the basic speed.

---

### Post by Salvar Fawkes on 2009-03-11
I did the very same thing to test the speed of mine, and I got some extremely strange results. The copy operation took significantly longer than a normal hard drive copy operation--it was running at about 5 MiB/s. During this time I was watching the System Monitor, and my memory usage wasn't going up at all--neither RAM nor swap. I had expected to see it rise by about 700 megabytes, but... nothing. When I copied the file back, I got speeds of about 40 MiB/s, which is about 2-4 times the speeds I get when just copying files around on the one drive. I am perplexed.
Oh, afterwards I deleted the file, and copied it again, and it was transferred instantly. The same thing happened if I only copied the file halfway--the part that was already copied over would already be "known" even after being deleted, and wouldn't have to transfer again. (Oh, and when I deleted the file, the .Trash-1000 file would appear, but nothing would show up in the trash can.)

I don't even know where to begin figuring this out. Where would be the appropriate place to ask about this?

---

