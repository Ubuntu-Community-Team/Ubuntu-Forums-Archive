---
title: "Burning Crusade Problem"
date: 2008-01-17
forum: Wine
---

### Post by killermad34 on 2008-01-17
I am going through the step-by-step process of installing The Burning Crusade on my computer.  I already installed the original WoW, I haven't run it yet but it installed and I can log in and everything fine.  Well I got all the stuff ready for BC and when I go to install it, it tells me that I have to purchase the original before I can install it...but I already have the original installed.  So any help with that would be appreciated.

---

### Post by spolta on 2008-01-17
Is this in Ubuntu or Windows...?

---

### Post by killermad34 on 2008-01-17
Ubuntu...

---

### Post by killermad34 on 2008-01-17
bump...

I have an active account and everything, I just can't seem to get Burning Crusade to acknowledge that I have the first version installed...

---

### Post by jaytek13 on 2008-01-17
You say you haven't run WoW at all... WoW has to be run and updated with all previous patches to 2.0 before being able to install 2.1 (BC).

---

### Post by Joeb454 on 2008-01-17
Please don't bump after 24 minutes :) Also this may get more responses if posted/moved to the gaming sub-forum.

Like the above poster said, chances are you'll need it all up-to-date first

---

### Post by killermad34 on 2008-01-17
A) Sorry, I bumped it because I wanted to add more information that I thought would help someone give me advice to fix it

B) Original WoW is all installed and updated.  I have run the game, I just can't get into my realm because I have a BC account and it wont log onto regular WoW.

---

### Post by Golem XIV on 2008-01-17
I assume you're using Wine to install.  You may want to check the [Wine sub-forum here]("http://ubuntuforums.org/forumdisplay.php?f=313") or go directly to the [Wine Applications Database]("http://appdb.winehq.org/") and look there if someone has an answer.

---

### Post by jaytek13 on 2008-01-17
The gaming forum might be best ( [http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93) ). They tend to know more about game-related issues in it than here in the beginner forums. 


After some searching, it seems some people have had this problem regardless of operating system, so it doesn't seem to be wine related. One person stated the BC installers looks in the registry to see of WoW is installed and doesn't simply look for the presence of WoW.exe. If you installed WoW by copying the files from another destination rather than doing a true install this might be the issue.

---

### Post by killermad34 on 2008-01-17
So how would I make it appear in the registry?

---

### Post by killermad34 on 2008-01-17
update!  So I started a new trial account, just to see if I could log into the original game, and I can.  Hell, it runs better on this new ubuntu install than it did on my xp desktop as far as framerate and everything.  So now all I have left to do is to get BC to recognize that I have it installed and I'll be all set.

---

### Post by jaytek13 on 2008-01-17
> **killermad34 said:**
> So how would I make it appear in the registry?


You'd have to install it from scratch using the cd's. Wine will create the registry keys (or Cedega).

---

### Post by K.Mandla on 2008-01-17
Moved to Wine subforum.

---

### Post by killermad34 on 2008-01-17
But that's the problem.  I purchased the game online. Which means you just download it, you don't have to have CD's....I do have the  Burning Crusade Cd's but those wont do me much good seeing as I can't install it until it recognizes the first install.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)  That's the tutorial that I followed step by step and everything has worked fine until coming time to install the BC expansion.

---

### Post by jaytek13 on 2008-01-17
> **killermad34 said:**
> But that's the problem.  I purchased the game online. Which means you just download it, you don't have to have CD's....I do have the  Burning Crusade Cd's but those wont do me much good seeing as I can't install it until it recognizes the first install.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)  That's the tutorial that I followed step by step and everything has worked fine until coming time to install the BC expansion.

Did you register BC on the WoW account management page?

---

### Post by killermad34 on 2008-01-17
I bought the game over a year ago, both the original and BC at the same time.  I have a lvl 62 character that I used to play on the BC all the time.  The only problem seems to be is that my BC installer doesn't seem to recognize that I have World of Warcraft installed.  Even though it is installed, I even tried un-installing it and re-installing it to no avail.  I'm really running out of ideas.

Gaming has been the only reason I have not rid of my XP partition yet and it looks like I'll still be keeping it if I can't get this figured out.  I have only been using Ubuntu for a couple weeks now and I do really love everything about it.  Except this now.

I have a hard time believing I'm the only one who has ever had the problem with BC not recognizing my original install.  But I can't seem to find the same problem anywhere on the forums.

---

### Post by jaytek13 on 2008-01-17
> **killermad34 said:**
> I bought the game over a year ago, both the original and BC at the same time.  I have a lvl 62 character that I used to play on the BC all the time.  The only problem seems to be is that my BC installer doesn't seem to recognize that I have World of Warcraft installed.  Even though it is installed, I even tried un-installing it and re-installing it to no avail.  I'm really running out of ideas.

Gaming has been the only reason I have not rid of my XP partition yet and it looks like I'll still be keeping it if I can't get this figured out.  I have only been using Ubuntu for a couple weeks now and I do really love everything about it.  Except this now.

I have a hard time believing I'm the only one who has ever had the problem with BC not recognizing my original install.  But I can't seem to find the same problem anywhere on the forums.


Well, as I said other's have posted having this same problem on Windows on the WoW forums... maybe you should try asking the WoW technical forum and see if you can't get a blue response as to the reason this might be happening. Don't mention your under Ubuntu, though, as then they will just write it off as "sorry we don't support it" even though other Windows users have had this problem.

---

### Post by killermad34 on 2008-01-17
Thanks.  I did post there a couple minute ago but, it was before I read your post, and I did mention I was on Ubuntu lol.  So we'll see how that goes.

---

### Post by killermad34 on 2008-01-17
Yea those forums are no help.  I have found multiple threads with the same problem, and most of them are unanswered.

The only thing I can think of, is that it isn't recognizing it as installed in the registry.  Even though when I go to regedit, it's all in there and everything.  I'll just have to stick to gaming on my Windows partition.  Sucks because the original works so well on Ubuntu.  I'll try installing with Discs next, but if that doesn't work I'm not really gonna waste any more time on it.  I'll still use Ubuntu for every day applications though.

---

### Post by killermad34 on 2008-01-17
Got it!  I found my BC cd's.  And took the right files off of them and it worked.  I don't know why the downloaded copy of BC wouldn't work, they're almost the same exact files.  Oh well though.

---

