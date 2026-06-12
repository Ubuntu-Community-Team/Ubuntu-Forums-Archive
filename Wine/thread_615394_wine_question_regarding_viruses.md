---
title: "wine question regarding viruses"
date: 2007-11-17
forum: Wine
---

### Post by cc93 on 2007-11-17
if i install wine i will be able to infect by virus?!:confused:

---

### Post by c0mp13371331337 on 2007-11-17
Stellar question, cc93.  I was wondering this myself when I first started using Wine and Linux.  While nothing is impossible in the realm of computers, I'm going to say that it's highly unlikely.  With wine, you need to specify a program to run with it.  So for example, if you've got a terminal open, and you're already in the directory that contains notepad.exe, you would need to run the command 'wine notepad.exe' where wine starts the compatibility layer between linux and the windows executible, and notepad.exe being that executible.

A regular, run-of-the-mill windows virus would not be able to execute itself in linux, even with wine, the same way it does in Windoze.  So in that respect, no.

And I have tried purposefully infecting my computer with some common viruses from windows and running them through wine with little to no luck.  Many viruses are very dependant upon the architecture of a windows file system, and while it's psudo-mocked in wine, most viruses just can't propogate or have the same destructiveness that they do in windows.

I read a great article where someone did basically the same thing, only took notes on their findings and went into great detail about what several viruses were able to do and not do in wine.  While I don't recall where/how I found the article, I can tell you that he had no luck whatsoever.  The worst any of them did were to put a few extra directories and files in his .wine directores, nothing malicious at all though.

So feel free to explore the realm of virus-catching in linux/wine.  It's a terrific way to pass the time and see just how solid a linux box really is!

---

### Post by hikaricore on 2007-11-17
[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

Remember NEVER run wine as root, this limits the majority of access.

Also you should avoid mapping your root partition as a drive for any reason.
As a general rule, if WINE can't access/see the files they are not there.

Since WINE runs in a "fake" environment (usually ~/.wine) this environment is the limits of what can even be attempted to be infected... if in the case that the virus actually can do what it intends to.  ^_^

---

### Post by cc93 on 2007-11-17
So i have not to wary about viruses right?:p
thank you :p

---

### Post by hikaricore on 2007-11-17
The general rule is be careful and don't trust "shady" software, but this is always the case with the Internet.

You have a very very low chance of there even being the possibility of being able to actually run virus/hijack code, even then it will likely not work as intended without a true ***dows environment.
 But don't let your ego get the best of you as a Linux user, if you share files with ***dows users there's still chance of passing something along if you don't know it exists.

Not trying to scare you, just common sense thought converted to rant-like reply text.  :)

---

### Post by cc93 on 2007-11-17
thx for all:P

---

