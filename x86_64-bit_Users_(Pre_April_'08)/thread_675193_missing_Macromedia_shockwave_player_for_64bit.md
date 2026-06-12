---
title: "missing Macromedia shockwave player for 64bit"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by roofninja on 2008-01-22
Over the weekend I got my new PC put together and working.  This is my first expierence with 64bit systems on Linux, so please excuse the deer in the headlight look.

I have been reading a lot about flash player and I realize it is the shockwave player that is not working.  When I go and find help on shockwave player, there is nothing about it.  Is there a fix for it?  Is there an alternative that will work?  Is that why people are using Gnash?

Thanks for any help.

---

### Post by Steveway on 2008-01-22
There is no Shockwave player for Linux.
What sites are not working that you try to use?

---

### Post by roofninja on 2008-01-22
> **Steveway said:**
> There is no Shockwave player for Linux.
What sites are not working that you try to use?

Because I don't have digital tv, yet, I can't get my X-Play on G4tv.  Here is a link that to a page.

[http://www.g4tv.com/xplay/features/19890/Will_Work_For_Games_Games_Tester.html](http://www.g4tv.com/xplay/features/19890/Will_Work_For_Games_Games_Tester.html)

What I find is strange is when I got home, it worked.  I was able to see, so I went to another page but then it stopped working.  I don't get this.

---

### Post by Steveway on 2008-01-23
I can watch that movie.
It uses Flash and not Shockwave.
There is a guide/script here on the forum somewhere that will help you installing Flash on a 64bit system.
Use the search and you'll find it.

---

### Post by SunEyed on 2008-01-23
> **Steveway said:**
> I can watch that movie.
It uses Flash and not Shockwave.
There is a guide/script here on the forum somewhere that will help you installing Flash on a 64bit system.
Use the search and you'll find it.

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by robbie carrobie on 2008-01-23
hey cannot believe it, i did it, with your help of course, i can watch videos on you tube, amazing, thanks so much, now please dont think i am being presumptuous but is their a simple method for enabling swift weasel to let me watch divx, thanks so much in advance - Regards Robert.

---

### Post by roofninja on 2008-01-26
> **Steveway said:**
> I can watch that movie.
It uses Flash and not Shockwave.
There is a guide/script here on the forum somewhere that will help you installing Flash on a 64bit system.
Use the search and you'll find it.

Yes, you are right, that page does use Flash and not Shockwave.  I have been waiting to post again to show the error on the page and any relevant errors that I could find.  Here it is.  When I the page stops it does this: Look at the attachment PNG and you will get the screen shot.  I also get this error or defunct when I check what is running

ps -e
 6873 ?        00:00:00 firefox
 6885 ?        00:00:00 run-mozilla.sh
 6889 ?        00:01:18 firefox-bin
 6924 ?        00:03:44 npviewer.bin <defunct>
 6993 ?        00:00:00 gnome-terminal
 6996 ?        00:00:00 gnome-pty-helpe

Is there a way to restart the npviewer.bin?  Maybe that is causing the problem?

---

### Post by roofninja on 2008-01-26
SunEyed,

Thanks for the thread post but I had already gone through it.

---

### Post by roofninja on 2008-01-26
Here is different page that might show what I was originally posted about.  Also I have included a screen shot.

[http://www.g4tv.com/attackoftheshow/blog/post/682295/Attack_This_The_Future_Is_Now.html](http://www.g4tv.com/attackoftheshow/blog/post/682295/Attack_This_The_Future_Is_Now.html)

---

### Post by Kilz on 2008-01-26
> **roofninja said:**
> Here is different page that might show what I was originally posted about.  Also I have included a screen shot.

[http://www.g4tv.com/attackoftheshow/blog/post/682295/Attack_This_The_Future_Is_Now.html](http://www.g4tv.com/attackoftheshow/blog/post/682295/Attack_This_The_Future_Is_Now.html)

It looks like you have tried to install a plugin, but failed. this leaves a blank place a lot of the time. Follow the link in post 5. my script will install flash and will try to remove failed attempts. But if you know what you tried before its always best to remove it if you can remember.

---

### Post by indeed on 2008-02-14
Any success? I'm experiencing the same problem. It's intermittant and occurs despite repeated reinstalls.

As well as the defunct npviewer process there's a lot of

*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed

going on when firefox is run from the command line.

---

### Post by MystikIncarnate on 2008-02-14
i found that the nswrapper usage of flash in firefox 64 causes a lot of problems.... flash crashes and will not restart until you completely close firefox, and reopen it.  annoying at best.

what i've done, is i downloaded an application from another repository, it's a 32-bit firefox with all plugins for 64-bit systems. works like a charm.  i have yet to find a webpage that doesn't load on it.

though it does crash occasionally, i've had much better experience with running the 32-bit version with all addons, rather than the 64-bit version with nswrapper 32-bit addons.

i'll try to find the repo and key CLI commands for everyone.

---

### Post by MystikIncarnate on 2008-02-14
that took a lot less time than i thought it would. ha.

I originally found this repo while trying to install cinlerra (a video editing app, similar to Premiere by Adobe, but free!)  so, this repo also has cinelerra and a few other applications.

for a list of applications and the CLI commands to add the repo to your ubuntu, go [here]("http://project.akirad.net/node/18").

after adding the repository, simply load up Synaptic and search for "ia32", and the 32-bit firefox should pop up to the top, add the complete firefox package, and it will install all necessary add-ons and plug-ins to give you a fully featured 32-bit firefox.

i'd like to mention that this will NOT replace your current firefox, so you'll have to go to the internet section of the applications to find the program.

---

### Post by Kilz on 2008-02-14
> **MystikIncarnate said:**
> that took a lot less time than i thought it would. ha.

I originally found this repo while trying to install cinlerra (a video editing app, similar to Premiere by Adobe, but free!)  so, this repo also has cinelerra and a few other applications.

for a list of applications and the CLI commands to add the repo to your ubuntu, go [here]("http://project.akirad.net/node/18").

after adding the repository, simply load up Synaptic and search for "ia32", and the 32-bit firefox should pop up to the top, add the complete firefox package, and it will install all necessary add-ons and plug-ins to give you a fully featured 32-bit firefox.

i'd like to mention that this will NOT replace your current firefox, so you'll have to go to the internet section of the applications to find the program.

Alternately, you can just run my [32bit firefox and plugins scrip]("http://ubuntuforums.org/showthread.php?p=1174435")t.

---

### Post by mad_max0204 on 2008-02-14
Did you try installing flash normally ???
Trust me it works

[http://ubuntuforums.org/showthread.php?t=696726](http://ubuntuforums.org/showthread.php?t=696726)

---

