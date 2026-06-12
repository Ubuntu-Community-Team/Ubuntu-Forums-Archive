---
title: "Gutsy 64 fresh install - a report"
date: 2007-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxgrrl on 2007-12-26
I had been using 32 bit Dapper for a while and was more than ready for an upgrade, so decided to take the plunge and run 64-bit Gutsy on my 3 y.o. AMD Athlon64 system.  Installing was not as smooth as it ought to be, so I thought I'd share the hiccups in case this helps anyone, as well as meeting my own need to vent.

1. the CD initially failed to boot properly.  Turns out it was looking for a floppy drive that the BIOS thought should be there -- definitely my fault.  However, the animated progress bar continued to tick on endlessly as though everything was fine, when it really wasn't. Luckily I had another computer running and could check the forums, figure out how to get the boot messages to scroll past, google the i/o error messages and change the bios.  A newbie might have given up at this point and just assumed Ubuntu was broken.  Would it be possible to have an error message display rather than just hang the install with the Ubuntu logo screen and misleading ticking progress bar?  

2.  props for the partitioning tool.  It's a lot easier to use than it used to be.  

3. everthing installed, I got a pop-up message about the available non-free nvidia drivers for my fx5200.  Great, maybe this time I won't have the dreaded nvidia compatibility problems that drove me away from 64 bit 3 years ago.  Well, almost.  Restarting X caused a black screen -- ugh! -- with no apparent rescue option. Again, I know just enough to use Alt and the F keys - f7, f8, whatever -- to get to a terminal and re-start/reconfigure X manually.  Turned out the nvidia package defaults to a higher resolution than either of the two plain-vanilla lcd monitors I tried would support.  I've seen this before in the forums, and I bet it defeats a lot of newcomers to ubuntu.  Maybe the install should default to a less aggressive setting and have a test/bailout routine for the user to change her own settings, rather than place a landmine in the user's way? 

4. once X started working  - wow, this thing can really fly.  Ticked the box for enhanced desktop effects.  The display is simply beautiful and super-responsive.  GF is now jealous because she just shelled out for a new dual core iMac and wants to know "why is your computer so much faster" :)

5. followed the  instructions in system help for how to get DVD's working ... once I figured out some missing dependencies, it appeared to compile something and install it without errors, but commercial DVDs still don't play.  I think of the system help as really the lowest common denominator of help .... if some advice is in there, it ought to be tested to work on a clean install without the user having to figure out her own dependencies, and should actually work.  I'm happy to dork around in the forums to get my dvds working but please don't put something in the system help if it has not been adequately tested and does not work!!!

6.  installed the mythtv packages through Synaptic.  Cool, will this be the time that I don't have to compile mythtv from source?  Yes!  Well, again, with a caveat.  The mythtv package claimed it was configuring mysql, and asked me to input a root password, but it never actually created the mysql database that is required for mythtv!  It took me 2 hours to figure this out, again because of the misleading install message that the package gave.  [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
](*,)
It sure did not help that the mythtv package generates a big ugly super-secure default password - why???  this is just television, for pity's sake -- then it asks you to input a different root password, masks what you type, and not requiring a re-type -- so I spent a long time assuming I was just mis-typing or misunderstanding the password.  I tried re-installing the myth packages and was on the point of reinstalling the whole operating system when I finally figured out that the problem was the incorrect message from dpkg, and there was no mysql database.  Honestly, I would rather have a package tell me "you need to create a database and configure mysql, please go figure out how", rather than claim to do it and botch the job.

7.  A lot of the configuration dialogs in "preferences", etc., are bigger than the desktop so you can't see the lowest layer of buttons.  Pretty strange for default behavior.   I'm using a Samsung LCD tv as my display but is that so terribly unusual these days?


Anyway, despite all these hiccups the OS itself is just lovely, beautiful and fast.  

Thank you for listening to my rant.  My thanks everyone who worked on 64 bit Ubuntu.  Despite my kvetching it's a lot better than just a few years ago.  Once I get the flash bug workaround going, and these other little annoyances fixed, it will be awesome!

---

### Post by fjgaude on 2007-12-26
Thanks for all the details of your install... one of these days all hardware will be recoginzed automatically and Linux would be perfect. Until then, we thank all the folks who work on open source.

Happy New Year.

---

### Post by thenewrhapsody on 2007-12-26
I totally agree, once you get around a few bugs things just tend to fly, not to mention looking good while doing it. I suppose with anything else, patience is the key.

---

### Post by Kilz on 2007-12-26
A post on here is a nice thing for other users. But to properly report problems to the developers so they can be fixed you need to file bug on launchpad. That even includes things that you feel need improving like a warning message.

---

### Post by Yellow Pasque on 2007-12-26
I <3 Linux women

---

### Post by linuxgrrl on 2007-12-27
> **Kilz said:**
> A post on here is a nice thing for other users. But to properly report problems to the developers so they can be fixed you need to file bug on launchpad. That even includes things that you feel need improving like a warning message.

yeah, I read the instructions for Launchpad and felt a little intimidated that I would have to tear down my whole system to show that the bug is "reproducible", or that I would get (figuratively) yelled at for reporting things that are already known such as the screen resolutions being too aggressive. 

But you've obviously been around the block a few times and iif you say it would be helpful for people to file these things, I will happily do it.

---

