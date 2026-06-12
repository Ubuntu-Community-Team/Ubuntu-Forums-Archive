---
title: "Xubuntu 64 bit -- random quasi-crashes"
date: 2008-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by mmbates on 2008-03-02
G'day,
I seem to be having a bit of a problem with random "quasi-crashes".  

Perhaps once every day, or two days, my 64-bit Xubuntu Gutsy will decide to freeze, seemingly randomly.  Tonight was a classic example:
I was using totem to play music.  Then all of a sudden, the music stops, so I do the obvious thing, and click on totem to see whats going on...then all of a sudden, the computer beeps and I'm back to the login screen.  So, I login again, and everything seemingly works ok, except totem doesn't work.  Then, after 10 minutes or so, the same thing happens with a different program.  And so on and so forth, until the system becomes really, really unstable.

Basically, the only way that I have found that will fix this up is, to restart with a rescue disk and e2fsck my main sda5 partition.  Then it is fixed (for another day or two at least) -- totem is now acting perfectly normal.  It seems to work best if I do it straight after the initial crash. When running e2fsck, it tells me that there are problems fixed, and there are more problems that need fixing the higher the number of times the computer crashes (between e2fsck's that is), i.e. the % of uncontiguousness increases the more times I let it crash -- which makes sense.  So, these crashes are obviously doing damage to my file system, and I gather that it is really unusual to have to e2fsck the file system that often, most of the posts I have read is of people complaining that their system gets fsck'd automatically after 38 mounts (saying that it's too frequent) ... I have just adjusted it so that mine gets fsck'd every three shutdowns!

I am only running 64 bit Xubuntu, no other OS.  I'm also using Phenom 9600 with 500GB Western Digital HDD, 4GB ram and a Gigabyte GA-MA790FX-DQ6 motherboard.  Can't remember what the graphics card is...but I think it's also some Gigabyte thingo -- Nvidia chipset.  I also have a 750GB Seagate external HDD hooked up to the main box via an e-sata cable.

I am planning on doing some reasonably serious number crunching with the computer (which is pretty much brand new), but I can't be afford to have to have it as unstable as it is.

I guess, what my question is: has anyone else had this problem?  Is it that 64 bit gutsy is unstable and is possibly causing the problem? Or is it that the computer has a stupid, hopeless operator?  If it is possibly a 64 bit OS problem how stable is 64 bit Hardy looking at the moment...?  Could it even be a virus...?  Gremlins...? Marsians or other extra-terrestrial life?  As you can tell, I'm stumped.

cheers,
Michael

---

### Post by gsmanners on 2008-03-02
My guess about your problem is that it may be kernel/driver-related.

Hardy is pretty stable. You will get broken packages every now and then, but it's pretty usable here.

---

### Post by felker2 on 2008-03-02
My first step would be to check the memory: run the 6th option from the live-CD boot menu. 

BTW: memtest is also in the boot option list of your installed Ubuntu.

---

### Post by mmbates on 2008-03-02
> My guess about your problem is that it may be kernel/driver-related.

Hardy is pretty stable. You will get broken packages every now and then, but it's pretty usable here.

G'day gsmanners -- Thanks for that.  If that's the case, I'm looking forward to Hardy's official release :)

> My first step would be to check the memory: run the 6th option from the live-CD boot menu.

BTW: memtest is also in the boot option list of your installed Ubuntu.
G'day felker2 -- ok, I'll give that a try.  I've only just started the computer up this morning, so will do the memtest overnight.  What's your thinking on this one?

I'll post the results tomorrow morning.

cheers,
Michael

---

### Post by Jouke74 on 2008-03-03
Random crashes are most often caused by memory problems (90%), or wrong memory settings in the BIOS (10%). A memtest will indicate if you have problems with your memory banks and it's current settings. (Please do not mess with the BIOS settings if you are unsure what you're doing).  

