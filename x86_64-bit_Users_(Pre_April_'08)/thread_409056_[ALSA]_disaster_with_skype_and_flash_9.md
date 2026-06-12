---
title: "[ALSA] disaster with skype and flash 9"
date: 2007-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicoladimaria on 2007-04-14
Whenever I try to use flash 9 (which uses alsa) or skype (configured with alsa) I get this error
ALSA lib pcm.c:2064:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_empty.so

here you can find some info about my alsa config
[http://pastebin.ca/439471](http://pastebin.ca/439471)

googling around I found out that we need something similar to this *gentoo* package
emul-linux-x86-soundlibs

It looks like here
[http://forum.kubuntu.sk/viewtopic.php?pid=9692](http://forum.kubuntu.sk/viewtopic.php?pid=9692)
they fixed the problem, but I can't understand the post language

thanks

---

### Post by nicoladimaria on 2007-04-14
I fixed this.
make a backup of /usr/lib32
download this file
```
wget -c http://tinderbox.x86.dev.gentoo.org/hardened/amd64/multilib/emul-linux-x86-soundlibs-2.5-r2.tbz2
```
than rename the extension from .tbz2 to tar.bz2
extract it (ignore warning)
you'll find a directory called usr with two subdirectories, bin and lib32
copy the files of bin inside your /usr/bin and the files inside lib32 in /usr/lib32
then run ```
sudo ldconfig /usr/lib32
```
you're done
now skype works with alsa and flash 9 too

---

### Post by Cappy on 2007-04-20
Awesome, this fixed my skype/flash! I had the same problem from a fresh Feisty install. I also had to sudo apt-get install ia32-libs too. I'm not sure why this even happens. Why is it that most AMD64 users don't have this happen on a default install?

One (small) problem, when I run sudo ldconfig /usr/lib32 I get this: 

```

ldconfig: /usr/lib32/libjack.so.0 is not a symbolic link

ldconfig: /usr/lib32/libalsatoss.so.0 is not a symbolic link

ldconfig: /usr/lib32/libogg.so.0 is not a symbolic link

ldconfig: /usr/lib32/libesd.so.0 is not a symbolic link

ldconfig: /usr/lib32/libartsc.so.0 is not a symbolic link

ldconfig: /usr/lib32/libvorbisenc.so.2 is not a symbolic link

ldconfig: /usr/lib32/libartsdsp.so.0 is not a symbolic link

ldconfig: /usr/lib32/libesddsp.so.0 is not a symbolic link

ldconfig: /usr/lib32/libmikmod.so.2 is not a symbolic link

ldconfig: /usr/lib32/libaoss.so.0 is not a symbolic link

ldconfig: /usr/lib32/libaudiofile.so.0 is not a symbolic link

ldconfig: /usr/lib32/libvorbisfile.so.3 is not a symbolic link

ldconfig: /usr/lib32/libvorbis.so.0 is not a symbolic link

ldconfig: /usr/lib32/libartsdsp_st.so.0 is not a symbolic link

```

It certainly doesn't seem bad but it keeps repeating this message on new apt-get installs. I assume I'm suppose to move these files somewhere and then use symbollic links in the /usr/lib32 folder instead, but I'm not sure where to move them.

Thank you nicoladimaria!

---

### Post by nicoladimaria on 2007-04-21
uhm, I don't use feisty yet and I'm not sure this apply to feisty too.
It's sad to know that a fresh feisty install still have the problem

---

