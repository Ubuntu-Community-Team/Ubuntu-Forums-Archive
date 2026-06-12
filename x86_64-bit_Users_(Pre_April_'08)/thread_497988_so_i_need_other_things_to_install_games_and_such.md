---
title: "so i need other things to install games and such"
date: 2007-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by bullsmack on 2007-07-10
i just downloaded drivers for my video cards and nvidia says that i need to do things to install these drivers. i have two 7900 gt oc cards (sli). 

   i am wondering if i need other programs to install these drivers(very confused as to what i need)?

   i do not mind having to do something to install programs and drivers, but i have no clue what i need to do this. also,....

   i am trying to install a game(Tribes Vengeance multi player demo ), and i am assuming that i cant just expect to run the exe and it work . soooo with that said, i did a word search (games) on the forum so i wouldn't have to post and the search showed 0 results. so here i am again trying to learn something. HELP!!!!!!,  so far i have installed updates (73 of them)
   what do i need to so to install this game? are there things i need to download to do this? and once i download whatever it is that i need. HOW WOULD I INSTALL THAT DOWNLOAD as well? this all seems so complicated. and there is absolutely no way that anyone would just KNOW these things if they never used Linux before. i see why the forums are so valuable now.

---

### Post by insomniacpyro on 2007-07-10
Linux is a completely different system from Windows, so your .exe files from windows will not work on your Linux installation.

That is, without something in Linux to run them. Your best bet is Wine, at 
[http://www.winehq.org/](http://www.winehq.org/)
After Wine is set up, you should be able to right-click the .exe and install the program in your new 'c drive' which Wine creates for setup files and such to install properly.

It's important to note that Wine (and just about every program that can run windows apps) will be a little choppy on game performance.

---

### Post by tgm4883 on 2007-07-10
If you try to use Wine to install your drivers, it wont work.  There is a linux way of doing things, and while I know what that is for single cards, im not sure if anything else is necessary for a SLI setup.

---

### Post by insomniacpyro on 2007-07-10
Soo to answer you questions from the newbie forum, You have to install Wine by first updating your Repository (it is on their site) then using the commands on their site to install it.

After that, just refer to my other post to run programs. I'm also a newbie, so this is from one to another. :)

---

### Post by dfreer on 2007-07-10
Before you get started, please note according to the application database at winehq, Tribes Vengence is not playable in wine. Not sure if you would really gain any sort of performance gain anyways (other than server uptime), so if you are looking at Ubuntu just to play and serve this game you are most likely going to be sorely dissappointed. It might work, it might not *shrugs*.
That being said, ubuntu is great for many other things, and if you do keep ubuntu you'll find that gaming is just *different* on ubuntu, not impossible. :)

---

