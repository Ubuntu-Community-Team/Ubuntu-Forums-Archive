---
title: "Rappelz"
date: 2007-02-04
forum: Wine
---

### Post by jcquik on 2007-02-04
Has anyone even tried using a free game called Rappelz in Ubuntu?  If not, i'm going to give it a shot.  The game to me feels like guild wars but you can see everyone even when you leave towns or join parties.  you can find Rappelz here --> [http://www.gpotato.com/](http://www.gpotato.com/)

other cool games they have at gpotato are Flyff and Space Cowboy Online.

---

### Post by jcquik on 2007-02-06
Well....no good news on this one.  i tried using wine to install and it did complete the install.  Only problem is now....it will not download the updates for the game.  i'm going to try either manually updating the game or just copy the files from the windows partition.  anyone tried this?

---

### Post by bahdom on 2007-02-16
Im trying it out too. Just installed it and, as you said, downloads wouldnt start. Trying manual update too =]

Tell me if it worked out for you.

---

### Post by jcquik on 2007-02-18
> **bahdom said:**
> Im trying it out too. Just installed it and, as you said, downloads wouldnt start. Trying manual update too =]

Tell me if it worked out for you.

no luck man.  i even tried virtualbox but i don't think virtualbox is designed for playing games on.  let me know what you find out.  i love rappelz....flyff too.

---

### Post by cjr2k3 on 2007-02-20
Had any luck? Im going to Download the game and see if i can add something to the subject :)

---

### Post by jcquik on 2007-02-21
no updates.  i'm trying out the new Beta 6 for Mepis because i could never get the CVS cedega script to install on ubuntu but it installed completely on Mepis.   patrick295767 made the script and i found it on these forums.  Hope to find out if it works tonight.  It will be cool if it works and I can create my 1st "How to"  :)

---

### Post by justin whitaker on 2007-02-21
I just finished downloading the game. I will try it with Crossover, and with Cedega, let you know if it works.

---

### Post by justin whitaker on 2007-02-22
UPDATE:

Cedega 5.2.10 will install the game, but once you try to run it, the login screen is completely blank. So it's absolutely useless.

---

### Post by justin whitaker on 2007-02-22
Update 2:

Wine 9.31 loads the login screen, but will not update. It also hardlocked my system....I'm thinking it's one of those weird games that requires IE to be installed for rendering the login and updates. 

Did anyone install IE4Linux and see if it worked?

---

### Post by jcquik on 2007-02-27
> **justin whitaker said:**
> 
Did anyone install IE4Linux and see if it worked?

yup....tried that too.  It wants to use active x i think.

---

### Post by sneaks on 2007-03-11
It wants to use the Mozilla Active X control.  I have tried installed firefox and mozilla in cedega but it still won't work. You can download Mozilla Active X control from here [http://www.iol.ie/~locka/mozilla/mozilla.htm](http://www.iol.ie/~locka/mozilla/mozilla.htm) but I can't find the .bin files it wants for mozilla.

---

### Post by jcquik on 2007-03-11
> **sneaks said:**
> It wants to use the Mozilla Active X control.  I have tried installed firefox and mozilla in cedega but it still won't work. You can download Mozilla Active X control from here [http://www.iol.ie/~locka/mozilla/mozilla.htm](http://www.iol.ie/~locka/mozilla/mozilla.htm) but I can't find the .bin files it wants for mozilla.


cool...thx man.  i'll give it one more shot with this.

---

### Post by sneaks on 2007-03-12
Another thing I am going to try is Crossover and install  Firefox and IE and see if that works. I know you said you would try virtualbox. What was the maximun mb you could set the video memory too?

---

### Post by sneaks on 2007-03-12
I just used Crossover and it installed fine and when I started it the update manager actually loaded and it updated but when I click start game it doesn't seem like its doing anything. I don't know if it takes a long time to load in Crossover but I know it is still running b/c I can look at my processes running and I see it.

---

### Post by Iarwain ben-adar on 2007-03-21
Bumpie?


Iarwain

---

### Post by jcquik on 2007-03-22
> **sneaks said:**
> ...I know you said you would try virtualbox. What was the maximun mb you could set the video memory too?

8 mb was max for video memory.

---

### Post by masterch on 2007-04-08
Easy, What you need to do in order to run rappelz is to install the ActiveX controls, because it need it to execute the launch.exe aplication.

So you can look for this file MozillaControl177.exe and installed it on the same folder where you are installing rappelz... Before install you will need to coppy your Mozilla Firefox folder to:
$\\ c_drive/Program Files/   because the activex installation will ask for it.

The bad think about all this workarround is that after you install all this the game will not start because it has some cand of protection and you will be stuck on the welcome screen with a bar geting some updates...

I hope this will help you, and some one will find a resolve for thi other stuff...

---

### Post by FragOnly on 2007-05-03
> **masterch said:**
> The bad think about all this workarround is that after you install all this the game will not start because it has some cand of protection and you will be stuck on the welcome screen with a bar geting some updates...

I hope this will help you, and some one will find a resolve for thi other stuff...

Rappelz uses HackShield Pro (google hackshield if you want to see their page).  HackShield is not loaded until after the update launcher (red button that you click to start the game), on windows you will see a nice little hackshield pro logo when it begins to load, at this point hackshield will load a bunch of custom dlls and remap some api's to protect its self, change many permisions so on.

