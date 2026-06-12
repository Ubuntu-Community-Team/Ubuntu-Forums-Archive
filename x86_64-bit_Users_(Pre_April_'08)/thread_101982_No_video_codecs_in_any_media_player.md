---
title: "No video codecs in any media player?"
date: 2005-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sanfam on 2005-12-11
So I've stumbled upon this little mystery for my otherwise cheery clamshell ibook...

No matter what media player I use (except for mplayer, which I cannot find to download anywhere (but as mentioned by someone else in the VLC thread, I believe) but am attempting to compile from the source as I type), I have no capacity to play any movies of almost any sort.  While I was able to accept totem not being able to play anything, vlc's failure struck me as odd.  Why would vlc, a player which is most famous for having in-built support for dozens of major types not function?  so yeah.  I'm lost.    Anybody else experience this, or perhaps have a usable binary install for mplayer-powerpc?  

I'm wondering if perhaps I have to download the individual codecs, but this need (if it so exists) has not been made paritcularly clear.  Plus, I'm kind of a n00b to linux in most respects, so while I can compile, I still can't troubleshoot compilation errors well.

I'll post updates as I get 'em.

---

### Post by kabus on 2005-12-11
Mplayer is in the multiverse repository. You have to activate it in you /etc/apt/sources.list file.


For codecs take a look here : 

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Edit : oops, don't know if this works on a mac.

---

### Post by ssam on 2005-12-11
if someone has writen an opensource codec for the format it will work on the mac, for example ffmpeg.

x86 users can also use w32codecs, which is a bundle of windows DLL files from windows media players. nobody has yet done a similar thing for powerpc.

have a good browse through synaptic and see what you can find.

---

### Post by spier on 2005-12-11
[QUOTE=Sanfam]
... except for mplayer, which I cannot find to download anywhere ...
[/QUOTE]

[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

---

### Post by Axios on 2005-12-11
[QUOTE=ssam]if someone has writen an opensource codec for the format it will work on the mac, for example ffmpeg.

x86 users can also use w32codecs, which is a bundle of windows DLL files from windows media players. nobody has yet done a similar thing for powerpc.

have a good browse through synaptic and see what you can find.[/QUOTE]


[http://www4.mplayerhq.hu/homepage/design7/codecs.html](http://www4.mplayerhq.hu/homepage/design7/codecs.html)


You can download some codecs for ppc, I just can't figure out how to use them.

---

### Post by ssam on 2005-12-11
[QUOTE=Axios][http://www4.mplayerhq.hu/homepage/design7/codecs.html](http://www4.mplayerhq.hu/homepage/design7/codecs.html)


You can download some codecs for ppc, I just can't figure out how to use them.[/QUOTE]

the powerpc codec wont download for me at the moment, so its hard to tell what you do with them.

.tar.bz2 is a bzip2 compressed tar archive. file-roller can open it. or on the command line use

```
tar -xvf filename
```
(tar should auto detect the compression type, if not use "-xvjf", see man tar for explanation)

in the archive there should be a README or INSTALL file with instructions.

---

### Post by T31 on 2005-12-14
In my case I dont use mplayer at all I just use xine-ui and it is enough, one more thing to make it work out with totem install the package totem-xine as well

:)

---

### Post by PhoenixP3K on 2006-03-28
I've been searching the forums for someone with a similar problem, and someone might be able to help me. 

I don't know if it is a coincidence, but after I installed the gnome deskbar app and all it's dependencies (like beagle)
My system lost the ability to use some codecs like DivX 5

I always use xine to play everything. But all of a sudden it started asking me this
[IMG]http://me2bz4u.com/~jkenscoff/playback.png[/IMG]
Even when I say yes there is sound but no picture. There is no image in Totem either, and in Nautilus, since then, the new files do not get a video thumbnail.

The only player that is still working fully is Mplayer. But I really don't like it and I would like my stuff to work like they did before!

I tryed uninstalling xine, the w32codecs, then re-installing. Rebooting and all.

The weird thing might be that in the xine screenshot "**The steam '/home/pho **" is an incomplete path to my file.

---

### Post by Entity on 2006-03-29
[QUOTE=ssam]the powerpc codec wont download for me at the moment, so its hard to tell what you do with them.
[/QUOTE]

Have you tried another mirror?

[http://www1.mplayerhq.hu/homepage/design7/codecs.html](http://www1.mplayerhq.hu/homepage/design7/codecs.html)
[http://www2.mplayerhq.hu/homepage/design7/codecs.html](http://www2.mplayerhq.hu/homepage/design7/codecs.html)
[http://www4.mplayerhq.hu/homepage/design7/codecs.html](http://www4.mplayerhq.hu/homepage/design7/codecs.html)

---

