---
title: "32 to 64 bit"
date: 2006-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Miakehl on 2006-03-11
I have the 32bit version of breezy installed on my averatec 6240 laptop and nothing seems to be working correctly. I have had the 64bit version installed before and everything work as far as I could tell. Is there any vital incompatibilities with the 64bit version and things such as mpegs, dvds, mp3s, or flash support? I really dont like the 32bit very much.

_Mia

---

### Post by vodgut on 2006-03-12
Some movie formats can be difficult, if there are no codecs compiled for 64-bit versions of the software (like totem).  You can install mplayer which will play some of the movie files, but not always as well.  I haven't yet tested whether or not I can play all my movies.  The 64-bit version of xmms works fine for mp3's.  Most of the incompataiblities arise when you have a 64-bit app and 32-bit plugins.

There's a wiki entry on Flash and Java here:

[https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

It worked for me, but yeah, you have to install the 32 bit version of FireFox.

---

### Post by Coolit on 2006-03-12
After reading another post on the forums where they recommended 64Bit users should try VLC for media files I tried it and its played everything I've thrown at it so far, it doesn't rely on the win32codec package where the problem lies.

So VLC will take care of most of your needs media wise ;)

---

### Post by Miakehl on 2006-03-12
Where can I get Vlc? Is it hard to aquire?

---

### Post by Coolit on 2006-03-12
I just installed it from the apt repo after adding some sources to my source list, I think I just enabled multiverse and universe, try that first :-) It wouldn't do any harm to add a back-ports repo also when your enabling multi/universe.

---

### Post by otake-tux on 2006-03-14
[QUOTE=Coolit]I just installed it from the apt repo after adding some sources to my source list, I think I just enabled multiverse and universe, try that first :-) It wouldn't do any harm to add a back-ports repo also when your enabling multi/universe.[/QUOTE]


I have vlc yet when I try to play an avi file, I get no sound.  

ideas?

---

### Post by Bandit on 2006-03-14
I have the latest version of Xine 1.1.1 and also have Totem 1.3.1 debs on my site for download for Breezy 64bit. Uninstall your current version of Totem before installing to avoid conflicts. Works very well. It can also be used to play MP3s.
Cheers,
Joey

---

### Post by Coolit on 2006-03-14
I would also ensure you have installed all the gstreamer plugins.

EDIT: Thanks for the .debs Bandit, grabbed X-chat, xine and Totem :-)

---

