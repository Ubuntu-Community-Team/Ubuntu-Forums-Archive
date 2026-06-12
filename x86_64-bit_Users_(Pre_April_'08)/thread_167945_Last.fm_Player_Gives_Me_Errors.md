---
title: "Last.fm Player Gives Me Errors"
date: 2006-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sykil on 2006-04-29
```
stephen@astarael:~/Desktop/Last.fm-1.1.4$ ./player
./player: error while loading shared libraries: libasound.so.2: cannot open
shared object file: No such file or directory
```
I have no idea what that's supposed to mean. When I used the older version, it worked just fine. I guess it should be noted that I use the precompiled binary (which, I would suppose, is 32-bit), but it worked just fine before.

P.S. You can get Last.fm Player from here: [http://www.last.fm/downloads.php](http://www.last.fm/downloads.php)

---

### Post by 23meg on 2006-04-29
See if installing libasound2 from the repositories helps. ```
sudo apt-get install libasound2 
```

---

### Post by Sykil on 2006-04-29
[QUOTE=23meg]See if installing libasound2 from the repositories helps. ```
sudo apt-get install libasound2 
```[/QUOTE]
I tried before; it's already installed.

---

### Post by ash211 on 2006-04-29
Try installing this .deb file:  [http://people.debian.org/~pxt/lastfm/lastfm_1.1.3-1ubuntu1-breezy_amd64.deb]("http://people.debian.org/~pxt/lastfm/lastfm_1.1.3-1ubuntu1-breezy_amd64.deb")

After this, I was able to run the last.fm player on my Kubuntu AMD64 box.  (I'm assuming you are running x64)

---

