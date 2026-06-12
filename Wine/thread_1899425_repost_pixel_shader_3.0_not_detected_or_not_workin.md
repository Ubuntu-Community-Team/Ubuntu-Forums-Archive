---
title: "repost: pixel shader 3.0 not detected or not working correctly"
date: 2011-12-23
forum: Wine
---

### Post by uh20 on 2011-12-23
my graphics card is a nvidia quadro fx 1400
it supposedly runs directx 9.0c and pixel shader 3.0

when trying to run dungeon defenders it then rants about not having shader 3.0
on one occasion, after switching wine versions, it did not come up with  this error and went to installing .net, i had to cancel since i did not  install .net 35 through winetricks then, and after restarting my  computer, it came up saying i had the wrong pixel shader again

a possible problem i read up on but did not get enough info was that  wine sometimes does not fully support directx 9c, and prefers to run  like it was only 9 instead

i now have all .net's in place, and it seems this is the only problem left to solve

oh, and dont post about getting a new graphics card, because i will do anything before buying a new one

---

### Post by ergo-proxy on 2011-12-23
> **uh20 said:**
> my graphics card is a nvidia quadro fx 1400
it supposedly runs directx 9.0c and pixel shader 3.0

when trying to run dungeon defenders it then rants about not having shader 3.0
on one occasion, after switching wine versions, it did not come up with  this error and went to installing .net, i had to cancel since i did not  install .net 35 through winetricks then, and after restarting my  computer, it came up saying i had the wrong pixel shader again

a possible problem i read up on but did not get enough info was that  wine sometimes does not fully support directx 9c, and prefers to run  like it was only 9 instead

i now have all .net's in place, and it seems this is the only problem left to solve

oh, and dont post about getting a new graphics card, because i will do anything before buying a new one

Pixel shader 3.0 is not fully supported in wine yet so don't expect too much neither is .net 3.* .

---

### Post by uh20 on 2011-12-23
indeed it is not, i fully expected dotnet to be experimental as i bought the game, if i recall correctly dotnet has no effect on why my game does not detect my card that should run pixel shader 3.0, so i assume its not my problem currently

---

### Post by uh20 on 2012-04-02
a bump to the topic after one month, i specifically want to know the progress of pixel shader 3 support in wine. multiple different google searches seem to be bringing up junk instead
whats even more annoying is i cant find a single place to test gpu in even the regular linux enviroment, i mean come on, its not that hard to test opengl benchmarks right?

---

### Post by cogadh on 2012-04-05
[http://www.winehq.org/status](http://www.winehq.org/status)

That should get you the info you need on the state of shader support in Wine. As for testing your graphics card...

[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

---

