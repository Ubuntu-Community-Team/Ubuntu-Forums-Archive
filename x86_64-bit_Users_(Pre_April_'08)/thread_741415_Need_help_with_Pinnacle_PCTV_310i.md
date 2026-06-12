---
title: "Need help with Pinnacle PCTV 310i"
date: 2008-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by LeonHeart on 2008-03-31
Hi guys, 
I recently bought a Pinnacle PCTV 310i tv card (Analog/DVB/Radio).
But I can't make it work.
I have found a few thing over the net but they didn't help.
Can anyone help me make my card work???

---

### Post by LeonHeart on 2008-04-13
Please guys, anyone???

---

### Post by mesilikas on 2008-04-13
&#915;&#949;&#953;&#940; &#967;&#945;&#961;&#940; &#966;&#943;&#955;&#949; &#960;&#945;&#964;&#961;&#953;&#974;&#964;&#951;.):P
It should we give the following solution in the English in order to can also other users use him.
Have also I same card TV and also I could not hear sound but completely accidentally fell on t o this n driver:

[http://www.cyberciti.biz/tips/debian-ubuntu-linux-configure-pinnacle-pctv-tuner.html#comment-143386]("http://www.cyberciti.biz/tips/debian-ubuntu-linux-configure-pinnacle-pctv-tuner.html#comment-143386")

This driver worked but only if each time where I run the TVTIME I run also this command:

```
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp
```

I wish to help you :)

---

### Post by abbas1872 on 2008-05-29
goto this address and follow the instructions [http://www.parker1.co.uk/mythtv_ubuntu.php](http://www.parker1.co.uk/mythtv_ubuntu.php)

---

### Post by adad on 2008-06-12
Have a look at this page:

[http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_310i](http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_310i)

I had no problems with Hardy Heron 64-bit recognizing both the analog and the digital part of the card. It configured everything correctly from the begining.

I just did a fresh install, then installed tvtime and had it scan for the channels.

---

