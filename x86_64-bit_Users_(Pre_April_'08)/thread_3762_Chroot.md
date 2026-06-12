---
title: "Chroot"
date: 2004-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rink on 2004-11-09
I have followed the instructions contained in [chroot instructions](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu) . 

What exactly is happening here?

I take it that I am installing seperate copies of 32bit software in a directory that I can switch to when I need to run 32 bit applications like wine.

If I need to install wine, I need to type 'chroot /var/chroot' to get into 32 bit mode, and then run 'apt-get install wine'.

Similarly, to run wine I need to type 'chroot /var/chroot' followed by 'wine notepad' or whatever.

Is that right?

---

### Post by dmatrix on 2004-11-09
You are correct. 

You may want to look at setting up dchroot as in the howto to avoid having to chroot everytime you would like to use your 32 bit chroot.

---

### Post by Rink on 2004-11-09
Dmatrix,

Many thanks for the reply.

What does 'dchroot -d' do?

I notice that the howto suggests reinstalling nvidia-glx. I take it this is to allow 32bit games to take advantage of the graphics card? If I don't need this, I don't need to install again.

---

