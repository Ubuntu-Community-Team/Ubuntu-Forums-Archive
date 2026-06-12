---
title: "Changing Virtual Memory Level"
date: 2008-08-18
forum: x86 64-bit Users
---

### Post by elmoosecapitan on 2008-08-18
When I first started running Hardy, I increased my virtual memory. I now want to decrease it, however, I forgot where I went and how to do it. Any suggestions? Thanks everyone!

cheers

---

### Post by tuxxy on 2008-08-18
Are you using virtualbox?

If it is then load up virtualbox but dont run ubuntu yet, click on the settings button  now here you can edit the base memory and video memory size for the virtualdisk.

---

### Post by elmoosecapitan on 2008-08-18
This isn't a virtual box, this is the pure and unadulterated version of Hardy Heron with kernel 2.6.24-19-generic.

---

### Post by cdtech on 2008-08-18
You want to resize your "Swap" partition. You'll have to use the "gparted live cd" to do this on your "primary" drive. You'll be able to move, size or whatever you want using "gparted".

What is the problem with your swap? Be sure that if you use hibernate to have enough "Swap".

---

### Post by elmoosecapitan on 2008-08-18
Alright, I'll try using the live CD. Thanks for the help.

---

