---
title: "Shouldnt WIFI work?! Man I need help...."
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicholaspaul on 2005-12-02
I bought an Asus WL-167G thinking it would work with Breezy PPC. I tried installing ulan ([http://etudiants.insia.org/~jbobbio/ural-linux/](http://etudiants.insia.org/~jbobbio/ural-linux/)) but after installing headers I get a problem with modprobe  - 
sudo modprobe ural
FATAL: Error inserting ural (/lib/modules/2.6.12-10-powerpc/net/ural.ko): Unknown symbol in module, or unknown parameter (see dmesg)

So I ran synaptic and installed R2500 drivers listed there, but am stuck from there. 

Isnt there a way this should work?? 

thanks!!

---

### Post by daller on 2005-12-02
Unfortunately that card needs ndiswrapper to work!

[http://www.linuxquestions.org/hcl/showproduct.php?product=2728&sort=8&cat=126&page=1](http://www.linuxquestions.org/hcl/showproduct.php?product=2728&sort=8&cat=126&page=1)

It WILL work on an i386 pc, though!

---

### Post by nicholaspaul on 2005-12-02
Oh dear. More junk to throw in my  shoebox. Thanks for the info, though :)

---

