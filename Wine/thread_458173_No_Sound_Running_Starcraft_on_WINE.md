---
title: "No Sound Running Starcraft on WINE"
date: 2007-05-29
forum: Wine
---

### Post by Tyke91 on 2007-05-29
hey guys! the title kinda says it all.


I'm an Ubuntu noob - I've been using it for around 9 days now and it's the best OS I've ever used..

however, I need to dual boot to windows just to play games, and I'm trying to get around that with my favorite game - Starcraft.

I downloaded Wine from the add/remove programs list and installed starcraft with it... It loaded great and i can play... but there is no sound. 

The sound is kind of crucial since it tells you whether you are being attacked or not.


has anyone else had this problem?


I'm running Feisty 32 bit.

---

### Post by Rospo Zoppo on 2007-05-29
Hi, try going into winecfg (type it in a terminal) and set the audio to Oss and Full Emulation. This settings worked to me :D

---

### Post by Tyke91 on 2007-05-29
I get this error when i try to do that

```

mykola@MykolaUbuntu:~$ winecfg
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

```

---

### Post by Tyke91 on 2007-05-29
LOL... surprisingly, it still works.

thanks m8

---

### Post by Tyke91 on 2007-05-29
Ah... but now it's got a different issue


Battle.Net wont work.

---

### Post by AvixK7 on 2007-06-06
I'm currently having a problem with Starcraft as well. When selecting OSS, there is no sound whatsoever. using ALSA has so far worked better but as soon as I enter a campaign mission, the sounds begin to stutter and loop without end.

any suggestions? as I've said, OSS doesn't work for me :(

thanks

PS. I'm using Feisty.

---

### Post by `GooZ´ on 2007-06-06
...try setting everything in winecfg to 'emulation'. It worked fine for me when using ALSA.

---

### Post by Tyke91 on 2007-06-06
yep. emulation works.

also, there is a downloadable add on to let battle.net work (though i can't remember where it is)

the performance is still shoddy, but once you get into the game online, it works perfectly.

---

### Post by Amyn on 2007-06-06
"also, there is a downloadable add on to let battle.net work (though i can't remember where it is)"

I have the same problem with Battle.net.  If you remember/come across it again, would you mind posting it here or pming it to me?

Thanks,

Amyn

---

### Post by AvixK7 on 2007-06-13
Sound is working now :) there's some persistent static sometimes but not loud enough to be distracting once you're playing. 

Thanks for the help :)

Dan

---

### Post by birddog165 on 2008-10-21
Hmm, mine only works when I change it to the ALSA drivers. Is that bad?

---

### Post by Ripfox on 2008-10-21
No. Whatever works with your hardware...Wine can be a fickle beast.

---

