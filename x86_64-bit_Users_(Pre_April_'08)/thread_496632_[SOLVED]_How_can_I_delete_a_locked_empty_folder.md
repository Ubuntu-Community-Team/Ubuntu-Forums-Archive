---
title: "[SOLVED] How can I delete a locked empty folder?"
date: 2007-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-07-09
I was making wireless network card drivers and I have this folder on my desktop now that I can't delete.

I have right clicked on it, brought up properties, attempted to change the permissions, all to no avail.  It still tells me I don't have permission to delete it.  I can rename it, move it around into other folders/places (including the trash can).  I can't empty it from the trash can, or delete it directly.

Advice please...:confused:

---

### Post by bigken on 2007-07-09
create a new folder drop in the new folder then delete it

well it worked for me might not for you

---

### Post by crjackson on 2007-07-09
> **bigken said:**
> create a new folder drop in the new folder then delete it

well it worked for me might not for you

That didn't work.  It turned out it had a hidden file inside.  I used the command line to navigate to the file and the command

rm --rt2500.mod

That deleted the file, then the folder was able to be deleted the normal way.

Thanks for your help.

---

### Post by stchman on 2007-07-09
> **crjackson said:**
> I was making wireless network card drivers and I have this folder on my desktop now that I can't delete.

I have right clicked on it, brought up properties, attempted to change the permissions, all to no avail.  It still tells me I don't have permission to delete it.  I can rename it, move it around into other folders/places (including the trash can).  I can't empty it from the trash can, or delete it directly.

Advice please...:confused:

You tried the following?

sudo rm -r -f ~/Desktop/<name of folder>

This should do the trick.

---

### Post by crjackson on 2007-07-09
> **stchman said:**
> You tried the following?

sudo rm -r -f ~/Desktop/<name of folder>

This should do the trick.

See the above post...  I did something like that, but not exactly.

---

### Post by Wiebelhaus on 2007-07-09
also

in the term "sudo nautilus" find the folder and kill it in the name of freedom! the freedom to delete any damn thing you want.

---

### Post by crjackson on 2007-07-09
> **sx66gns said:**
> also

in the term "sudo nautilus" find the folder and kill it in the name of freedom! the freedom to delete any damn thing you want.

Awesome.  I really like this...

---

