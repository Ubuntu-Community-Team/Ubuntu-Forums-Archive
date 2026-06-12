---
title: "Wine and Halo"
date: 2006-12-06
forum: Wine
---

### Post by tophatandy on 2006-12-06
I had ubuntu installed on my old computer that was on no network and just ran off the basic installation programs..

mainly used it for word processing..so thats not a problem..


all this is besides the point..

now that I did a custom build and am connected to my homes lan..
I want to run some windows video games (i.e. Halo) 

I have been reading up on wine and tried (I think successfully) downloading it from the repos.. it says I have it..


now.. This is a microsoft game and I doubt will run but would still like to run other games even if Halo doesnt work out..


How do I use wine to install windows games.. 

that is if I have it...

Help would be very much appriciated..:D

---

### Post by pay on 2006-12-07
Run winecfg to test if wine is installed. I use this script to setup wine```
wget http://sidenet.ddo.jp/winetips/files/wine-config-sidenet-1.9.2-test2.tgz
tar zxvf wine-config-sidenet-1.9.2-test2.tgz
cd wine-config-sidenet
./sidenet
```Then to install games put the cd in the drive and run```
wine /media/cdrom0/Setup.exe
```

---

### Post by aidanr on 2006-12-07
looks like (unsurprisingly) you're out of luck with halo
[http://appdb.winehq.org/appview.php?iVersionId=2720](http://appdb.winehq.org/appview.php?iVersionId=2720)

---

### Post by tophatandy on 2006-12-07
thanks.

I have wine, and now know how to use it and that I cant use it with Halo.


Thats all my questions answered.


Thanks for the Help.

:D

---

### Post by Zyphrexi on 2006-12-10
I actually *Have* heard of someone getting wine to work with Halo, but I have no clue how he did it. I've tried cp'ing *.dll from windows to wine to use, but no love.

---

### Post by tophatandy on 2006-12-10
interesting..

if you could find out how he got it to work, that would be lovely..

in the meantime I will look around to see if anyone else has gotten it to work also.

Thanks for the lead.

:D

---

### Post by Zyphrexi on 2006-12-11
It'd be kind of cool to get games with known issues to work in wine.

I think it's usually a dll issue, but my exp with the intricacies of wine is extremely limited.

The guy I'm talking about was a member of an online community of this game that I sometimes play. So there's maybe a 1/100 chance i'll be able to ask him that, and 1/1000 that i'll remember.

---

### Post by HAARP on 2006-12-11
I got damn close to launching, but that's it. There are indeed people who managed to play it, but I ain't one of them.

---

### Post by tophatandy on 2006-12-11
hmm.

I need to find one of the said individuals who managed to get halo to launch.

If you know, are, or find someone who has managed to launch and run halo..

please post and share some details.

---

### Post by Mike'sHardLinux on 2006-12-11
I would also like to get Halo working in Linux. I just searched the net for a while (over an hour), and didn't find a single instance of anyone even claiming to get Halo working. ONE person CLAIMS to have gotten the DEMO working. They call them self "|{urse" on the forums (not Ubuntu forums). Here's what they claim works (on the demo):

> i got the halo demo to work fine on my debian box, the textures suck but the sound is in synch and theres very little lag, cedega failed to install the game for me and install hung on the "creating system icons" message. so i ctrl alt esc'd the installer (which was 99% complete), opened konsole cd'd my way to ~/.cedega/halo demo/c_drive/Program Files/Microsoft Games/Halo Trial, typed cedega halo.exe and *POOF*. the chat function doesn't work in multiplayer (which pisses me off to no end, theres nothing worse than pwning some retard night after night and never being able to ridicule him) beyond that and the lame textures the gameplay is faster than win or mac.

If there are indeed "people" who have gotten Halo to work in Linux, they aren't speaking up on the internet much.

:(

---

### Post by tophatandy on 2006-12-13
thanks for the lead.

will try the demo now..

once again.

thank you.

=D

---

### Post by tophatandy on 2006-12-13
anyone who knows anything..


any information would be nice..

thanks in advance.

=D

---

### Post by Jercos on 2006-12-25
apparently, using a native msxml4.dll makes the chat work... but I cant afford to shell out for cedega to test that...

---

### Post by mrbiscuit on 2006-12-29
Well Well. You're very lucky that I am one of those people that have gotten Halo to run, though I tell you, it's not *picture perfect*. But it can be done, just yeah it's not for the light hearted.. Lol

---

### Post by Mike'sHardLinux on 2006-12-29
> **mrbiscuit said:**
> Well Well. You're very lucky that I am one of those people that have gotten Halo to run, though I tell you, it's not *picture perfect*. But it can be done, just yeah it's not for the light hearted.. Lol

ummmmm........... so................... Are you going to tell us what you had to do to get it to work?

:mrgreen:

---

### Post by Zyphrexi on 2006-12-29
I'm guessing it might be one of those 1337 things where if you can't figure it out, it's too complex for you. The trouble being is there's not much output on where it went wrong in wine.

(this dll is missing, blah blah blah)

since wine itself doesn't know, how are we supposed to know, trial and error?

---

### Post by HAARP on 2006-12-30
I've been trying to get it to work for the past few days. I'm also been in contact with the Wine developers.
Apparently you need a DX9-capable video card. More information to come when I have such a card.
In the meantime, you guys can post some errorlogs wine gives you to the console. ( [http://pastebin.ca/](http://pastebin.ca/) )

---

### Post by PisstMSTRCHIEF on 2006-12-30
[http://appdb.winehq.org/appview.php?iVersionId=2720&iTestingId=1304](http://appdb.winehq.org/appview.php?iVersionId=2720&iTestingId=1304)

Hmm.... gold you say.

just thought that a gold rating is a little odd if it doesn't work

---

### Post by tophatandy on 2006-12-30
> **PisstMSTRCHIEF said:**
> [http://appdb.winehq.org/appview.php?iVersionId=2720&iTestingId=1304](http://appdb.winehq.org/appview.php?iVersionId=2720&iTestingId=1304)

Hmm.... gold you say.

just thought that a gold rating is a little odd if it doesn't work

YES.

so you.. have to upgrade to the new wine (beta) to make it work?

at least its something..

=D

---

### Post by HAARP on 2006-12-31
> **tophatandy said:**
> YES.

so it.. have to upgrade to the new wine (beta) to make it work?

at least its something..

=D

Not, that's not it.

---

### Post by tophatandy on 2006-12-31
wow.. just realized i made a really bad gramatical mistake there.. you can blame that on my trip to germany for the holidays.. been speaking german for like 2 weeks straight..

so my apoligies for the mistake..

but anyway..

I dont understand what this is saying then...

---

### Post by HAARP on 2006-12-31
> **tophatandy said:**
> wow.. just realized i made a really bad gramatical mistake there.. you can blame that on my trip to germany for the holidays.. been speaking german for like 2 weeks straight..

so my apoligies for the mistake..

but anyway..

I dont understand what this is saying then...

I don't see any mistake on your side.

Ein Update zur neuesten Version wird nichts ändern ;)

(A update to the newest version won't change anything)

---

### Post by PisstMSTRCHIEF on 2007-01-01
It says Garbage now, don't know if they changed it or I may have just misread it the first time.

---

### Post by Zyphrexi on 2007-01-04
gold is under debian. Though I wonder what the difference is. After all Ubuntu is updated far more than debian is. Also look at the wine version that achieved the gold rating, 0.9.23.

After reading more about the glitches, it became apparent to me that my vid card doesn't really support a lot of the features that cause the glitches. Things like shaders, or directx 9.

---

### Post by LEADPingu on 2007-01-04
hahaha evil, i had the trial ALMOST work, problem is, i think, that wine doesn't have direct X9 support yet

---

### Post by tophatandy on 2007-01-04
ahh i see..

but isnt ubuntu based off of a debian core..

i think that dual booting for right now is the best way to go..

even if i have to support a corrupt company to play a game...

oh well..

I guess i will wait for two things..

1. wine to get updated so i can play halo on ubuntu
2. a new kernel update so i can use full hardware excelration on my gaming comp..

after that glitch i am seriously considering an ati card after using ONLY nvidia cards my whole entire life..
I also heard that Mr. Torvalds was having some legal issues with nvidia so they were thinking about removing their drivers from their servers and halt all updates..
never seen ati complain...

another thing..

cant you just like.. idk.. downgrade (i think) your wine version .. or maybe its upgrade i dont know..

o well..

any updates on anything would be nice..

---

### Post by HAARP on 2007-01-05
Ok. Series 4 Geforce cards won't work. Got a series 6 one now, it works. Uhh yeah, it's glitchtown. Not really playable

---

### Post by Zyphrexi on 2007-01-05
why can't more companies simply use opengl? It'd reach a broader audience. Stupid stupid rat creatures.

---

### Post by Enverex on 2007-01-10
Just for the benefit of the people currently watching this thread I'll repeat here what I put in another thread and add a little more for clarity.

The "Distro" parts of AppDB don't really mean anything, it's just for the sake of segragation. Doesn't matter if you're on Slack, Ubuntu, Gentoo, Debian, it should work just as well (or not in some cases).

Also, Wine DOES have DX9 support (and SM3 support).

Halo does currently work almost perfectly. Simply install it, update it, replace the .exe with a NoCD patched version (Wine doesn't support most copy protections yet) and start the game. The key point here is to set the graphics NO HIGHER THAN MEDIUM. For some unknown reason the game crashes shortly after the intro if you use HIGH graphics mode. Other than that it should be fine.

---

### Post by Zyphrexi on 2007-01-10
hey, sweet, that's awesome to hear. I thought wine supported dx9. what's up with all the nocd stuff though, according to some forums i've been trolling that's all illegal (though I do it anyway), it'd be nice to get some support on that kind of stuff.

---

### Post by Enverex on 2007-01-11
Yeah, it's due to the US' DMCA which is just plain insanity and isn't enforced anywhere really simply because it's plain silly (like those old Draconian rules you find posted around sites). As long as you own a legal copy of the game and are using it within reason and not doing anything immoral then there really isn't a problem.

---

### Post by tophatandy on 2007-01-11
Thanks.

Will read up some more about this no cd thing.

=]

---

### Post by |{urse on 2007-01-16
Hi i was googling my nick and saw a quote of a post of mine on ozzu forums in here about getting halo to work on linux. Btw it was only the demo & only worked with cedega which costs 15 bucks! i was on str8 deb but switched to ubuntu. Edgy runs this fine with the same procedure i mentioned before. :-k if anyone can give me a link to a howto on enabling wine to perform exactly like cedega (since its basically the same prog.. thieves) then i'm pretty sure i could hook jo0s up with a decent set of installation instructions. I know gamers go thru serious withdrawals when they switch to *nix
but is a demo really worth 15$ :neutral:

---

### Post by |{urse on 2007-01-16
sorry heres that quote..
I would also like to get Halo working in Linux. I just searched the net for a while (over an hour), and didn't find a single instance of anyone even claiming to get Halo working. ONE person CLAIMS to have gotten the DEMO working. They call them self "|{urse" on the forums (not Ubuntu forums). Here's what they claim works (on the demo):

Quote:
i got the halo demo to work fine on my debian box, the textures suck but the sound is in synch and theres very little lag, cedega failed to install the game for me and install hung on the "creating system icons" message. so i ctrl alt esc'd the installer (which was 99% complete), opened konsole cd'd my way to ~/.cedega/halo demo/c_drive/Program Files/Microsoft Games/Halo Trial, typed cedega halo.exe and *POOF*. the chat function doesn't work in multiplayer (which pisses me off to no end, theres nothing worse than pwning some retard night after night and never being able to ridicule him) beyond that and the lame textures the gameplay is faster than win or mac.
If there are indeed "people" who have gotten Halo to work in Linux, they aren't speaking up on the internet much.

---

### Post by Enverex on 2007-01-16
I've already told you it works. Install, apply NoCD, start, set to medium graphics, play. That's it.

---

### Post by twist2b on 2007-12-01
thats wiered becuase halo boots up fine with me.... i havnt installed yet.... but i have to find my code to install it.... (lost it looking for it NOW :P)
anyways yea ill let you guys know if i have any luck! Halos huge, im suprised they wouldnt make a fix for it!

---

### Post by Enverex on 2007-12-02
> **twist2b said:**
> thats wiered becuase halo boots up fine with me.... i havnt installed yet.... but i have to find my code to install it.... (lost it looking for it NOW :P)
anyways yea ill let you guys know if i have any luck! Halos huge, im suprised they wouldnt make a fix for it!

It really isn't huge, heh.

---

### Post by painejake on 2007-12-06
Hey i got halo working in wine VERY sketch tho im still trying to sort it out if anyone wants me to ill post a tutorial when i get it working properly i will:guitar:

---

### Post by Enverex on 2007-12-06
Current issues with Halo are...
```

Bug # - Problem
219 	 Programs refuse to run because of safedisc copy-protection
7640     Mouse too slow / lags in games
8845 	 Screen usage is messed up when in Virtual Desktop mode
9598 	Combat Evolved crashes on startup
10673   Gnome panel bars overlap in fullscreen mode

```

Bug 9598 is the main problem, it means you can't use sound in Wine unless you roll back to 0.9.42

---

### Post by ethana2 on 2007-12-30
Fresh Ubuntu gutsy x86 install on a Dell Latitude x64 laptop...
WINE 0.9.52 from winehq apt on december 30th.

Halo trial installed with no problems at all.  Upon launching, it crashes immediately.  'debug' does nothing.

---

### Post by Sockerdrickan on 2007-12-30
It works with 0.9.52 for me

---

### Post by indianballer24 on 2008-01-14
Can you give the steps to how you got it to work?

---

### Post by Yoshiman007 on 2008-04-04
I haven't personally tried anything on this yet, but from lurking, the instructions on the wine AppDB page : [http://appdb.winehq.org/appview.php?iVersionId=2720](http://appdb.winehq.org/appview.php?iVersionId=2720) are nearly identical, but less detailed than the ones on Halopedia: [http://halo.wikia.com/wiki/Halo:_PC_%28Linux%29](http://halo.wikia.com/wiki/Halo:_PC_%28Linux%29) . Hope someone is still interested in making this work if these instructions don't clean everything up.

---

