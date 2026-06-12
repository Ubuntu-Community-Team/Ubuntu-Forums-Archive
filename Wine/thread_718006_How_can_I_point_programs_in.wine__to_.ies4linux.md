---
title: "How can I point programs in.wine  to .ies4linux ?"
date: 2008-03-07
forum: Wine
---

### Post by zami on 2008-03-07
How can I get a program installed via wine, to use IE6 installed via ies4linux?

For example, I've got a Popcap game that, to register, needs to launch IE6.

The game resides in .wine
IE6 resides in .ies4linux

I have tried installing IE6 with plain Wine, and also with Wine Doors, both with no success.  But IEs4Linux works just fine.  Now I just need to integrate it with the rest of my windows programs.

Any help would be much appreciated!  

zami

---

### Post by karth on 2008-03-08
AFAIK each wine prefix acts as a separate windows environment. You'd better install all your programs that require IE into the .ies4linux prefix

---

### Post by zami on 2008-03-09
Thank you!  I should have tried that.  I've since yanked out my .ies4linux directory but I'm sure this isn't the last time it will come up.

Good thinkin' Karth, thanks.

-zami

---

