---
title: "cedega"
date: 2007-09-29
forum: Wine
---

### Post by anemptygun on 2007-09-29
Just wondering.. I am not having any luck getting counter-strike source to work on wine, anyone have anything good or bad to say about cedega?

---

### Post by anemptygun on 2007-09-29
anyone?

---

### Post by oneadvent on 2007-09-29
Personally, it was pointless for me...it did not play cs any better...and it really did not play cs:s any better at all either.

Of course, I was playing it on a 400 dollar laptop, but you asked.

Everything else has worked fine for me.

---

### Post by anemptygun on 2007-09-30
Well I'm going to be on a nice desktop. So performance shouldn't be an issue since I couldn't get wine to work at all :( just considering my options. How easy was it to get cs set up?

---

### Post by frodon on 2007-09-30
Counter strike source works far better with wine so i would advice you just to try to solve the issues you have with wine, i have been running counter strike source with wine for more than a year without any big problem and it runs really smoothly.
The first thing for you is to read thoroughly the following page :
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731&iTestingId=14688](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731&iTestingId=14688)

Also make sure that you have the latest wine version or at least one which is known to work really well with wine (for instance 0.9.43 or 0.9.41).

Then post here the problems you have with wine, many users are running CS:S with wine so they will be able to help you.

---

### Post by anemptygun on 2007-09-30
Thanks frodon I will try to use that page to fix my problems! :) Any other problems and I will post here.

---

### Post by Arukas on 2007-09-30
Hello,

  I thought I would share my expierence with Cedega.  I tried Cedega, because I thought it would work better than Wine.  I haven't had nothing but trouble with Cedega getting it to work.  I found that Wine works better, funny how it worked out that way.  

-Arukas

---

### Post by reset3x on 2007-09-30
> **Arukas said:**
> Hello,

  I thought I would share my expierence with Cedega.  I tried Cedega, because I thought it would work better than Wine.  I haven't had nothing but trouble with Cedega getting it to work.  I found that Wine works better, funny how it worked out that way.  

-Arukas

Thanks for sharing this.. I was about to cave in and try Cedega and someone in another post told me the same... Just another confirmation to convince to to stick with Wine...

Peace to you!!!

---

### Post by cameran on 2007-09-30
i had a lot of problems with wine, no problems with cedega.  i was up and running with almost the same performance as windows in no time.

