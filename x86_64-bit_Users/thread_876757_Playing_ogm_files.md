---
title: "Playing ogm files"
date: 2008-08-01
forum: x86 64-bit Users
---

### Post by MeneM on 2008-08-01
Hi All,

I've been searching (googling around) the internet and these fora, but I seem to have an issue that is not very common.

I cannot play ogm files.

The sound is there, but no video, very weird.

I'm thinking the container is ogm, the sound is vorbis, but the video is xvid I think.

I've installed restricted-extras, various theora libraries, xvid codec, ffmpeg, transcode (out of pure desparation).

Even VLC let's me down, as it's not playing the video as well.

Any idea's perhaps?

---

### Post by gsmanners on 2008-08-01
Try this:

sudo apt-get install ogmtools
ogminfo <filename>

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by MeneM on 2008-08-02
Hi and thanks for replying,

The ogminfo returns this:```

mark@tpol:/mnt$ ogminfo ./Cars.ogm 
(ogminfo.c) OGG stream 1 is of an unknown type (bad header?)
(ogminfo.c) (a1/serial 1) Vorbis audio (channels 2 rate 44100)
(ogminfo.c) (a2/serial 2) Vorbis audio (channels 2 rate 44100)
```


But the file itself is identified as ogg data:```

mark@tpol:/mnt$ file ./Cars.ogm 
./Cars.ogm: Ogg data
```

The file plays just fine on other Ubuntu laptops of mine, but my new laptop with a new installation of Ubuntu no longer wants to play these files anymore.

Thanks,
Mark

---

