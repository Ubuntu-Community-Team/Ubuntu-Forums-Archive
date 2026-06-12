---
title: "Wich is better Wine, Play On Linux or Cross Over Linux ?"
date: 2011-07-29
forum: Wine
---

### Post by sadaruwan12 on 2011-07-29
Hi all,


I want to play HitMan game series from Eidos but I know that I must use one of the above mention emulator layers to run it under Ubuntu. Currently I'm using Natty (11.04) and I just want to know which one is better.

I tried wine ones but it was not very supportive so wish you nice people could help me thank you in advance.

---

### Post by robgraves on 2011-07-29
i'm not really qualified to answer, as i've not really ever got wine to work effectively for me, but i have experimented with wine and play on linux and the impression i get is that play on linux is really just a frontend for wine, and installs wine when you install POL, so essentially they are the same thing, i don't know anything about Cross Over Linux.

---

### Post by sadaruwan12 on 2011-07-29
> **robgraves said:**
> i'm not really qualified to answer, as i've not really ever got wine to work effectively for me, but i have experimented with wine and play on linux and the impression i get is that play on linux is really just a frontend for wine, and installs wine when you install POL, so essentially they are the same thing, i don't know anything about Cross Over Linux.

Thank you for your answer, Only you had the heart to do it my thread got moved here but no one except you answers so how person could get quick answer.

If the mod. who moved this here must answer but nothing all the active users are in beginners section very few are in else places this section is called wine I'm not asking about wine I'm asking which is better to use If i asked any thing about wine then this move would have been justified.

I might get kicked out for this bet please consider this before kicking me ok.

Thank you.

---

### Post by Mark Phelps on 2011-07-29
You  asked a question about Wine -- THIS is the correct section for such a question.  Quit "whining" about the Mod doing their proper job moving your post here.

Second, they're all derivatives of Wine.  The difference being that Play on Linux and Crossover Linux offer additional aids to ease the installation and configuration of Windows apps.

But in the end, if it doesn't work well in Wine (and MOST of the stuff doesn't work well in Wine), the other two are not going to make it work better.

---

### Post by cwwilson721 on 2011-07-29
You ask an odd question. Why?

wine is the 'base' for all of the above. So none are 'better".

However, there are differences:

wine is the 'base' program for all of them. It provides the required dll's, etc. to allow a Windows program to work in Linux.

Play on Linux adds a GUI for installing and running the Windows programs to wine. It also has a few 'tweaks' to make SOME programs install easier. With that being said, it doesn't do enough 'over and above' plain wine to be useful, and it has many 'quirks' of it's own that need to be worked around (in some cases).

Crossover is wine that you HAVE TO PAY FOR. The advantage to that is since you paid money, Crossover will support it. You ask them, they will work on it for you. Also, wine is made by the developers of Crossover.

Taking all of this in, it comes down to your own preferences:
[LIST]
[*]Do you want the least frills? wine
[*]Do you want just a paint job? POL
[*]Do you want to pay more to use it? Crossover
[/LIST]

With all that being said, I prefer wine. Why? Let's take a car analogy:

wine is the basic Ford Taurus. It does it's job. It's also out of warranty, so you have to do all the work yourself. But it runs fine.

POL is a coat of coat of paint (that cannot be changed, except by POL) and different tires on your aforementioned Taurus. It really does little to the actual running of the vehicle, and they welded the wheels on so you can't change them. If you don't like the color, too bad. If you don't like the wheels, too bad. If something goes wrong, was it wine, or POL? Too bad. It's a layer of complexity that is rarely ever required. It's pretty, but doesn't add enough functionality to be worth the hassles (imo).

Crossover is like taking the Taurus, putting on a non-changeable  coat of paint on it, welding on wheels, and being charged $890,000.00 for it. And they electrified the car body so nobody else can work on it. But they do stand behind their product. Which is a good thing, because nobody else can work on it.

So. Get the 'original', and make it your own (takes some work), get a neat paint job, and always wonder (POL), or pay for a free product?

NOTE: All the above is simplified a great deal. This is just a general comparison.

---

### Post by brian70809 on 2011-07-30
Wine is the backbone, but not all NEW users to Linux are comfortable with it.  However, if you are, it has some advantages as far as patches and quicker updates..

Crossover is the paid version of Wine.  It uses the opensource developments and their own programmers to create a version of Wine for Novice and Expert linux users.  It also uses bottles to enclose each config of wine for each launched Wine application.  For many, this solves a lot of compatibility issues that wine has.  It is $49.. Pretty cheap for a program that will save people a lot of time and for the programs it supports is Turnkey.  And that is what it is designed for.  It also has versions for the Mac.

PlayOnLinux is a script engine to install programs using Wine.  My experience with it is very limited.