If you are going to use a phenom for number crunching and stable system I urge you to read this carefully: [http://www.heise.de/english/newsticker/news/100231](http://www.heise.de/english/newsticker/news/100231) (you should have done this earlier). And then mainly the part about the problem, not the solution. This could also be the cause of your instability. Solutions range from driver updates, kernel recompiles, BIOS updates etc. So read the websites of your computer parts manufacturers about dealing with this problem.

Finally, if you have an old power supply unit also check if it is able to produce enough power. 
 
Good luck.

---

### Post by mmbates on 2008-03-03
G'day Jouke74,
> **Jouke74 said:**
> If you are going to use a phenom for number crunching and stable system I urge you to read this carefully: [http://www.heise.de/english/newsticker/news/100231](http://www.heise.de/english/newsticker/news/100231) (you should have done this earlier). And then mainly the part about the problem, not the solution. This could also be the cause of your instability. Solutions range from driver updates, kernel recompiles, BIOS updates etc. So read the websites of your computer parts manufacturers about dealing with this problem.

Ok thanks for this.  I have had a look around the net a bit and found a seemingly interesting article here: [http://www.lostcircuits.com/cpu/amd_phenom/](http://www.lostcircuits.com/cpu/amd_phenom/)  From what this says, basically, with the load that I have been putting on the machine (which so far, has been mundane tasks like playing music, sending emails, using LaTeX and occassionally compiling something) -- Erratum 298 shouldn't really affect those things.  It would kind of indicate that it may come into play when I become a bit more demanding though, but, if you believe that article, it still shouldn't be too too bad.

I also did a search of the AMD & Gigabyte websites and couldn't find anything on "Erratum 298" -- so it would seem that Erratum 298 isn't totally earth shattering.  Having said that, I wish I had have known about it before I bought the processor :)

Since there seems to be very little knowledge out there at this stage about the actual effect of this bug, I think I might just adopt a wait and see approach.

> **Jouke74 said:**
> 
Finally, if you have an old power supply unit also check if it is able to produce enough power. 
 
The power supply is a new one, and should be more than sufficient to run the machine (like capable of producing about 200W over and above what the machine should roughly need).

> **Jouke74 said:**
> 
Good luck.
 
Thanks ... looks like I'll need it.  I am about to put the machine to bed for the night, so will start up the memtest and post results tomorrow morning.

cheers,
Michael

---

### Post by Jouke74 on 2008-03-03
The issue is that I think you might also be right with your title. Hence, my interest in the topic.

I have done lots of number crunching with Xubuntu Gutsy already and I am afraid it is indeed not the most stable version of Xubuntu for this type of work. Xubuntu Feisty Fawn was better. I have had a couple of times that the Gutsy kernel "resetted" itself after running Bash shell scripts calculating simulations for a long time (3 days and nights in a row). I never had that under Feisty running similar sims. However, it did NOT crash the computer to a hang completely, I could still use it. And since I can run most programs without any issues I assume that we have different problems.

I am currently not running any serious stuff, so I'll await Xubuntu Hardy and see how it goes there.

---

### Post by zubrug on 2008-03-04
I have a phenom 9500 on a ecs a770m-a, I had these random lock-ups and freezes running any 64bit ubuntu including other ubuntu based distro's as well as OZ OS. 
Have not upgraded my bios and am running sidux with no problems under all kinds of loads.
I have a hard time believing it is a hardware issue as I can log into my hardy 64bit hardy partition and bang, lock with-in an hour or two simply running ktorrent, I have tried to create this event in sidux running vbox with xp, iceweasel/flash, ktorrent, beryl, superkaramba, sidux-irc, while playing Blue Planet 1080 on mplayer and all four cores run between 2-30%.

---

### Post by mmbates on 2008-03-04
Hi All,
memtest was still running when I left home this morning (it has been running now for about 35 hours -- so far, 41 tests passed, no errors found).

> **zubrug said:**
> I have a phenom 9500 on a ecs a770m-a, I had these random lock-ups and freezes running any 64bit ubuntu including other ubuntu based distro's as well as OZ OS. 
Have not upgraded my bios and am running sidux with no problems under all kinds of loads.
I have a hard time believing it is a hardware issue as I can log into my hardy 64bit hardy partition and bang, lock with-in an hour or two simply running ktorrent....

G'day zubrug,
so I gather what you're saying is that for some reason, 64 bit ubuntu doesn't like Phenom processors...?  Seems a bit weird ... also, I gather that I can't expect a great improvement with the release of Hardy right?

So -- I gather that what you're implying is that (should the memory end up being ok) in order to avoid these problems, I'm best advised to go to another distro (like Sidux), or go to a 32 bit OS?

As an aside, have you had any hardware compitibility problems -- e.g. I couldn't get my wireless card to get a stable connection to my router (but when I put it into my ancient 32 bit computer, it worked without any problems).

cheers,
Michael

---

### Post by mmbates on 2008-03-05
Well ... after 45.5 hours of Memtest, and still going strong, I decided enough was enough.  I needed my computer back.  So 55 passed tests and 0 errors later, I quit before it had finished -- but seems like the signs weren't bad...

Does anyone else have any insights about this problem that *ubuntu seems to have with phenom processors?  Do *ubuntu developers know that this problem exists?  Are these problems seen on the 32 bit version?

---

### Post by Jouke74 on 2008-03-05
Well that excludes memory and the hardware as a problem, as you already indicated. Memtest keeps running until you stop it. 55 passes and no errors means everything is fine.

---

### Post by gsmanners on 2008-03-05
I looked around, and that particular CPU has been fully supported since 2.6.18 (between Edgy and Feisty), so I'm thinking it's more likely a clash between the mobo and the kernel.

---

### Post by mmbates on 2008-03-05
> **gsmanners said:**
> I looked around, and that particular CPU has been fully supported since 2.6.18 (between Edgy and Feisty), so I'm thinking it's more likely a clash between the mobo and the kernel.

G'day gsmanners,
I would have suspected that too, but it seems as though zubrug and I are having similar problems on different motherboards.

> **zubrug said:**
> I have a phenom 9500 on a ecs a770m-a, I had these random lock-ups and freezes running any 64bit ubuntu...

[http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?DetailId=844&DetailName=Feature&MenuID=1&LanID=0](http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?DetailId=844&DetailName=Feature&MenuID=1&LanID=0)

On the other hand, I'm running a Gigabyte GA-MA790FX-DQ6: [http://www.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=2690](http://www.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=2690).  

They seem to be fairly different boards as they are not even running the same chipsets (zubrugs is 770, while mine is 790).  EDIT: Unless it just so happens that both boards clash with the kernel...

What I find really strange is that Sidux, which zubrug has no problems with, is also a Debian derivative (albeit an "unstable" branch) -- so Ubuntu and Sidux can't be too too dissimilar.......???  EDIT: so could it be that Sidux is running a later version of the kernel that supports zubrugs board....?

I guess the obvious thing to do would be to test this by installing Sidux side by side with Gutsy and see how easily I can get each of them to crash ...  I might save that project for the weekend, unless someone can come up with a better idea between now and then?

cheers,
Michael

---

### Post by mmbates on 2008-03-05
Need to vent a bit of frustration now.  I've just had a pretty bad crash -- e2fsck has been running now for over 1.5 hours on the gparted rescue cd.  In the past it has generally taken only 5-10 minutes to get things back on track :(  Unfortunately, gparted doesn't show the output of e2fsck (except in a log) so I can't see what is taking so long at this stage.  I'm back on my ancient 32 bit system now waiting for my new, super duper one to (hopefully) be resurrected.  

RE: the motherboard issue, I found this review on a very  similar motherboard running the 790 chipset.  It claims all is good with the world, as a number of features of these motherboards have been supported by Linux for quite some time... [http://www.phoronix.com/scan.php?page=article&item=956&num=6](http://www.phoronix.com/scan.php?page=article&item=956&num=6)

As my grandmother says ... life wasn't meant to be easy.

---

### Post by gsmanners on 2008-03-06
I think there's a bit of difference between yours (DQ6) and that one on Phoronix (DS5). Even so, you're probably right.

I guess that pretty much leaves the hard drive interface as the potential culprit. If the SATA or whatever is a problem, there could be a bug in hal, the file system drivers, or perhaps some part of the kernel. Not sure how to test that except by swapping out connecting to SATA for PATA or some other interface.

---

### Post by Jouke74 on 2008-03-06
For Sidux, Gutsy and Hardy you can make a comparsion in Kernel versions by comparing the manifest list of the distros from the websites.

Just maybe you can test the live CD of Hardy Heron, to see if this Kernel version is running  and if you have problems with that distro. Please note that this is an alpha version so different stability issues might come up. Also you can run the Live CD of Gutsy for a while to see if you have problems without any harddisk access (plant some stuff on a USB stick) and compare the two.

A hardware Sata problem is not excluded, but more unlikely if everything on Sidux works correct.

---

### Post by mmbates on 2008-03-06
I guess the main thrust of the article wasn't so much the specific motherboard, but the chipset -- seemingly they felt that the board was reasonably representative of the 790 chipset motherboards.

Anyhoo...I recovered, backed up all my data and have resized my gutsy partition.  I'm going to see if I can run sidux eros as a dual boot with my gutsy and see if I can replicate these problems in sidux.  I recently have aquired my number crunching software, so I should be able to push it pretty hard (actually, the big crash this morning happened while I was extracting the PGI Fortran and C compilers).

File system drivers, hal ... I think that's all a bit beyond my level of experience.  So I guess the best that I can do to help to try and get to the bottom of this, is to post the results that once I've got Sidux up and running.

cheers,
Michael

PS. Thanks for taking such a big interest in my problems gsmanners & Jouke74 -- it's nice to have someone to chew these things over with

---

### Post by chip_munk on 2008-03-06
You may want to cast a "quick" glance at this thread. [http://ubuntuforums.org/showthread.php?t=587905&page=1]("http://ubuntuforums.org/showthread.php?t=587905&page=1") which has plenty of 64 bit problems running 7.10 Gutsy.

It seems different solutions work for different people. Maybe you will find something of use to your situation in there. Warning though ... it's currently 60+ pages.

I point you here because reading it helped me overcome my problems of 64bit Gutsy.

Cheers
Chris

---

### Post by mmbates on 2008-03-11
G'day everyone,
Well,  I tried out Sidux Nuz 2008-01 at first, but that's still in the testing phase and was a bit unstable.  So, I went back a step and I have now been running 64 bit Sidux Eros 2007-04.05 [http://www.sidux.com/Article376.html](http://www.sidux.com/Article376.html) for nearly a week now without a single crash.  

I had some compile errors that I had to smooth out when porting my number crunching programme, but that's all sorted out now and everything is running smoothly.  Initially I ran it on one core for about 24 hours without any problems (the software wont run multi-core without some major changes to the code, which I couldn't be bothered doing -- and I'm looking at parameter space anyway, so there are certain advantages to running several flavours at the same time).  

I have just started two more (so am using three cores -- all running between 95--100% virtually all the time).  They should be done in about two weeks.  

So ... I think that it would be fair to say that it would seem to me that this is a problem with Ubuntu, and from what zubrug said earlier on, the problem is not solved under the versions of Hardy that have thus far been released.

I also got a private message from someone else with the same mother board and processor who is having trouble:
> 
Hi Mmbates,

I'm writing to you because you seem to have a working system, that according to:
[http://ubuntuforums.org/showthread.php?p=4447135](http://ubuntuforums.org/showthread.php?p=4447135)
is almost the same as the mine, which doesn't work. SO how did you get it working? I've got a MA790FX-DQ6 gigabyte motherboard, like you, and a phenom 9600 chip. Yet my system continually locks up. Become completely unresponsive. Leaves no logs that I can find and needs to be reset every time. I'm talking in terms of like 5 to 10 minutes of up time, not an occasional annoyance.

PLEASE HELP

Thanks

I wrote back and explained the problems that I'd also been having and pointed her/him to this thread.  I'm waiting to hear back to see how (s)he goes.

So, if Sidux manages to behave itself while this batch of programmes are running, I plan to (unforunately) remove Gutsy from my system (as I'm presently running a dual boot Eros/Gutsy system) and run the machine as a sole Eros system.

cheers,
Michael

---

### Post by czechman86 on 2008-03-11
i have been having these same problems, but with 32 bit ubuntu. i recently tried the 64 bit ubuntu and found it to be more stable, but didnt bother to test it long enough to see if i encounter these random crashes. i have run a mem test and around the third or fourth loop, i noticed fail signals coming back around different lines. what are the implications of this and what are the ways to fix it? i know that this is on the thread of someone elses problems, but perhaps we can fix two birds with one band aid.

---

### Post by Jouke74 on 2008-03-12
@czechman86
If you have errors in the memory test you need to probably buy new memory, unless you messed around with the memory timings in BIOS. In that case you can "loosen" them a bit or set the detection to automatic. If you haven't got a clue what this means bring your computer to a persons who does know. Memory failures often cause random crashes of the computer, and most likely explains your instability. You can check which memory bank is broken, by testing them one at a time.

@mmbates
I guess Sidux it is for now. Happy you got that working. Now maybe please report a bug file to the Hardy developers so they can have a look at it and get this hardware combination to run on Hardy as well.

---

### Post by mmbates on 2008-03-12
Thanks all.  I will put in a bug report to the Hardy Developers and hopefully it will be sorted out eventually :)

---

