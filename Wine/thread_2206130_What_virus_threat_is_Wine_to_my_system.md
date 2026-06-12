---
title: "What virus threat is Wine to my system?"
date: 2014-02-17
forum: Wine
---

### Post by michael-piziak on 2014-02-17
I seen a movie on youtube where they said that Wine could get corrupted on your system with all the viruses and such out there for Windows.

What threat is Wine to my system?  All I use it for is to play SNES emulation with.  I download the Roms while in Ubuntu, but open the Roms with Wine.

I don't use Internet Explorer or go on the net in any way with Wine.

---

### Post by Don_Stahl on 2014-02-18
There is a good set of answers (it's a question with several possibilities) on [http://unix.stackexchange.com/questions/1729/does-installing-and-using-wine-open-up-your-linux-platform-to-windows-virus](http://unix.stackexchange.com/questions/1729/does-installing-and-using-wine-open-up-your-linux-platform-to-windows-virus)

The upshot opinion seems to be, yes a Windows virus executable may run on Wine. But it's unlikely that it was written to take advantage of a Linux system, so it is unlikely to damage your system the way it would on a Windows machine.

But opinions are like hair, everybody has a few somewhere.

---

### Post by SeijiSensei on 2014-02-19
Plus the extent of damage will be minimal.  It would affect only ~/.wine.  If you're concerned about this, back up the .wine folder in your home directory and keep it safe.  Then if anything untoward occurs, you can just blow away the affected .wine and replace it with the clean copy.

---

### Post by vanquishedangel on 2014-04-13
Dont be fooled entirely!  Not to make anyone panic but wine symlinks to other areas in linux, like your pictures, desktop, music, videos, and your home folders. Granted a windows virus cannot really harm your linux install however the integrated symlinks can give access to your data easy. This has been tested and some viruses work in wine. I will repost to this thread with an example but yes it can cause problems with data access and downloading and installing things (in wine).

---

### Post by vanquishedangel on 2014-04-13
Here is the thread I promised:

[http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

He ran the virus known as etherape, he messed up his email client and some other things happened. Since somethings are located in your home folders (ie your email client) it is possible that a windows virus may have access to that information when run in wine.

---

### Post by CitadelUniversal on 2014-04-15
A good advice is from Wine's FAQ about the virus threat - here's the link [http://wiki.winehq.org/FAQ#head-3cb8f054b33a63be30f98a1b6225d74e305a0459](http://wiki.winehq.org/FAQ#head-3cb8f054b33a63be30f98a1b6225d74e305a0459)

---

