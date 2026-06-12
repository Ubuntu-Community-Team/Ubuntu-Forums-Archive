---
title: "Problem Installing From Source"
date: 2008-06-13
forum: x86 64-bit Users
---

### Post by danthebugman on 2008-06-13
I recently made the jump to Xubuntu 8.04 AMD64 after having used Ubuntu for the last year and a half.  I've my spare time the last few days getting everything set up the way I like.  One of the programs I simply cannot live without is Scid.  It's a chess database program I use almost daily.  I've also thought of toying with ChessDB which is just a little different.  I have not been able to find .deb files for either program, but not really an issue since both programs are available as source code.  I've never had an issue compiling from source with Scid before, but for some reason I cannot figure out what's going on here.  So I think this is where I'm having the problem:

```

daniel@dan-xubuntu:~/Chess/chessdb$ make
g++  -o pgnchessdb src/pgnchessdb.o src/misc.o src/index.o src/date.o src/namebase.o src/position.o src/game.o src/gfile.o src/matsig.o src/bytebuf.o src/textbuf.o src/myassert.o src/stralloc.o src/mfile.o src/dstring.o src/pgnparse.o src/stored.o src/movelist.o  -lz
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status
make: *** [pgnchessdb] Error 1

```

Suggestions??
Thanks,
Dan  :confused:

---

### Post by Cappy on 2008-06-14
Scid is in the universe repository

```
sudo apt-get install scid
```

---

### Post by danthebugman on 2008-06-14
It's not the most current version.

---

### Post by Cappy on 2008-06-14
Sorry, it's hard to judge what you may have already tried.

```
sudo apt-get build-dep scid
```
should do it.

If that still doesn't work then use
```
sudo apt-get install zlib1g zlib1g-dev
```

It's a good idea to "make clean" before running make again.

---

### Post by pwc on 2008-09-12
Has anyone here been successful in installing the latest version(3.6.25) of Scid from the source code. I too use Scid often and have since using Ubuntu for 2-3 years. But the Synaptic version is 3.6.1-2 and is quite old(2003) and the latest version has a lot of nice new features. 
Anyway I uninstalled Scid with Synaptic and downloaded tar.bz2 file, extracted the scid folder and did  "./configure"  with this result:

wayne@antec:~/Scid/scid$ ./configure
configure: Makefile configuration program for Scid
    Renaming "Makefile" to "Makefile.bak"
    Tcl/Tk version: 8.4
    Your operating system is: Linux 2.6.24-19-generic
    Location of "tcl.h": not found
    Location of "tk.h": not found
    Location of Tcl 8.4 library: /usr/lib
    Location of Tk 8.4 library: /usr/lib
    Location of X11 library: /usr/lib
    Checking if your system already has zlib installed: yes.
Not all settings could be determined!
The default Makefile was written.
You will need to edit it before you can compile Scid.
wayne@antec:~/Scid/scid$ 

I'm stuck here, anyone know how to solve this?

Thanks, pwc

---

### Post by Yellow Pasque on 2008-09-12
When a configure script outputs a message like that, you should open Synaptic, do a search for the utility that it's complaining about, and download the corresponding -dev packages. In this case:
```
sudo apt-get install tk-dev tcl-dev
```

---

### Post by pwc on 2008-09-13
Well gosh Temujin, darned if that didn't work! Now I have Scid installed. This is a great forum thanks to people like you. Thanks for your quick response and help.

pwc

---

### Post by Kappity on 2008-09-25
> **Temüjin said:**
> When a configure script outputs a message like that, you should open Synaptic, do a search for the utility that it's complaining about, and download the corresponding -dev packages. In this case:
```
sudo apt-get install tk-dev tcl-dev
```

Okay, now a related question from somebody else, except that I'm using Ubuntu 8.04 instead of Xubuntu.  I've had SCID 3.6.1.2 working, but would like to upgrade to version 3.6.25

Got the same error messages mentioned by pwc above, so I did the apt-get install for tk-dev and tcl dev.  Then when I typed "./configure" it apparently worked, and told me just to type "make" to install the program.  Did that, it churned for a while, and seemed to be installing things.  Didn't give any messages that were clearly errors, but there were a bunch of messages about "warning, deprecated conversion."  Finally it finished whatever it was doing, and went back to a command prompt.

I typed "scid", and it told me that scid was not installed, and to type "sudo apt-get install scid" to install it.  Unfortunately, if I do that, it just goes out and gets the old version 3.6.1.2, while I would like to get the latest version 3.6.25.

It's obvious that something went wrong with the install, but I really don't know what to look for.  Does this "deprecated conversion" message (there were many of them) give anybody a clue?

Any help appreciated.  Typing this from my Mac, and I've got a different chess database program for it, but I'd like to get the latest scid for my Ubuntu computer.  Of course, if I wait a couple of months, the latest version might be available through Synaptic Package Manager, but it would be nice to know that I can get it working without that.

---

### Post by Yellow Pasque on 2008-09-25
If make was successful then use this to install the program:
```
sudo make install
```

---

### Post by Kappity on 2008-09-25
> **Temüjin said:**
> If make was successful then use this to install the program:
```
sudo make install
```

That did it.  Thanks for your help.

---

### Post by cesarakg on 2008-10-24
You mean, you didn't installed with "sudo apt-get", but installed with "make; sudo make instal"?

I have scid installed with "sudo apt-get install", but want the most recent version, so I have to uninstall with synaptic, and dirt my hands with make and the alikes?

---

### Post by Mazin on 2008-10-25
Dirty your hands... kids these days :lolflag:

While the usual procedure is indeed
```
./configure
make
sudo make install
```

I recommend that you use checkinstall instead of "make install".  Checkinstall will generate a .deb package out of your compiled program.  This way, you get a package that can be upgraded, removed, or shared easily.

```
./configure
make
sudo checkinstall
```

---

### Post by flc65 on 2009-02-26
Hy
i have installed SCID on UBUNTU (sudo apt-get install scid).
I'm new on UBUNTU ....
Where i find it and start? In the desktop?

Thank
  Flavio

---

