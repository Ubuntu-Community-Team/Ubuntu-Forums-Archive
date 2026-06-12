---
title: "Guild Wars Linux Guild"
date: 2005-08-18
forum: Wine
---

### Post by remin8 on 2005-08-18
Guild Wars works great on my ubuntu box! I am in a guild called Linux Huggers Anonomous and it would be great to grow this all Linux guild. Email me or look up Remin Of Eight when your playing!

---

### Post by bloodpuppy on 2005-08-18
does Guild Wars come with linux support or did you have to do something to get it to work?

---

### Post by Mishura on 2005-08-19
He used the latest Cedega to run it.  There is no native linux client, yet.

---

### Post by kisain on 2005-08-25
ok how the heck are you running guild wars in linux with point2play and cedega (the current version)? i have been trying to play guild wars ever sence i bought it and i just get a stupid blank screen with a mouse pointer everyone else can get it to run
i bought it off the internet and installed it in point 2 play and nothing do i need the cd?

i know my box can play it cause i play it in my windows partition

please help

thanx

---

### Post by Tentious on 2005-09-07
I am able to install GW, but when I try to launch it, I get a black screen, sometimes i won't even get that, i'll get a box to the left side and my box freezes up(cursur and everything, TOTAL lockup) and I have to shut it down manually and start up. Anyone out there able to get Guild Wars and Cedega working?

---

### Post by e^e on 2005-09-20
It's working! I also had the black screen problem, this is what i had to do , add this 
to your config file, if it's already there, just uncomment it.

"PixelShadersLevel" = "1.3"

previously it was set to 1.1 by default. It even gets rid of the annoying "unsupported hardware" message that usually pops up.

 Make sure you launch it in full screen mode, because it will lag alot in windowed mode. Surprisingly it works on my old gf 2mx too :D. so there you go.

---

### Post by madjo on 2005-09-20
[QUOTE=strongbone]My friend was over the other day, and I showed him [http://www.exploitsrus.com/gw.html](http://www.exploitsrus.com/gw.html) It is a site with cheats, bugs, dupes, etc for guild wars. He told me it was against the rules for gw to do this. Is this true? I am used to cheating on video games for my whole life, so I was sort of shocked to hear this.[/QUOTE]
 cheating, especially in online games, is frowned upon.. and I think it is indeed against the rules of Guildwars...and I think especially Guildwars (and other MMORPGs) is really a game you can learn to play yourself, instead of relying on cheats all the time, try investing some of your skills and improve them :)

---

### Post by jyank on 2005-09-20
Bah, I would join but I lost my log-in info due to some exploit and NCSoft pretty much said "oh well" the only way for me to play again is to pay $50 for a new CD-Key and start over.  lame

---

### Post by peoples_opium on 2007-10-22
hey can any one help me with installing guild wars?  im a complete noob  so it neads to be siple with no jargon.  Thanks:)

---

### Post by justin whitaker on 2007-10-22
> **peoples_opium said:**
> hey can any one help me with installing guild wars?  im a complete noob  so it neads to be siple with no jargon.  Thanks:)

It's not a simple thing if you are just using Wine. It's not deep arcane teminal knowledge, but it's not drop the coasters in and away you go either. 

There is a script floating around that automates it for you.

---

### Post by peoples_opium on 2007-10-22
ok then were can i find how to install it in wine?

---

### Post by dziemecki on 2007-12-10
Try here:

[http://wiki.guildwars.com/wiki/Linux](http://wiki.guildwars.com/wiki/Linux)

Your mileage may vary, but it's about 90% perfect on WINE.  Some minor graphics anomolies, problems with screen caps and texmod (naturally) wont work.  Still, pretty good.

---

### Post by dziemecki on 2007-12-31
Is it my imagination, of has the latest WINE upgrade hosed GW?  I'm getting full OS freezes on mission starts, now.

---

### Post by K.Mandla on 2008-01-03
Moved to Wine subforum. ;)

---

### Post by ariedry on 2009-04-03
its working on wine?

---

### Post by Bios Element on 2009-04-03
> **ariedry said:**
> its working on wine?

Short answer: Yes.

Long answer: I've not tried to get it working recently but it's got a platinum rating on the Wine AppDB. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)

---

### Post by sonnenenergie on 2010-09-01
It is possible to play it on Linux using Wine, CrossOver or using a virtual machine. [IMG]http://sunrent.de/smileynormal.ico[/IMG]

---

### Post by dano0955 on 2011-01-23
> **Tentious said:**
> I am able to install GW, but when I try to launch it, I get a black screen, sometimes i won't even get that, i'll get a box to the left side and my box freezes up(cursur and everything, TOTAL lockup) and I have to shut it down manually and start up. Anyone out there able to get Guild Wars and Cedega working?

You need to wine regedit  Htkey Usr Machine/software/wine add new key Direct3D choose Direct3D add string value  Multisampling enable or disable whichever works for you

---

