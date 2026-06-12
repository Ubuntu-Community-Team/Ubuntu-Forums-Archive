---
title: "vlc seg faulting?"
date: 2006-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by brodieboy on 2006-10-31
hello, I just did a fresh install due to upgrade problems, and now when I try to watch a DVD with VLC, this is the output:

...
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
Segmentation fault (core dumped)

and thats it, no more. Has anyone else noticed this?
of course, this in on an AMD 64 bit system....

---

### Post by BatteryCell on 2006-10-31
You have libdvdcss right?

---

### Post by kuja on 2006-10-31
I'm not sure if this is 64-bit specific or not, but I just gave it a try and it gave me a segmentation fault as well.

---

### Post by brodieboy on 2006-10-31
Right on now we are getting somewheres....
I am originally a Gentoo user, and somewheres in this form someone linked to Sabayon linux, am grabbin it right now...

To answer yes I installed libdvdcss and that error I posted is after it grabs keys (unencrypting) .
Where did yours seg fault?

---

### Post by kuja on 2006-10-31
Same place.

---

### Post by brodieboy on 2006-11-03
###BUMP###
so is anyone else in x86_64 Edgy land experiencing a VLC crash while trying to play a DVD? Or is it only kuja and myself with this unfortunate deal....

---

### Post by kuja on 2006-11-03
If you haven't already, you should file a bug report in launchpad. (I'd do it, but I'm strapped for time at the moment. For now, you could use any other player, of course. I thin RAOF said he has the release candidate of mplayer in his repos. (?Janvitus?). Anyhow, we're probably out of luck at getting this version of VLC playing DVDs.

---

### Post by Azakus on 2006-11-03
I've had this happen before too. The way I solved it was by removing the config files in "~/.vlc".
Worked perfectly after that.

---

### Post by wilspa on 2006-12-23
I am having the same problem as the others. I looked for a config file in ~/.vlc, but couldn't find one. I am also using a 64 bit Athalon processor, and I have libdvdcss installed.

---

### Post by Azakus on 2006-12-24
You won't directly see a file with a period infront of it because those files are hidden. Run this code and try VLC again.
```
rm ~/.vlc
```
Also, you shouldn't post to a thread that is over a month old. It might not get an answer.

---

### Post by tomdkat on 2007-03-13
> **Azakus said:**
> I've had this happen before too. The way I solved it was by removing the config files in "~/.vlc".
Worked perfectly after that.You rock!  I had vlc problems (not segfaults, it just wouldn't run) and doing this solved my problem too!  :)

Peace...

---

### Post by azazel00 on 2007-04-17
My vlc wont run either. Ever since I moved to Feisty.

```
azazel@ubuntux:~$ vlc
VLC media player 0.8.6 Janus
Segmentation fault (core dumped)

```

I tried to remove the .vlc but it isnt even created (I guess since it never actually ran, it didnt create the config files).

---

