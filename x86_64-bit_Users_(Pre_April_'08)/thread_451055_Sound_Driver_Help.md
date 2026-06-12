---
title: "Sound Driver Help"
date: 2007-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by nirvana21 on 2007-05-21
This is the first time I have ever used Linux and im really enjoying ubuntu. But I played around a little too much and somehow totally killed my sound driver. I did not have 5.1 sound so I went to realtek's website and got their driver. That was probably the wrong thing to do, because I lost all my sound. I suppose I should have just stuck with ALSA sound but I am new and can do alot of stupid stuff. I read some stuff and tryed a few things and this is all I can tell you:

-I have intergrated sound on my Asus mobo, ac97 (I don't know much else)
      I don't know if it matters but im using amd X2 3800+

-my sound card is not on restricted drivers manager

-when I run 

sudo hdparm /dev/hdc  

I get this:

modinfo: could not find module snd
modinfo: could not find module snd
modinfo: could not find module snd
modinfo: could not find module snd-opl3sa2
modinfo: could not find module snd-cs4236
modinfo: could not find module snd-cs4232
modinfo: could not find module snd-cs4231
modinfo: could not find module snd-es18xx
modinfo: could not find module snd-es1688
modinfo: could not find module snd-sb16
modinfo: could not find module snd-sb8

So I feel really dumb and anything you could do to help would help. :neutral:

---

### Post by diddler on 2007-05-21
Which Linux driver did you try? I ask not because I have a solution to your problem, but to avoid doing the same thing to my system :)

---

### Post by nirvana21 on 2007-05-21
I downloaded it from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false")

the second one under linux (others)

---

