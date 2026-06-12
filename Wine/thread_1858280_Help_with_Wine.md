---
title: "Help with Wine"
date: 2011-10-12
forum: Wine
---

### Post by MetalRider on 2011-10-12
Hello all.  I have been trying to install a Yahtzee game by Hasbro for Windows by using wine.  I have gotten all the files onto my Wine virtual C drive, and when I try to run the game, the opening screen pops up ok, but then it asks me to insert the CD in the cdrom, which is already in there and I am stuck at that point.
Any ideas?

---

### Post by Elfy on 2011-10-12
Thread moved to Wine.

There is a linux yahtzee game that works without needing wine - tali

It's in the software centre

---

### Post by _____ on 2011-10-12
Why does everyone just recommend something from the software center when people are actually having an issue? Everyone has told me the same thing about Civilization II, which I cannot get to work in WINE because Natty Narwahl IS CRAP. "get freeciv from the software center", freeciv sucks, Civilization II is better and maybe her yahtzee game blows that weak game in the software center out of the water.

---

### Post by ergo-proxy on 2011-10-12
> **MetalRider said:**
> Hello all. I have been trying to install a Yahtzee game by Hasbro for Windows by using wine. I have gotten all the files onto my Wine virtual C drive, and when I try to run the game, the opening screen pops up ok, but then it asks me to insert the CD in the cdrom, which is already in there and I am stuck at that point.
Any ideas?
 
It's propably caused by DRM which is not recognized by wine. In such case the only solution would be using 'a vitamine'  :(

---

### Post by ergo-proxy on 2011-10-12
> **_____ said:**
> Why does everyone just recommend something from the software center when people are actually having an issue? Everyone has told me the same thing about Civilization II, which I cannot get to work in WINE because Natty Narwahl IS CRAP. "get freeciv from the software center", freeciv sucks, Civilization II is better and maybe her yahtzee game blows that weak game in the software center out of the water.
 
It's not fair blaming ubuntu because you can't get working a windows game :/
 
What I can advise is to check with different wine versions (especially the stable one). I did small research and it seems CIV2 is not well supported in wine on the contrary to Civ4. If it's so important for you perhaps try virtualboxing?

---

### Post by gesti on 2011-10-12
> **MetalRider said:**
> Hello all.  I have been trying to install a Yahtzee game by Hasbro for Windows by using wine.  I have gotten all the files onto my Wine virtual C drive, and when I try to run the game, the opening screen pops up ok, but then it asks me to insert the CD in the cdrom, which is already in there and I am stuck at that point.
Any ideas?

It was long time ago when I had similar problems. Back then what I normally did, just download a no-cd crack and that fixed it for me.

---

### Post by MetalRider on 2011-10-12
Thanks for the advice so far!   Yeah, I know about the Yahtzee game in the software center.  Tried it already, but the Windows version I have is much better.  I'd really like to get it going if possible.

I'm at a loss as to what is meant by 'a vitamine' and "a no cd-crack" though.  Can you elaborate?

Sorry about putting this request in the wrong area.  I had actually never scrolled down far enough to see there was a specific Wine area.  ;)

---

### Post by gesti on 2011-10-12
No-cd crack is normally just an exe file with which you need to replace your original Yahtzee exe file. With this new exe file your game won't ask for CD.
If you can tell me what is version and who is the maker of your Yahtzee I can try to find you one.

---

### Post by MetalRider on 2011-10-12
The CD was done by Hasbro Interactive and is actually titled Ultimate Yahtzee, but it is so old that it was designed to run as far back as Windows 95 and I don't have a clue what version it is.  I hope you can help me and I surely do appreciate the offer!!  :)

---

### Post by gesti on 2011-10-13
> **MetalRider said:**
> The CD was done by Hasbro Interactive and is actually titled Ultimate Yahtzee, but it is so old that it was designed to run as far back as Windows 95 and I don't have a clue what version it is.  I hope you can help me and I surely do appreciate the offer!!  :)

Sorry MetalRider, but no joy. Couldn't find a no-cd crack/patch for it. Found a portable version of it but it wouldn't run either... :sad:

ergo-proxy siad:
> In such case the only solution would be using 'a vitamine'  :sad:
so what is a 'a vitamine'?

---

### Post by MetalRider on 2011-10-13
Thanks for trying gesti!

---

### Post by MetalRider on 2011-10-13
I got it working! 
 Not so much on my own, but I came across this topic in the forum archive, [http://ubuntuforums.org/showthread.php?p=10033626#post10033626](http://ubuntuforums.org/showthread.php?p=10033626#post10033626) and TidusBlade made a comment that caught my eye.  What I did was to open the CD's contents, copy all of that to my home folder, and then open up the virtual c drive and manually copy the files and folders obtained from the CD to the virtual c drive, and it finally worked.  Don't have any sound working, but my wife and usually listened to music while we were playing the game anyway, so no big deal.

Thanks to everybody for trying to help!  I happily consider this topic solved.  :D

---

