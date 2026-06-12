---
title: "WoW Addons"
date: 2007-02-13
forum: Wine
---

### Post by russianbandit on 2007-02-13
To all the WoWers on Linux out there:

If you use Ace2 addons and are familiar with Ace Updater, is there a Linux version of Ace Updater?

I'm using Ace2 addons in WinXP and well as Feisty. The Ace Updater makes it really nice for me to update my addons in windows. I was looking for a Ace Updater Linux version, but did not succeed. Does anyone know about such an app? I am also thinking about writing a little program/script to do this for me. How hard would something like that be?

---

### Post by hikaricore on 2007-02-13
I havn't personally used it but you could probably run the software in WINE without a hitch.

Just a thought, I doubt there is or will ever be an addon updater for linux unless blizzard releases a native client which in turn would generate interest in someone writing said addon updater.

---

### Post by Toxicity999 on 2007-02-15
the ui.worldofwar.net one uses .net, if this one doesn't it should work fine. Have you even tried it in wine? If this is open source look at how they see what's new, and adapt that to some type of python gui script-set and call it good. Even a bash script to do it would suffice. If you're terminal kind of person.

---

### Post by justin whitaker on 2007-02-15
I'd try it in WINE, like the guys (I assume) before me said. 

I would love a script that autoupdated those UI add ons on linux. I wouldn't think it would be hard to do....a python script along the automatix type model would suffice.

---

### Post by russianbandit on 2007-02-16
Tried the WINE, but the App is written in .NET

I'm thinking of making a script in ruby. If I make any decent progress I will post it here.

---

### Post by Toxicity999 on 2007-02-16
Talk to the devs of the original program, ask how they communicate with the servers that host the mods, and their database. If they're willing to help out then all you need is a UI.

---

### Post by Jovec on 2007-02-20
In the same boat here.  I put together a really crude script that merely fetches all my addons and unzips them.  No master addon list, version checking, or installing of new addons.  You can do the whole thing with wget and unzip.

---

### Post by Toxicity999 on 2007-02-20
I'm going to try to get ahold of the people at ui.worldofwar.net and see if they would be willing to give us soem help in launching a linux client for this. They probably would give the generic we don't want to go through the trouble to support you "crappy" (to them I assume) OS. But I'll just ask for information rather than them actually doing it.

---

### Post by hikaricore on 2007-02-20
> **Toxicity999 said:**
> I'm going to try to get ahold of the people at ui.worldofwar.net and see if they would be willing to give us soem help in launching a linux client for this. They probably would give the generic we don't want to go through the trouble to support you "crappy" (to them I assume) OS. But I'll just ask for information rather than them actually doing it.

They're actually not bad people :P  I used to post mods there like a year ago, they were very supportive of their mod authors and userbase.  Honestly if they can give us portable source, this can likely happen.  But personally I don't trust/like automatic mod updaters.  Besides it's easy enough to do myself in about 10 minutes.

---

### Post by cmon on 2007-08-27
Any news about an automatic Ace2 addon updater for Linux?

---

### Post by derekr44 on 2007-08-29
Most of my mods are also Ace2-based.  Something like this would be great.

sudo apt-get update Ace2 :popcorn:

---

