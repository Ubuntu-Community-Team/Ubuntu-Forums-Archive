---
title: "is there a sound FAQ?"
date: 2005-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by rah on 2005-08-28
I have a AMD64 3700+ with a ASUS A8N-SLI motherboard, which has a built-in soundcard -- I think it's a Realtek ALC850.  I installed Ubuntu on this machine a couple of days ago.  I've discovered that I don't have sound.  The computer beeps when I do something it doesn't like, but when I try to play an mp3 file, Totem plays it, but I don't hear anything.

Is there some kind of sound FAQ I can look at -- some kind of checklist I can walk myself through to figure what I can do to fix this?  I know this forum must get sound questions all the time, that's why I'm looking  for some kind of reference.  (Although if anyone can help me out, I would appreciate it immensely. :smile: )

---

### Post by DancingSun on 2005-08-28
[QUOTE=rah]I have a AMD64 3700+ with a ASUS A8N-SLI motherboard, which has a built-in soundcard -- I think it's a Realtek ALC850.  I installed Ubuntu on this machine a couple of days ago.  I've discovered that I don't have sound.  The computer beeps when I do something it doesn't like, but when I try to play an mp3 file, Totem plays it, but I don't hear anything.

Is there some kind of sound FAQ I can look at -- some kind of checklist I can walk myself through to figure what I can do to fix this?  I know this forum must get sound questions all the time, that's why I'm looking  for some kind of reference.  (Although if anyone can help me out, I would appreciate it immensely. :smile: )[/QUOTE]
Just use the forum's search feature.  You'll find lots of threads about sound how-to's/problems.

---

### Post by Steve1961 on 2005-09-04
If you're getting some sound from your system, even just error messages, try one of these links:

[http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon](http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon)

[http://ubuntuforums.org/showthread.php?t=32063&highlight=gandalf+sound](http://ubuntuforums.org/showthread.php?t=32063&highlight=gandalf+sound)

The first option produces much better quality sound in my MSI K8 Neo4 Platinum.

If you can't get any sound at all you could try following this how to, but just adapt it for your sound chip by searching the alsa website for the driver you need.

[http://ubuntuforums.org/showthread.php?t=19307&highlight=soundblaster+24](http://ubuntuforums.org/showthread.php?t=19307&highlight=soundblaster+24)

Hope this helps.  I initially had startup and sustem sound but couldn't play oggs in XMMS until I followed the first link and then set XMMS's sound driver to esd.

Also, don't forget to install all the codecs listed in the ubuntu guide.

---

