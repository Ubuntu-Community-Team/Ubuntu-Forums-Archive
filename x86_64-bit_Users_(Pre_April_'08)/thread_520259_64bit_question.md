---
title: "64bit question"
date: 2007-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by pitmansm on 2007-08-08
can i run 32 bit stuff deb etc.. mozilla  etc... wine  flash plugin inside 64bit ubuntu? kinda like 64bit processor but 32bit software  but can i run 64bit software i.e  32bit mozilla or of the like inside 64bit ubuntu . so i can choose waht programs i wan t to be 64 bit and not

---

### Post by kuja on 2007-08-08
Yes and no. For it to be a straightforward install there either needs to be a package or a script available (plenty of scripts floating around);,else, you can do it without a package and it will run find so long as you have the deps installed (many of which are included in the ia32-libs-* packages), but otherwise you'll need to install the deps manually (or perhaps with a script like the one cappy wrote, it seems to work well)

So yeah it can be done. If you don't mind a little bit of extra setup, and after the setup.

---

### Post by John.Michael.Kane on 2007-08-08
> **pitmansm said:**
> can i run 32 bit stuff deb etc.. mozilla  etc... wine  flash plugin inside 64bit ubuntu? kinda like 64bit processor but 32bit software  but can i run 64bit software i.e  32bit mozilla or of the like inside 64bit ubuntu . so i can choose waht programs i wan t to be 64 bit and not

For wine theres a repo [Wine for Ubuntu, Debian, and Debian-based distributions]("http://www.winehq.org/site/download-deb").

For  flash, and other codec's check the sticky-thread below.
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by Kilz on 2007-08-08
> **pitmansm said:**
> can i run 32 bit stuff deb etc.. mozilla  etc... wine  flash plugin inside 64bit ubuntu? kinda like 64bit processor but 32bit software  but can i run 64bit software i.e  32bit mozilla or of the like inside 64bit ubuntu . so i can choose waht programs i wan t to be 64 bit and not

The packages you named, 
Wine - There is a package that installs the 32bit application layer avilable from the wine repositories.
mozilla - See links in my signature
Flash - See links in my signature.

Flash can be used by the 64bit browser, if you use nspluginwrapper. Unless you need java, the 64bit browser and nspluginwrapper is the way to go.
For the most part the applications most people would need to be 32bit can be counted on the fingers of one hand. There are 64bit versions of almost everything , but the proprietary things like flash.

---

### Post by ATAQ on 2007-08-08
64 bit linux is backward compatible with 32 bit lInux. 
Type in console "sudo apt-get install lin32"
and then you can execute 32 bit programs.
its basically just a 32 bit emulater. and it does the job nicely. I used to run 
Mozilla Firefox 32 bit using that, when flash was an issue!

---

### Post by pitmansm on 2007-08-09
so if i install 64bit linux i can run 32bit apps like vdrift and flight gear etc... do i have to go anyhtign special to it or? just clickand run

---

### Post by michael37 on 2007-08-10
> **pitmansm said:**
> so if i install 64bit linux i can run 32bit apps like vdrift and flight gear etc... do i have to go anyhtign special to it or? just clickand run

You may need to get some 32-bit libraries (more details here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)), and then yeah... just click and run on your executable.

---

### Post by michael37 on 2007-08-10
> **ATAQ said:**
> 64 bit linux is backward compatible with 32 bit lInux. 
Type in console "sudo apt-get install lin32"
and then you can execute 32 bit programs.
its basically just a 32 bit emulater. and it does the job nicely. I used to run 
Mozilla Firefox 32 bit using that, when flash was an issue!

Umm?  64-bit Fiesty doesn't have lin32.  Do you mean ia32-libs?

---

### Post by pitmansm on 2007-08-10
thnx for the replys im dling 64bit ubuntu now gonna try it

---

### Post by Sockerdrickan on 2007-08-11
Good luck!

---

