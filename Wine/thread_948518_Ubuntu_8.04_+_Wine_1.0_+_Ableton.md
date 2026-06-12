---
title: "Ubuntu 8.04 + Wine 1.0 + Ableton"
date: 2008-10-15
forum: Wine
---

### Post by C0MM4NDER on 2008-10-15
Hi.

In my school we started using a music creation tool Ableton, and i wanted to try it on my laptop with Ubuntu os.

Installing the software went painless, only thing is that everytime i launch the program it need internet connection because it cannot save that "Trail" have been activated (2weeks) But this is not my main problem. (maybe it is so dunno havent tried it on xp or mac)

Main problem = Wine dont render whole app, it cuts the down bit and there is no way to fix it what i know of. here is qouple of screnshots photos (nokia n95) pics in attachment

please help because i love ubuntu and using that program would be awsome ;)

Best Regards Commander

---

### Post by simtaalo on 2008-10-15
not quite sure how to fix it, i dont have much knowledge with wine.but if you do get ableton working properly on it ill be impressed.

next time you need to take a picture of your screen, use the screenshot function, its in accessories. much easier to see whats going on than a cam-phone picture.

---

### Post by C0MM4NDER on 2008-10-15
When i hocked up my external samsung monitor to my laptop and run ableton it worked perfectly only problem is that "it need" higher res. My laptop got 1280x800  when using my external on 1680x1050 it worked nicely sound everything works.

Problem is hghest res is 1280x800 on my laptop so how could i fix it ?

---

### Post by niffcreature on 2008-11-14
go to wine>config>graphics and try emulating a virtual desktop of your resolution, uncheck "allow window manager to control/decorate windows". 
this all works fine for me (before the rest of ableton stopped working for other reasons) and my resolution is 1024x768.
oh, and i dont know if wine has a menu for config in version 1.0, if not you can just run winecfg in the terminal. actually im not sure if you can really do any of that in wine 1.0, you might want to use the latest beta.
simtaalo: dont be surprised. ableton live is gold in the wine appdb.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2113](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2113)
comm4nder, you should take a look at that too. if anything else isnt working for you (im surprised it works as well as you describe) you should be able to figure out a version combination that works.

hope this helps.

---

### Post by rstets on 2009-02-03
> **C0MM4NDER said:**
> Hi.

In my school we started using a music creation tool Ableton, and i wanted to try it on my laptop with Ubuntu os.

Installing the software went painless, only thing is that everytime i launch the program it need internet connection because it cannot save that "Trail" have been activated (2weeks) But this is not my main problem. (maybe it is so dunno havent tried it on xp or mac)

Main problem = Wine dont render whole app, it cuts the down bit and there is no way to fix it what i know of. here is qouple of screnshots photos (nokia n95) pics in attachment

please help because i love ubuntu and using that program would be awsome ;)

Best Regards Commander

Having exactly the same problem here (laptop, 1280x800). Comm4nder, did you solve that problem?

**UPDATE:** 
I've run winecfg (Wine Configuration dialog) and unchecked 
1. "allow the window manager to decorate ..."
2. "allow the window manager to control ..."
3. "emulate a virtual desktop" (this was previously checked by me trying to solve the problem described above)
4. hit "ok"

after that the problem seems to be gone, but be ready to pay for this %)
1. wine apps are no longer controlled by wm, so they no longer show in taskbar and window switcher
2. wine apps are always on top

...so I guess that solution is good only when you need to work with ableton only 
which is ok for me as long as it seems to be the only app I miss so much in linux %)))

---

### Post by jon.reeve on 2009-02-07
I have the same display problem (~1200x600 here and I only get half of Ableton!) and I also can't figure out how to get Ableton to recognize external MIDI input. Has anyone got this to work?

---

### Post by laimonas on 2009-03-20
Hi everyone,

maybe any one of you was heard anything about how to solve this problem:

[http://img14.imageshack.us/img14/736/screenshotahm.png]("http://img14.imageshack.us/img14/736/screenshotahm.png")

This is what i see, when i want turn on my ableton settings. I'm using Wine 1.0.1 and Ableton 7.0.3. As all you can see, in this case i can't configure any of options with the screen like this.

Please HELP ](*,)

---

### Post by laimonas on 2009-03-21
I've found the answer myself. After 4 hours of searching yesterday, today I've got success after about 10 minutes of searching :).
The problem was the older version of wine (I've installed wine through command line and I don't know why, but in server cache was older version - 1.0.1 wine), so I remove the old version and manually downloaded wine from them website (now there are version 1.1.17 for ubuntu):

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

And after newer version installation the problem was gone. Also i found in other forums, that the similar problem with rendering was till the 1.1.13 version. 

So hope this will be helpful for someone and will save them time. Cheers!

---

### Post by laimonas on 2009-03-21
> **jon.reeve said:**
> I have the same display problem (~1200x600 here and I only get half of Ableton!) and I also can't figure out how to get Ableton to recognise external MIDI input. Has anyone got this to work?

Hi jon.reeve if I understand correctly you problem with Midi controller, that you can't control Ableton with that controller. The solution, i think are simple:

go to Ableton Options -> Preferences
Choose MIDI Sync and there you have to see that you external controller are recognised. If it's recognised then all you'll have to do is to click on Remote column and make it ON

[[IMG]http://img22.imageshack.us/img22/5687/remote2.th.png[/IMG]](http://img22.imageshack.us/my.php?image=remote2.png)

---

