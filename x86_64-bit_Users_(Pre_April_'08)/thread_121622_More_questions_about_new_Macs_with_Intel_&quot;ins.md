---
title: "More questions about new Macs with Intel &quot;inside&quot;"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by learning_bird on 2006-01-25
On a previous thread ( [http://ubuntuforums.org/showthread.php?t=111010](http://ubuntuforums.org/showthread.php?t=111010) ) it was said that it'll there be no Ubuntu - Debian to cover the new CPU's and that should be used the x86 distro.

My questions are:

-How does Ubuntu - Debian deals with the EFI bootloader on the new Macs? I know of one Linux EFI implementation at the moment ELILO ( [http://sourceforge.net/projects/elilo](http://sourceforge.net/projects/elilo) ). Are there plans to use it? What's the present situation?

-How will Intel Mac graphic cards drivers ( which have a new and different firmware ) be used on the x86 distro?

Thanks.

---

### Post by learning_bird on 2006-01-25
Just a follow-up : according to these news ( [http://news.com.com/2061-10791_3-6030005.html](http://news.com.com/2061-10791_3-6030005.html) , brought to my attention through arstechnica ) Red Hat is starting the work to boot RH-Fedora on the new Macs.

"Red Hat spokeswoman Gillian Farquhar confirmed last week that the company hopes to help its developers figure out how to get Linux working on the new Macs. "That's definitely happening," Farquhar said of the effort, though it hasn't gone far because the Linux seller doesn't yet have any of Apple's new machines."

---

### Post by mscman on 2006-01-25
[QUOTE=learning_bird] -How does Ubuntu - Debian deals with the EFI bootloader on the new Macs?[/QUOTE]
I'm curious about this as well.  I know that the EFI bootloader is what's preventing the new Intel Mac owners from running Windows on them, although I don't really know why they would want to (NOT trying to start a flame war here, I'm just saying there are enough ports of Windows software for Mac users anyway...)  Are there ways around this problem with linux?

---

### Post by learning_bird on 2006-01-25
The "Windows on Intel Macs" problem seems to be caused by the fact that MS don't have any EFI implementation even on the most recent builds of Vista Beta than EFI itself. And ELILO is prepared to boot EFI only on Itanium processors.

So the question remains : what work is being done on ELILO or another EFI "bootloader" on Ubuntu-Debian?

---

### Post by slux on 2006-01-25
[QUOTE=mscman](NOT trying to start a flame war here, I'm just saying there are enough ports of Windows software for Mac users anyway...)  Are there ways around this problem with linux?[/QUOTE]

Why did you make the remark then? What's enough? Even if there was exactly one piece of software not ported that might be very important for someone. Just keep in mind that not everyone has the same software needs as you and the world'll be a better place with less flamewars.

---

