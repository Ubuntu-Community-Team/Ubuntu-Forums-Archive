---
title: "Xgl/Compiz... is that all there is?"
date: 2006-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by hajk on 2006-06-18
Decided to take the plunge and install the Xgl/Compiz packages mirrored from our esteemed forum participant RAOF (at [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) dapper eyecandy). It took a bit of doing, but finally there it was... but how disappointing all:

1. Windows greyed out when not active...
2. Menus and similar labels bobbing and weaving before settling down to be read.
    I do have sealegs, never been seasick, but this stuff just might induce it.
3. Switching between workspaces with a motion-sickness-inducing swirl, the 
    "spinning-cube" idea no doubt.

Where is the added value of this, I wonder.

BTW, almost all HOWTOs and wiki pages mention that xmodmap must be changed -- not so, just accept the Gnome keyboard settings when first starting this stuff.

So, I happily count myself out on Xgl/Compiz. I do like the other (non-eyecandy) stuff in RAOF's repository, though...

---

### Post by purfier on 2006-06-18
Some like eyecand like xgl/compiz, others dont. Thats the way it is, and thats why ubuntu is a good thing, You dont need to use things you dont like;)

---

### Post by RoNoVe on 2006-06-18
1. disactivate "trailfocus"
2. change your wobble setting.
3. the cube rocks! ;)

You know you have to configure software, don't you?

---

### Post by JoWilly on 2006-06-18
[quote=hajk]
Where is the added value of this, I wonder.
[/quote] 
What a strange mind... :confused:

Why do people dress in defferent ways ? Whats the added value of this ?

Why do people use windows and others use linux or mac ?

Why do people repaint their homes ?

Why don't we all use the same backgound picture ?

Why ... ... ... :rolleyes:

---

### Post by FluffyElmo on 2006-06-19
Other neat features, hit *F12* with multiple programs on the same desktop for a useful expose style effect. Drag programs from one desktop to another in dual head just by using the virtual desktop applet. *Alt-Tab* shows snapshots of the program windows instaed of just icons, including playing video.

Run *gset-compiz* to enable additional effects and turn off or tone down the ones you don't. After a bit of tweaking I find I can't do without xgl...it's not just the eye-candy, my desktop is much more responsive. Firefox even renders pages faster with XGL than without...which I didn't expect at all.

---

### Post by angkor on 2006-06-20
[QUOTE=hajk]Decided to take the plunge and install the Xgl/Compiz packages mirrored from our esteemed forum participant RAOF (at [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) dapper eyecandy). It took a bit of doing, but finally there it was... but how disappointing all:

1. Windows greyed out when not active...
2. Menus and similar labels bobbing and weaving before settling down to be read.
    I do have sealegs, never been seasick, but this stuff just might induce it.
3. Switching between workspaces with a motion-sickness-inducing swirl, the 
    "spinning-cube" idea no doubt.
[/QUOTE]

Install 'gset-compiz',

```
sudo apt-get install gset-compiz
```

and configure compiz to your liking. I don't have a spinning cube nor wobbly windows, I just have an extremely fast hardware rendered desktop (except for resizing :().

Not everybody needs to adjust xmodmap, but some people do. That's why the howto's include it...what's the problem?

---

### Post by hajk on 2006-06-20
Hey folks, I was a bit taken aback by some of the reactions to my original post... as if I had trodden on some deeply held beliefs. Yes, of course I know that Compiz requires some further setup, and that the busy-busy, twirling-twirling, dancing-dancing effects can be turned off -- but that makes my original question the more pressing: what is the added value (other then entertainment)?

Anyway, there's no accounting for taste, is there? I don't mean that in any denigrating way.

