---
title: "very bad perfomance"
date: 2009-05-29
forum: x86 64-bit Users
---

### Post by aakhil536 on 2009-05-29
Hello guys.....I'm using ubuntu 9.04 (amd 64 ) in my laptop.....but the saadest thing my laptop doesnt have perfomance in this.....
my laptop
....................................................................................
hp dv5 1106ax
amd 64 turion x2
3gb ram
ati radeon 3450 512mb...........

......................................................................................
previously Iwas using vista...Its very sad that I'm not getting perfomance in my system....It seems like I have only 512mb ram....also I have problems with microphone...
[SIZE=6]**can somebody help me?**[/SIZE]:KS

---

### Post by Arup on 2009-05-29
Have you enabled video drivers via admin>hardware drivers?

---

### Post by Anubis on 2009-05-29
It's hard to even read what you typed, so I have no idea what your talking about.

---

### Post by avilella on 2009-05-30
Can you specify what sort of performance is lacking?

Try benchmarking with phoronix-test-suite:

sudo apt-get install php5-gd
wget [http://www.phoronix-test-suite.com/releases/repo/pts.debian/files/phoronix-test-suite_1.8.1_all.deb](http://www.phoronix-test-suite.com/releases/repo/pts.debian/files/phoronix-test-suite_1.8.1_all.deb)
sudo dpkg -i phoronix-test-suite_1.8.1_all.deb
phoronix-test-suite install qgears2
phoronix-test-suite benchmark qgears2

> **aakhil536 said:**
> Hello guys.....I'm using ubuntu 9.04 (amd 64 ) in my laptop.....but the saadest thing my laptop doesnt have perfomance in this.....
my laptop
....................................................................................
hp dv5 1106ax
amd 64 turion x2
3gb ram
ati radeon 3450 512mb...........

......................................................................................
previously Iwas using vista...Its very sad that I'm not getting perfomance in my system....It seems like I have only 512mb ram....also I have problems with microphone...
[SIZE=6]**can somebody help me?**[/SIZE]:KS

---

