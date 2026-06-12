---
title: "New to Linux - am i better off starting with the 32 bit version?"
date: 2005-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Doctoxic on 2005-08-05
I have a Athlon 60 3000+ (venice) on order, and i have never used Linux before but want to start with my new build.

I have found Linux to be very different to Windows and know its going to be a very steep learning curve for me.  Looking at the A64 forum things seem to get even more complicated.

Do you  reckon i would be better off just installing the 32bit Ubuntu, or are the setup/usage differences really not that great?

many thanks

Doc

---

### Post by Sam on 2005-08-05
I use Hoary AMD64. Certain things are different than the 32bit version (eg: no w32codec package, but there are alternatives). For some things, this is really a mess (eg: Firefox with Flash, etc...) but still possible.

I cannot tell you if there are more performances than the 32bit (some people say that's insignificant), but my computer really rocks with an Athlon 64 3400+. And I can tell myself than I'm using the next generation of cpu architecure (despite every problem encountered) !

If you never used Linux before but if you have good computer backgrounds, you can try the 64bit version for a while...

---

### Post by Doctoxic on 2005-08-05
is it possible to update from the 32 to 64 bit versions?

i am thinking i had better start on 32 bit as it seems easier

thanks

---

### Post by Lord Illidan on 2005-08-05
Aye, from all that I have heard in the forums, it seems that you should better take it easy and go with 32 bit at first, at least until you get used to Linux, then you can backup your data and try installing 64 bit.

---

### Post by Darkscot on 2005-08-05
I am using 32 bit Ubuntu on an Athlone 64 3000+ and it works great.  I did try the 64 bit version at first and did get problems (can't remember what exactly so they couldnt have been too bad!).  

I would stick with the 32 bit for now and look at 64 bit in a few months.

---

### Post by Lord Illidan on 2005-08-05
Your processor is fast enough that the difference will not be too big. If most of your linux time is spent writing documents or browsing the web, you will see almost no difference at all.

---

### Post by Doctoxic on 2005-08-05
[QUOTE=Lord Illidan]Your processor is fast enough that the difference will not be too big. If most of your linux time is spent writing documents or browsing the web, you will see almost no difference at all.[/QUOTE]
 thanks all

gonna go with 32bit first as suggested

---

### Post by DancingSun on 2005-08-05
Ubuntu is my first taste of Linux, and I had it the 64-bit way :D.

Overall, not a lot of problems besides getting annoyed with the lack of applications available to AMD64, but the Official Ubuntu Backports has just started to port over apps for AMD64, so I think the experience is going to be a lot better from now on.

---

### Post by Jet2k5 on 2005-08-05
If this is your first Linux system then I would highly recommend Ubuntu 32-bit.  Althought 64-bit is great and all, there has been some problems with it.  I hope ( and we are as in the other users ) that a lot of these programs go away with breezy.  So if you are beginner just use 32-bit to make sure that everything is working fine, and you learn the inside outs of Linux.  Then make the move to the 64-bit version.

-Luis

---

### Post by gordyt on 2005-08-05
Doctoxic I installed the 64-bit version and was a little frustrated at first.  Then I read the excellent post about installing the 32-bit chroot facility from [this thread](http://ubuntuforums.org/showthread.php?t=24575).

That really cleared up some things.  Now anytime I want to install something that hasn't been ported, I just do it from the chroot environment and it works great. 

--gordy

---

### Post by Jet2k5 on 2005-08-05
[QUOTE=gordyt]Doctoxic I installed the 64-bit version and was a little frustrated at first.  Then I read the excellent post about installing the 32-bit chroot facility from [this thread](http://ubuntuforums.org/showthread.php?t=24575).

That really cleared up some things.  Now anytime I want to install something that hasn't been ported, I just do it from the chroot environment and it works great. 

--gordy[/QUOTE]

This is a great howto.  I didn't even think that something this good could excist.  However why would one need to install things like xorg and gnome in a 32-bit environment?  I'm sort of curious of how a 32-bit chroot environment works.  I know that you install packages using 32-bit synaptic that go into /chroot/ and you run them from /chroot/.  But why bother installing xorg from /chroot/ ?

I think In my opinion is to just make packages 32-bit and 64-bit.  But then again I'm sure that would run into lib problems and get confusing.  eh I don't know I have about a week to get my computer, and about a week to decide if I want to go ubuntu 32 , ubuntu 64 , or another distro.  Or just plaing windows :P

---

### Post by immortal on 2005-08-07
i think you should use 32 mode if you can i have ubuntu amd64 bit mumbo jumbo and dont understand anything i can use most program that are installed also i can get on the net use email and gain messanger so im not totatlly lost but i can not install anything rtcwet a game will not install in 64bitlinux maybe there is a way but does it work so as a new user to ubuntu try the 32 bit version first there isnt much support or help in the 64bit anyways i been triing to install  cod (call of duty) i have the loki installer i have the orginal cds and yet it wont install then i find out wine doesnt run in 64 bit yet so its useless to install cod you get my point and this is only my second day back to linux gave up on linux bout 6 months ago cause i couldnt do anything this time i get a lil farther but still no luck i wish i could change it to 32 bit but i dont even know how to burn a cd in linux 64
e

PLEASE READ THIS BEFORE YOU MAKE A CHOICE

---

### Post by Jet2k5 on 2005-08-07
[QUOTE=immortal]i think you should use 32 mode if you can i have ubuntu amd64 bit mumbo jumbo and dont understand anything i can use most program that are installed also i can get on the net use email and gain messanger so im not totatlly lost but i can not install anything rtcwet a game will not install in 64bitlinux maybe there is a way but does it work so as a new user to ubuntu try the 32 bit version first there isnt much support or help in the 64bit anyways i been triing to install  cod (call of duty) i have the loki installer i have the orginal cds and yet it wont install then i find out wine doesnt run in 64 bit yet so its useless to install cod you get my point and this is only my second day back to linux gave up on linux bout 6 months ago cause i couldnt do anything this time i get a lil farther but still no luck i wish i could change it to 32 bit but i dont even know how to burn a cd in linux 64
e

PLEASE READ THIS BEFORE YOU MAKE A CHOICE[/QUOTE]


I did not understand one bit of that sentence unless for the last one.  I take it english isn't your first language? Or you did bad .. very bad in grammar school :P

As far as Call of Duty working wit Cedega, I will keep you guys posted on that.  I'm buying that game and I'll tell you guys how it goes.

---

### Post by Sam on 2005-08-07
[QUOTE=immortal]i think you should use 32 mode if you can i have ubuntu amd64 bit mumbo jumbo and dont understand anything i can use most program that are installed also i can get on the net use email and gain messanger so im not totatlly lost but i can not install anything rtcwet a game will not install in 64bitlinux maybe there is a way but does it work so as a new user to ubuntu try the 32 bit version first there isnt much support or help in the 64bit anyways i been triing to install  cod (call of duty) i have the loki installer i have the orginal cds and yet it wont install then i find out wine doesnt run in 64 bit yet so its useless to install cod you get my point and this is only my second day back to linux gave up on linux bout 6 months ago cause i couldnt do anything this time i get a lil farther but still no luck i wish i could change it to 32 bit but i dont even know how to burn a cd in linux 64
e

PLEASE READ THIS BEFORE YOU MAKE A CHOICE[/QUOTE]
Ouch !!! :shock: :shock: :shock:

---

### Post by immortal on 2005-08-08
sorry for the bad post its like 3 am,Im tired of trying to get ubuntu to play games.On another note with 64bit ubuntu you cannot install wine. Does this also mean cedega? I have loki installers for cod and farcry they both work nice in windows but I cannot get them to work in ubuntu amd64 is giving me lots of problems.You can create chroot (lets you install 32 bit apps) but I only been on linux for 48 hrs so i dont know much.

---

### Post by disciple3d on 2005-08-11
It's perfectly possible to get cedega / point2play working on AMD64 Ubuntu as I have.  

It's pretty much the same as 32bit in fact.  You will first need your 64 bit Nvidia/AMD driver working properly with acceleration, but all you need to do then is download the .deb installer from [www.transgaming.com](www.transgaming.com), and run (as root) from the console:

dkpg -i point2play_xxx.deb

You shouldn't have any problems, at least with the version I tried (2.0.1)

dpkg gives me the following required dependancies:

Depends: libc6 (>= 2.2.4-4), xlibmesa3 | libgl1, xlibs (>> 4.1.0), wget

If you do have dependancy problems, then see this link on adding more repositaries.  I use the backports repositary, along with selecting the universe and multiverse options in the synaptic package manager:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

However, getting games to work is another issue.  You'll have to check the games database on specific support.

---

### Post by Flac on 2005-08-11
Hey there, If im not to late in replying with this...


 Ubuntu 64 was my first linux installation. I'd never even touched linux before i used ubuntu64. I now also have 32 bit version installed on my new lappy.

 In all honesty, at this stage in the game, there isnt much difference between 64-bit and 32-bit. The biggest letdown 64-bit has is no flash player. But chroot is actauly cake to install if you find a good guide, i managed to do it(it sounds complicated, but its really simple, just takes a little while to do)

Its my recomendation, that you might as well go for the 64-bit and enjoy your full processing power. If you are really leary about it, ubuntu has a great partition maker in the installation, you could probably very easily build yourself a dual boot 32-bit/64-bit.(though what do i know, im still a linux newbie)

But honestly, from one linux newbie to another, 64 bit isnt as bad as it sounds reading the forums. Support is getting better, and everyone here is always more then willing to share how they got there system to work. I know i've gotten quite a bit of help from people, when in doubt, consult the forums. You'll do fine :)

Of course, Keep in mind. I do use my windows boot more then my linux boot on my desktop more(just for sake that all i use my computer for is gaming) So i may not experience a lot of the problems that others have had. But i do try to read the forums a bit, and most of the problems are just reoccuring problems, that are slowly getting fixed.(actauly pretty quickly, support has gone up immensly)

---Flac

---