See the posts at [http://www.ubuntuforums.org/showthread.php?t=200393]("http://www.ubuntuforums.org/showthread.php?t=200393")
for a pointer to downgrading the packages updated from RAOF's repository back to their original Ubuntu Dapper ones.

Peace...#-o

---

### Post by henriquemaia on 2006-06-20
[quote=hajk]Hey folks, I was a bit taken aback by some of the reactions to my original post... as if I had trodden on some deeply held beliefs. Yes, of course I know that Compiz requires some further setup, and that the busy-busy, twirling-twirling, dancing-dancing effects can be turned off -- but that makes my original question the more pressing: what is the added value (other then entertainment)?

Anyway, there's no accounting for taste, is there? I don't mean that in any denigrating way.

See the posts at [http://www.ubuntuforums.org/showthread.php?t=200393]("http://www.ubuntuforums.org/showthread.php?t=200393")
for a pointer to downgrading the packages updated from RAOF's repository back to their original Ubuntu Dapper ones.

Peace...#-o[/quote] 
Answering your question: 

Last time I tested XGL, I was amazed by the realtime transparency. That's very useful. That together with the scroll up/down mouse wheel shortcut to make a window more or less transparent gives more productivity to the desktop. There is more to XGL than just eyecandy.

---

### Post by Kilz on 2006-06-20
[QUOTE=hajk]Hey folks, I was a bit taken aback by some of the reactions to my original post... as if I had trodden on some deeply held beliefs. Yes, of course I know that Compiz requires some further setup, and that the busy-busy, twirling-twirling, dancing-dancing effects can be turned off -- but that makes my original question the more pressing: what is the added value (other then entertainment)?

Anyway, there's no accounting for taste, is there? I don't mean that in any denigrating way.

See the posts at [http://www.ubuntuforums.org/showthread.php?t=200393]("http://www.ubuntuforums.org/showthread.php?t=200393")
for a pointer to downgrading the packages updated from RAOF's repository back to their original Ubuntu Dapper ones.

Peace...#-o[/QUOTE]

Its 100% eye candy! :D But some people like it alot. Dose it ad value? Well if you value eye candy it dose.  :D Some people claim its faster, I havent seen that.
Personaly I grew tired of it and turned it off. It wasnt for me. But if someone else wants to spend a couple hours banging thier head into a wall to get it to work. Have fun. :D 
Linux and Ubuntu is all about choice, you can chose to make it whatever you want. Even if all you want it eye candy.

---

### Post by angkor on 2006-06-20
[QUOTE=hajk]but that makes my original question the more pressing: what is the added value (other then entertainment)?
[/QUOTE]

You don't seem to understand the point of xgl. What you see is a preview of what is possible when your desktop is no longer rendered by your cpu but by your grapics card. 

In the future (who knows when) linux will drop the old X and take a new approach to dekstop rendering. When your cpu is longer occupied with rendering the desktop it will free up cycles to do more important tasks and make your system perform better.

If you have a powerful graphics card atm you will see that a XGL&Compiz desktop is more responsive and smoother than an ordinary X desktop.

Have you ever seen OSX in action? That is a hardware accelerated desktop. The eye-candy is an added bonus...or not if you don't like it. ;)

[http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl)

---

### Post by angkor on 2006-06-20
oops....double post.

---

### Post by JoWilly on 2006-06-20
[quote=Kilz] But if someone else wants to spend a couple hours banging thier head into a wall to get it to work.[/quote] 
Couple of hours ? Wow, I'm sorry for you.

It takes less than 2-3 minutes to set up over here (could probably take even less).

Xgl is very easy and needs very few steps to set up (I have installed it on ati and nvidia systems, 32 and 64 bit), but there are unfortunately many missleading posts on these forums with much confusing and unecessary things that are not needed like scripts to start compiz,  installing  xgl  into /opt, exporting library paths, etc... What a mess.

As always there are of course people without appropriate drivers for their gfx card or laptop (complain to your manufacturer), but if you are not one of the unlucky ones and got a decent gfx card it shouldn't be any trouble at all.

Forum staff should clean all those missleading long threads and sticky posts up and leave only the relevant information.

---

### Post by hajk on 2006-06-21
> **angkor]You don't seem to understand the point of xgl. What you see is a preview of what is possible when your desktop is no longer rendered by your cpu but by your grapics card. 

In the future (who knows when) linux will drop the old X and take a new approach to dekstop rendering. When your cpu is longer occupied with rendering the desktop it will free up cycles to do more important tasks and make your system perform better.

If you have a powerful graphics card atm you will see that a XGL&Compiz desktop is more responsive and smoother than an ordinary X desktop.

Have you ever seen OSX in action? That is a hardware accelerated desktop. The eye-candy is an added bonus...or not if you don't like it.  said:**
> http://en.wikipedia.org/wiki/Xgl[/url]

Thanks for your reply, the first useful comment on this topic that I've encountered in a long time. I'll keep following it from a distance, it might be useful when my dual core Opteron processor gets loaded to the gills with work...;)

---

### Post by angkor on 2006-06-21
[QUOTE=hajk]Thanks for your reply, the first useful comment on this topic that I've encountered in a long time. I'll keep following it from a distance, it might be useful when my dual core Opteron processor gets loaded to the gills with work...;)[/QUOTE]

