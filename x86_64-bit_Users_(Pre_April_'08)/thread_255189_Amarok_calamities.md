---
title: "Amarok calamities"
date: 2006-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Negyxo on 2006-09-11
Firstly, i'm not sure that this is 64bit specific problem, so don't be hating if i'm in the wrong place. I'm a bit of a newbie, so don't be hard on me. 

I installed amarok with no problems, then i did the "first time load" configurations and point the app to my extensive mp3 folder. At the time when i installed amarok i didn't have my mp3 playback down pat (i could get mp3 playback from VLC but not rythmbox or anything else really). But, point being, when Amarok tried to build my collection, i believe it crashed due to my mp3 playback not being in place when i scanned my collection. 
Now, i got gstreamer all set up correctly and when i load up Amarok it tries to build my collection and faild at 1% every time. 

So, any ideas ?

Oh, i've tried reinstalling Amarok a couple times and i'm never able to get it to do that "first time launch" wizard. Anyway for me to really remove any mark of amarok from my machine ?

Thanks a lot.. (been reading this forum for a while now, finally had to post something...)

---

### Post by kuja on 2006-09-11
```
sudo apt-get remove --purge amarok
sudo apt-get install amarok
```

That should remove any trace of it before reinstalling... Might work.

---

### Post by Negyxo on 2006-09-11
Well, i've tried your purge command (which had promise) but unfortunately it reached the same ends as doing a clean remove using synaptic. I just freezes when it tries to build the collection! It's maddening. I'm going to go search around and see if anyone has had simple problems as i have... but if anyone knows anything that could help me.. it would be much appreciated.

---

### Post by Lord Illidan on 2006-09-11
Try deleting your ~/.kde/share/apps/amarok folder.

---

### Post by Negyxo on 2006-09-11
Well, tried that.. it seemed to have some sort of effect. After a clean reinstall it crashed at 3% this time (trying to build the collection still). Is there anywhere else info is stored for amarok ?

---

### Post by kuja on 2006-09-11
Try the latest amarok, 1.4.3.
Add the following line to your /etc/apt/sources.list file:

deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

Then do a simple "sudo apt-get update && sudo apt-get upgrade".

Hopefully the problem is resolved in 1.4.3.

---

### Post by infinityPlusOne on 2006-09-12
I have been experiencing the same problems.  Does the OP store his Mp3s on a network share?  All my music is on my NAS and I am unable to get Amarok to work.  I have read other posts on various forums discussing this same problem, and often people are trying to use it to access their media on a network share.  During the initial setup, I pointed Amarok to my network share, and now even after completely removing Amarok and then re-installing it, it seems to check there for my music.  I have tried unmounting my shared drives as well as installing version 1.4.3 to no avail.

I would definitely be interested in figuring out how to get Amarok to re-run the initial configuration wizard.  If somebody knows how to do this it would be greatly appreciated.

---

### Post by kuja on 2006-09-12
```
amarok --wizard
```

Start amarok from a terminal with that to get the wizard. 

As per else, if the network share uses samba, you could try using smbfs mount, maybe that could work.

---

### Post by infinityPlusOne on 2006-09-13
Thanks Kuja!  I'll try that out tonight.

---

### Post by shoagun on 2008-01-05
I recently installed ubuntu 7.10 64 bit an installed amarok, and I'm having the exact same problem as Negyxo.  Amarok would consistently get stuck at 1% when building my music collection.  I tried purging it and reinstalling and now it gets consistently stuck at 3%.  

elsewhere in the forum, the posted solution to this sort of problem is to uncheck the "watch folders for changes" option, delete .kde/share/apps/amarok/collection.db, and then recheck the "watch folders for changes" option.  This does not seem to do anything.  I've also tried all the suggestions posted above.  

After some playing around , it seems the problem is clearly related to the amount of music I have, which isn't that much (~35 GB).  If I only include fractions of my total set, amarok can build my collection.  as the fraction gets bigger, amarok begins to stall. the bigger the fraction, the lower the percent that amarok stalls at.  

the weirdest thing is that when i load my collection by choosing the parent directory to all my music, it always gets stuck at 3%.  However, if I instead go into that directory and individually choose each subdirectory (still including all my music), it always stalls at 65%.  Could it somehow have something to do with the depth of my directory tree?

Also, i've noticed that doing
```

sudo apt-get remove --purge amarok
rm -r ,kde/share/apps/amarok

```

does not remove all remnants of amarok, because when i reinstall amarok, it always starts with the same settings it had before i got rid of it.

Has anyone figured out any sort of solution?  Is anyone else still having this problem?  Is it clear to anyone if this problem is related to the 64 bit verson of ubuntu, or running amarok in gnome?  Is it possible to have a collection "too big" for amarok?  Any thoughts would be appreciated.  thanks!

p.s. I should add also that my collection is local and i'm using the SQlite option for database.

---

### Post by kuja on 2008-01-06
> **shoagun said:**
> I recently installed ubuntu 7.10 64 bit an installed amarok, and I'm having the exact same problem as Negyxo.  Amarok would consistently get stuck at 1% when building my music collection.  I tried purging it and reinstalling and now it gets consistently stuck at 3%.  

elsewhere in the forum, the posted solution to this sort of problem is to uncheck the "watch folders for changes" option, delete .kde/share/apps/amarok/collection.db, and then recheck the "watch folders for changes" option.  This does not seem to do anything.  I've also tried all the suggestions posted above.  

After some playing around , it seems the problem is clearly related to the amount of music I have, which isn't that much (~35 GB).  If I only include fractions of my total set, amarok can build my collection.  as the fraction gets bigger, amarok begins to stall. the bigger the fraction, the lower the percent that amarok stalls at.  

the weirdest thing is that when i load my collection by choosing the parent directory to all my music, it always gets stuck at 3%.  However, if I instead go into that directory and individually choose each subdirectory (still including all my music), it always stalls at 65%.  Could it somehow have something to do with the depth of my directory tree?

Also, i've noticed that doing
```

sudo apt-get remove --purge amarok
rm -r ,kde/share/apps/amarok

```

does not remove all remnants of amarok, because when i reinstall amarok, it always starts with the same settings it had before i got rid of it.

Has anyone figured out any sort of solution?  Is anyone else still having this problem?  Is it clear to anyone if this problem is related to the 64 bit verson of ubuntu, or running amarok in gnome?  Is it possible to have a collection "too big" for amarok?  Any thoughts would be appreciated.  thanks!

p.s. I should add also that my collection is local and i'm using the SQlite option for database.

Hmm, I (still) don't have a solution, though I thought I'd let you know that most of the settings are stored in the ~/.kde/share/config/amarokrc file.

Perhaps you'd have better milage with this issue at bugs.kde.org?

---

### Post by shoagun on 2008-01-06
Quick question though, do you have this same problem using Kubuntu?  And do you use the 64 bit version?  I'm trying to figure out if this is a general Amarok problem.  I would think if it was a general Amarok problem, it would have been fixed by now, since many people must have collections >35GB and this post goes back a year....

---

### Post by gerbman on 2008-01-06
> **shoagun said:**
> Quick question though, do you have this same problem using Kubuntu?  And do you use the 64 bit version?  I'm trying to figure out if this is a general Amarok problem.  I would think if it was a general Amarok problem, it would have been fixed by now, since many people must have collections >35GB and this post goes back a year....I'm having the same problem in 7.10 Gnome. Mine consistently gets stuck at 31% with CPU usage at 100%. The closest information I've found is [here]("http://osdir.com/ml/kde.amarok.bugs/2005-06/msg00524.html"), but it's not very helpful. Any Amarok experts out there with a hint?

---

### Post by kuja on 2008-01-07
> **shoagun said:**
> Quick question though, do you have this same problem using Kubuntu?  And do you use the 64 bit version?  I'm trying to figure out if this is a general Amarok problem.  I would think if it was a general Amarok problem, it would have been fixed by now, since many people must have collections >35GB and this post goes back a year....

If you're asking me I can't really say, as my collection is only 15GB at the moment .... though I could probably rig up a test to see what would happen if I had, say, 45GB, without any trouble and see how things go. In fact. I'm feeling adventurous tonight seeing .... something about me and the midnight hour .... I'm always so productive! Strange eh? I suppose I could even see about maybe, say, testing it from within GNOME too .... maybe. Not sure if I feel  like installing that right now. Oh, and I"m indeed using 64-bit :)

---

### Post by shoagun on 2008-01-07
Well, I have found a "solution."  That is, stop using amarok!  I had only first tried Amarok a few months ago, but I loved it so much, I really wanted to make it work on my Ubunut 7.10 64 bit system.  Since I just can't seem to figure out a work around for this bug, I finally tried something else: Exaile.  It's awesome!  It has everything I loved about amarok, and it's not having any troubles loading my music library :)

Thanks to all the Exaile developers for doing such a great job!!

---

### Post by rune0077 on 2008-01-07
> **shoagun said:**
> 
the weirdest thing is that when i load my collection by choosing the parent directory to all my music, it always gets stuck at 3%.  However, if I instead go into that directory and individually choose each subdirectory (still including all my music), it always stalls at 65%.  Could it somehow have something to do with the depth of my directory tree?


If you've remembered to check the "scan folders recursively" this should not be an issue. If it's unchecked for whatever reason, then that could very well be the problem.

---

### Post by gerbman on 2008-01-07
> **rune0077 said:**
> If you've remembered to check the "scan folders recursively" this should not be an issue. If it's unchecked for whatever reason, then that could very well be the problem."Scan folders recursively" is checked - I don't see how that could cause the collection building process to freeze.

---

### Post by rune0077 on 2008-01-07
> **gerbman said:**
> "Scan folders recursively" is checked - I don't see how that could cause the collection building process to freeze.

Well me neither. Have you checked this thread: [http://ubuntuforums.org/showthread.php?t=307911](http://ubuntuforums.org/showthread.php?t=307911)

It seems to be the same problem, except the OP's scan gets to over 50% complete. According to this, the solution is to just be patient and wait a long time, and the scan will complete itself. Don't know, but it seems worth a try.

---

### Post by gerbman on 2008-01-07
> **rune0077 said:**
> Well me neither. Have you checked this thread: [http://ubuntuforums.org/showthread.php?t=307911](http://ubuntuforums.org/showthread.php?t=307911)

It seems to be the same problem, except the OP's scan gets to over 50% complete. According to this, the solution is to just be patient and wait a long time, and the scan will complete itself. Don't know, but it seems worth a try.Thanks for the reference...I'll let it run overnight and see if it gets past it. Strange bug.

---

### Post by gerbman on 2008-01-07
> **gerbman said:**
> Thanks for the reference...I'll let it run overnight and see if it gets past it. Strange bug.Indeed, the collection building resumed progress after a long while. All's well that ends well, I suppose.

---

### Post by shoagun on 2008-01-07
With Amarok, I did try letting it scan overnight once (but for me, that's only 4 hours), and it was still stuck when I got up, so I killed it.  Just for comparison, Exaile was able to read in my whole library of >8,000 songs in about a minute.

---

### Post by gerbman on 2008-01-07
> **shoagun said:**
> With Amarok, I did try letting it scan overnight once (but for me, that's only 4 hours), and it was still stuck when I got up, so I killed it.  Just for comparison, Exaile was able to read in my whole library of >8,000 songs in about a minute.4 hours might not have been enough. My library is only 1700 songs, and it took 2 hours. Might want to let it run for a day or two if you want to try to go back to Amarok - personally, I can't live without the Context tab  ;)

---

