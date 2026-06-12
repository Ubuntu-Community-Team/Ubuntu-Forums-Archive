---
title: "A Few Very Basic Questions"
date: 2006-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Frank65 on 2006-03-31
I have recently downloaded Inkscape for my now "Ubuntu-ed" iMac. But I'm trying to find out where it went.

I searched for the file and found it in one directory (repository, is that right?) and got it to extract. Where the extraction files went to, I haven't a clue.

Do all downloaded files go to the same place? 
Can I create a dir/rep and steer the download/extraction to it?
I'm looking forward to Fluxbox soon.

Also, can I create a shortcut/alias on the desktop to run a program?
Can I create a folder on the desktop to save misc. files to?

I have no fear of the command line, and if I must use that way to achieve results then so be it.

I must say, that I'm enjoying the heck out of this new OS experience, but I must admit that right now I feel like I'm trying to walk with both legs in a burlap bag. But I'm smiling all the way.

Thanks for your help.

Frank65

---

### Post by 3rdalbum on 2006-03-31
Where did you download Inkscape from? Synaptic/apt-get, or from the Inkscape website?

Installing from Synaptic should put an item into Applications > Graphics.

If you've downloaded from the Inkscape website, then you've most likely downloaded the source code. Unless you want the latest version, type this into a terminal:

```
 sudo apt-get install inkscape 
```
and it'll do everything for you.

If you definately want to install the program from source, double-click the .tar.gz file. This will open the Archive Manager. Click the Extract button, and it'll ask you where you want it extracted to. Choose your home directory.

Now, follow the instructions in the INSTALL file in the Inkscape source directory that has just been created. It'll probably be something like:

```

./configure
make
sudo make install

```

---

### Post by Zimmer on 2006-03-31
Surely to install Inkscape you need ony go to  System>Administration>Synaptic Package manager   search for Inkscape and mark it for installation, then click Apply.
It should then appear on your Applications>Graphics  menu..

---

### Post by linear on 2006-03-31
There's a nice "beginner's guide" (mainly about software installation) [here]("http://www.ubuntuforums.org/showthread.php?t=153118").

---

### Post by Frank65 on 2006-04-01
I apparently downloaded the source code to Inkscape, so ***3rdalbum's*** advice did the trick. Tonight, I tried downloading Fluxbox with less than successful results. ("No acceptable C compiler found in $Path.)

This weekend I will play with my new OS a bit more, and print out a bunch of FAQs and Beginners' Guides and just read. And then read some more.

I'm sure I'll return with many questions, some of them I hope aren't so incredibly basic.

Thanks for your help again.

Frank65

---

### Post by jdp on 2006-04-01
Unless you really have a specific reason to, installing from source isn't the greatest for Ubuntu.  Using Synapic and the repositories means that things have been tweaked to work on Ubuntu correctly.  By going form source you may have to find, fix, and tweak on your own.  And even then it might not work right.  Synaptic/apt was designed to take most of the tedious guess work out of installing software on Linux.

The general rule of thumb is to only install from source if something isn't in the repositories, or if you need a bleeeding edge version that hasn't been updated in the repositories.

---

### Post by 3rdalbum on 2006-04-03
I agree, use the repositories whenever you can; but don't be afraid of compiling from source. It's actually not difficult (just tedious sometimes if you don't have all the required libraries and you have to keep searching on Synaptic)

Make sure you keep a copy of the Makefile, otherwise you'll find it a bit difficult to uninstall Inkscape. The same applies to anything you install from source.

---

