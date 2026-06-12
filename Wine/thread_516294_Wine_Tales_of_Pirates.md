---
title: "Wine Tales of Pirates"
date: 2007-08-03
forum: Wine
---

### Post by Nythain on 2007-08-03
so has anyone gotten tales of pirates to actually run with a recent version of wine and feisty... i can get it to install, and get it to load the updater window... but when i click on enter game, it closes out.

i've checked the appdb and people have similar problems though thiers were fixed with running as root wich didnt help for me... i havent tried the dll due to the fact that i dont have a windows install and im not sure if its one of those dlls i can just download and slap on there... also it aparently didnt help other poeple much anyways...

im sure its gotta be playable because i've seen screenshots of it being done, and others report on appdb that it works, so anyone with any luck that could share how they got it going would be great

---

### Post by cogadh on 2007-08-03
Did you try using an older version of Wine? It appears the game worked fine before version 0.9.37.

---

### Post by Nythain on 2007-08-03
and thats what i was totally afraid of... gonna be one hell of a hassle to try and find an old version and compile manually... maybe ill just wait and see if they fix teh problem in later releases :)

---

### Post by cogadh on 2007-08-03
You can get a precompiled deb package from the Wine repositories:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Nythain on 2007-08-03
you are my hero... give it a try over teh weekend and see how it goes... thanks for the help and the link... didnt realize winehq had an archive

---

### Post by Insomnia777 on 2007-09-07
Did you it work? I'm using wine too and I'm even trying it on Cedega but on Cedega it crashes, and on wine I can't see the cursor >.< ah yes I have a Nvidia card, and it has 3d acceleration on (yet on Cedega it says it isn't)

---

### Post by cogadh on 2007-09-07
Not that I doubt you, but if Cedega says you don't have 3D acceleration, then I think we need to start with your video card/drivers as the source of your problem. However, just to possibly confirm that, what does it say in the terminal when you try to run Tales of Pirates?

---

### Post by Insomnia777 on 2007-09-07
When I type "cedega tales of pirates" it says:

```
/usr/lib/transgaming_cedega/gddb.py:19: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser

```

Then it starts Cedega and the window crashes with the msg in the terminal saying:
```
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2377, in <module>
    gtk.main()
KeyboardInterrupt
```

And thanks Cogadh for helping me out, I installed ubuntu all alone and all the other basic stuff alone "literally speaking"

---

### Post by Hellaxe on 2007-11-19
For me it started when **i turned off the sound** on the winecfg.
No sound -> it started.
The main problem is that I can't see the characters. I see everything, even the weapons but not the character itself.
It's a peaty because my daughter can't play on ubuntu.
By the way i'm still using Feisty (hope to upgrade this week) and wine is 0.9.47.
[http://img84.imageshack.us/img84/7054/talesmw6.jpg](http://img84.imageshack.us/img84/7054/talesmw6.jpg)

---

### Post by Hellaxe on 2007-11-19
Have managed to fix my problem by selecting the Vertex shader suport by Hardware. Before it was [COLOR="Red"]None[/COLOR].
See the pic:

[[IMG]http://img206.imageshack.us/img206/4439/wincfg1je3.jpg[/IMG]](http://imageshack.us)


But I have another issue. The wallpaper (if i called so) behind the character selector turned blue. I cannot see the picture.
[B][COLOR="DarkRed"]
BIG EDIT:[/COLOR][/B] Sound works. Changed sound to ESD and it's great.:lolflag:

---

### Post by annalove on 2008-05-16
hey,do you know the 8thgame?
that is a new game company,but their services are excellent.
They deliver the gold in time,and their plvling is very safe.I just want to share my surprises with you, it is very great!
if you have time,you can have a try on their website.I believe you can get the surprise.
[www.8thgame.com](www.8thgame.com)

---

### Post by xyrer on 2008-08-29
I installed wine 1.0, the game seems to run fine if i deactivate sound, but it crashes the whole system, I mean, windows-style crash, only thing to do is hard reset.

---

### Post by Crafty Kisses on 2008-08-29
> **xyrer said:**
> I installed wine 1.0, the game seems to run fine if i deactivate sound, but it crashes the whole system, I mean, windows-style crash, only thing to do is hard reset.

That's really weird, did you check your error logs?

---

### Post by xyrer on 2008-09-02
mm, forgive my n00bness, but where are those logs located?

---

### Post by fefofefo on 2010-07-12
When i open the game i get this error:

[img]http://www.shrani.si/f/36/s0/3r6rIqUL/error2.png[/img]

My **winecfg** looks like this:

[img]http://www.shrani.si/f/1g/g1/7Q5xoaW/1.png[/img]

[img]http://www.shrani.si/f/2m/FZ/3Y8YoboV/2.png[/img]

[img]http://www.shrani.si/f/2t/10V/1luuMXfw/4.png[/img]

Im usin Wine 1.1.42 and the test results say it should work:

[img]http://www.shrani.si/f/H/pz/1fY9hoGI/5.png[/img]

What to do ? >_<

---

### Post by fefofefo on 2010-07-12
If i run it in the terminal i get this error:

[img]http://www.shrani.si/f/3/cE/49JJUI23/6.png[/img]

---

### Post by cogadh on 2010-07-12
First of all, you really shouldn't resurrect 2 year old threads like this. Wine changes a lot and very quickly so even though you are having a problem with the same game as the subject of this thread, your problem is completely unrelated to the items in this thread. 

Second, you really should search the forums before posting, the problem you are having is a very common one (common to every app run in Wine on the current Ubuntu, in fact). Its a simple permissions issue. You need to mark the game's .exe as an executable.

Third, [you should never, **NEVER** run wine using sudo permissions or a root account]("http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014"). Not only does doing that screw up the current permissions on your .wine directory, it potentially allows harmful Windows malware full access to evey thing on your Linux system, which can do just as much, if not more damage than it can on Windows. Since you have already done this, the best thing to do is delete your .wine directory and start all over again without using root permissions.

Lastly, I have to compliment you on providing some of the best troubleshooting info I've ever seen on these forums. If every forumite posted with the kind of detail you provided, problems would be so much easier to solve.

---

### Post by fefofefo on 2010-07-12
Solved the problem some minutes ago, my 3D linux games didn't work, and when i repaired those and restarted my computer Tales of Pirates started working also =)

Anyway thank you for your responding on my post, and I'm sorry that I posted it in a old thread.

Peace Fefo :D

---

### Post by yahyaco on 2011-02-08
my system crash after i open tales of pirates in few minutes it crash and i must switch off the computer, can you help me guys:confused:
i am on ubuntu 10.04 and wine 1.2.

---

### Post by bandecopz on 2011-02-26
:P hi buntu folks, i,m using wine 1.2.2 and ubuntu 10.04 and it is 95% working. 
i found some the letters in the game itself not too clear and i cannot go directly to the forum. i have to open the firefox to be able to get into the forum but regards the game i would say it is fine alright.
gud luck to all buntu folks..
mabuhay!!!!!!!!!!!!!!
si!!!!!!!!!!!!
PINOY!!!!!!!!!!!!!!!!!!
Mautas na pamilya bansot...

---

