---
title: "Game with 64bit wine"
date: 2006-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by greyghostx on 2006-10-29
I installed wine and it works fine and I put in a game and installed it and when I try to run it from the game disc it starts up and when I try to play it says "Please insert game disc" but the disc is already in.

Any ideas?

---

### Post by cocteau on 2006-10-29
is there a 64bit wine? I thought that was still 32 bit.

Anyway to answer your question, wine doesn't support many types of copy-protection so that's probably your problem. There's a database of what games work with wine somewhere but I don't have the link. 

Solutions include, getting a nocd crack for your game or using Cedega. I've gone for the latter myself and it works great :)

---

### Post by kuja on 2006-10-29
> **cocteau said:**
> is there a 64bit wine? I thought that was still 32 bit.

Anyway to answer your question, wine doesn't support many types of copy-protection so that's probably your problem. There's a database of what games work with wine somewhere but I don't have the link. 

Solutions include, getting a nocd crack for your game or using Cedega. I've gone for the latter myself and it works great :)
The link is [http://appdb.winehq.org](http://appdb.winehq.org)
It is possible to build a 64-bit wine, there are instructions for it on the winehq website, though I find it's easier to just use the 32-bit, because it's prepackaged whereas I would have to compile the 64-bit wine myself.

---

### Post by Jonnycat26 on 2006-10-29
> **greyghostx said:**
> I installed wine and it works fine and I put in a game and installed it and when I try to run it from the game disc it starts up and when I try to play it says "Please insert game disc" but the disc is already in.


I would guess that your wine configuration is screwed up somehow.

Try typing winecfg and making sure your windows cd drive really points to the appropriate mountpoint.

---

### Post by greyghostx on 2006-10-29
Yeah my cd drive wasn't being directed to the right spot, thanks. But now it's running slow and the font is pretty large when I start the game what causes this?

---

### Post by fabertawe on 2006-10-30
> **kuja said:**
> The link is [http://appdb.winehq.org](http://appdb.winehq.org)
It is possible to build a 64-bit wine, there are instructions for it on the winehq website, though I find it's easier to just use the 32-bit, because it's prepackaged whereas I would have to compile the 64-bit wine myself.

I compiled Wine (following their instructions) on a previous Dapper install and it worked but you're still using the 32bit libs so it's really not worth the bother like you say.

Paul

---

