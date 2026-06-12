---
title: "X Server Animating Too Fast!"
date: 2006-08-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by RAdams on 2006-08-27
My X Server is going crazy! Everything moves too fast - flash animations, games, gifs, even the blinking cursor... I can't think of any change that would have affected it so, except possibly a recent update push that upgraded my libmesa (but I use fglrx).

Sometimes, when I hit a key on my keyboard, it will repeat that key 5-10 times...

I've seen some weird stuff before, but this is outta sight...

Anyway, here's my fglrxinfo:
> 
ronadams@Osiris:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)


My xorg.conf:
[http://pastebin.com/777580](http://pastebin.com/777580)

If you need any other environment variables, tell me and I'll post them.

I was thinking about just reinstalling fglrx (I use the instructions at ubuntuguide.org), but I want to explore what exactly went wrong here, and I generally avoid "nuke fixes".

Suggestions?

EDIT: I ran init 1, to see if the cursor would still blink too fast at the maintenance screen. It did.

Also, I should mention that my Windows x64 Partition is not having any problems.

---