They all have their strengths.. I use Wine and Crossover because sometimes one version will correct a problem before the other one.  The self configuration makes installing programs faster for me on many applications.

Good Luck!

---

### Post by sadaruwan12 on 2011-07-30
Ahhhhh, Finally thank you and sorry for that whining post I was very upset when I wrote that sorry again to the community and mod too please forgive me.

I was up all night that day trying to figure it out my friends I'm a very active person in the "Absolute Beginner" section and I answer most questions that I know how to solve and I got little upset 'cos most people looked at my post and by passed it with out even saying any thing except for the first answer I got thx for tat.

My fellow posters sorry again and thank you for the compression of details thank you.

---

### Post by Dlambert on 2011-07-30
Correction, WINE is not developed by Crossover, WINE is mostly funded by crossover. I would Try playonlinux first, i Used to use it, and enjoyed it, but once i became more experienced with wine, I just didn't need a GUI.

---

### Post by brian70809 on 2011-07-31
And Crossovers Funding does what????

Pay for Development.. 

It's the chicken or the egg.. lol..

It's all good.

---

### Post by dtfinch on 2011-07-31
I don't use PlayOnLinux anymore (used it a very short time), but it can maintain multiple wineprefixes and wine versions so each program can run on its own customized setup.

The downside I saw was that its game install scripts tend to specify much older versions of wine than are actually needed. And I was writing my own startup scripts for everything anyway because I have dual monitors and a lot of games need the resolution changed before running them.

I build my own wine from the latest source, with minor changes, and all my games just happen to get along in one wineprefix for now. Though I think I would have been better off starting with multiple prefixes.

---

### Post by jparshall on 2011-08-01
> **cwwilson721 said:**
> You ask an odd question. Why?

Crossover is like taking the Taurus, putting on a non-changeable  coat of paint on it, welding on wheels, and being charged $890,000.00 for it. And they electrified the car body so nobody else can work on it. But they do stand behind their product. Which is a good thing, because nobody else can work on it.


I'd, ummm, say that "890,000" represents a *slight* exaggeration on your part.  ;-)  You can get a copy of CrossOver for as little as $39.95.  And the "electrified car body" analogy is, I think, suspect as well.  Our product is, as you say, based on Wine.  We do have some proprietary bits around installers and what not, but that's mostly a wrapper for Wine.  We use free Wine as our core, and our own Wine code base is 95% identical with free Wine.  

Of course, everything we do in Wine goes back to free Wine, so whether you're using free Wine, or POL, or CrossOver, you're using a very large amount of CodeWeavers' work, because we're the largest Wine development group on the planet.  And you're welcome.  So, if you like Wine, and you want it to get better, the easiest way to make that happen is to give us money, so that we can pay our  long-suffering developers, so that they can make it better.  Alternately, by all means please feel free to contribute Wine code yourself (except that Wine development is probably the hardest development work on the planet, and is roughly as much fun as climbing Mt. Everest in a scuba suit and stripper heels.)

Cheers,

-jon parshall-
COO
[www.codeweavers.com](www.codeweavers.com)

---

### Post by sadaruwan12 on 2011-08-03
Wow, I didn't thought this might happen a response straight from codeweavers.

So ok 'cos of you we got wine and hats of for that and also thank you for the mighty contributions you do to keep open source moving forward.

You know there are some people like to do it the easy way and some to do it there own way mostly in linux community we like to do thing in our own way so some times you ppl might get blasted but brush them of 'cos trough that you'll ge ideas to improve wine and even to improve your self that's what drive this beautiful world of FOSS forward unlike the money centric win world.

Again I thank you for your contributions to the FOSS community.

Oh and I re-marked this as unsolved 'cos it seems to be getting some interesting feed back so thought to continue please feel free to post your comments on the topic.

---

### Post by PayPaul on 2011-10-30
An interesting debate going on here. I had searched first for a resolution and graphics problem so first went through some of the troubleshooting steps outlined in the "before you post here" thread. I did solve the problem by finding out I could change the resolution of programs to a higher one in Wine config. It took some fiddling and trial and error but now the program, Dynamic Photo HDR by MediaChance works more or less flawlessly with none of the blurred and pixelated graphics as before. The solution was to up the resolution in the Graphics tab to 1024 X 760. I can now navigate through the program with little inconvenience.

That said I'd like to add a question that I believe is corollary to the discussion here. What works better, Wine installed from Software Center or Wine that is self compiled? Are there any additional options or possibilities for making it better or more compatible when compiling the program from source? If there are or if there's any kind of benefit could someone lead me through the steps?

My current version has given me some troubles but I've been able to learn how to use Wine Config to solve most of them. For what it is trying to do I give the code writers credit.

---

