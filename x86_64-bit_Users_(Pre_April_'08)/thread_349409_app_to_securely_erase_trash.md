---
title: "app to securely erase trash"
date: 2007-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tim T on 2007-01-30
i'm running 6.10 x64 ubuntu, and am looking for an application to securely and permanently erase the files in my trash bin. something that could erase free disk space would be nice too. a program called "eraser" was what I used in win 98-xp, and it worked great. is there a similar product for ubuntu? I tried looking in the repository, in google, and here of course, but thus far to no avail.

---

### Post by LotsOfPhil on 2007-01-30
I am not sure that this is what you are looking for, but, what about shred?

---

### Post by kuja on 2007-01-30
Shred is a good tool, but keep in mind that shred isn't 100% secure when used on journaling file systems like ext3, xfs, jfs, reiserfs, etc. If you don't care about that, then go ahead and use it anyway, but I just thought I'd say so.

---

### Post by Tim T on 2007-02-03
> **LotsOfPhil said:**
> I am not sure that this is what you are looking for, but, what about shred?

i'm looking for something that can permenantly destroy anything in my  trash bin, or wipe free space. basically turn everything back to "0"

---

### Post by Wight_Rhino on 2007-02-03
How about "wipe"?

[http://wipe.sourceforge.net/]("http://wipe.sourceforge.net/")

---

### Post by Tim T on 2007-02-03
> **Wight_Rhino said:**
> How about "wipe"?

[http://wipe.sourceforge.net/]("http://wipe.sourceforge.net/")

i'll give it a try and see how it works. THX!

---

### Post by xyz on 2007-02-26
This one is good:
[Darik's Boot and Nuke]("http://dban.sourceforge.net/")

---

### Post by dfreer on 2007-02-26
> This one is good:
Darik's Boot and Nuke

lol, DBAN is good for wiping your ENTIRE HARD DRIVE, not just the trash can. Although if that is what you want...

---

### Post by xyz on 2007-02-27
> **dfreer said:**
> lol, DBAN is good for wiping your ENTIRE HARD DRIVE, not just the trash can. Although if that is what you want...
ho ho ho...he just wants to wipe trash!!yeah then dban is really not a good idea!!
I use:
```
shred -fuvz file.extention
```

---

### Post by pjwigan on 2007-03-04
I've found this page useful for free space erasure:

[http://ubuntuforums.org/showthread.php?p=1979932](http://ubuntuforums.org/showthread.php?p=1979932)

---

