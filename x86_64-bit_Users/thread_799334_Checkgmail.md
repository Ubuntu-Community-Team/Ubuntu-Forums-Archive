---
title: "Checkgmail"
date: 2008-05-18
forum: x86 64-bit Users
---

### Post by fieldstone on 2008-05-18
I'm having a bit of a problem with Checkgmail on Hardy. When I install it and try to run it, I get the following messages:

Creating translations file at /home/jlf/.checkgmail/lang.xml ...
Updating translations file ...
Wide character in print at /usr/local/bin/checkgmail line 4801.
 ... done!
Cannot decode string with wide characters at /usr/lib/perl/5.8/Encode.pm line 166.
A thread exited while 2 threads were running.


What does this mean, and how do I fix it?

---

### Post by abhiroopb on 2008-05-19
Just a note, do you use pidgin? You can use pidgin to notify you if you have e-mail (quite handy!)

---

### Post by jespdj on 2008-05-19
I don't know about that error. I use another Gmail checker program, [cgmail](http://cgmail.tuxfamily.org/). It's also in the Ubuntu repository.

---

### Post by Mr_bleu on 2008-05-19
I use swiftdove.

---

### Post by cypherpunk on 2008-10-29
This worked for me:

% sudo aptitude install libunicode-string-perl

You can also install it using the synaptic package manager.

Cheers

---