cedega really has been for the best thing for me with linux.  i had lots of problems with wine (and i'm a linux server admin at work) but no problems with cedega for my games.

i wish they'd offer a cedega trial or something so people could try without paying and you could see which works best for you!

cameran

---

### Post by reset3x on 2007-09-30
> **cameran said:**
> i had a lot of problems with wine, no problems with cedega.  i was up and running with almost the same performance as windows in no time.

cedega really has been for the best thing for me with linux.  i had lots of problems with wine (and i'm a linux server admin at work) but no problems with cedega for my games.

i wish they'd offer a cedega trial or something so people could try without paying and you could see which works best for you!

cameran

What about CVS? what version do you end up with?

---

### Post by anemptygun on 2007-09-30
> **reset3x said:**
> What about CVS? what version do you end up with?

What is CVS?

---

### Post by cameran on 2007-09-30
i have never used the cvs version of cedega i just bought it.  that version seems to work great for me.

i think there was a post here recently about a script to install cedega cvs version or something, it was within the past 2 weeks for sure...

cameran

---

### Post by anemptygun on 2007-10-01
This is what happens. I tried the fix but no change occurred. Any ideas.

**Counter Strike crashes as soon as you join a game.**

You most likely have other program(s) using sound. On most systems OSS sound driver can be used by one program at a time. To check if any program(s) using sound run 'lsof /dev/snd/pcm* /dev/dsp' and stop all programs listed. Also alsa-oss emulation doesn't always support hardware acceleration. To fix this start 'winecfg' go to "Audio" tab and set "Hardware Acceleration" to "Emulation".

---

### Post by frodon on 2007-10-01
So you tried to put your audio from "Hardware Acceleration" to "Emulation" ?
Also in the winecfg window check that in the audio tab you only have OSS drivers enabled, CS:S runs really bad when ALSA audio drivers are enabled.
Then to help us to understand what is the problem give us the command you use to run the game, start your game pasting your command in a terminal and post the log you get when the game crash and finally tell us what option you added to counter strike via the steam interface. I use the -gl and -dxlevel 80 options to run CS:S, that means that i use the opengl interpreter and force CS:S to run in the directx 8 mode.

---

### Post by Perfect Storm on 2007-10-01
> **reset3x said:**
> What about CVS? what version do you end up with?

CedegaCVS don't even come near the pay version of Cedega or wine.

Sometimes Transgaming are giving trials out.

---

### Post by Sockerdrickan on 2007-10-01
cedega<wine

source engine works with wine

---

### Post by anemptygun on 2007-10-01
> **frodon said:**
> So you tried to put your audio from "Hardware Acceleration" to "Emulation" ?

Ok I made sure that I did this.

> **frodon said:**
> 
Also in the winecfg window check that in the audio tab you only have OSS drivers enabled 

I had done this as well.

> **frodon said:**
> 
Then to help us to understand what is the problem give us the command you use to run the game, start your game pasting your command in a terminal and post the log you get when the game crash

will do asap.

> **frodon said:**
> 
And finally tell us what option you added to counter strike via the steam interface. I use the -gl and -dxlevel 80 options to run CS:S, that means that i use the opengl interpreter and force CS:S to run in the directx 8 mode.


I did not add any options to the command except for WINEDEBUG=-all before the application launch. I will also try this out.

---

### Post by anemptygun on 2007-10-01
> **Tux0r said:**
> cedega<wine

source engine works with wine

It's interesting that the majority of people have said that wine is better than cedega, yet you pay for cedega.

---

### Post by Sockerdrickan on 2007-10-01
Yes lol. It's just that some games run only with Cedega like Battlefield Vietnam

---

### Post by anemptygun on 2007-10-01
lol I havent played that game in so long! battlefield 2 was so much better!

---

### Post by Sockerdrickan on 2007-10-01
lol no lol
Vietnam is the best one :D :guitar: Don't make me want to play it now!!

---

### Post by anemptygun on 2007-10-01
hmm i didn't like the fact that i would get killed through bushes and I couldn't even see the enemy


(ga! I must say lol more. lolololololololol)

---

### Post by anemptygun on 2007-10-02
> **frodon said:**
> 
...Start your game pasting your command in a terminal and post the log you get when the game crash and finally tell us what option you added to counter strike via the steam interface.

How do I find the log?

This is the command i tried.

```

WINEDEBUG="fixme-all" wine steam -applaunch 240 -gl -dxlevel80

```

---

### Post by frodon on 2007-10-02
I'm not sure you can pass the -gl and -dxlevel 80 commands at this step, these are options you generally add via the steam interface, in steam right click on your game and choose property you should see a button for launch options.

---

### Post by anemptygun on 2007-10-02
> **frodon said:**
> I'm not sure you can pass the -gl and -dxlevel 80 commands at this step, these are options you generally add via the steam interface, in steam right click on your game and choose property you should see a button for launch options.

Adding these options in steam yielded no change.

---

### Post by frodon on 2007-10-02
What happen exactly ?

---

### Post by anemptygun on 2007-10-02
Steam starts up just fine, and counter-strike starts up fine. When I join or create a game everything goes ok. I can stay in the game for about 20-30 seconds before it freezes up and kicks me out of counter-strike. But steam is still up and running and works fine.

---

### Post by Desert Storm on 2007-10-02
I used Wine, on my old computer
It worked perfect
But Cedega, only caused troubles =D

---

### Post by frodon on 2007-10-02
anemptygun, try to choose the windows 98 mode in winecfg, i have met some users for whom it solved the issue.
For test purpose you can also test the directx 7 mode (-dxlevel 70) and see if it improve things.

---

### Post by anemptygun on 2007-10-02
Ahhh:-k will try as soon as I get home.

---

### Post by anemptygun on 2007-10-02
AH HA! I'm pretty dure that did it! I will keep playin' around to make sure. but so far works great!

---

### Post by frodon on 2007-10-03
This is a bug that some users have, i have it myself if i use 1280*1024 resolution, hope wine developers will fix this bug one day, feel free to add your experience to the bug report related to this problem, maybe one more user reporting the same bug :
[http://bugs.winehq.org/show_bug.cgi?id=7698](http://bugs.winehq.org/show_bug.cgi?id=7698)

---

### Post by reset3x on 2007-10-04
> **Artificial Intelligence said:**
> CedegaCVS don't even come near the pay version of Cedega or wine.

Sometimes Transgaming are giving trials out.

Thanks for the info AI !!!

---

### Post by anemptygun on 2007-10-05
ARG! Now that steam had an update there is no longer support for windows 98!

---

### Post by RebounD11 on 2007-10-05
CS 1.6 better with Cedega; CS Source better with Wine; NFS Carbon better with Cedega; Trackmania Nations better with Wine; KotOR better with Cedega; Call of Duty 2 better with Wine;Warcraft 3 better with Cedega; MOHAA better with Wine; Lineage 2 doesn't work at all neither with Wine neither with Cedega (off topic: HEEEELP with that!!! even started a topic).

Best to have both if U want to play more - otherwise Wine wins cause it's free.

---

### Post by derekr44 on 2007-10-05
I've had better luck with standard Wine and Crossover than with Cedega.

$0.02

---

### Post by cameran on 2007-10-05
> **anemptygun said:**
> ARG! Now that steam had an update there is no longer support for windows 98!

anemptygun,

Please post this on the Cedega forums (if you're a subscriber).  There are a few people including myself who have reported this error.  Transgaming is asking for more info so the more folks posting on this issue the better.

Thanks!

Cameran

---

### Post by anemptygun on 2007-10-05
Except I'm using wine. i just asked about cedega to see if anyone had anything good to say.

---

### Post by kingqw on 2008-03-28
So, in theory, Cedega is useless

---

