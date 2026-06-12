---
title: "beware f-spot"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ssam on 2005-10-20
beware of using f-spot on powerpc for a few days until a fix for [https://launchpad.net/distros/ubuntu/+sources/f-spot/+bug/3338](https://launchpad.net/distros/ubuntu/+sources/f-spot/+bug/3338) gets into the repos

---

### Post by Entity on 2005-11-27
[QUOTE=ssam]beware of using f-spot on powerpc for a few days until a fix for [https://launchpad.net/distros/ubuntu/+sources/f-spot/+bug/3338](https://launchpad.net/distros/ubuntu/+sources/f-spot/+bug/3338) gets into the repos[/QUOTE]

Do you know when f-spot will be updated?

---

### Post by ssam on 2005-11-27
the bug seems to have moved to [https://launchpad.net/malone/bugs/3338](https://launchpad.net/malone/bugs/3338) i think maybe it has got lost in malone.

i am using a deb that i build with the patches. i shall up load it to my website.

update:

you can download the fixed deb here [http://www.tygier.co.uk/pub/f-spot_0.1.3-1ubuntu1.1_powerpc.deb](http://www.tygier.co.uk/pub/f-spot_0.1.3-1ubuntu1.1_powerpc.deb)

use
```
sudo dpkg -i f-spot_0.1.3-1ubuntu1.1_powerpc.deb
```
to install it.

---

### Post by az on 2005-11-27
What is the bug?

---

### Post by Entity on 2005-11-27
[QUOTE=ssam]the bug seems to have moved to [https://launchpad.net/malone/bugs/3338](https://launchpad.net/malone/bugs/3338) i think maybe it has got lost in malone.

i am using a deb that i build with the patches. i shall up load it to my website.

update:

you can download the fixed deb here [http://www.tygier.co.uk/pub/f-spot_0.1.3-1ubuntu1.1_powerpc.deb](http://www.tygier.co.uk/pub/f-spot_0.1.3-1ubuntu1.1_powerpc.deb)

use
```
sudo dpkg -i f-spot_0.1.3-1ubuntu1.1_powerpc.deb
```
to install it.[/QUOTE]

Many thanks, it works.

---

### Post by Entity on 2005-11-27
[QUOTE=azz]What is the bug?[/QUOTE]When you rotate a photo in your f-spot catalog, you get an error and the file itself on your hard drive is corrupted and you can't open it anymore... You've just lost this nice girl's picture you took last week-end :)

---

### Post by ssam on 2005-11-27
if you have lost photos then maybe you should contact Larry Ewing, one of the f-spot devs. he offered to fix any of mine ( [http://bugzilla.gnome.org/show_bug.cgi?id=319190](http://bugzilla.gnome.org/show_bug.cgi?id=319190) ). i think you just need to put the byte back in the correct order.

---

### Post by Entity on 2005-11-27
[QUOTE=ssam]if you have lost photos then maybe you should contact Larry Ewing, one of the f-spot devs. he offered to fix any of mine ( [http://bugzilla.gnome.org/show_bug.cgi?id=319190](http://bugzilla.gnome.org/show_bug.cgi?id=319190) ). i think you just need to put the byte back in the correct order.[/QUOTE]No data has been lost :) I tried this on a copied file simply because of your post... I wanted to verify if it had been fixed since then. Thanks anyway.

---

### Post by az on 2005-11-27
So, this only affects PPC, right because it is big-endian?  (I looked up the meaning of endian on wikipedia - I am not that smart)

---

### Post by ssam on 2005-11-28
[QUOTE=azz]So, this only affects PPC, right because it is big-endian?  (I looked up the meaning of endian on wikipedia - I am not that smart)[/QUOTE]

yeah thats right. i think sparc and a few other architectures are bigendian too.

most of the time the compiler deals sorts out the byte order, but if the programmer explicitly ask for a the first bit in a byte they would get a different answer on big endian and little endian systems.

you get similar bug if you make explicit assumption about the size of a interger, sometimes it is 32bits and sometimes 64bits (or 16bit on old hardware).

---

### Post by az on 2005-11-28
[QUOTE=ssam]yeah thats right. i think sparc and a few other architectures are bigendian too.
[/QUOTE]

Yes, of course.  I meant in Ubuntu.

---

### Post by autocrosser on 2005-11-28
Well--I applied the patch last night & tried to rotate a picture I had copies of--still responded with a error---Dual 1.25 with 2G of memory--Error stated it had "run out of memory":???:  I only have the thumbnail now--full-size is "invalid size of entry (8, expected 0 x 1)

---

### Post by Entity on 2005-11-28
[QUOTE=autocrosser]Well--I applied the patch last night & tried to rotate a picture I had copies of--still responded with a error---Dual 1.25 with 2G of memory--Error stated it had "run out of memory":???:  I only have the thumbnail now--full-size is "invalid size of entry (8, expected 0 x 1)[/QUOTE]Can you try Sam's package instead? You can download it [here]("http://www.tygier.co.uk/pub/f-spot_0.1.3-1ubuntu1.1_powerpc.deb").

---

### Post by autocrosser on 2005-11-28
That was with sam's package---no joy for me---

---

