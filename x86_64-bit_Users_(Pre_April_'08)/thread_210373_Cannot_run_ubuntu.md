---
title: "Cannot run ubuntu"
date: 2006-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by erixz on 2006-07-06
Hello,
I installed ubuntu on my PC today, but when I start ubuntu, I get theese error messages:

[[img]http://img503.imageshack.us/img503/4347/img65127gm.th.jpg[/img]](http://img503.imageshack.us/my.php?image=img65127gm.jpg)

[[img]http://img471.imageshack.us/img471/1150/img65144sy.th.jpg[/img]](http://img471.imageshack.us/my.php?image=img65144sy.jpg)

[[img]http://img470.imageshack.us/img470/1922/img65155mg.th.jpg[/img]](http://img470.imageshack.us/my.php?image=img65155mg.jpg)

How can I fix this? 

Thank you, 
Erixz.

---

### Post by zhoux on 2006-07-06
**could you provide bigger pictures? (you can load them straight to this forum) **

i think i might've had similiar problems...does it mention anything about the **X** server failing to start?

---

### Post by erixz on 2006-07-06
Click at the pictures to see large version. 

Yes something about an X...
Someone who can help me? Hope so!

---

### Post by Kilz on 2006-07-06
[QUOTE=erixz]Click at the pictures to see large version. 

Yes something about an X...
Someone who can help me? Hope so![/QUOTE]
What video card do you have?

---

### Post by zhoux on 2006-07-06
my fault....for some reason i don't see the pictures, instead i see the link to the pictures, and when i clicked the link, the pictures are tiny....but whatever...

it has something to do with video card and the driver X is trying to use, so could you provide us with the content of you xorg.conf file?

it is located at /etc/X11/xorg.conf, you can use this command to view in w/out a GUI:

sudo nano /etc/X11/xorg.conf

as for how to show us....i guess you have to take another pictures or something....

---

