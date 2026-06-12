---
title: "Flash issues on Jaunty amd64"
date: 2009-04-28
forum: x86 64-bit Users
---

### Post by karimruan on 2009-04-28
Hey I am running 9.04 x64 edition on my HP dv67000 with an AMD Turion x64 mobile processor, dual booted with windows vista SP1. I cannot get flash to function properly in my browser (firefox 3.0). I get the menu to appear but cannot click any buttons. A prime example is the game at darkorbit.com. I cannot click on the start button with loads the game. Same with YoVille on myspace/facebook, and a few websites I have made with Windows. Any one have any idea as to what I could do?

---

### Post by cjazz on 2009-04-29
What version of Flash are you using -- Adobe, swfdec, gnash? How did you install it?

---

### Post by karimruan on 2009-04-29
Not sure what version. I was in firefox, and it said to install the plugins, so i did. I did it right from that little pop up window.

---

### Post by Geekkit on 2009-05-02
It's broken:

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/320196](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/320196)

---

### Post by inobe on 2009-05-02
if anyone has upgraded **swfdec-mozilla** is the problem, remove that in synaptic.

---

### Post by interceptorV8 on 2009-05-05
> **inobe said:**
> if anyone has upgraded **swfdec-mozilla** is the problem, remove that in synaptic.


THANK YOU.  problem solved!    AS SOON (the VERY SECOND) as i uninstalled it, the flash movie started playing.

---

### Post by trash on 2009-05-05
swfdec-mozila wasn't the problem for me, but this thread fixed it..

[http://ubuntuforums.org/showthread.php?t=1134734&highlight=opera+64+flash&page=2](http://ubuntuforums.org/showthread.php?t=1134734&highlight=opera+64+flash&page=2)

---

### Post by karimruan on 2009-06-29
I have the non free version of adobe flash player 10. I have tried everything I can think of, from switching the directory that libflashplayer.so is in to reinstalling several times. Basically, my wife needs to play yoville on ubuntu so that I have a reason to kick windows. That is all she uses it for. Buttons just don't work with flash games for me. Anyone have any suggestions?

---

### Post by philinux on 2009-06-29
First this.

Use synaptic and uninstall all flash.

```

Then
sudo updatedb

and

locate libflashplayer.so


```
Make sure all instances gone.
Get the 64 bit flash from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Unpack the tar file and move the libflashplayer.so file to:-

/home/user/.mozilla/plugins

create the above directory if not already.

---