### Post by cmon on 2007-09-12
Try this Java version it works perfectly for me :) [http://code.google.com/p/jwowupdater/](http://code.google.com/p/jwowupdater/)

---

### Post by hikaricore on 2007-09-12
> **cmon said:**
> Try this Java version it works perfectly for me :) [http://code.google.com/p/jwowupdater/](http://code.google.com/p/jwowupdater/)

that is @#%^ing fabulous!

---

### Post by derekr44 on 2007-09-13
Yes.  This is a glorious post.

Oh, and I do like your custom title, Hikari :popcorn:

---

### Post by hikaricore on 2007-09-13
> **derekr44 said:**
> Yes.  This is a glorious post.

Oh, and I do like your custom title, Hikari :popcorn:

Glad someone got the joke.  ^_^

---

### Post by ZarathustraDK on 2007-09-13
While on the topic of addons for WoW with wine this one is nice :

[http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html]("http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html")

Basically it allows you to change a lot of video-options in-game while running WoW in OpenGL. Without it you'd usually freeze/crash the game, leaving you with the option of either editing WTF.cong manually, or switching to D3D while changing video stuff in-game. Good stuff.

---

### Post by Seraed on 2007-09-13
I'll have to check out that jwowupdater. I *was* using jUniUploader since my guild has wowroster installed, but it doesn't quite work well with our installation for some reason. Basically, I just used it for the wowace svn client that was built into it. As the name suggests, it is a Java version of UniUploader.

Anyhow, for some reason it is having trouble connecting to the wowace svn at the moment so I'll give that jwowupdater a try.

---

### Post by hikaricore on 2007-09-14
Not that scanning through WoWAce: [http://files.wowace.com/](http://files.wowace.com/)
For updates, is too terribly time consuming anyway.  I actually do it to get away from PVP for about an hour sometimes.  ^_^

---

### Post by tlink on 2007-09-25
OMG this solves my largest headache with wow on linux.  Loving jWowUpdater!

---

### Post by Nyct on 2007-10-24
Noob question here, and really sorry to revive a thread... but how exactly do I get the java updater to work?

I have downloaded...but I have no idea what to do next!

Cheers for a reply :P

---

### Post by Zypher on 2007-10-25
Ive been looking around for something better tha JWoWUpdater, which doesn't support as far as i know, indapendant libraries.

[http://wuu.vagabonds.info/](http://wuu.vagabonds.info/) - WoW UI Updater

it is a decent program, however ive had some issues with it under linux, but it works moderately.

edit, found this script

[http://code.google.com/p/wowacepy/](http://code.google.com/p/wowacepy/)

really very good.

---

### Post by lckeeper1 on 2008-03-18
Sorry to bump such an old thread, but I just wanted to echo how well that python script works.

I recently upgraded to 64 bit and did not want to go through installing 32-bit java, so I was at a bit of a loss on how to update, but this script is magical.

Highly recommended.

---

### Post by hostguy on 2008-08-13
I found a WoW addons updater called WUU at [http://wuu.vagabonds.info/wuuki/Main_Page]("http://wuu.vagabonds.info/wuuki/Main_Page"). I installed it on my windows partition and am waiting for the WoW install to complete on my Ubuntu partition so I can try it out. The only issue I have is that you have to run it from terminal as:

```
python WUU.py

```
N00bie time!! 

I want to create a custom launcher for this rather than having to run it from command line. The question I have is how can I create a custom launcher for this? I can't seem to figure out how to set up a launcher to cd /path/to/directory and then run it as python WUU.py from a command line in the custom launcher. Can anyone help me out here?

---

### Post by ooobuntooo on 2008-08-13
Try WoWMatrix!

[http://www.wowmatrix.com/download/](http://www.wowmatrix.com/download/)

There is a Linux version!

---

### Post by Toxicity999 on 2008-08-13
I found WoWMatrix horrid, and locked in.

As for your starting script, I'd just make a symlink to WUU.py, you could then make a script for that, or launch it directly, whatever.

Or
```

# /bin/sh
cd /path/to/wuu
python WUU.py

```

Should do fine.

---

### Post by riteandritual on 2009-02-01
> **ooobuntooo said:**
> Try WoWMatrix!

[http://www.wowmatrix.com/download/](http://www.wowmatrix.com/download/)

There is a Linux version!

Sure there's a linux version (even says Ubuntu on it!) but when I untar it its just a file... what do i do? how do I run it? 

I tried "sh wowmatrix" to disasterous consequences for my terminal, which I closed in panic... I'm one of those people who shouldn't be allowed to run linux, lol.

I've searched everywhere but I can't find help anywhere. And wowmatrix doesn't work on wine. and wuu.py doesn't work for me but spouts errors.

Help!

---

### Post by riteandritual on 2009-02-01
Where there's a will there's a way... even with noobs like me!

I made my wine World of Warcraft folder one of my VirtualBox shared folders, and used VirtualBox with XP to run WowMatrix .... now I don't have to search for updates on my dozens of addons! Huzzah!

---

### Post by darkknight045 on 2009-02-02
Wowmatrix is what I use as well.
I love it.

---

### Post by achelis on 2009-02-08
You can simply double-click the extracted "wowmatrix" file in nautilus.

Alternatively (haven't tried this and not an expert) I think you can run it from the terminal

```

./wowmatrix

```

---

