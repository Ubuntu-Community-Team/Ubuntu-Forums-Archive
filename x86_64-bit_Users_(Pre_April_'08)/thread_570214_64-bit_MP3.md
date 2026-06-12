---
title: "64-bit MP3?"
date: 2007-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dark Aspect on 2007-10-08
How do I play back Mp3 files with 64-bit Ubuntu if the [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") don't install on 64-bit Ubuntu?Is there some Library I can install and use or do I have to use a 32-bit music player?

I am complete noob at 64-bit OS's and I just installed 64-bit Ubuntu.I have a few useful links and I know I have to install 32-bit fire fox for flash but I don't know if I need a 32-bit music player to play back mp3s.

---

### Post by LowSky on 2007-10-08
i got ubuntu restricted extras to install on my 64bit machine with no problem that I can remember... maybe i'm wrong...

---

### Post by RomeReactor on 2007-10-08
Hi. To be able to play back MP3 files in Rhythmbox, you need to install **gstramer0.10-plugins-ugly**, same as in 32-bit.

---

### Post by FuturePilot on 2007-10-08
If I understand this right those will install fine on 64 bit. The only thing that won't are the W32 codecs.

---

### Post by Dark Aspect on 2007-10-08
> **LowSky said:**
> i got ubuntu restricted extras to install on my 64bit machine with no problem that I can remember... maybe i'm wrong...

E: Couldn't find package gstreamer0.10-pitfdll

...........Maybe I missed something.............

---

### Post by RomeReactor on 2007-10-08
[There isn't a gstreamer0.10-pitfdll for 64-bit]("http://packages.ubuntu.com/feisty/libs/gstreamer0.10-pitfdll"), apparently; as for w32codecs, in 64-bit Ubuntu you need the [w64codecs]("http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20061203-0medibuntu2_amd64.deb").

---

### Post by Dark Aspect on 2007-10-08
> **RomeReactor said:**
> [There isn't a gstreamer0.10-pitfdll for 64-bit]("http://packages.ubuntu.com/feisty/libs/gstreamer0.10-pitfdll"), apparently; as for w32codecs, in 64-bit Ubuntu you need the [w64codecs]("http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20061203-0medibuntu2_amd64.deb").
Yes I see that now,sorry.

if I remove the gstreamer0.10-pitfdll then it works with:

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

---

### Post by RedMist on 2007-10-08
I use 64bit Kubuntu. To get mp3 support in Amarok I opened a terminal and typed /usr/lib/amarok/install-mp3

Voila.....plays mp3's.

---

### Post by John.Michael.Kane on 2007-10-08
Run these commands
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

Followed by.
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

Finally, run :
```
sudo aptitude update && sudo aptitude install w64codecs gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

Hope this helps.

---

### Post by bapoumba on 2007-10-08
Moved to "x86 64-bit Users".

---

### Post by jamesford on 2007-10-08
i have yet to find a media format i cant play on my 64 bit machine and i havent done anything weird to get htem to play

---

### Post by tikal26 on 2007-10-08
for ubuntu install
ubuntu-restricted-extras

for kubuntu
kubuntu-restricted-extras

Do you have multiverse enable

---

### Post by atomicblue on 2007-10-20
Thank you!  This is very easy to do, even for a new user!

---

### Post by billmilosz on 2007-10-20
I tried that

When I did               sudo aptitude update && sudo aptitude install w64codecs gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse


I got        E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: Couldn't read list of package sources
bill@low-transcend:~$ 


so, this didn't work.

I have been trying for 2 days to get MP3 streams or files  to play on this Ubuntu 7.10  64 bit  install and haven't been able to make it work.  I hate to say it, but it's no wonder ubuntu hasn't really made more than marginal progress in replacing Windows as a desktop.

I can't get the "ugly" gstreamer codecs to install from Synaptic, I get  
 gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable

If ubuntu was so great it wouldn't be so difficult to do something simple like install an MP3 codec.

---

