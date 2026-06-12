---
title: "Keyboard: no scancodes with showkey -s"
date: 2009-09-22
forum: x86 64-bit Users
---

### Post by fenrasa on 2009-09-22
Hi,

I'm using a fully updated/upgraded Ubuntu 9.04 with the
Microsoft Digital Media Keyboard 3000 (Cheap and a lot of buttons to map - so I thought).
 [http://www.microsoft.com/presspass/images/press/2008/03-11dmk3000_lg.jpg](http://www.microsoft.com/presspass/images/press/2008/03-11dmk3000_lg.jpg)
And there it began.

As Google told me, there is an easy and a hard way to map keys. 
[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)

As nothing described worked, I searched a little bit more and found the command
showkey [-s|-k|..], which I used in a "real console" (STRG+ALT+F1)

For about half of my buttons this method worked, for the other half, like the 5 super-duper custom keys, it didn't. They did not even appear in the list of the buttons i pressed, no scancode what-so-ever.
Is this a bug or is it me being n00bish?

greetings from good old europe.

---

### Post by fenrasa on 2009-09-24
[CENTER][IMG]http://cdn1.knowyourmeme.com/i/17660/small/bump_by_fallenjrblue.jpg?1252548095[/IMG]
[/CENTER]

Hello, it's me again. Instead of just bumping I try to give you ppl some more information.

As I understand the matter at hand, there are two levels of keystroke-recognition.
- Kernel
- X-Server

Level: X;
At first, I tried the gnome gui for shortcuts. That didn't work, ofc.
2nd: xev, didn't work either.
3rd: keytouch. The dead buttons weren't recognized either.

Level: Kernel;
4th: showkeys -s -> nothing, too bad.
(yes, i played with dmesg / dmesg -c and such stuff too)

Googling has shown me, that this error occured once before, at least, in 2008. A Kernel upgrade fixed it back then. I guess. For the time being, waiting for a fresh repository is my way. :KS

Here is the list of not-responding-keys:
ZoomIn, ZoomOut, "Messenger", Custom1, -2, -3, -4, -5.

Greetings

---

### Post by tiagosab on 2009-09-25
Just to note I have the same problem here, using Debian squeeze/sid. Just the left windows key (super_R) also does not work, and have no keycodes in showkeys.

I have tried to `cat` events from the keyboard in /dev/input, to a file, and these keys do not show up. I tried to `cat` from /dev/usb*, but it does not work (and I don't even know if that should work - the error is "no such device or address").

And there are no messages from the kernel in /var/log/syslog, /var/log/kern.log or /var/log/messages about unknown keys.

Tiago Saboga.

---

### Post by tiagosab on 2009-09-25
Ah, and it's not x86_64 specific: I have also tried this in a 32 bit system (debian lenny), with the same results.

---