Thanks. 

If you're proc doesn't get loaded to the gills frequently you obviously bought the wrong (too expensive) proc. ;)

---

### Post by Kilz on 2006-06-21
[QUOTE=JoWilly]Couple of hours ? Wow, I'm sorry for you.

It takes less than 2-3 minutes to set up over here (could probably take even less).

Xgl is very easy and needs very few steps to set up (I have installed it on ati and nvidia systems, 32 and 64 bit), but there are unfortunately many missleading posts on these forums with much confusing and unecessary things that are not needed like scripts to start compiz,  installing  xgl  into /opt, exporting library paths, etc... What a mess.

As always there are of course people without appropriate drivers for their gfx card or laptop (complain to your manufacturer), but if you are not one of the unlucky ones and got a decent gfx card it shouldn't be any trouble at all.

Forum staff should clean all those missleading long threads and sticky posts up and leave only the relevant information.[/QUOTE]

The thing is, at this point, Xgl is experimental. While it may go smooth for your install, its not even slightly guaranteed to go smooth for others. I have a ATI graphics card and run the ATI drivers, maybe that's why it took so long. I had to hunt down troubleshooting tips, finally found out I needed to add a few things from a SuSE page.
I agree 100% we need a howto that gathers all the info in one place. But seeing how its still in the experimental stage, stuff changes quickly.

---

### Post by JoWilly on 2006-06-21
[quote=Kilz]The thing is, at this point, Xgl is experimental. While it may go smooth for your install, its not even slightly guaranteed to go smooth for others. I have a ATI graphics card and run the ATI drivers, maybe that's why it took so long. I had to hunt down troubleshooting tips, finally found out I needed to add a few things from a SuSE page.
I agree 100% we need a howto that gathers all the info in one place. But seeing how its still in the experimental stage, stuff changes quickly.[/quote] 
I would say  "still in development" fits better than "experimental". Xgl/compiz has been rock stable on the 7 installs I did (different machines, nvidia and ati cards) since the first day it was released. Of course I was lucky to get drivers that supported the cards properly. I see drivers as the only problem with xgl today (apart from the fact of having it set up automatically at install as it would be easier for newbies), and this is the problem of the manufacturers, this has nothing to do with xgl (opengl is an open standart, if your closed source drivers do not support the standart correctly for your card you can only look at your manufacturer).

The problem you explain, only confirms that you where misslead by the messy information of the mess of threads we have on these forums. I know the suse page very well, and an ati 9800XT was the first card I installed xgl on several months back when it was released, and I can assure you that ati was not the reason why it took so long for you.

The problem is that when xgl came out, everyone tried to do his own "sauce" which now results in a mess of different and often complicated ways to do the same "easy" things.

You say it is experimental and that stuff changes quickly, but absolutely "nothing" has changed in the way of installing xgl/compiz since the very first day it was released, be it on nvidia or ati.

Of course it is not newbie ready yet, as a newbie needs click and run... but this has nothing to do with xgl beeing experimental, it is the problem of a missing installer (and proper drivers for some).

---

### Post by JoWilly on 2006-06-21
@ Kilz :

To add to my previous post, I will agree with you in saying that xgl is experimental the day you will agree with me that Ubuntu is experimental compared to windows. ;)

You can call this comparing apples with apples :D

---

