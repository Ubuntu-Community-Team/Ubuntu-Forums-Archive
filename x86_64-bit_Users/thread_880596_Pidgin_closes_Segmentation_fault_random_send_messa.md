---
title: "Pidgin closes Segmentation fault random send message"
date: 2008-08-05
forum: x86 64-bit Users
---

### Post by lferree on 2008-08-05
I just wanted to post this for those who may be having this problem.  If you run Pidgin from terminal, it closes with Segmentation fault after sending/receiving IM.  When you login, Pidgin closes after sending/receiving a message.

For the life of me I couldn't figure this out and I thought a bad update came thru, living with it by using Kopete for a while.  Not being a KDE-ish fan, I decided I must get Pidgin going again.

Looking back, I suspect PulseAudio has something to do with this.  I used it for a while, had more problems than it was worth, and went back to ALSA.
[COLOR="Red"]
The fix for me, was going into Pidgin -- Tools / Preferences / Sounds tab and changing Sound Method from Automatic to ALSA.[/COLOR]

So I guess every time an IM went in/out *and it makes its little noise* it crashed when it wasn't going thru the proper audio source.

I hope this helps someone.

---

### Post by Altay_H on 2008-08-12
Thanks for posting. I've been having this issue as well. It just randomly started when I booted up today. Unfortunately your solution didn't work for me, but it's better than nothing. I wish the error was more specific...

---