Anyway, if your having problems before you click the red button to launch the game, then its not HackShield relate (and yes the game does use imbeded IE, for update, ingame stores, and a few other panels).

You can by pass the launcher by launching the game its self, but it requires a somewhat long command line.

I've heard reports of people getting the updater/launcher fully working, but once they launch the game they get a blank/black/white screen where the login screen should be, thus making the game useless.

That being said, I don't think this game will be supported by any flavour due to its intensive protection system, of course if some very popular games suddenly started using HackShield im sure this would change very fast ;)

[http://transgaming.org/forum/viewtopic.php?t=6410](http://transgaming.org/forum/viewtopic.php?t=6410) 
a very short forum stating games that use hackshield are not supported under cedega.

---

### Post by nimirooyn on 2007-08-04
> **sneaks said:**
> It wants to use the Mozilla Active X control.  I have tried installed firefox and mozilla in cedega but it still won't work. You can download Mozilla Active X control from here [http://www.iol.ie/~locka/mozilla/mozilla.htm](http://www.iol.ie/~locka/mozilla/mozilla.htm) but I can't find the .bin files it wants for mozilla.



dude, the mozilla addup is for the 1.5... i have the 2.0.
got anything better?

---

### Post by nimirooyn on 2007-08-10
anyone found a solution?

I really need to stop using my mams pc cause I prefer the Linux on the "other guy"
and I can't cause i have no way of operating games...

---

### Post by Faud on 2007-09-26
Anyone able to figure away to get hackshield working ?

---

### Post by nimirooyn on 2007-10-05
same question here...
still working on it but if someone already found a way I'll be more then pleased...

---

### Post by ionredline on 2007-10-13
This is actually a really cool game.  It's almost exactly like Lineage 2 - but FREE!!

However, a funny thing I've come across, is that even some windows users cannot get the game to even work for them as well.  Those that I've talked to regarding this are Vista users.

---

### Post by nimirooyn on 2007-10-14
already found a way of working it in the vista arena...
works fine.

but I want to play it in the linux sys so I can injoy all worlds.

---

### Post by SaMuRaI_777 on 2007-10-22
I may be wrong, but doesn't Silk road use hackshield as well, and that could be run with wine?
[http://www.cedega.com/forum/viewtopic.php?t=6410](http://www.cedega.com/forum/viewtopic.php?t=6410)

And Nostale also has Ie's in game and it runs fine...
so where did I go wrong? :confused:

---

### Post by warmfreeze on 2007-11-20
i didn't have any problems with the launcher using cedega ..nor updating ..everything went smoothly untill i launched the program in the launcher ..the splash screen for hackshield comes up and then i get an error that says "cannot load hackshield engine" so even in the best case scenario it still wont work ..also tried in crossover and i get the same result.

---

### Post by escobar_ on 2007-11-20
Has anyone been able to run this game?

---

### Post by nimirooyn on 2007-11-20
nop..
still trying my *** off..

---

### Post by ionredline on 2007-11-24
The really sad thing - is this game is the only reason I keep a windows partition...  lol

---

### Post by nimirooyn on 2008-01-04
I'm with you on that...
moreover, i talked to their tech support and they say that the game works best with the XP... when i told them that i think the HACK shield they told me that it's too bed and that theirs no why to play without it.

---

### Post by LetMeSitOnYourFace on 2008-02-20
Hey I am running Fedora 8 for i86x64amd and using crossover for windows emulation. So far I can't get rappelz to update with the launcher it only loads a window with scroll bars and a close button at the top and shows the rappelz news on the left and other things.  I have installed IE 6 with crossover and directX 9 with crossover and still nothing.

 going to try on saturday to get the update and do it manualy and also see about installing active X.

---

### Post by Alegrya on 2008-05-29
bugger that none of you could get this working, I so miss gaming since moving exclusively to using an Ubuntu system.

used to be a Guild Wars player, has anybody got that working nicely under wine?

---

### Post by kazuya on 2008-05-29
I feel your pain. Rappelz like 2 moons and many of these other korean f2p games tend to use gameguard or some security application belonging to a company called GameH, if Im not mistaken. The app is really bad and very unsecure. As such, it is not designed to work in the WINE emulation world. For the most part I dual boot just to play those games and then give up on them after a while.

My favorite right now is 2moons. If u ignore the bots and ads sometimes, the game is awesome for pvp, pve, etc. It is a martial arts based type game, but I am yet to find another f2p game as good as it. I know folks who tried rappelz and like it also.

A better game to try that may work in Wine is Requiem: Bloodymare Open Beta RequiemOBTClient. I'm asking in forum on who has gotten it to work.

If those games leave out gameguard, the game would run flawlessly on the linux system also.
One gripe with it is that it may be gory.

---

### Post by Nrlegend on 2008-08-28
Hayy guyz try using WINE and then installing, virtual pc 2007 at the windows website that might work imma try it and then tell you iight!?:wink:

---

### Post by zymjh on 2008-11-23
Bump

---

### Post by poisonkiller on 2008-11-24
> **Nrlegend said:**
> Hayy guyz try using WINE and then installing, virtual pc 2007 at the windows website that might work imma try it and then tell you iight!?:wink:
Does Virtual PC 2007 support DirectX (9.0)? If not, then your idea won't work. As long as GameGuard doesn't add support for WINE (which it probably won't), we won't be able to play any games using GameGuard.

---

### Post by ionredline on 2009-10-18
Bump

---

