---
title: "Some question about Ubuntu 9.04 64bit"
date: 2009-08-04
forum: x86 64-bit Users
---

### Post by y1nn on 2009-08-04
I have a few questions about Ubuntu 9.04 64 bit on behalf of my brother who is getting a new PC and wants to use this OS.

The PC he is getting contains:

Intel i7-920 2.66ghz
3gb DDR3 RAM
Nvidia Gefore 9500 gt 1gb

Are all of these compatible with Ubuntu 9.04 64bit?

And as well does World of Warcraft Function well with Ubuntu 9.04 64bit?

---

### Post by howefield on 2009-08-04
Ubuntu will work very well with that hardware. 

I believe World of Warcraft works well in Linux using wine.

---

### Post by y1nn on 2009-08-04
Im new to Ubuntu and Linux, may I ask what Wine is and does it come standard with Ubuntu 9.04?

---

### Post by rideburton56 on 2009-08-04
Wine allows you to run certain windows programs in ubuntu, and it does come standard with Ubuntu.

---

### Post by completist on 2009-08-04
WINE is an acronym for **W**ine **I**s **N**ot an **E**mulator.  Software that allows windows software to run on Linux.

[http://www.winehq.org/](http://www.winehq.org/)

It does not come with Ubuntu but the repository for it can be enabled then its a download away.  You can use the directions that follow to download and install wine.


[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Bölvaður on 2009-08-04
This hardware is an absolute overkill! I would like your brother's computer!!!

> **y1nn said:**
> What is Wine and does it come standard with Ubuntu 9.04?
no it does not come preinstalled, but it has stable version of it in the ubuntu repository. If you had Ubuntu you could click on my link to install it. [This link]("apt:wine")

People have had trouble getting WoW to work but on the other hand, many have managed to get higher fps than in windows... so it might be up to you how well you know how WoW and Windows works and interacts... or how talented you are in following instructions from the winehq.org website on how to do the configs for wow.

[quote="description from the repositories"]Wine is a compatibility layer for running Windows applications on Linux.
Applications are run at full speed without the need of cpu emulation. Wine
does not require Microsoft Windows, however it can use native system dll
files in place of its own if they are available.

This package includes a program loader for running unmodified Windows executables
as well as the Wine project's free version of the Windows API for running programs
ported from Windows.

 Homepage: [http://www.winehq.org/]("http://www.wine.hq.org")

[COLOR=Silver]Canonical does not provide updates for wine. Some updates may be provided by the Ubuntu community.[/COLOR][/quote]

---

### Post by jacklinux on 2009-08-04
> **howefield said:**
> Ubuntu will work very well with that hardware. 

I believe World of Warcraft works well in Linux using wine.
For a WINE program it runs well, but as a whole its rarther poor, the connection is a issue

---

### Post by y1nn on 2009-08-05
I just noticed that the file name at the end say amd64, Does this mean anything towards the Intel i-7 that he will be using.

---

### Post by 3Miro on 2009-08-05
> **y1nn said:**
> I just noticed that the file name at the end say amd64, Does this mean anything towards the Intel i-7 that he will be using.

No, amd64 is just the name, it applied to both AMD and Intel CPUs.

I have personally installed wine on an older laptop with 8.04 (and I don't remember which version of wine). The entire deal required to mount the cd with a special command (i.e. you type one command in the Terminal). Google "world of worcraft wine" and/or "world of worcraft winehq". I have not played the game.

---

