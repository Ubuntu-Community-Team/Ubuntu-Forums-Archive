---
title: "WINE Problems"
date: 2008-05-09
forum: Wine
---

### Post by TonyFordz on 2008-05-09
Does anyone know of a good Windows Emulator that will allow the use of the ext *.msi which is a Microsoft Install file ext. I am trying to revert to Ubuntu & be able to play my games like the one I play most right now is 2Moons which you can find at [http://2Moons.TonyFordz.net](http://2Moons.TonyFordz.net) its a Free MMO with no monthly charges to play. I cant install it because its not an exe so therefore I am likely yet again to reformat all over to play this game again but I honestly do not want to dual boot or even have windows on my computer any more.

Also the main problem I get with WINE every time I have tried to use Ubuntu is that once I install a game all is well until update time because I will get errors like "Cant change Directory", or some other error preventing the updates which leaves me unable to play any of my games.

Stand alone programs work fine because they just run when you click them but anything that installs & needs to update will not function properly.

Also someone on 2Moons told me about another Emu called RAID but I am not yet able to find it any ideas?

Thank you to anyone who can provide me with some useful information & avoid the "noobness" remarks I am here looking for help not jerks.

Tony

---

### Post by Kinst on 2008-05-09
Wine can do .msi files. 

For example, to install the Microsoft XML parser I put this command in the terminal:

```
msiexec /i msxml3.msi
```

msiexec just means do something.

---

### Post by cogadh on 2008-05-09
2Moons doesn't work in Wine (or at least it didn't the last time it was tested):
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9017](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9017)

Your other problems would be easier to address if you told us what applications/games are getting those problems. Many apps run in Wine need very specific custom configuration, either in Wine or in the app, in order for them to work correctly.

I've never heard of an emulator called RAID, are you sure that is not an acronym for something?. Oh, and **W**ine **I**s **N**ot an **E**mulator, its an alternate implementation of the Windows API.

BTW - You generally won't find jerks here, we were all noobs at one time and we all come here to give back the help we got when we were noobs.

---

### Post by TonyFordz on 2008-09-24
Yes well I am again in need of some way to play my games & not have to use Windows XP because its very unstable & I am so damn sick & tired of the glitches, errors, blue screens, unsafeness of surfing without some jack*** making your surfing experience unpleasant with spyware, trojans, and so on.

There has to be a good safe & working method to play these games on Linux so that I can permanently do away with Windows & Microsoft.

Does anyone know of an alternative to WINE that will allow me to play 2Moons, ArchLord, and other MMORPGs?

Also the problems I was having with WINE wasn't so much playing a game or having it load it was more so the fact it wouldn't do the updates it would crash or not understand what was going on & not just with games with anything that required updates.

I really suck at Ubuntu because I dont understand the Linux file system or structures so yeah I have a very long way to go.

Thank you for the help,
Tony Ford

---

### Post by aoanla on 2008-09-24
There really is no alternative to Wine in the sense of "something which provides a Windows API translation layer for Linux". 
Cedega, Crossover Office and PlayOnLinux are all forks or repackagings of Wine.

You could try running XP in a Virtual Machine, but that's probably not going to deal with the problem you state - that XP is unstable and icky.


Wine is, of course, constantly improving. If it has been a while since you last used it, you might find it more effective now than you did then. Again, it would help if you told us *which games* you've had problems updating in the past...

---

### Post by asdfoo on 2008-09-24
> **TonyFordz said:**
> Yes well I am again in need of some way to play my games & not have to use Windows XP because its very unstable & I am so damn sick & tired of the glitches, errors, blue screens, unsafeness of surfing without some jack*** making your surfing experience unpleasant with spyware, trojans, and so on.

There has to be a good safe & working method to play these games on Linux so that I can permanently do away with Windows & Microsoft.

Does anyone know of an alternative to WINE that will allow me to play 2Moons, ArchLord, and other MMORPGs?

Also the problems I was having with WINE wasn't so much playing a game or having it load it was more so the fact it wouldn't do the updates it would crash or not understand what was going on & not just with games with anything that required updates.

I really suck at Ubuntu because I dont understand the Linux file system or structures so yeah I have a very long way to go.

Thank you for the help,
Tony Ford

I have three responses to your post:

1. the only reason your Windows XP would be unstable is hardware fault, eg overheating or bad ram _OR_ buggy drivers for your video card.

2. As for your programs which you say you can't get working on Wine, which video card do you have?  If it's an ATI, then that can certainly be a problem for a lot of users because the fglrx drivers are far from good and Wine is known to expose bugs in fglrx.

If you have nvidia then I would try each of these games again using the latest version of Wine, if one does not function correctly, check to see if anyone has bothered to file a bug report in the Wine bug tracker for the issue [http://bugs.winehq.org](http://bugs.winehq.org) - if you can't find any, create one report for each problem, describing what the application is and the steps to reproduce the problem.

3. GNU/Linux isn't inherently safer than Windows, an inexperienced user can trash things and users can still fall victim to hacking attempts, it's just less widespread because there is only a small amount of GNU/Linux users compared to Windows users.

---

### Post by aoanla on 2008-09-24
> **asdfoo said:**
> 
3. GNU/Linux isn't inherently safer than Windows, an inexperienced user can trash things and users can still fall victim to hacking attempts, it's just less widespread because there is only a small amount of GNU/Linux users compared to Windows users.

While the general point is true (inexperienced, non-security conscious users are the main risk, regardless of the OS they have), it's worth noting that GNU/Linux does do certain things better than XP - generally, it enforces the concept that user accounts are not root accounts, it doesn't run as many random services on random ports, and the openness of the source code helps people to spot security flaws more easily.

---

### Post by TonyFordz on 2008-12-04
> **asdfoo said:**
> I have three responses to your post:
2. As for your programs which you say you can't get working on Wine, which video card do you have?  If it's an ATI, then that can certainly be a problem for a lot of users because the fglrx drivers are far from good and Wine is known to expose bugs in fglrx.

Question on this note, I prefer ATI cards with windows its just preference but what cards are best compatible with Ubuntu & Wine? I honestly love Ubuntu but its more about fear then like because we fear things we dont understand which in most cases keeps us from using things that could be better or at least thats the way it is for me. I feel totally stupid when using linux because its so different then windows as far as commands. I dont understand the file structure in which things are placed or any of the commands otherwise I would most likely enjoy it much more then windows.

So if someone knows what hardware works best with both Ubuntu & Wine please let me know because I very much want to be able to play my games in Wine & am hoping that Steam Games will work with WINE because I have quite the collection of games on my steam account about 60+ games & right now am waiting on the 2 500GB HDs I just ordered for my steam games.

Also to get this out of the way if I may how do I change the user & pass for my Ubuntu the main user because I will be selling this laptop since I have fixed it & would like to be able to change the information so that I do not have to reinstall everything.

Thank you everyone for the comments & help...

):P

---

