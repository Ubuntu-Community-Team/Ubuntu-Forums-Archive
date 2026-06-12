---
title: "Open office crashy?"
date: 2007-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Raptor45 on 2007-03-06
Recently I've had some struggles with open office not being entirely stable; it crashed on multiple occasions while editing some simple graphs. Is this problem related to the 64bit version? People I've talked to say they haven't had problems in 32bit linux.  I also have been unable to print, which I think might possibly be complicated by 64bit? Might there be any reality to that?

I usually like running the bleeding edge software which takes full advantage of my system, however recently I've been trying to make a more complete switch to Linux. Generally I  don't mind messing with things to get them going, which wasn't a problem when I was primarily using windows. However with trying to switch, it is becoming frustrating to have to fight with things to get them to work right when I actually want to get something done. Is this just a few generic problems I've been running into, or might it actually be worth my time to downgrade to 32bit? Just curious...

---

### Post by John Jason Jordan on 2007-03-06
> **Raptor45 said:**
> Recently I've had some struggles with open office not being entirely stable; it crashed on multiple occasions while editing some simple graphs. Is this problem related to the 64bit version? People I've talked to say they haven't had problems in 32bit linux.  I also have been unable to print, which I think might possibly be complicated by 64bit? Might there be any reality to that?

I usually like running the bleeding edge software which takes full advantage of my system, however recently I've been trying to make a more complete switch to Linux. Generally I  don't mind messing with things to get them going, which wasn't a problem when I was primarily using windows. However with trying to switch, it is becoming frustrating to have to fight with things to get them to work right when I actually want to get something done. Is this just a few generic problems I've been running into, or might it actually be worth my time to downgrade to 32bit? Just curious...
I'm assuming you're on Edgy. I *live* in OOo and I wish I had never upgraded from Dapper to Edgy. Dapper amd64 with OOo 2.0.2 worked great. But 2.0.4 on Edgy is a mess for me. Drag and drop editing of text is broken, the web page wizard crashes OOo, lots of settings in Tools > Options are not saved to the default template, additions to the spelling dictionary are not saved, and I could go on. I have over a hundred hours in troubleshooting without resolving the problems.

I recently booted to the Edgy amd64 live/install CD and tried OOo. I had exactly the same problems. Then I booted to the 32-bit Edgy live/install CD and the problems disappeared. Previously I tried installing OOo 2.1 and the problems persisted. These tests prove to me that the source of the trouble is in Edgy amd64, not OOo. 

On a happier note, I recently downloaded Feisty amd64 Herd 5, booted to it, and launched OOo. It worked perfectly! So my guess is that if you have problems with OOo on Edgy, you can fix them all when Feisty amd64 is released on April 19. The final beta is due on March 19, or you could even use the current Herd 5. Personally, Herd 5 ran great with zero problems for me, but bear in mind that it is still full of bugs and not officially supported. Personally, I am going to live with the OOo mess until April 19. As soon as the final version of Feisty is released I will do an apt-get dist-upgrade and say good riddance to Edgy.

I started with Hoary amd64 and have been faithful to Ubuntu ever since. I loves me my Ubuntu, but Edgy was not one of Ubuntu's better moves.

---

### Post by Raptor45 on 2007-03-06
Glad to hear feisty is an improvement; many people seem to hold that opinion. My plan is to wait until beta 1 is out to upgrade, the herd releases seem a bit premature for real use. I'm interested to hear that most of my gripes with OOo are indeed 64bit related. I suppose this leaves me with two real questions:
-Should I downgrade to 32bit Edgy while waiting for Feisty beta 1?
-When Feisty is released, should I stick to 64bit, or move to 32 for ease of use?

---

### Post by John Jason Jordan on 2007-03-06
> **Raptor45 said:**
> Glad to hear feisty is an improvement; many people seem to hold that opinion. My plan is to wait until beta 1 is out to upgrade, the herd releases seem a bit premature for real use. I'm interested to hear that most of my gripes with OOo are indeed 64bit related. I suppose this leaves me with two real questions:
-Should I downgrade to 32bit Edgy while waiting for Feisty beta 1?
-When Feisty is released, should I stick to 64bit, or move to 32 for ease of use?
Of course, such decisions are up to you. What is right for me or anyone else here may be wrong for you. But consider that if you downgrade to 32-bit you can upgrade to 32-bit Feisty, but not to 64-bit Feisty. If you later want 64-bit Feisty you will have to reinstall and start over. Having said that, if you back up your /home folder you should be able to preserve most of you settings when you reinstall 64-bit Feisty. You'll still have to reinstall all your applications, however.

Should you use 32-bit or 64-bit Feisty? I cannot answer that question, and if anyone else here tries to, their opinion will likely be wrong. Again, it's what's right for you. Personally, I have always used 64-bit Ubuntu, starting with Hoary when I first bought this laptop. Why 64-bit? Because I needed a laptop for school, and I wanted to learn Linux. I figured 64-bit would be a bit more challenging, therefore I would learn faster. Today I have everything working fine in 64-bit Ubuntu Edgy (except OOo), including things that a lot of people can't seem to get working. Yes, it took me some googling and some tweaking to get everything working that I needed, but that was the education part. I do not regret my decision. But my decision may be completely wrong for you. My advice is to peruse the forums extensively. Spend hours reading stuff on the 64-bit forums. After a while you will come to a decision that makes sense for *you*.

---

