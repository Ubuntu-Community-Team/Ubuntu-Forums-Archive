---
title: "Upgrading Dell notebook to 64"
date: 2007-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Johnny K on 2007-05-28
I should be getting my Dell notebook in a week or two. As soon as I get it, I'm going to upgrade Ubuntu to the 64 bit edition (unless it ships with the 64 bit edition, which I doubt).

-Do I have to burn an iso and wipe the whole drive to upgrade to the 64 bit edition?
-If yes, will wiping the drive cause any problems? Do the Ubuntu notebooks contain any special drivers that would be lost by reinstalling Ubuntu?

---

### Post by Mr_bleu on 2007-05-28
I'm not expert, but I think 
$sudo apt-get upgrade 
would work.
On my kid's computer it upgrade via the update manager, although this was from dapper to fiesty, both 32bit.

---

### Post by Blender on 2007-05-28
> 
...unless it ships with the 64 bit edition, which I doubt...

It most probably won't.

> 
Do I have to burn an iso and wipe the whole drive to upgrade to the 64 bit edition?

Yes, you will have to do a clean install, as there are differences in the directory structure (lib32, lib64, lib -> lib64), among other things.

> 
If yes, will wiping the drive cause any problems? Do the Ubuntu notebooks contain any special drivers that would be lost by reinstalling Ubuntu?

I guess you'll have to wait until the first units ship and it's known what modifications Dell made to the default Ubuntu installation.

---

### Post by Johnny K on 2007-05-28
Thanks for the great help, Blender!

Is there any way I can check what modifications Dell has made once I receive the notebook?

---

### Post by Blender on 2007-05-28
> **Johnny K said:**
> Thanks for the great help, Blender!

Is there any way I can check what modifications Dell has made once I receive the notebook?
You're welcome.

I don't know. I guess they will make a public list of the modifications.
If not, people will find out anyway.

I'd suggest you simply wait :)

---

### Post by Kilz on 2007-05-28
Since you are **paying** for the laptop with it **preinstalled**.
1. You should get a restore disk, or any drivers they loaded.
2. You should receive some form of support for 30 days or so.
3. The laptops were most likely chosen because the hardware is such that it will work with Ubuntu.

---

### Post by Johnny K on 2007-06-08
I heard that the Dellbuntus ship with 6 partitions. When I install 64 bit Ubuntu, should I wipe the whole drive, or just overwrite a specific partition?

---

