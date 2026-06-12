---
title: "need banshee help"
date: 2007-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by elmo541992 on 2007-06-19
I'd like to use banshee for my media player, because it'll read my iPod and is very similar to itunes.  I've tried to play the mp3 and aac songs from my iPod, and it says there no codec.  where can i get the codec for this??  I've looked in the package manager, and i couldn't really find any thing.  so if someone could help me play mp3 and aac in banshee, or convert them to ogg, that would be greatly appreciated.

---

### Post by John.Michael.Kane on 2007-06-19
Run this in terminal.
```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse 
```

For further codec installs eg dvd playback run these commands

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

Finally, run :
```
sudo aptitude update
```

```
sudo aptitude install totem-xine libdvdcss2 w64codecs acidrip brasero libxine-extracodecs
```

For any other programs eg: flash java wine read here
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by elmo541992 on 2007-06-19
thanx lots!!!!

---

### Post by gauteh on 2007-11-24
> **elmo541992 said:**
> thanx lots!!!!

Hey does this still work? installing medibuntu broke my banshee mp3 support.. it neither wants to compile from source.

im 32 bit.

- gaute

---

### Post by tallgurl1337 on 2007-12-14
I had the same problem with codecs, but I input those codes into terminal, and now the songs just won't play!
Sound works just fine in all other programs, and banshee pops up to remind me that I'm "listening" to a particular song, though there is no sound coming from the program...:confused:

---

