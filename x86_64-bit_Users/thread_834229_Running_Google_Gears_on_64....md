---
title: "Running Google Gears on 64..."
date: 2008-06-19
forum: x86 64-bit Users
---

### Post by Dark_Fire on 2008-06-19
Yea I know, its only called "Gears" now... But "Gears" has no meaning in a Title, and google still makes it... :P

Anyway, so I found out Gears is not supported by 64 bit processors. Can anyone help me by any chance?

They said I should use "nspluginwrapper" but im not sure how to? Im running Ubuntu 8.04 64 with FireFox3 and Opera...

Thanks in advnace...

---

### Post by northwestuntu on 2008-06-19
i am also waiting for a 64bit version of gears.  i think you could install the 32bit version of firefox 3 and it should work?

i've heard it should be out soon for 64bit firefox.

---

### Post by Dark_Fire on 2008-06-21
> **northwestuntu said:**
> i am also waiting for a 64bit version of gears.  i think you could install the 32bit version of firefox 3 and it should work?

I've heard it should be out soon for 64bit Firefox.

:/ I never used it before, but it sure sounds awesome... Just hoped I could get it...

According to Google there is a way to install in on 64bit computers... But cant seem to get that to work thou.

Anyway, thanks allot.

---

### Post by cariboo on 2008-06-22
Here is a snippet from the script I use to install flash10.
You can use it as an example to help install the plugin for google gears:

```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so Firefox can find it."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
```

These are for the flash plugin so you will have to change libflashplayer.so to the google gears file.

Good luck

Jim

---

### Post by Dark_Fire on 2008-06-22
> **cariboo907 said:**
> Here is a snippet from the script I use to install flash10.
You can use it as an example to help install the plugin for google gears:

```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so Firefox can find it."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
```

These are for the flash plugin so you will have to change libflashplayer.so to the google gears file.

Good luck

Jim

well the Google Gears file, when I extract it, consists of a lot of files. I tried the .so file but it just said it "is not a valid NPAPI plugin".

I tried so with all the other files that came in the package... Same message.

Any other ideas?

---

### Post by cariboo on 2008-06-22
Maybe you could post a link to the instructions that say you have to use nspluginwrapper.

Jim

---

### Post by Dark_Fire on 2008-06-24
Hey, here is a link:
[http://code.google.com/support/bin/answer.py?answer=83194&topic=11691](http://code.google.com/support/bin/answer.py?answer=83194&topic=11691)

There are 2 options. Thats from google's support page...

cariboo907: Thank you so much for all your effort so far!

---

### Post by The_pensive on 2008-07-16
I followed different instructions to get gears in FF3... now i can see in the list of addons...but it doesn't seem to be working. Reading in google code forum, they said they 'would' develop gears for 64bit, but simply cannot due the testing time, and so on.. 
I guess why it's been sold a 64bit processor, if few software run on it...

---

### Post by mohdshakir on 2008-09-05
There's an article on installing this on 64-bit linux at [Techrecipes]("http://www.techrecipes.net"):
[http://www.techrecipes.net/linux/google-gears-in-64-bit-linux.html]("http://www.techrecipes.net/linux/google-gears-in-64-bit-linux.html")

I've personally installed it on Hardy and it works just great

---

### Post by PuleX on 2008-09-07
> **mohdshakir said:**
> There's an article on installing this on 64-bit linux at [Techrecipes]("http://www.techrecipes.net"):
[http://www.techrecipes.net/articles/google-gears-in-64-bit-linux.html]("http://www.techrecipes.net/articles/google-gears-in-64-bit-linux.html")

I've personally installed it on Hardy and it works just great 

The patched addon linked from Techrecipes works for me. However, I sometimes get a Firefox popup error message about the fact that this addon cannot be (automatically) upgraded.

---

### Post by The_pensive on 2008-09-16
Thanks for the article. I'll try it.

---

### Post by jaduncan on 2009-02-03
I've just posted updated and legacy builds of Gears at [http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html]("http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html")

---

### Post by jaduncan on 2009-02-03
I have put up a working 64 bit binary for the most recent Gears as of 02/02/09 and the legacy versions at [http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html]("http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html")

So no upgrade notices, and Offline Gmail works smoothly.

---

### Post by johnjohn2 on 2009-02-04
> **jaduncan said:**
> I have put up a working 64 bit binary for the most recent Gears as of 02/02/09 and the legacy versions at [http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html]("http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html")

So no upgrade notices, and Offline Gmail works smoothly.

Thanks man downloading now

---

### Post by eris23 on 2009-05-15
New version at [http://jms.id.au/~shenki/gears/gears-linux-x86_64-opt-0.5.20.0.xpi](http://jms.id.au/~shenki/gears/gears-linux-x86_64-opt-0.5.20.0.xpi)

---

### Post by Vadi on 2009-07-09
> **eris23 said:**
> New version at [http://jms.id.au/~shenki/gears/gears-linux-x86_64-opt-0.5.20.0.xpi](http://jms.id.au/~shenki/gears/gears-linux-x86_64-opt-0.5.20.0.xpi)

Doesn't work on ff 3.5

---

### Post by Linux Kelley on 2009-07-09
> **jaduncan said:**
> I have put up a working 64 bit binary for the most recent Gears as of 02/02/09 and the legacy versions at [http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html]("http://www.jaduncan.com/2009/02/gears-on-64-bit-gnulinux.html")

So no upgrade notices, and Offline Gmail works smoothly.

I see you have a update dated 05/18/09.

Thanks!

---

### Post by born on 2009-08-21
Hi everyone! I am using the Google Gears to use Google Agenda Offline. 
I am very glad because the applications was ported to 64 bits and run perfectly! 

 I am using Linux born-laptop 2.6.26-2-amd64 #1 SMP Fri Mar 27 04:02:59 UTC 2009 x86_64 GNU/Linux

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.7) Gecko/2009030810 Iceweasel/3.0.9 (Debian-3.0.9-1)
[B]
Thankn Joel! You are fantastic! [/B]

[http://dev.laptop.org/~joel/gears/gears-linux-opt-0.5.5.0+r3022_FIREFOX3_ONLY.xpi](http://dev.laptop.org/~joel/gears/gears-linux-opt-0.5.5.0+r3022_FIREFOX3_ONLY.xpi)

---

### Post by BadgerKid on 2009-09-16
> **Vadi said:**
> Doesn't work on ff 3.5

See this link for a version that works with firefox-3.5:

[http://code.google.com/p/gears/issues/detail?id=335#c33](http://code.google.com/p/gears/issues/detail?id=335#c33)

:)

---

### Post by davidtrounce on 2009-09-20
Any news on this issue. I cant run Google analytics without it.

Regards,

David
[http://www.gamesfromeverywhere.com.au]("http://www.gamesfromeverywhere.com.au/")

---

