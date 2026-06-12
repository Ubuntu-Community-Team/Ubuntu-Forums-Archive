---
title: "64 bit even necessary?"
date: 2007-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by PresidentJFJ on 2007-07-29
I recently tried to install 64x Kubuntu after playing with 32 bit Ubuntu for a bit. All I came across was problems. Not only with Kubuntu, which I can't seem to get running without installing Ubuntu first. 32 bit programs wouldn't run. I know I can workaround and make them work somehow, but it seems like too much work. The reason I tried to switch to 64 bit is that I have 4gb of RAM. It recognized my 4gb but that's about as far as I got. I couldn't even get kdm to stop, restart, log out without getting frozen at a black screen. Is this just Kubuntu? I have an Intel E6600 core 2 duo processor. Do I need AMD?

So my question is, is it really easy enough to use 64 bit Ubuntu at the moment? My 32-bit Ubuntu running kde recognizes 2.7gb of my RAM, and I have a 4.5gb swap partition. Is it worth it for me to try 64 bit again? Can I run everything that I can run in 32 bit Ubuntu? It could have been Kubuntu that was the problem. Integrated apps such as kate and adept would only work periodically. Should I spend tomorrow reinstalling in 64 bit?(I don't mind, as I have no plans:)) Will wine work? Which wine package do I download if I'm running 64 bit? 64 bit or 32 bit package?

As you can tell I'm VERY confused. Please give me some insight. Thanks so much, these forums are fantastic!

---

### Post by misfitpierce on 2007-07-29
Well honestly more and more programs are starting to be configured for 64 bit as well since feisty's time. More and more users are starting to use 64 bit which will in turn bring more support programs wise for 64 bit. I find pretty much everything I need 64 bit without a problem. 64 Bit does show increase in some things such as copying files etc and I would recommend staying with it.

---

### Post by PresidentJFJ on 2007-07-29
A big thing for me is the ability to use Wine. I have wine running fantastic in 32 bit . When I tried to install it for 64 bit I got the message, wrong architecture=x86_64. So can I run Wine in 64 bit? I rarely use windows now, and I don't want to have to reboot every time I want to go on steam.

Another thing. I don't get a boot up graphic when I boot in 64 bit and I can't stop kdm. Why is that? Is teh classic Ubuntu bar filler not inclluded in 64 bit? My monitor goes to sleep then wakes back up when the login screen comes up. I know it's not just Kubuntu because I'm on the 64 bit Ubuntu Feisty livecd right now and the same thing happens. My monitor goes to sleep as its booting then wakes back up when it's loaded. Thanks for all the help.

---

### Post by russo.mic on 2007-07-29
I've got wine running under 64 bit.  It works great.  You have to compile from source, but it's worth it.  it only took me about 30 min, but it might take you longer if your new to compiling stuff.

All I can add to the 64 vs. 32 big argument is that my Apple Macbook Pro runs quiter, cooler, and the battery lasts longer running 64 bit, which I just upgraded to last week.  But I think it's because the 64 bit kernel handles the 2 processors better thank the 32 bit.  

More and more software is getting supported for 64 bit.  Flash is now possible (okay, okay, it's a 32 bit web browser, but it still works) DVD playback is a breeze, I can't find a reason not to give it a shot.

---

### Post by Rhubarb on 2007-07-29
There's a wine repository that you can use for feisty 64bit:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I'm using these repositories here on my 64bit install, it's perfect :)

---

### Post by Kilz on 2007-07-29
Is this Thread even necessary?

The Original poster is making his Second post in the 64bit section. One to complain. Where are the posts asking for help or to be pointed in the right direction? where are the posts explaining his problem? Instead we get FUD. 
I can almost bet that the person starting topics like this have under 20 posts on the forum and less that 5 on the 64bit section. Each and every time its a newbie who cant post , and has no ability to see sticky posts, or use the search function on the Forums.
I personally think these posts, that only complain should be removed. Just like Goodbye Ubuntu posts. They serve little purpose but to fuel more FUD and scare off new users who may read them.

---

### Post by John.Michael.Kane on 2007-07-29
As said before in this section of the forum anything that can be done on 32bit ubuntu can be accomplished using 64bit ubuntu, and It's not about is it worth installing 64bit or 32bit as neither one is perfect, and they both come with their bag of issues.

What I usually suggest to users wanting to try 64bit ubuntu is to use it for thirty days without rebooting into 32bit ubuntu, and make use of the guides made for 64bit, This will allow you to see for your self if it's worth it or not,

In the end it's about the end user being willing to solve whatever issue they come across be it on 32bit ubuntu or 64bit ubuntu or any other distro for that matter.

You may want to read the the thread below, As it would help with installing, and understanding 64bit ubuntu.
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

Also for installing wine on 64bit it's completely doable. 
[Wine for Ubuntu, Debian, and Debian-based distributions]("http://www.winehq.org/site/download-deb")

---

### Post by PresidentJFJ on 2007-07-29
Thanks for all the replies. I'm sorry if you think this thread is useless, but as many threads as there already are about switching to 64 bit, I wanted help personally. I'm sorry, but I think that is what forums are all about.

Anyways, I will try 64 bit again. I seem to have a better idea of where to go with it now. The only question I have now is how do I get a boot up graphic instead of just a blakc screen? Thanks alot, everyone, and I'm sorry if you think this thread is useless.

---

### Post by John.Michael.Kane on 2007-07-29
As for you blank/black screen issues were going to need to know your video card model.

Barring knowing the above info. Try using boot parameter (make sure to hit F6 first).

```
nosplash
```

or
```
nosplash noapic nolapic
```

---

### Post by Kilz on 2007-07-29
> **PresidentJFJ said:**
> Thanks for all the replies. I'm sorry if you think this thread is useless, but as many threads as there already are about switching to 64 bit, I wanted help personally. I'm sorry, but I think that is what forums are all about.

Anyways, I will try 64 bit again. I seem to have a better idea of where to go with it now. The only question I have now is how do I get a boot up graphic instead of just a blakc screen? Thanks alot, everyone, and I'm sorry if you think this thread is useless.

Your post wasn't about a problem, the title wasn't "help with wine" Which is all over the forums and could have been found with the most simple search. [In fact the post right under yours and on the top page deals with wine. ]("http://ubuntuforums.org/showthread.php?t=432604")That or a look at the sticky posts.
Instead you made blanket statements shooting down the whole 64bit version. Help is what the forms are all about, what you did wasn't asking for help, but spread garbage. Realize there are good ways and bad ways of getting help and you chose the wrong way imho.

---

### Post by PresidentJFJ on 2007-07-29
All I really did was state the problems that I was having and then ask if the advantages of using 64 bit override the problems. I don't really see how I'm spreading garbage. I'm stating what happened to me, and asking if it's worth the work of trying to fix it. Everybody else that replied to my post either gave me insight or helped me with problems. I'm sorry if I didn't word my post PERFECTLY but the only garbage here is you bashing me for asking a simple question.

Oh and I'm using an 8800gts BTW. I'll try what you said and see if that helps.Thank you.

---

### Post by Kilz on 2007-07-29
> **PresidentJFJ said:**
> All I really did was state the problems that I was having and then ask if the advantages of using 64 bit override the problems. I don't really see how I'm spreading garbage. I'm stating what happened to me, and asking if it's worth the work of trying to fix it. Everybody else that replied to my post either gave me insight or helped me with problems. I'm sorry if I didn't word my post PERFECTLY but the only garbage here is you bashing me for asking a simple question.

Oh and I'm using an 8800gts BTW. I'll try what you said and see if that helps.Thank you.

Here is the title of your post " 64 bit even necessary?" Dose it say "help me fix wine? Dose it say "I have a problem please help? No it asks if 64bit is necessary and that you think it isnt. 
Everyone else can be nice as pie. Guess they arnt sick of people who cant even bother to look at the top page of the forum posting garbage.

---

### Post by PresidentJFJ on 2007-07-29
Notice in the title I have a question mark. Maybe because I put even before necessary you think it's a rhetorical question. My question was, "Is 64 bit even necessary?". Most people answered me and said either yes or maybe. You just said "you're dumb" basically. I'm sorry if you took the question the wrong way. If you're really sick of helping noobs, don't. That would be better than shooting them down.

Also, the ~nosplash didn't work. I ran it in terminal and it says, "~nosplash: command not found"
How am I supposed to run this command? the same thing happened for the second command. Thanks.

I also tried using wine. It doesn't work when I try to run steam_install.exe
jack@jack-desktop:~$ wine /home/jack/Desktop/STEAM_INSTALL.EXE
wine: creating configuration directory '/home/jack/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/jack/.wine'.
jack@jack-desktop:~$ wineserver: could not save registry branch to /home/jack/.wine-LiMMpp/system.reg : No such file or directory
wineserver: could not save registry branch to /home/jack/.wine-LiMMpp/user.reg : No such file or directory

What could I do to fix this? thanks.

---

### Post by John.Michael.Kane on 2007-07-29
> **PresidentJFJ said:**
> Also, the ~nosplash didn't work. I ran it in terminal and it says, "~nosplash: command not found"
How am I supposed to run this command? the same thing happened for the second command. Thanks.
That command is run before the install at the boot prompt,However. if you already have ubuntu 64bit installed you should try installing the drivers for your card using one these methods

Command line method:
[nvidia_udsf_feisty]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_1")

Or

Envy script method:
[Envy]("http://www.albertomilone.com/nvidia_scripts1.html")


> **PresidentJFJ said:**
> I also tried using wine. It doesn't work when I try to run steam_install.exe
jack@jack-desktop:~$ wine /home/jack/Desktop/STEAM_INSTALL.EXE
wine: creating configuration directory '/home/jack/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/jack/.wine'.
jack@jack-desktop:~$ wineserver: could not save registry branch to /home/jack/.wine-LiMMpp/system.reg : No such file or directory
wineserver: could not save registry branch to /home/jack/.wine-LiMMpp/user.reg : No such file or directory

What could I do to fix this? thanks.

I'm not sure about that error.

You may want to look at the bottom of this thread.
[HOWTO: Installing and Running Steam]("http://appdb.winehq.org/appview.php?iVersionId=1554")

Also since your trying to get gaming going under 64bit you may want to also have a talk with  the members in the [Gaming & Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93") section

---

### Post by PresidentJFJ on 2007-07-29
I already have the drivers installed for my card actually. I have compiz fusion running so the drivers are fine. I simply don't get that graphic where the black bar fills up with orange/orange fills up with black when I boot up/turn off. My monitor goes to sleep then comes back on in around 10 seconds. It's not a big deal by any stretch, I'm just wondering if theres a way to fix it.

---

### Post by praxis22 on 2007-07-29
As far as I know if you're running 64bit you can only use 64bit binaries under wine, that is 64bit XP/Vista binaries. So if you're looking to run steam, then you may have to find a 64bit version. 

The nosplash stuff needs to be added to your grub menu.lst entry. you'll find the file in /boot/grub/menu.lst

you'll need to edit that file, and find the line that is your boot string. I suggest you do a search for a FAQ to tell you how to do this without screwing up your boot environment. 

If you've got a 8800gts and 4Gb of RAM, it's likely that you a cutting edge rig, in which case you may not experience the best hardware support, this is because Linux is a community effort, and unless everyone, (especially the developers) have your hardware, they wont be able to experiment with it, etc. Most of the people who write software for Linux do not get paid, they do this for fun, using their own hardware.

---

### Post by izanbardprince on 2007-07-29
> **praxis22 said:**
> As far as I know if you're running 64bit you can only use 64bit binaries under wine, that is 64bit XP/Vista binaries. So if you're looking to run steam, then you may have to find a 64bit version. 

The nosplash stuff needs to be added to your grub menu.lst entry. you'll find the file in /boot/grub/menu.lst

you'll need to edit that file, and find the line that is your boot string. I suggest you do a search for a FAQ to tell you how to do this without screwing up your boot environment. 

If you've got a 8800gts and 4Gb of RAM, it's likely that you a cutting edge rig, in which case you may not experience the best hardware support, this is because Linux is a community effort, and unless everyone, (especially the developers) have your hardware, they wont be able to experiment with it, etc. Most of the people who write software for Linux do not get paid, they do this for fun, using their own hardware.

32-bit binaries run fine in Wine on AMD64

---

### Post by dabl on 2007-07-29
No, 64-bit isn't necessary.

Actually, 32-bit isn't necessary, either.

16-bit was kind of a waste of electricity too, come to think of it.

8-bit was overkill.

IBM Selectrics used those long paper tapes and a bunch of electricity, and made a bunch of noise in the process.  Too many mechanical parts to wear out.

Ball point pens run out of ink and skip and stuff -- you can't rely on 'em

These fancy graphite pencils are forever breaking and getting dull.

I remember the goose quill needed sharpening all the time, and that was if you didn't run out of ink.

I think a stick scraping in the dirt was pretty reliable, though.  There are lots of sticks and lots of dirt, and it's all free. Yeah, THAT'S the ticket!

:guitar:

---

### Post by praxis22 on 2007-07-30
:lolflag:

---

### Post by kuja on 2007-07-30
> **praxis22 said:**
> As far as I know if you're running 64bit you can only use 64bit binaries under wine, that is 64bit XP/Vista binaries. So if you're looking to run steam, then you may have to find a 64bit version. 

The nosplash stuff needs to be added to your grub menu.lst entry. you'll find the file in /boot/grub/menu.lst

you'll need to edit that file, and find the line that is your boot string. I suggest you do a search for a FAQ to tell you how to do this without screwing up your boot environment. 

If you've got a 8800gts and 4Gb of RAM, it's likely that you a cutting edge rig, in which case you may not experience the best hardware support, this is because Linux is a community effort, and unless everyone, (especially the developers) have your hardware, they wont be able to experiment with it, etc. Most of the people who write software for Linux do not get paid, they do this for fun, using their own hardware.
Apparently you don't know very far :lolflag:
As aforementioned, 32-binaries work fine.

In fact , I wonder if 64-bit binaries even work in WINE ...Probably not too much demand for it at the moment seeing as 64-bit windows blows ...

---

### Post by russo.mic on 2007-07-30
Calm down kilz, he was just asking a question.  He wanted some opinions on if 64 bit is worth the extra hassle, what can and can't be done, and if the majority of people think it's a good idea.  just because a thread mutates, that's no reason to discount it.  The search function doesn't care what the topic of the post is, and someone else might benefit from any information that comes out of this thread.  I agree, the annoying goodbye ubuntu posts are unnecessary, (maybe there should be a section for them, so that everyone else could just ignore them) but for Christ's sake, maybe NASA hasn't sent someone to the 3rd moon of Pluto yet, but they sure have had some good ideas trying. 

just my $0.02.

Russo

---

### Post by praxis22 on 2007-07-30
> **kuja said:**
> Apparently you don't know very far :lolflag:
As aforementioned, 32-binaries work fine.

In fact , I wonder if 64-bit binaries even work in WINE ...Probably not too much demand for it at the moment seeing as 64-bit windows blows ...

Provided you install the 32bit version of wine, and all the 32 bit support libs, then of course 32 bit binaries will work, however this is the 64bit forum. QED.

[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)

---

### Post by Kilz on 2007-07-30
> **russo.mic said:**
> Calm down kilz, he was just asking a question.  He wanted some opinions on if 64 bit is worth the extra hassle, what can and can't be done, and if the majority of people think it's a good idea.  just because a thread mutates, that's no reason to discount it.  The search function doesn't care what the topic of the post is, and someone else might benefit from any information that comes out of this thread.  I agree, the annoying goodbye ubuntu posts are unnecessary, (maybe there should be a section for them, so that everyone else could just ignore them) but for Christ's sake, maybe NASA hasn't sent someone to the 3rd moon of Pluto yet, but they sure have had some good ideas trying. 

just my $0.02.

Russo


The topic you suggest, if 64bit is worth it, has been gone over , and over, and over, and over. There is a sticky that links to at least a dozen threads on the subject. A simple search will bring up 3 times as many.
The first post was a complaint on "how nothing works for him on the 64bit version". Sadly , it was the first post in this section of the original poster.  That first post is on the same par with Gooodby ubuntu posts imho. Its just a "Goodbye 64bit" imho.
The one question he dose ask about the 64bit version, about Wine is also a covered topic. There are literately hundreds of wine posts in the 64bit section, and stickys with links. Come on, the search works, this is beating a dead horse. IMHO we need to stop spoon feeding people information that is so easy to find, it isnt funny.

---

### Post by praxis22 on 2007-07-30
RANT

Sadly this is what years of Microsoft dependence has done for us.  The average computer user has seemingly lost the faculty of critical thought, either that or they're so used to being spoon fed that they never developed "the joy of finding things out" to quote Fenyman.

Only today on a technical list I'm on for Solaris admins, did somebody ask what "multipathing" was and what commands they needed to use to set it up. throw two words into google and it's the first link that shows up, and this guy is presumably being paid to do his job.

Still, one way to separate the men from the boys is to put them in a machine room with a VT100 terminal and no internet connection and tell them to get on with it. Sink or swim.

Though back on topic, if you can't hack a 64bit install, download the 32bit variant and use that, can't hack that either? Go back to windows. 

[shakes head]

/RANT

---

### Post by russo.mic on 2007-07-31
Your right kilz,  

and HOW DARE the starter of this thread come to your house, and force you to sit behind your computer, log on to the forum, and read this dead horse.

---

### Post by tgm4883 on 2007-07-31
The thread is titled in a way to agitate users.  It does nothing to help the forum or the OP and should probably be changed.  I'll defend kilz here, as there is so much crap going around regarding 64 bit that we don't need anymore.  Straightening out all the lies is becoming a full time job.

As to the WINE talk.  There is (although I believe it is still in development) a WINE to run 64-bit windows programs called [WINE64.]("http://wiki.winehq.org/Wine64")  This is not the same as [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) which runs 32-bit windows programs on 64-bit linux.

Wine64 != WineOn64bit

---

### Post by s3a on 2007-07-31
Isn't it true that 4 GB of RAM acts as 2.6 GB's of RAM while running in a 64-bit OS because the code is larger but on the beneficial point of view, it increases CPU speed, but,  is the CPU speed benefit large enough to make up for RAM loss?

I have read this somewhere on the internet, so if someone could add something, it would be beneficial to many users (I think)....if not then, to me. :)

P.S.
I think this is why they say have more than 4 GB of RAM on a 64-bit machine.

---

### Post by tgm4883 on 2007-07-31
> **s3a said:**
> Isn't it true that 4 GB of RAM acts as 2.6 GB's of RAM while running in a 64-bit OS because the code is larger but on the beneficial point of view, it increases CPU speed, but,  is the CPU speed benefit large enough to make up for RAM loss?

I have read this somewhere on the internet, so if someone could add something, it would be beneficial to many users (I think)....if not then, to me. :)

P.S.
I think this is why they say have more than 4 GB of RAM on a 64-bit machine.

No.  In fact, though your whole post, i'm not sure if you hit even close to one thing that could be considered a fact.  Everyone that reads your post is dumber for doing so, and may god have mercy on your soul.

j/k

But really, the answer is no.  32-bit Operating Systems cannot see 4GB ram, not the other way around.  Also, programs that are written for 64-bit processors are faster than their 32-bit counterparts.  Not twice as fast, but they can see a 30% increase in speed.

---

### Post by praxis22 on 2007-07-31
You need 4Gb to get Vista to work at a decent speed:

[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9011523](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9011523)
[http://www.theinquirer.net/default.aspx?article=37756](http://www.theinquirer.net/default.aspx?article=37756)
[http://www.planetamd64.com/index.php?showtopic=30508](http://www.planetamd64.com/index.php?showtopic=30508)

But it may not actually see it all:
[http://support.microsoft.com/kb/929605](http://support.microsoft.com/kb/929605)

The reasons for this are complex, but don't really affect Linux, in fact the 32 bit  variant of BSD can allegedly see 4Gb due to the way it maps memory, even though the maximum addressable memory on a 32 bit OS is normally 2Gb. 

here endeth the lesson :)

---

### Post by s3a on 2007-08-05
> **tgm4883 said:**
> No.  In fact, though your whole post, i'm not sure if you hit even close to one thing that could be considered a fact.  Everyone that reads your post is dumber for doing so, and may god have mercy on your soul.

j/k

But really, the answer is no.  32-bit Operating Systems cannot see 4GB ram, not the other way around.  Also, programs that are written for 64-bit processors are faster than their 32-bit counterparts.  Not twice as fast, but they can see a 30% increase in speed.

I re-read what you said and when I said the "acts as 2.6 GB RAM" part I did not mean that it only see's that much in 64-bit but instead that it see's the whole 4 GB but only performs in terms of capacity of storage as 2.6 GB's of RAM since the 64-bit code is in fact larger than the 32-bit code. Unless I missunderstood him, this person whom I know knows a lot about computers has confirmed this for me.

---

### Post by tgm4883 on 2007-08-05
> **s3a said:**
> I re-read what you said and when I said the "acts as 2.6 GB RAM" part I did not mean that it only see's that much in 64-bit but instead that it see's the whole 4 GB but only performs in terms of capacity of storage as 2.6 GB's of RAM since the 64-bit code is in fact larger than the 32-bit code. Unless I missunderstood him, this person whom I know knows a lot about computers has confirmed this for me.

eh not exactly.  The above analogy would indicate that a 64-bit computer with 4 GB of ram would run like a 32-bit computer with 2.6GB ram (if im reading your correctly).  While the programs would be larger "due to swollen pointers and possibly other types and alignment padding", I don't believe that the gap would A:  translate to a gap that large. and B:  reduce the performance of the computer.

The key here, is that the computer (while running a proper 64-bit application) is able to perform much faster than a 32-bit counterpart.  Otherwise you would see no performance benefit from running 64-bit and would actually see a performance hit compared to a similar 32-bit system (which is not the case.)

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by RAOF on 2007-08-05
> **tgm4883 said:**
> ...
The key here, is that the computer (while running a proper 64-bit application) is able to perform much faster than a 32-bit counterpart.  Otherwise you would see no performance benefit from running 64-bit and would actually see a performance hit compared to a similar 32-bit system (which is not the case.)
...

Well, kinda.  Actually, for almost all architectures 64bit code **is** slower than 32bit code.  It's only because the 32 bit x86 (IA32) architecture has some glaring faults which are rectified in x86-64 that 64bit x86 code runs faster than 32bit x86 code.

This is why Debian is (slowly) working towards multiarch.  If the world contained only x86 processors, they probably wouldn't bother - there's no (significant) downside to x86-64 code.  Other architectures (PPC, etc) really want to use 32bit code where possible and have 64bit code only for programs which need a 64bit address space.

---

### Post by tgm4883 on 2007-08-05
> **RAOF said:**
> Well, kinda.  Actually, for almost all architectures 64bit code **is** slower than 32bit code.  It's only because the 32 bit x86 (IA32) architecture has some glaring faults which are rectified in x86-64 that 64bit x86 code runs faster than 32bit x86 code.

This is why Debian is (slowly) working towards multiarch.  If the world contained only x86 processors, they probably wouldn't bother - there's no (significant) downside to x86-64 code.  Other architectures (PPC, etc) really want to use 32bit code where possible and have 64bit code only for programs which need a 64bit address space.

So the speed increase is due to rectified faults rather than the increase of registers and such in 64-bit processors?  Interesting, I hadn't heard that before.

Now this multiarch that Debian is working toward, am I correct to assume that in doing so there would be no need for seperate 64-bit releases?  Can I also assume that when Debian changes to multiarch that Ubuntu will follow?

Any links?  I'd like to read up on both of these issues.

---

### Post by RAOF on 2007-08-05
> **tgm4883 said:**
> So the speed increase is due to rectified faults rather than the increase of registers and such in 64-bit processors?  Interesting, I hadn't heard that before.

Actually, for x86-64 it is (among other things) because there are more compiler-visible registers.  It's just that x86-64 is pretty much the only arch for which this is the case - other 64bit architectures just make the registers 32bits wider, and (essentially) don't change anything else.

> **tgm4883 said:**
> 
Now this multiarch that Debian is working toward, am I correct to assume that in doing so there would be no need for seperate 64-bit releases?  Can I also assume that when Debian changes to multiarch that Ubuntu will follow?
...

There will still be separate 64bit releases, as far as I'm aware; it's just that the ia32-libs packages (for example) would disappear, and we'd have a distro-wide 32/64 bit parallel-installability system.  Yes, after Debian does it, we'll get it by default.

[http://wiki.debian.org/multiarch](http://wiki.debian.org/multiarch)

---

### Post by MrHorus on 2007-08-06
> **s3a said:**
> Isn't it true that 4 GB of RAM acts as 2.6 GB's of RAM while running in a 64-bit OS because the code is larger but on the beneficial point of view, it increases CPU speed, but,  is the CPU speed benefit large enough to make up for RAM loss?

No.

A 32bit CPU can address a maximum of 4GB of RAM and is a limitation of all 32bit archetectures.

If you have 4 GB of RAM then you have 4GB - it matters not if you are running a 32bit of a 64bit machine.

I don't get what you mean about RAM being lost of the code being bigger - you aren't going to magically lost 2/5ths of your RAM by running a 64bit system - that's nonsense.

---

### Post by Kilz on 2007-08-06
> **tgm4883 said:**
> 
Now this multiarch that Debian is working toward, am I correct to assume that in doing so there would be no need for seperate 64-bit releases?  Can I also assume that when Debian changes to multiarch that Ubuntu will follow?

Any links?  I'd like to read up on both of these issues.

If you notice the dates on the page RAOF links to, they are all 2 years old. Multiarch has stalled in Debian. If I remember right, there is some political problem with it in Debian. Don't count on it ever making its way to Ubuntu. The good thing is, that the longer they take the need for this gets less and less. The packages needed for most people can be counted on one hand, and there are scripts/howto's for all of them. Also if you really need to run some other 32bit application, its possible to manually install it. Do a search for getlibs, the script will automatically get and install whatever libraries the application needs.

---

### Post by tgm4883 on 2007-08-06
> **Kilz said:**
> If you notice the dates on the page RAOF links to, they are all 2 years old. Multiarch has stalled in Debian. If I remember right, there is some political problem with it in Debian. Don't count on it ever making its way to Ubuntu. The good thing is, that the longer they take the need for this gets less and less. The packages needed for most people can be counted on one hand, and there are scripts/howto's for all of them. Also if you really need to run some other 32bit application, its possible to manually install it. Do a search for getlibs, the script will automatically get and install whatever libraries the application needs.

I did notice that it hasn't been talked about in 2 years.  I also remembered something you (I think it was you) said a while back about the devs and wondered if Debian's multiarch is was the reason for it.  I remembered you saying some time back something about the devs could put i386 debs in the 64-bit repo and eliminate the need for your workarounds, but they wouldn't do it.

I'm glad you replied to this as I had wondered what your thoughts on it were.  When I think of 64-bit, the first things that comes to mind is Kilz.

---

### Post by butcher99 on 2007-08-09
> **Kilz said:**
> Is this Thread even necessary?

The Original poster is making his Second post in the 64bit section. One to complain. Where are the posts asking for help or to be pointed in the right direction? where are the posts explaining his problem? Instead we get FUD. 
I can almost bet that the person starting topics like this have under 20 posts on the forum and less that 5 on the 64bit section. Each and every time its a newbie who cant post , and has no ability to see sticky posts, or use the search function on the Forums.
I personally think these posts, that only complain should be removed. Just like Goodbye Ubuntu posts. They serve little purpose but to fuel more FUD and scare off new users who may read them.

 Actually, his question is a very good question.   Is it really necessary?  I am a new user to UBUNTU and logged in to read this question then I get a fud reply along with some well reasoned posts
   I am not sure his question is a complaint.  He asked a legitimate question and then posted his reasoning.  

  You can take them as complaints or constructive criticism.

---

### Post by Kilz on 2007-08-09
> **butcher99 said:**
> Actually, his question is a very good question.   Is it really necessary?  I am a new user to UBUNTU and logged in to read this question then I get a fud reply along with some well reasoned posts
   I am not sure his question is a complaint.  He asked a legitimate question and then posted his reasoning.  

  You can take them as complaints or constructive criticism.

That you as a new user read the post proves my point. The question in itself is FUD. It asks a pointed question. A question that has been gone over and over and over. Yet it still pops its head up. If you want the answer, look in the sticky posts.

---

### Post by MikeStone on 2007-08-09
Didn't I read somewhere about being respectful to other people's feelings and leave moderating to the moderators?

Anyway, at the risk of getting bashed, I'm going to toss in my two cents, from the perspective of a relative newcomer to Ubuntu in specific and Linux in general. After a short stint with the 64 bit version, I'm now on the 32 bit to stay.  At least for the near future.  I'm a software engineer by trade, so I certainly have the knowledge and the skills to jump in there and tinker it to death.  What I lack is the time or the desire to do so.  My PC isn't a toy or a pastime.  It's a tool.  I don't want to spend time getting things to work, when I could be spending that time on more productive endeavors.  To me, the extra hassle presented by 64 bit just isn't worth it, no matter how trivial other's see that as.  Am I using my hardware to its fullest extent?  No.  But then I don't have the need to.  Any more than I feel the need to play my stereo at 200 decibels just so I can say I'm using my speakers to their full potential. 

Bottom line is this.  Everyone's needs and expectations are different.  There is no one set of rules that fit everyone.  There is no one valid answer to questions like "Is it worth it?".  The answer depends on your individual needs.  The real question is "Is it worth it to YOU?".  

32 bit works for me.  And that's all that really matters.

---

### Post by Kilz on 2007-08-09
> **MikeStone said:**
> Didn't I read somewhere about being respectful to other people's feelings and leave moderating to the moderators?

Anyway, at the risk of getting bashed, I'm going to toss in my two cents, from the perspective of a relative newcomer to Ubuntu in specific and Linux in general. After a short stint with the 64 bit version, I'm now on the 32 bit to stay.  At least for the near future.  I'm a software engineer by trade, so I certainly have the knowledge and the skills to jump in there and tinker it to death.  What I lack is the time or the desire to do so.  My PC isn't a toy or a pastime.  It's a tool.  I don't want to spend time getting things to work, when I could be spending that time on more productive endeavors.  To me, the extra hassle presented by 64 bit just isn't worth it, no matter how trivial other's see that as.  Am I using my hardware to its fullest extent?  No.  But then I don't have the need to.  Any more than I feel the need to play my stereo at 200 decibels just so I can say I'm using my speakers to their full potential. 

Bottom line is this.  Everyone's needs and expectations are different.  There is no one set of rules that fit everyone.  There is no one valid answer to questions like "Is it worth it?".  The answer depends on your individual needs.  The real question is "Is it worth it to YOU?".  

32 bit works for me.  And that's all that really matters.

The guidelines say, stick to the facts, discuss on topic. if someone is suggesting a lie is the truth I do not believe I have to candy coat the fact a lie is a lie.

In other words you have swallowed the FUD hook, line, and sinker. Exactly what "Extra Work" are you avoiding? Please give real examples of things you would have to do to get the 64bit version to work. Not just "I cant run 32bit packages" but the exact packages. Because if you cant, you have let Fear, Uncertainty, and Doubt influence you.

---

### Post by MikeStone on 2007-08-09
> **Kilz said:**
> The guidelines say, stick to the facts, discuss on topic. if someone is suggesting a lie is the truth I do not believe I have to candy coat the fact a lie is a lie.

In other words you have swallowed the FUD hook, line, and sinker. Exactly what "Extra Work" are you avoiding? Please give real examples of things you would have to do to get the 64bit version to work. Not just "I cant run 32bit packages" but the exact packages. Because if you cant, you have let Fear, Uncertainty, and Doubt influence you.

I didn't say "I can't run 32bit packages".  If you're going to quote someone, at least make sure they said what you quote.  I never said I CAN'T run anything.  All I said was that it takes extra effort to make some things work under 64 bit.  Are you trying to say it doesn't?  You have Howto's at the bottom of your own posts showing how to make things work in 64 bit.  These are extra steps that you don't have to do under 32 bit.  That's extra effort.  Is it a LOT of extra effort?  I never said that.  I merely said it was enough to make me stick with 32 bit for the time being.  Is it enough to justify my decision?  My call.  Not your's.   Do I "Fear" it?  Do I have "Uncertainty"?  Do I have "Doubt"?  Hardly.  I simply don't feel any motivation to do it.  As I said.  32 bit works for me.  And that's all that matters.

---

### Post by Kilz on 2007-08-09
> **MikeStone said:**
> I didn't say "I can't run 32bit packages".  If you're going to quote someone, at least make sure they said what you quote.  I never said I CAN'T run anything.  All I said was that it takes extra effort to make some things work under 64 bit.  Are you trying to say it doesn't?  You have Howto's at the bottom of your own posts showing how to make things work in 64 bit.  These are extra steps that you don't have to do under 32 bit.  That's extra effort.  Is it a LOT of extra effort?  I never said that.  I merely said it was enough to make me stick with 32 bit for the time being.  Is it enough to justify my decision?  My call.  Not your's.   Do I "Fear" it?  Do I have "Uncertainty"?  Do I have "Doubt"?  Hardly.  I simply don't feel any motivation to do it.  As I said.  32 bit works for me.  And that's all that matters.

The "I can't run 32bit packages" was an example of what not to say. Your use of the links in my signature shows you to have no knowledge of the subject. If you had, you would know that one is for older versions, and that the one for nspluginwrapper wouldn't even count as more time, that is unless you count 30 seconds.
Fact is, that 32bit and 64bit both have thier problems. Have you even looked at the entire rest of this forum? It contains nothing but 32bit users. All with problems. Please prove to me that 64bit is less of a problem. Prove to me that 32bit is a seamless install with no problems. I will point you [here]("http://ubuntuforums.org/forumdisplay.php?f=73"), and [here]("http://ubuntuforums.org/forumdisplay.php?f=132"), and [here]("http://ubuntuforums.org/forumdisplay.php?f=140"). 
Something "new users" dont seem to understand is that there is no easy cant fail install of linux. They keep blathering the same old FUD without even thinking about it. Thats the whole problem and my stance, DONT repeat anything that you yourself dont know to be true from experience. Because when you do, it shows your lack of real knowledge.
After all you , yourself, [are a self admitted newcomer to Linux]("http://ubuntuforums.org/showpost.php?p=3128323&postcount=4"). With a WHOPPING 6 WHOLE days of experience. How do you know enough to have an opinion on what is easy and what isnt?

---

### Post by MikeStone on 2007-08-09
> **Kilz said:**
> The "I can't run 32bit packages" was an example of what not to say. Your use of the links in my signature shows you to have no knowledge of the subject. If you had, you would know that one is for older versions, and that the one for nspluginwrapper wouldn't even count as more time, that is unless you count 30 seconds.
Fact is, that 32bit and 64bit both have thier problems. Have you even looked at the entire rest of this forum? It contains nothing but 32bit users. All with problems. Please prove to me that 64bit is less of a problem. Prove to me that 32bit is a seamless install with no problems. I will point you [here]("http://ubuntuforums.org/forumdisplay.php?f=73"), and [here]("http://ubuntuforums.org/forumdisplay.php?f=132"), and [here]("http://ubuntuforums.org/forumdisplay.php?f=140"). 
Something "new users" dont seem to understand is that there is no easy cant fail install of linux. They keep blathering the same old FUD without even thinking about it. Thats the whole problem and my stance, DONT repeat anything that you yourself dont know to be true from experience. Because when you do, it shows your lack of real knowledge.
After all you , yourself, [are a self admitted newcomer to Linux]("http://ubuntuforums.org/showpost.php?p=3128323&postcount=4"). With a WHOPPING 6 WHOLE days of experience. How do you know enough to have an opinion on what is easy and what isnt?


Wow.  You really are full of yourself.  And I thought it was just a summer thing.  While I'm new to Linux, I'm a software engineer with 36 years experience.  So I know a couple of things.   But that's immaterial as I don't have to PROVE anything.  Certainly not to the likes of you.   I stated an opinion.  Nothing more.  In my opinion, 32 bit does everything I need it to do.  Again, that's all that matters.  Your opinion on the matter counts for zip.

See ya.

---

### Post by John.Michael.Kane on 2007-08-09
IMHO just agree to disagree, As there seems to be no way to find common ground.

On top of that. theres no need to turn this thread into a flame war or worse.

---

