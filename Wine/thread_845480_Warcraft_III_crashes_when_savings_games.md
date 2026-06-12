---
title: "Warcraft III crashes when savings games"
date: 2008-06-30
forum: Wine
---

### Post by STVA on 2008-06-30
Hello.  I am interested in the single player experience of WC3, rather than multiplayer.  The game runs perfectly in OpenGL mode, on either the Wine that comes with 8.04, or with the latest version.

My problem is that WC3 crashes most times I try to save a game.  Has anyone else had this problem?  Everything else works, but this issue pretty much makes the game unplayable.

Thanks in advance.

---

### Post by STVA on 2008-07-01
Does anyone else have this problem?

---

### Post by STVA on 2008-07-03
Can anyone confirm that they can save games correctly?

---

### Post by arrgghh on 2008-07-11
yep, same problem. haven't found a way around it yet.

---

### Post by dima338 on 2008-07-17
I also have the same issue, however I was actually able to save once or twice. I've found the bug on the Wine website but there seems to be no solution there either....[http://bugs.winehq.org/show_bug.cgi?id=11188]("http://bugs.winehq.org/show_bug.cgi?id=11188")

---

### Post by wootah on 2008-12-19
I was really looking forward to playing through the campaign too :(

I can confirm this bug and I also reviewed the Wine bug tracker. A few things that are helpful such as upgrading to the current version of wine (compile from source).

I'll try that out and see what happens :)

---

### Post by k@e on 2008-12-19
If you don't mind compiling Wine by yourself, you can apply this patch to the source to fix the problem:

[http://bugs.winehq.org/attachment.cgi?id=8368](http://bugs.winehq.org/attachment.cgi?id=8368)

---

### Post by wootah on 2008-12-20
> **k@e said:**
> If you don't mind compiling Wine by yourself, you can apply this patch to the source to fix the problem:

[http://bugs.winehq.org/attachment.cgi?id=8368](http://bugs.winehq.org/attachment.cgi?id=8368)

Well I downloaded and installed the current version (1.1.10) and it fixed my save problem! I haven't thoroughly tested it (I played the intro campaign, first level moved around and saved a few times after 5 minutes... no crash).

I hope this helps someone?

---

### Post by wootah on 2008-12-20
> **k@e said:**
> If you don't mind compiling Wine by yourself, you can apply this patch to the source to fix the problem:

[http://bugs.winehq.org/attachment.cgi?id=8368](http://bugs.winehq.org/attachment.cgi?id=8368)

Is this a 100% confirmed fix?

(continuing from my previous post)

I played for a little while longer making it a few levels in and saved near the beginning of a new level... which crashed... and then corrupted my save file. 

Gotta start over again :(

EDIT: It appears that that patch applies only to a BattleNet issue resulting in dropped games ?
EDIT2: Looks like it did fix an issue for BattleNet and saving, but in the earlier versions (pre 1.1.10)

---

### Post by illepic on 2008-12-22
Same problem here too.  Any news on a fix?

---

### Post by illepic on 2008-12-22
So far, setting permissions on the "save" directory within the Warcraft III folder to read and write by all (not very safe, I know :( )has allowed me to save, that might help others.

---

### Post by illepic on 2008-12-22
Also, I've found that if I overwrite a previous save, I have better luck getting it to "take".

---

### Post by wootah on 2008-12-23
Well, I'm able to go on and of with or without problems.... it's very odd. Other than using the current version, I have made no modifications.

It seems weird--I get the best luck if I play into a level for 5 minutes AFTER the intro of whatever (where characters are talking).

Saving on top of a save file had no change for me. Are you using the latest stable build (not the same that is available in the repos) ?

---

### Post by krisvdm on 2009-06-22
Ive found that it is often the sound that causes the crashes. Go into Wine configuration (you can get it with winecfg in terminal).
Click on sound tab and try Hardware acceleration - Emulation.
Also use a single sound driver (OSS seems better for older games, but also try ALSA).
Put your sample rate down a bit (it doesnt really affecr=t sound quality, but sometimes helps to stabilize things).

---

### Post by NightMKoder on 2009-06-22
If you guys are on the newer ubuntu's (ie pulseaudio), wine doesn't like those and crashes on many occasions. use pasuspender when launching wine - ie.

```

pasuspender wine ....exe

```

---

### Post by spin_on_this on 2009-06-23
It isnt the sound. its a bug that has been in WINE for ages. They just dont fix it for whatever reason.

---

### Post by PRAEst76 on 2010-05-30
I'm not sure exactly what causes this but setting global read/write access on all my saved games seems to help. Haven't had the game crash out nwhile saving since.

```
chmod 666 ~/.wine/drive_c/Program\ Files/Warcraft\ III/save/Profile1/*.w3z
```

...or whatever your path to the saved games are.

I still tend to alternate saves just incase. There is nothing more furstrating that a game crashing half-way through saving and invalidating your only saved game. This is why my copy of Black and White has been lying in the neighbours hedge for the past six years...

---

