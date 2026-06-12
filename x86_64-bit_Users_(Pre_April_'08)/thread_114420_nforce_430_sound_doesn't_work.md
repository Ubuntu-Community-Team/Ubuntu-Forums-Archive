---
title: "nforce 430 sound doesn't work"
date: 2006-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by gakrivas on 2006-01-08
I am using a GA-K8N51GMF-9 motherboard, which contains an integrated nforce 430 sound chip. I am using Breezy AMD64. I can't get the sound to work. I have tried both the driver contained in the kernel and the driver that nvidia offers. lspci|grep snd  returns nothing.

Any help?

---

### Post by WelterPelter on 2006-03-27
Did you get this to work? I just bought the same board.

---

### Post by shambling on 2006-03-28
see:
[http://www.nvnews.net/vbulletin/showthread.php?t=57791](http://www.nvnews.net/vbulletin/showthread.php?t=57791)

&

[http://www.ubuntuforums.org/showthread.php?t=150387&highlight=nforce](http://www.ubuntuforums.org/showthread.php?t=150387&highlight=nforce)

Have not had time to read through the nvidia fourms fully, or setup alsa yet.

Installed 0310 nforce driver, works to a point. Only media players that use OSS work, anything that trys to use alsa fails to work, alsa mixer cant find card.

Hope this helps in some way.

---

### Post by arubin on 2006-04-10
Have you tried modprobe snd-hda-intel?

---

