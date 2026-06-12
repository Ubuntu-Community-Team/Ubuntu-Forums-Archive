---
title: "Help getting Fraxy running under Linux"
date: 2008-02-14
forum: Wine
---

### Post by Crembo on 2008-02-14
Hello, first post by a linux newbie here!

I've been trying to get [Fraxy]("http://mokeron.hp.infoseek.co.jp/zg/fraxy_main.html")(Also on [TIGSource]("http://tigsource.com/articles/2007/05/16/fraxy")!), an awesome bossrush make-your-own boss shooter (page in Japanese), working under Linux through WINE. Unfortunately I get an illegible error message, and WINE isn't handling the Japanese characters so I can't even begin to try and debug the problem.

Can anyone help?
Edit: I should probably add more information. I use Ubuntu 7.10, use WINE 0.9.45 from the winehq.org repos, I have an ATI Radeon 9800 card, I managed to get Knytt Stories working perfectly with music too and finally when running the game via terminal there is no output at all...

---

### Post by Crembo on 2008-03-07
Bump.

---

### Post by happyhamster on 2008-03-08
- Make sure you have Japanese language support installed (System-->Administration-->Language Support). After installing, you'll have to reboot.

- You can then start wine like this:

LANG=ja_JP.UTF-8 wine program_name.exe

Good luck, and let us know if it worked.

---

### Post by Crembo on 2008-03-08
Well, it did work. Now I get an error message in Japanese. How do I copy-paste that into google translation or some such?

---

### Post by happyhamster on 2008-03-08
I don't know actually. Perhaps you could try opening a topic in General Help or the Community Cafe. Just ask for someone who can read Japanese and attach a screenshot. That's what I would do anyway :)

---

### Post by subverted on 2008-04-24
> **Crembo said:**
> Hello, first post by a linux newbie here!

I've been trying to get [Fraxy]("http://mokeron.hp.infoseek.co.jp/zg/fraxy_main.html")(Also on [TIGSource]("http://tigsource.com/articles/2007/05/16/fraxy")!), an awesome bossrush make-your-own boss shooter (page in Japanese), working under Linux through WINE. Unfortunately I get an illegible error message, and WINE isn't handling the Japanese characters so I can't even begin to try and debug the problem.

Can anyone help?
Edit: I should probably add more information. I use Ubuntu 7.10, use WINE 0.9.45 from the winehq.org repos, I have an ATI Radeon 9800 card, I managed to get Knytt Stories working perfectly with music too and finally when running the game via terminal there is no output at all...

By the way, how did you get the sound working for KNYTT. I have it working in WINE now but no sound.

---

### Post by Crembo on 2008-04-25
To get sound working in Knytt, I configured WINE to use ALSA (and only ALSA) as a sound driver. Check it out at the appropriate tab in the WINE configuration utility.

---

### Post by subverted on 2008-04-27
> **Crembo said:**
> To get sound working in Knytt, I configured WINE to use ALSA (and only ALSA) as a sound driver. Check it out at the appropriate tab in the WINE configuration utility.

No such luck on my end. I even upgraded to latest version of Wine. I'm using Fedora 8 though. Of course, Nifflas or someone might consider how to make a version of Knytt compatible with Linux. I'm not sure how to do that myself. Stupid question of course, is there a way to make an .exe file into a linux bin file? I really know nothing about it, but since Knytt isnt a truly installable program even in windows, could one convert the exe to source using some other program then make it executable in Linux using "chmod". There's something called reflector that might open the source for Knytt, but I'm not sure. I'll give it a try myself. Not sure if it works on linux...

[http://www.aisto.com/roeder/dotnet/](http://www.aisto.com/roeder/dotnet/)

---

### Post by Crembo on 2008-05-01
Cross-compilation - **not** recommended. Knytt is written in multimedia or games factory and those systems are not linux-able.

The game really only has trouble installing. Once unpacked, it should work fine... Perhaps you can get a windows-enabled friend to unpack it for you?

---

### Post by subverted on 2008-05-05
> **Crembo said:**
> Cross-compilation - **not** recommended. Knytt is written in multimedia or games factory and those systems are not linux-able.

The game really only has trouble installing. Once unpacked, it should work fine... Perhaps you can get a windows-enabled friend to unpack it for you?

By the way, I just got the sound to work. The problem was strangely connected to Firefox browser. I was trying to figure out what was crashing my Gecko Firefox on flash vids. I got around to finding out it was something called pulseaudio alsa. It was recommended to remove this from Firefox and from Linux in general, so I did it. Strangely, I think the fact of its being installed outside of WINE was causing conflicts. Alsa only works when installed in WINE alone, and actually doesn't even seem useful elsewhere in Linux. But the sound works now in Knytt, which is okay with me. Maybe my browser stops crashing too.
 
This is the line to remove pulseaudio and Alsa:

yum remove kde-settings-pulseaudio alsa-plugins-pulseaudio

---

