---
title: "Running a 32 Bit Binary On 64 Bit Ubuntu"
date: 2007-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by DuckFOO on 2007-09-21
I have a closed source, binary only program named Vuescan that I use with my scanner. It works fine in 32 bit Ubuntu but not 64 bit Ubuntu, which I prefer due to the amount of RAM in my computer (4GB). Assuming that it is possible to install 32 bit compatability libraries for Ubuntu, how does one figure out which ones is needed for a particular application to work?


Thanks!

---

### Post by Lonthong on 2007-09-21
I had to install the following if I want to "force architecture" 32bit CAD software:
sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl dpkg-dev
Just give it a try

---

### Post by ViRMiN on 2007-09-21
You may also need to run the app through 'linux32' (see manpage for details).  I've not needed to do it yet but, just thought I'd mention it just in case!

---

### Post by DuckFOO on 2007-09-21
Thank you so much! I will give it a try when I get home.

---

