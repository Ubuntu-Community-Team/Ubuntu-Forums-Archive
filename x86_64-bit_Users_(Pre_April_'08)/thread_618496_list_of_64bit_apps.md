---
title: "list of 64bit apps"
date: 2007-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by svtfmook on 2007-11-20
is there a list of just 64bit applications somewhere?

---

### Post by dfreer on 2007-11-20
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
My 64-bit synaptic reports approx 22,000 packages available. What are you looking for?

---

### Post by sgtbug on 2007-11-20
try [www.getdeb.net](www.getdeb.net) for packages that may not be available in the default repo..

---

### Post by svtfmook on 2007-11-20
i'm just looking to replace the 32bit apps with 64bit apps.

---

### Post by rsambuca on 2007-11-20
Do you have the 64bit version of Ubuntu installed?  You can't just install 64bit programs onto a 32bit operating sytem.  It won't work!

---

### Post by dfreer on 2007-11-20
If you do have a 64-bit ubuntu, then the better question might be "Is there a list of applications that **don't** work with 64-bit?". Or "These programs I use a lot in 32-bit ubuntu, do they work in 64-bit? Here's what I use:"

---

### Post by svtfmook on 2007-11-20
i have ubuntu amd64

---

### Post by dfreer on 2007-11-20
Then, pretty much anything you install using the standard repositories is going to be a 64-bit app. The exceptions would include 32-bit libaries, typically designated as lib32xyz or ia32-libs-xyz. You won't be able to even run most 32-bit code without 32-bit shared libraries. 

Is there specific 32-bit apps you want to run, or apps that you used in 32-bit that you want to run native 64-bit versions of?

---

### Post by svtfmook on 2007-11-20
well, i installed swiftweasel 64 and swiftdove 64 and i like how they run (quick), what i'd like, is as much 64bit apps as possible, ie k9copy (or something similar), gimp, etc.  but i'd like to see what is available in 64 bit.

---

### Post by dfreer on 2007-11-20
k9copy has a 64-bit .deb, a simple:
```
sudo apt-get install k9copy
```
Should take care of that. GIMP is included by default in ubuntu, so it's already installed (since you have 64-bit ubuntu installed, all of the programs installed by default will be 64-bit programs).

I think I see the cause of confusion here. The 32-bit version of firefox is sometimes repackaged to install on a 64-bit system, because some plugins only work with the 32-bit version of firefox. Some people will then call the default firefox installed on their computer "Firefox64", and the 32-bit version "Firefox32". 

The important thing to note here, is that when you install Firefox from the official repositories, you are installing the 64-bit version. Just because it doesn't have 64 in it's name, does not mean it's not a 64-bit package. In fact, your system will **not** allow you to install packages marked as being 32-bit, if you were to try normally installing a 32-bit .deb it will bring up an error.

The 64-bit Swiftweasel will probably not run any faster than the 32-bit swiftweasel, although it's quite likely either version will run faster than firefox.

As long as you stick to the official repositories, you will only be installing 64-bit software. If you would like to be able to enter a program's name, and see if there is a 64-bit version of it, you can use that link I posted earlier:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
As you can see, if you do a search for k9copy, it will show as having a 64-bit (amd64) and 32-bit (i386) package available:
[http://packages.ubuntu.com/gutsy/kde/k9copy](http://packages.ubuntu.com/gutsy/kde/k9copy)

---

### Post by John.Michael.Kane on 2007-11-20
These posts [http://ubuntuforums.org/showpost.php?p=3802168&postcount=4](http://ubuntuforums.org/showpost.php?p=3802168&postcount=4) [http://ubuntuforums.org/showpost.php?p=3769172&postcount=2](http://ubuntuforums.org/showpost.php?p=3769172&postcount=2) should give an idea that what you want is avilable.

---

### Post by OpenFish on 2007-11-22
u can get lots of 32 apps running on 64systems as the kernels are so alike but u will need all the 32 library's so use something like ia32-libs-gtk! and nspluginwrapper lets u use flash in 64bit browsers with these tools i rarely need grub any more (except for games)

---

