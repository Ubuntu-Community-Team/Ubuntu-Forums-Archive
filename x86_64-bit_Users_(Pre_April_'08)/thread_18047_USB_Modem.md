---
title: "USB Modem"
date: 2005-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by tranceConscious on 2005-03-04
How do I make my usb modem work???

---

### Post by kubla on 2005-03-05
[QUOTE=tranceConscious]How do I make my usb modem work???[/QUOTE]

You start by learning how to ask a question. Try reading this first:

[http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=277](http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=277)

For starters though, unplug the modem and type:

lsusb

then plug the modem in and type

lsusb

Compare the output.

Go to google and do a bit of research on the device name.

If you get reasonably far along with your attempts, post again here with some specific information including: the type of modem you're trying to get running, kernel version, etc.

Ian

---

