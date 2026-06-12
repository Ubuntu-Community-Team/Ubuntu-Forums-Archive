---
title: "zero% success rate with PC games"
date: 2008-09-16
forum: Wine
---

### Post by N00b-un-2 on 2008-09-16
I'm not going to say that it can't be done.  we've all seen the screen shots to prove it, and I'm sure plenty of you out there have gotten windows games to work with at least some degree of success in Ubuntu either using wine or Cedega, but so far I'm batting a thousand.
I have tried installing some of my favorite PC games on Linux including Call Of Duty 4, Final Fantasy VII for PC (I've tried both the older version and the more recent Ultima Edition), and Need For Speed: Underground 2.
I've tried installing them both in Wine and in Cedega, and the closest I've been able to come to playing anything on my computer was when I loaded the EXE file of NFS:U2 from my windows partition in Cedega, and all I got was sound and no video followed by a complete system crash and I had to reboot.
And that's just my desktop PC that has a good graphics card and a fast processor with plenty of ram.  I have absolutely no success of any kind with games on my laptop.

Is it possible to get a single game working on my Linux box that isn't an open source game?  Or am I doomed to keep that other partition on my hard drive?

---

### Post by Thelasko on 2008-09-16
> when I loaded the EXE file of NFS:U2 from my windows partition in Cedega
That's your problem, you need to install the game in Wine just as you would in Windows.  You can't use games installed in your Windows partition with Wine.

[Please read this entire post.]("http://ubuntuforums.org/showpost.php?p=2995067&postcount=1")

---

### Post by N00b-un-2 on 2008-09-16
I'm fully aware of that.  Apparently you didn't read what I posted.  I said that I ATTEMPTED to install those games in linux.  As in, I went to install them and they didn't install properly.  In Cedega I've had no luck installing whatsoever, and in wine I can install, but the files are not playable.  pay attn

---

### Post by darthmob on 2008-09-16
> **Thelasko said:**
> You can't use games installed in your Windows partition with Wine.[/URL] my experience is that installations often give more trouble than just starting the game. especially when using non iso images. the 3 games I played via wine (diablo 2, max payne 1 & 2) worked well while being started from the windows partition.

nevertheless thanks for the link!

PS: there are a handful of commercial games available with linux clients. for example by id software (Quake and Doom series) (have a look at their official ftp for demos [_**here**_]("http://zerowing.idsoftware.com:6969/")). 
the only adventure / rpg I know so far is On the Rain-Slick Precipice of Darkness. a demo is availabe for download [**_here_**]("http://www.playgreenhouse.com/game/HOTHG-000001-01/").

---

### Post by Toxicity999 on 2008-09-16
FFVII for PC, seriously? that barely had compatibility with the platform it waas designed for.
 
[http://appdb.winehq.org](http://appdb.winehq.org)
 
The best amount of information will be there in the test dat and comments. another option, if you have a beefy system, try the new VMware beta, is had direct rendering support up to DX9c right now.

---

### Post by Calmatory on 2008-09-16
My own personal experience is the exact same. With an exception that I am not really a "gamer". I might play once a week, or month. But for me, no game has ran flawlessly as they do on Windows. People around Linux communities claim "Most of the games work without problems", when majority of the games actually do NOT work WITHOUT problems.

Another issue I hate is WINE. Yes, WINE. E.g. in version 0.9.2 game Y works, then in 0.9.3 it doesn't, then it starts working again in 0.9.8 and gets crippled again in 1.0.1 and never works after it really. So one WINE version for each game, it seems.

---

### Post by gogadan on 2008-09-16
i had issues with running warcraft n wine so i went out and got a new graphics card and with a bit of tweaking using a guide i found on google it works perfectley in wine.i had a ati and now i got a nvida.the thing that i get the impression of and with my wn experance is that the drivers for nvida are way better than ati in hardey heron.this may be a diffrent case for you but i thought i jus drop in my opinion anyways after all the more info you get the easyer it be to solve the problem :).

---

### Post by Toxicity999 on 2008-09-16
> **Calmatory said:**
> My own personal experience is the exact same. With an exception that I am not really a "gamer". I might play once a week, or month. But for me, no game has ran flawlessly as they do on Windows. People around Linux communities claim "Most of the games work without problems", when majority of the games actually do NOT work WITHOUT problems.

Another issue I hate is WINE. Yes, WINE. E.g. in version 0.9.2 game Y works, then in 0.9.3 it doesn't, then it starts working again in 0.9.8 and gets crippled again in 1.0.1 and never works after it really. So one WINE version for each game, it seems.

You try managing an entire win32 tree of source with submissions from hundreds of random people with their own coding styles, principles and ideas. Alexandre does an awesome job considering the load. =P

Simple fact is, this happens. If you want it to stop, follow the procedures for regressions testing, post your results, and hopefully someone will help you. But honestly, if you're not doing this, you have *absolutely no* place to complain. Talking about regressions on ubuntu forums is not exactly going to alert the core wine devs of issues. Go through the proper channels.

This is the world of free software, a million eyeballs both fixed on the code and final project. If those people attached to said eyeballs don't fix the problems, or at minimum report them in a helpful way, the concept is flawed.

And anyone who tells you "most games work flawlessly on wine" are neither wrong, nor right. A lot of stuff works for a lot of people. But not every last bit works for everyone. Short of putting a YMMV warning on every single wineboot, I'm not sure what can be done to get this across better.

Sorry if that came off whatever-ish, but it's the truth. And this goes for everyone, this is a place for general tips and tricks. We'll help you as we can. but *real* problems, need to be filed as bugs against wine. Chances are someone's reported your issues in some form, if they have, supplement their data. If you file a bug with no data, people will be more than happy to tell you what they need to see to assist you.

---

### Post by hikaricore on 2008-09-16
> **N00b-un-2 said:**
> And that's just my desktop PC that has a good graphics card and a fast processor with plenty of ram.

[B]Define "good graphics card".
Define "fast" processor.
And define "plenty" of ram.[/B]

Your game also needs to be supported by WINE (or ewww cedega, waste of time imho even speaking of cedega).
Games with OpenGL support or compatible direct3d support that WINE can convert will run better.

If no one has ever successfully run <insert game title here> under WINE, you will not likely be the first to do so.

---

