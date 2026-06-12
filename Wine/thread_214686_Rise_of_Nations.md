---
title: "Rise of Nations"
date: 2006-07-12
forum: Wine
---

### Post by thunderduck3141 on 2006-07-12
anyone had any luck with this one?
I am going to have it by tomrrow and will be trying it with the latest cedega (full)
thanks for your replies
thunderduck3141

---

### Post by BuffaloX on 2006-07-13
I haven't tried it, but I saw somewhere that there are some problems.
But maybe it was Wine, also there's been updates recently, so maybe situation is better now.

One thing that may be difficult is multiplayer. Most Microsoft games behaves a bit weird on network.

I am very interested in your results.

---

### Post by Breepee on 2006-07-13
Let us know if it works, I'll jump a hole in the sky if it does. Great game!

---

### Post by christhemonkey on 2006-07-13
Yeah, ill jump higher if it does! :p

Its an awesome game.

---

### Post by thunderduck3141 on 2006-07-13
hmmmm
i tried all three exe files in the iso and none worked
i tried RONSETUP.EXE and it said something about an unhandled exception and "started debugging"
i tried RISE.ESE and got not response
and i tried NATIONS.EXE and got no response
i will try and burn it to a cd when i get my hands on some and give it another go
i have a feeling this has something to do with "copy protection" (should be called "anti-digital rights software")
i looked at the transgaming wiki, but i dont go by what they say (often linux noobs right the reviews), and he at least got it to install

---

### Post by BuffaloX on 2006-07-13
Thanx for telling 
Too bad it didn't just work.

---

### Post by thunderduck3141 on 2006-07-13
idk maybe it was a bad down... err disk

---

### Post by thunderduck3141 on 2006-07-13
that i bought
with money...

---

### Post by Perfect Storm on 2006-07-14
You should check out Transgaming game list before buying Cedega to avoid dissapointment, furthermore you might check their forum which may give a hint on the specific game you want to run.

---

### Post by Breepee on 2006-07-14
Do you have Windows? Maybe you can install it there, apply the no-cd cracks (helps alot because it removes the copy-protection shizzle) and then move the files to Ubuntu.

---

### Post by KingBahamut on 2006-07-14
Rise of Nations will not work happily on or happily with Cedega. I have heard some users that claim theyve gotten it to run under wine, but I havent seen any conclusive evidence to suggest that this is the case. As with most MSFT games (Halo comes to mind as being an example) trying to run them under wine/cedega has had limited result.  But im sure that as wine improves, and in this so wll cedega/winex , this wll change with the eb and flow of time.

---

### Post by thunderduck3141 on 2006-07-14
yes i see your point

---

### Post by Breepee on 2006-07-16
Age of Mythology is an MS game that works accorind to winehq these days.

---

### Post by thunderduck3141 on 2006-08-02
no i dont have windows, and i refuse to let it in my house :D 
i have been pushed to the point of looking for the disk (which i had my gf hide on me) when trying to get black and white 2 run, but luckily i didnt :wink:

---

### Post by Orval on 2006-12-14
I have installed Rise of Nations and Thrones and Patriots without any problems (Ubuntu Edgy and Wine 0.27), however it does not run (error reading xml file). I installed msxml.msi from the M$ website, but no luck. I tried to reinstall msxml from the RoN CD, but still no luck.

Has anyone any idea of how to get msxml to work?

---

### Post by Orval on 2006-12-14
I de-installed wine, removed my ./wine directory, reinstalled wine and installed Rise of Nation. Wine creates a new ./wine and installation works as before.
After installation the installer asks if I want to play. Yes I do, of course!
So I start Rise of Nation. This time no XML read error and the main menu appears. So far so good, but it is as far as it goes. The mouse cursor is there, the buttons light up under the cursor, but I cannot click the buttons in.

Thats the end of the story, I guess.

---

### Post by Orval on 2006-12-15
Not quite the end of the story.

In the apps database on winehq I read that the buttons can be clicked if you hold the right mouse button pressed while left-clicking on the buttons.

That works!

However, I cannot change any of the drop down menu's in the single-player startup screen.

I can play a game, though. But the resource area is black, so I cannot see how much resources are gathered. And that is a pretty essential part of the game.

When I try to install the Thrones and Patriots extension the installer complains that PidGen.dll cannot be loaded. So I copied it from my Windows\System32 map to ./wine/drive_C/system32. Without any luck...

---

### Post by meng on 2006-12-15
The various versions of RON may have different compatibilities with wine/cedega. Bottom line is that despite it being on the cedega compatibility list, I couldn't get it (RONGold) to work there, nor with latest wine, so I went back to WinXP tail between my legs.

---

### Post by Orval on 2006-12-20
> **Orval said:**
> Not quite the end of the story.
When I try to install the Thrones and Patriots extension the installer complains that PidGen.dll cannot be loaded. So I copied it from my Windows\System32 map to ./wine/drive_C/system32. Without any luck...

This error should be avoided if you copy mfc42.dll from your windows installation to the ./wine/drive_C/system32 map, so I read on the Wine appsdb. I will try that tonight.

---

### Post by Orval on 2006-12-20
Well, that worked. Thrones and Patriots is installed, but the same problems occur as with Rise of Nations alone.

---

### Post by phibonoacci on 2007-05-18
can i get an update on progress within this topic.  i want to play ron bad, but i cant get it to work in wine

---

### Post by weedmonk on 2007-11-08
Any updates?

---

### Post by marquisdesade on 2007-12-08
Okay, I just tried RON out on my box independent of these forums, and actually came here to check if people had any suggestion for my problem (sound not working). 

Anyway, I've got RON (the original one, not thrones and patriots) to work pretty well on my ubuntu 7.10 box with wine 0.9.46. I get 45+ fps, but I dont get any sound. As Orval notes upthread, I have to keep my right mouse button pressed and left-click to have any effect during the menus before the game, but during the game, it works as it's supposed to. Except for the sound. 

I guess I did pretty much the same things Orval describes: copy pidgen.dll from a windoze XP install on the same machine, and mfc42.dll from the web. Because I had installed age of mythology before RON, I installed DX (version 9, i think... whatever is packaged with AOM). RON setup went smoothly; it told me that my msxml parser was bad and asked me if it should repair it... I said 'sure' and it came back happy.

So my issue is only the sound; gameplay seems better than it did in windows (maybe some of that is just my bias :). Oh, and I couldn't get fullscreen (1280x1024) yet, but I think I will be able to if I try as I have that resolution with AOM.

If anyone is interested: AOM and AOM titans expansion work *perfectly*. Near-native responsiveness, sound is also good. Of course, I have a 256 MB graphics card and 1G ram.

hope this helps someone, and please post any updates for sound not working (I know/tried the naive solutions like killall esd and making sure no process is blocking dev/dsp...)

marq

---

### Post by marquisdesade on 2007-12-08
Update on my post above: what i get seems to be as far as what most people have got according to 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4590](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4590)

---

