---
title: "Mplayer binary codecs packages for amd64"
date: 2006-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by juah on 2006-12-09
Hi,

I've already managed pretty well IMHO to keep my Edgy simple enough regarding  flash and win32 codec issues. I've got flash 9 running via nspluginwrapper and  wmv9 working nicely with 64-bit firefox with mediaplayer connectivity and vlc.

I have copied the latest win32 (essential-20061022)
codecs in /usr/lib/win32 -folder. Now I noticed theres some binaries for amd64 architecture in [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) !
(essential-amd64-20061203). Now all this confuses me a bit, somebody plese tell me:

- What are these amd64 binaries, there's much less in that package than in i386?, certainly they're not enough to substitute the whole i386 package?
- Can I benefit using these amd64 binaries, if I changed vlc -> mplayer and used these?
- does my vlc (out of the ubuntu amd64 box) even use these i386 binaries?

---

### Post by Hallavej on 2006-12-11
You can't use win32codec on amd64 ubuntu. You may have downloaded them but they are not doing anything. Not in vlc, mplayer or any other player.
About the amd64 binaries. Cook works without them in mplayer. I dont know about the others. I dont think a lot of people use them.

---

### Post by juah on 2006-12-11
Yes it makes sense, that 64-bit programs don't use 32-bit codecs, doesn't it, 

But what about this HOWTO:

[http://www.ubuntuforums.org/showthread.php?t=75278&highlight=win32+video+codecs](http://www.ubuntuforums.org/showthread.php?t=75278&highlight=win32+video+codecs)

How come it is adviced to download 32-bit codecs and use totem-xine or xine-ui, no matter whether you're 32-bit or 64-bit Ubuntu user! 

Is it that totem-xine and xine-ui are in fact 32-bit programs though they're delivered in amd64-architecture/package?:-k

---

### Post by Hallavej on 2006-12-11
> **juah said:**
> Yes it makes sense, that 64-bit programs don't use 32-bit codecs, doesn't it, 

But what about this HOWTO:

[http://www.ubuntuforums.org/showthread.php?t=75278&highlight=win32+video+codecs](http://www.ubuntuforums.org/showthread.php?t=75278&highlight=win32+video+codecs)

How come it is adviced to download 32-bit codecs and use totem-xine or xine-ui, no matter whether you're 32-bit or 64-bit Ubuntu user! 

Is it that totem-xine and xine-ui are in fact 32-bit programs though they're delivered in amd64-architecture/package?:-k

It is just a bad HOWTO for 64 bit users because it is not clear what is relevant on 64-bit, and w32codecs are not!. Neither totem, xine or any other media player in ubuntu amd64 is a 32-bit program.

---

### Post by juah on 2006-12-12
Ok. Got it. so in that HOWTO the win32 codecs are in vain for 64-bit users.
Thanks!

---

### Post by Kilz on 2006-12-12
> **juah said:**
> Ok. Got it. so in that HOWTO the win32 codecs are in vain for 64-bit users.
Thanks!

The problem with win32 codecs is they are 32bit. The 64bit media players cant use them. Just like 64bit Firefox cant use 32bit plugins.
You can use win32 codecs. But you have to install a 32bit mplayer to do this. There is a howto in the 64bit sticky that tells how to do this. But on Edgy there is a problem installing that version. This is because of missing libraries the Ubuntu developers removed from Edgy. You may be better off compiling the mplayer 1 rc1 that doesn't need the codecs because of the FFmpeg project.

---

### Post by juah on 2006-12-12
Thanks Kilz, this is usuful information. I just thought I might try 32-bit mplayer, but maybe I stick with 64-player from RAOF repos or use VLC which does the same trick. They play almost everything I need at the moment. Wma9spdmo (Windows Media 9 Audio Speech DMO) doesn't work but maybe survive without it. For that I quess I'd have to struggle with 32-bit player and I'm not so sure if I'm prepared for that.#-o

---

