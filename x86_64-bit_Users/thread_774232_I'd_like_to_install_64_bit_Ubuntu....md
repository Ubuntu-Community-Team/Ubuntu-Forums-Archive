---
title: "I'd like to install 64 bit Ubuntu..."
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by MarcelloSav on 2008-04-29
... on my MacBook, but I have some questions:
I have Ubuntu on my MB since feisty, but only the 32 bit version. Now, I'd like to use the Core 2 Duo architecture at 64 bit. My problem is that I use this laptop for studying and I'd like to avoid problems, just because I need it. Is it possible to install the 64 bit version without losing all my configurations? May I make a backup (or something similar) of my actual home partition and recover it after 64 bit re-installation?

Thank you for for your replies, and forgive my bad english.
Marcello.

---

### Post by Kilz on 2008-04-29
> **MarcelloSav said:**
> ... on my MacBook, but I have some questions:
I have Ubuntu on my MB since feisty, but only the 32 bit version. Now, I'd like to use the Core 2 Duo architecture at 64 bit. My problem is that I use this laptop for studying and I'd like to avoid problems, just because I need it. Is it possible to install the 64 bit version without losing all my configurations? May I make a backup (or something similar) of my actual home partition and recover it after 64 bit re-installation?

Thank you for for your replies, and forgive my bad english.
Marcello.

If you have a separate home partition it will be possible to mount the home partition in the new install. But I think the safest way is to do a duel install if you have hard drive space. Then mount the old install to a folder (this is what I did). You then can move over the files you need and get the new install working just as you like it. Then when its all working and moved, delete the old partition and reclaim the hard drive space.

---

### Post by MarcelloSav on 2008-04-29
Oh disk space is exactly one of my problems! :D The other problem is that MB doesn't like a number of partitions greater than four, so for me it's impossible to create a new partition. However, I forgot to tell you that (for the same problem), I can't separate root and home...
However, thanks for your reply... ;)

---

### Post by Sef on 2008-05-04
> The other problem is that MB doesn't like a number of partitions greater than four, so for me it's impossible to create a new partition. 

You can't create more than 4 primary partitions, so what you need to do is for the fourth partition is make it a logical partition.  You can make as many partition as you want with a logical partition.

---

