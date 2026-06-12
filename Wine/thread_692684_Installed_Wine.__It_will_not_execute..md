---
title: "Installed Wine.  It will not execute."
date: 2008-02-10
forum: Wine
---

### Post by awilki01 on 2008-02-10
I followed the procedure at this url to install Wine on Gutsy Ubuntu:
 
[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")


Everything seemed to go perfect during install.  I even have it listed under my applications list.  When clicking on it, it does absolutely nothing.  Even the 'configure wine' option doesn't do anything.

I tried 'winecfg' from a terminal and get the following:

```

adam@adam-ubuntu:~$ sudo winecfg
wine: creating configuration directory '/home/adam/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/adam/.wine'.
adam@adam-ubuntu:~$ wineserver: could not save registry branch to /home/adam/.wine-HWdMzf/system.reg : No such file or directory
wineserver: could not save registry branch to /home/adam/.wine-HWdMzf/user.reg : No such file or directory

```

Any ideas?

---

### Post by Whiffle on 2008-02-10
First try 
```

sudo rm -fr /home/adam/.wine  #this will delete your .wine directory

``` 


Then, try running wine without sudo, wine doesn't need sudo to run.

---

### Post by awilki01 on 2008-02-10
Thanks!  I removed the /home/adam/.wine

However, I'm still getting:

```

adam@adam-ubuntu:~$ winecfg
wine: creating configuration directory '/home/adam/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/adam/.wine'.
adam@adam-ubuntu:~$ wineserver: could not save registry branch to /home/adam/.wine-IWLYRj/system.reg : No such file or directory
wineserver: could not save registry branch to /home/adam/.wine-IWLYRj/user.reg : No such file or directory

```

---

### Post by Whiffle on 2008-02-10
I see the problem but I really have no idea whats causing it.  It looks liek its creating a directory called .wine, as it should, but it is trying to save to a directory called .wine-IWLYRj, which isn't what it should do.  Thats a new one...hmm.

---

### Post by awilki01 on 2008-04-16
Anyone else have any ideas what may be happening here?  I tried reinstalling it...

```

adam@adam-ubuntu:~$ winecfg
wine: creating configuration directory '/home/adam/.wine'...
ALSA lib ../../src/confmisc.c:769:(parse_card) cannot find card ''
ALSA lib ../../src/conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib ../../src/confmisc.c:769:(parse_card) cannot find card ''
ALSA lib ../../src/conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
Could not load Mozilla. HTML rendering will be disabled.
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/adam/.wine'.
adam@adam-ubuntu:~$ wineserver: could not save registry branch to /home/adam/.wine-5nejpv/system.reg : No such file or directory
wineserver: could not save registry branch to /home/adam/.wine-5nejpv/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/adam/.wine-5nejpv/user.reg : No such file or directory

```

---

### Post by Caesum on 2008-04-16
I was having this problem with winecfg seg faulting and it turned out to be my video drivers (nvidia with an 8800gt graphics card). Reinstalling the video drivers properly sorted it out

---

### Post by awilki01 on 2008-04-17
I have an 8800gt.  I'll have to try that.  Thanks!

---

