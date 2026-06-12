---
title: "Gnome MPlayer and real audio..."
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by hajk on 2008-01-27
OK, I have installed the essential codecs in /usr/local/lib/codecs, and kmplayer will play real streaming media using these codecs. But kmplayer is a KDE application, and installing it also loads tons of KDE stuff -- I don't want that. 

The Xine engine does use those codecs, but produces garbled sound (the mplayer home site warns about that).  

So, then there's mplayer, and also gnome-mplayer: should be able to find those codecs, right? But I haven't been able to get them to play real streaming media -- a configuration issue? 

Advice from mplayer gurus appreciated!

---

### Post by prince_niceguy on 2008-01-28
install vlc... it is one stop shop... and it is gtk app. so no need to worry. also it has mozilla plugin which plays almost all files on the different web sites. I think real does not work in it. you can use helix player... that too is gtk app i think

---

### Post by hajk on 2008-01-28
Yes, I know about VLC, and no, it doesn't handle real media (a matter of principle). So, seeing that I do have a rather large HD, I've repented and installed kmplayer (plus all KDE stuff that comes with it). Plays real media like a charm, using the essential codecs from the MPlayer home site.:)

---

### Post by prince_niceguy on 2008-01-28
have you tried smplayer. it is like kmplayer but for gtk.

---

### Post by hajk on 2008-01-28
Nope, doesn't work either! Strange... what is it that kmplayer does and {g,s}mplayer doesn't?:confused:

---

### Post by rvm4000 on 2008-01-28
> **prince_niceguy said:**
> have you tried smplayer. it is like kmplayer but for gtk.

Actually SMPlayer uses Qt (Qt only, it won't install anything from kde, well at least with [my packages](http://smplayer.sourceforge.net/downloads.php)).

> **hajk said:**
> Nope, doesn't work either! Strange... what is it that kmplayer does and {g,s}mplayer doesn't?:confused:

SMPlayer should play real files, as long as the essential codecs are installed. Take a look at the mplayer log (Options -> View logs), does mplayer complain about something?

---

### Post by prince_niceguy on 2008-01-28
> **rvm4000 said:**
> Actually SMPlayer uses Qt (Qt only, it won't install anything from kde, well at least with [my packages](http://smplayer.sourceforge.net/downloads.php)).


I thought SMplayer was gtk... realised that i am wrong...thanks for pointing that out. :)

---

