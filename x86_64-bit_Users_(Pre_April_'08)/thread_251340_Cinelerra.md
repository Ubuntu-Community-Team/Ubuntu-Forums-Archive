---
title: "Cinelerra"
date: 2006-09-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by ColinG on 2006-09-05
Has anybody managed to get Cinelerra running on  Ubuntu or Kubuntu 64 bit? If so how please?

Thanks
Colin

---

### Post by kuja on 2006-09-05
Well, as far as I can tell, it's not in the main repositories.

You can get the source for Cinelerra [here](http://heroinewarrior.com/download.php3).

To compile it will probably be something like this.
```

tar jxvf cinelerra-2.1-src.tar.bz2
cd cinelerra-2.1-src
make
sudo make install

```

Give it a try and let me know, meanwhile, I think I might set it up and take it for a spin myself.

Edit: On second thought, this isn't going to work too well on dapper. It requires a few things that more or less require edgy (gcc-4.1, newer kernel, stuff like that). Fooey. Oh well. Maybe an outdated version would work....

---

### Post by ColinG on 2006-09-05
Hi Kuja,

I think you will find the compile much harder than that. There are many threads on this forum re building the package and it looks to be a nightmare. 

Good luck though and if you do crack it shout very loudly.

Colin ;)

---

### Post by kuja on 2006-09-05
So I noticed. Maybe an older version will compile?

---

### Post by kievking on 2006-09-05
Scroll down to the fisherman's reply. 

[http://ubuntuforums.org/showthread.php?t=244862&highlight=fisherman](http://ubuntuforums.org/showthread.php?t=244862&highlight=fisherman)

---

### Post by kuja on 2006-09-05
I do believe we're looking for a 64-bit build here kievking. I've run across those already, and they're all 32-bit.

Oh, and I've been working at getting cinelerra to compile for the last couple hours. It's rough going, but progress seems to be being made. It's a lot of work though. Unless you're really desperate to get it working, this is probably WAY too much work. I think  my current issue is something to do with mjpeg tools ...

---

### Post by ColinG on 2006-09-06
Sure are talking 64 bit. 

Cinelerra is a jerky as hell in 32 bit; at least the version I got hold of was. The new Mandriva (2007) has Cinelerra in its repositories and it runs better - vid playback is still not as smooth as Kino but it is useable.

---

### Post by aouie on 2007-06-28
As has been pointed out in other places, the AMD64 packages for edgy listed at the [Cinelerra CV site]("http://cvs.cinelerra.org") works in feisty too.
Sincerely,
Aouie

---

### Post by benplanet on 2007-07-04
[https://help.ubuntu.com/community/CinelerraOnFeistyAMD64](https://help.ubuntu.com/community/CinelerraOnFeistyAMD64)

---

