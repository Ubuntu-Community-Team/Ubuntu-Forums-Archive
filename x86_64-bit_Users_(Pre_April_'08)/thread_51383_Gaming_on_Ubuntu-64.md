---
title: "Gaming on Ubuntu-64"
date: 2005-07-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jet2k5 on 2005-07-23
I was curious of how one would play games on Ubuntu-64.  From my knowledge I understand that you can install Cedega on Hoary 64 with the *dpkg --force-architecture*.  So I know that installs Cedega on a 64-bit machine, but what about the games?  Can you install a game the same way?  Or does that game have to be in a 32-bit chroot mode ( which I'm starting not to like so much ).

So I was wondering how you would install a game under Cedega that is installed on a 64-bit system.  Also what are the steps to installing games that run on Linux like ET, or Quake .. or most favorite Americas Army.

Help me understand this dumb questions but I've been trying to answer it myself.  :-P

---

### Post by negatory on 2005-07-23
I've answered in [this post](http://ubuntuforums.org/showthread.php?p=267914#post267914).
Overall gaming is very good and very fast.If you've installed Cedega in your base 64bit system you can install the games as you would do in windows.
Hope that helps.
Pedro Carrico

---

### Post by Jet2k5 on 2005-07-23
[QUOTE=negatory]I've answered in [this post](http://ubuntuforums.org/showthread.php?p=267914#post267914).
Overall gaming is very good and very fast.If you've installed Cedega in your base 64bit system you can install the games as you would do in windows.
Hope that helps.
Pedro Carrico[/QUOTE]


What throws me off is that you talk about having a 32-bit enviroment.  Last time I checked Americas Army doesn't have .debs.  What I'm trying to say is, can I just download AA on my 64-bit machine, and then just do *sh americas-army-xxxblah.bin* and this will install the game for me?  Or with that will I run into problems?

To tell you the truth I'm not planning on playing most of my games on Linux, only the ones that I know there is client for.  All the others I'm going to play on windows.  I know it's dumb but this is probably one of the few things that Windows own over Linux on.  However AA is going to be playing under Linux and not windows ;)

---

### Post by joekr on 2005-07-24
I run Neverwinter Nights natively in Gentoo64... and I also did the same thing with Hoary64... so I'm guessing a good number of native games will work, if not all.

---

### Post by negatory on 2005-07-24
I just have a 32bit chroot for macromedia and w32codecs.In America's Army you just have to download the client,untar it,and play.There's no need for a 32bit chroot.
Pedro Carrico

---

### Post by Jet2k5 on 2005-07-24
[QUOTE=negatory]I just have a 32bit chroot for macromedia and w32codecs.In America's Army you just have to download the client,untar it,and play.There's no need for a 32bit chroot.
Pedro Carrico[/QUOTE]

Thank you that was the answer I was looking for.  Thanks to you to joekr.  So as far as Linux naitive games even though you are on a 64-bit system it doesn't require a 32-bit chroot mode for games?  If so sounds good, because most of the games that I'm going to be playing are free games that I can get my hands on, before I start buying them :)

---

### Post by negatory on 2005-07-24
Glad I could help...Now my doubts lay on running 32bit debs in my 64bit enviroment...
I hadn't got the time to try yet...
Pedro Carrico

---

### Post by DancingSun on 2005-07-24
I think this is how it works:

If a 32-bit program or a game requires external libraries that are 32-bit, but you have the 64-bit versions, this is where the chroot would come in.  But if a 32-bit program or game does not require any external libraries, then it will run just fine on AMD64 without doing anything extra.

America's Army seems to be self-sufficient, so it runs just fine.  In fact, I just came back from playing AA :D.

Enemy Territory, however, requires some external library that I don't even have on my Ubuntu AMD64, so that doesn't even install.

Edit:  I also play Neverwinter Nights on my 64-bit Ubuntu.  I just finished a module called Tales of Aterra - The Awakening, it's a must play module, really nicely written, much better than the BioWare modules! :grin:

---

### Post by Jet2k5 on 2005-07-24
[QUOTE=DancingSun]I think this is how it works:

If a 32-bit program or a game requires external libraries that are 32-bit, but you have the 64-bit versions, this is where the chroot would come in.  But if a 32-bit program or game does not require any external libraries, then it will run just fine on AMD64 without doing anything extra.

America's Army seems to be self-sufficient, so it runs just fine.  In fact, I just came back from playing AA :D.

Enemy Territory, however, requires some external library that I don't even have on my Ubuntu AMD64, so that doesn't even install.

Edit:  I also play Neverwinter Nights on my 64-bit Ubuntu.  I just finished a module called Tales of Aterra - The Awakening, it's a must play module, really nicely written, much better than the BioWare modules! :grin:[/QUOTE]


So ET doesn't run straight out of the box on Ubuntu 64-bit?  So if you need to run it in 32-bit chroot mode, does that mean that you have to install the nvidia drivers in the chroot system too?  Or just run the game from there would do the job?

---

### Post by DancingSun on 2005-07-24
[QUOTE=Jet2k5]So ET doesn't run straight out of the box on Ubuntu 64-bit?  So if you need to run it in 32-bit chroot mode, does that mean that you have to install the nvidia drivers in the chroot system too?  Or just run the game from there would do the job?[/QUOTE]

Well, you got me on the nVidia drivers question, since I don't do chroot at all.  I'd rather keep it simple.  I don't know how chroot works in detail (haven't done any reading on that yet), I just know that it provides an isolated 32-bit environment for 32-bit apps to run in.

As you already know, AMD64 is just an extension of the 32-bit x86 architecture, so the processor itself understand the x86 instructions whether in 32 or 64-bits.  The difference is the 64-bit binaries can access the extra registers on the processor (essentially "memory" available on the CPU), while the 32-bit ones will just ignore it.  This is why 64-bit and 32-bit binaries will most likely have trouble talking to each other.

Neverwinter Nights provides its own copy of the SDL library, so that it does not need to depend on the OS to have the correct version.  Some say this is bloat, since it is possible that you are providing something that the OS already has, but it's an easy way to make sure your program will run on different machines since you don't introduce dependencies.

ET's installation, however, failed at something that has to do with glibc, which is the GNU C Library.  In additonal to not finding it on my computer and Synaptic, my guess is that ET would require a 32-bit version of this library.

I believe that the bi-architectures described by RedHat and the like are basically methods to resolve the problem of making a program accessing the correct version of the libraries.

If Ubuntu for AMD64 can get something like this implemented, then it should be a lot easier to run 32-bit programs along with 64-bit ones.  But for now, I only play games on my Ubuntu AMD64 if they work nicely out-of-the-box, otherwise I just boot back into my 32-bit Windows XP :D.

---

### Post by Jet2k5 on 2005-07-25
Well I'm going to be also running windows 32-bit.  Mostly just for Battlefield 2 and several other games that don't have a Linux Client nor supported by Cedega.

But all of the games that are supported in Linux I am going to be running them from Linux.  Don't see a need to run them in windows unless something is not going right.  I should **finally** be getting my final components in next week.  I'm praying to god, that I pull that money :)

---

### Post by DancingSun on 2005-07-25
[QUOTE=Jet2k5]Well I'm going to be also running windows 32-bit.  Mostly just for Battlefield 2 and several other games that don't have a Linux Client nor supported by Cedega.

But all of the games that are supported in Linux I am going to be running them from Linux.  Don't see a need to run them in windows unless something is not going right.  I should **finally** be getting my final components in next week.  I'm praying to god, that I pull that money :)[/QUOTE]

Do you shop at newegg.com?  If not, I'd recommend them to you, their shipping is really fast!

---

### Post by Jet2k5 on 2005-07-25
Of course I shop with newegg.com!  Right now I've got every single part besides the CPU, RAM, MOBO, and video card.  I got an envision Flat CRT but it had some defects so I'm shipping that back tomorrow for a refund.  After that I'm just going to go to an Electronic store like Best Buy or Circuit City to buy a nice cheap monitor.

Newegg is the good stuff :)

---

### Post by DancingSun on 2005-07-25
Heheh, right on!  My AMD64 rig is also put together by parts bought on Newegg!  I built it just 3 weeks ago  :grin:

---

### Post by Jet2k5 on 2005-07-25
[QUOTE=DancingSun]Heheh, right on!  My AMD64 rig is also put together by parts bought on Newegg!  I built it just 3 weeks ago  :grin:[/QUOTE]

I can't seriously wait for this to come through.  I  mean I've been waiting almost all summer and I still can't get all the cash I need :)

When I build this computer I'm going to be one of the happiest kids alive.  \\:D/

---

### Post by kaffeend on 2005-08-10
[QUOTE=][/QUOTE]
 I have just installed Ubuntu for amd64 a week ago (my first Linux distro) and I just cannot make AA or ET run... I really wanted to play TrueCombat: Elite, which is a mod for ET, but I have no idea how I will do it. The reason ET won't work is apparently due to nvidia glx (but I don't know enough, so I'll just shut up about it).

---

### Post by DancingSun on 2005-08-10
[QUOTE=kaffeend]I have just installed Ubuntu for amd64 a week ago (my first Linux distro) and I just cannot make AA or ET run... I really wanted to play TrueCombat: Elite, which is a mod for ET, but I have no idea how I will do it. The reason ET won't work is apparently due to nvidia glx (but I don't know enough, so I'll just shut up about it).[/QUOTE]
Getting AA up and running is easy, you just need to modify the permissions of the .run file and make it executable.  Then you can either double click on it, or execute the file in the terminal by typing:
```
./armyops23-linux.run
``` in the directory where the file resides.  The installer will then launch.

ET is another story.  I also play True Combat: Elite in Windows, so I tried to install this.  But as mentioned in my post somewhere above, the installation of ET will complain that some version of glibc is needed.  I believe this is because ET wants a 32-bit version of the glibc and I have the 64-bit version, but I haven't look too much into this.

---

### Post by Tamir on 2005-08-10
I play ET on my amd64 without problems, just linux32 filename.run .

---

### Post by DancingSun on 2005-08-10
This is the error I get when installing ET:
```
bill@Apollo:~$ linux32 Desktop/et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password:
su: Authentication failure
Sorry.
./setup.sh: line 143:  4315 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.0

See http://zerowing.idsoftware.com/linux/ for troubleshooting

```

---

### Post by Jet2k5 on 2005-08-10
Looks like it's running into permisson problems.  Try putting a *sudo* in front of it.

---

### Post by DancingSun on 2005-08-10
Same message, minus:

```
It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password:
su: Authentication failure
Sorry.
```
:(

It's a seg fault, plus it only "recommended" to install as super user.  My guess is that the installer will default to installing under "/user/" if you ran it as a super user, like the dooom3 demo.

 A seg fault means the program is trying to access certain parts of the memory when it is not allowed to do so.  Which is the reason I brought up my argument.

Tamir, did you have a different GNU C Library installed?  I just have whatever came with Ubuntu....

---

### Post by Tamir on 2005-08-10
I should check it, it's on gentoo. anyway, I think you can install by superuser (su -), fakeroot, or sudo. tell us how it goes.

---

### Post by DancingSun on 2005-08-10
[QUOTE=Tamir]I should check it, it's on gentoo. anyway, I think you can install by superuser (su -), fakeroot, or sudo. tell us how it goes.[/QUOTE]
So you mean you play ET on Gentoo?

Anyway, my last post was the report for installing using the "sudo" command.  Basically got the same error message, except that it didn't ask me for super user password this time (since I'm already running it as a super-user).

---

### Post by Yagisan on 2005-08-12
[QUOTE=DancingSun]et-linux-2.55.x86.run[/QUOTE]
Please use the current version of ET. it is 2.6.0, I suggest you get the bittorrent download to save yourself some trouble. I installed it with ```
sudo linux32 ./et-linux-2.60.x86.run
``` and it went in fine. If you have sound issues or hangs after that, search the forums, there are several solutions, esp in the warty howto. You will need to update punkbuster after you install et, and before your run et for the first time.

---

### Post by DancingSun on 2005-08-12
[QUOTE=Yagisan]Please use the current version of ET. it is 2.60, I suggest you get the bittorrent download to save yourself some trouble. I installed it with ```
sudo linux32 ./et-linux-2.60.x86.run
``` and it went in fine. If you have sound issues or hangs after that, search the forums, there are several solutions, esp in the warty howto. You will need to update punkbuster after you install et, and before your run et for the first time.[/QUOTE]
Hehe, I was a step faster and went on the zerowing website shown in the error message and found out that the error I encountered were bugs of older releases.  I originally got my ET download from True Combat: Elite's website, and apparantly they're not aware of the new full release download and pointed visitors to download 2.55 then apply the patches.  I was able to find the ET 2.60 bittorrent download, and the installation went without problems.

But just as you suspected I got into sound problems.  Currently I'm using [this solution](http://ubuntuforums.org/showthread.php?t=30302&highlight=enemy+territory+sound).  But I just found out that Id's site has another one.  I will try that out tomorrow, it's too late now....after playing True Combat: Elite :P

Still, thank you, Yagisan, for your help! :D  I'm now happily playing my favorite game on AMD64!

---

### Post by Jet2k5 on 2005-08-12
Good stuff.  I got like a week!

---

### Post by DancingSun on 2005-08-12
[QUOTE=Jet2k5]Good stuff.  I got like a week![/QUOTE]
STILL!?  You said that like 3 weeks ago, every week!  :roll: 
But do let me know when you're all set.  Maybe we can play TC:E together sometime!  Something like an Ubuntu64 gang  :grin:

---

### Post by Jet2k5 on 2005-08-12
[QUOTE=DancingSun]STILL!?  You said that like 3 weeks ago, every week!  :roll: 
But do let me know when you're all set.  Maybe we can play TC:E together sometime!  Something like an Ubuntu64 gang  :grin:[/QUOTE]

I know but I keep on being put down time after time.  For example this week I went back to school.  I had to buy new clothes and a bunch of new book  :-?  so that sort of leaves me pooor for a while.  But right now I have almost enough, I'm waiting to get paid on tuesday and also get my money back from newegg.

---

### Post by DancingSun on 2005-08-12
Cool.  So what parts are you still missing?

---

### Post by Jet2k5 on 2005-08-12
[QUOTE=DancingSun]Cool.  So what parts are you still missing?[/QUOTE]

All I have left are the:

CPU ( AMD64 3500+ Venice Core )
Mobo ( Some DFI LAN one )
Ram ( Corsair 2 x 512 PC3200 Dual-Channel )
Video Card ( eVGA nforce 6800GT 256MB PCI-e x16)

I'm also missing a monitor but that might come into play later, right now i"m just going to use a really really old one that I have.  I'll have to check out the local stores to see what they have.  Or I might just wait and save up for a good good LCD screen.  With like 4ms response time!  Now that's good for gaming :)

---

### Post by DancingSun on 2005-08-12
[QUOTE=Jet2k5]All I have left are the:

CPU ( AMD64 3500+ Venice Core )
Mobo ( Some DFI LAN one )
Ram ( Corsair 2 x 512 PC3200 Dual-Channel )
Video Card ( eVGA nforce 6800GT 256MB PCI-e x16)

I'm also missing a monitor but that might come into play later, right now i"m just going to use a really really old one that I have.  I'll have to check out the local stores to see what they have.  Or I might just wait and save up for a good good LCD screen.  With like 4ms response time!  Now that's good for gaming :)[/QUOTE]
Wow...you're really going for the meat aren't ya? :D
Lets see, almost every component you want is higher grade than mine!

I have:
CPU: AMD64 3000+ Venice Core
Mobo: Chaintech Nforce4 Ultra
Memory: Kingston Value RAM DDR400 512MB x 2
Video Card: Chaintech gForce 6600GT 128 MB PCI-E

Beware on the LCD though.  The pixel response time on manufacturer's specs can be very misleading at times.  For example, I read in a news article that Samsung has ads that say they have a LCD that have 4ms pixel response time.  But on their website, that same LCD model has 8ms pixel response time.  Which one is correct?  Well, both of them are, according to Samsung.  The 8ms time is measured from grey to white (or black) and back to grey again.  While the 4ms time is measured from grey to white (or black) only.  For LCD screens, don't buy it until you've seen it in action!  Other factors like color reproduction are very important!

I'm staring at this crappy 15" Dell LCD in my office now, and it is really bad in color reproduction and contrast, and something is just weird about its brightness that it will give me a headache if I stare at it for a long time.  But if I turn down the brightness, text will not be as sharp.

---

### Post by Jet2k5 on 2005-08-12
If I have the money I'm going to buy a kick-butt CRT that I saw at Best Buy.  I have a couple of buddies who actually own them and have nothing but good things to say about it.  On the other hand the LCD is not going to be VGA more like DVI :)  Those pixel times are measured from grey to grey which is what counts.  LCD's are good for gaming if you spend the money for the right ones.  Really anything from 16ms and below should do the job just fine.  For example the people at the BF2 opening day brought in nice sony LCD's and set them up for people to test the game.

I'm going for good parts that cost a lot now, but will last me a while.  The only things that I might upgrade for the holidays is maybe the RAM.  But other than that I don't think I'll need to upgrade anything :)

---

### Post by DancingSun on 2005-08-12
No wonder you're poor! ;-) 
Well, honestly, if my computer didn't die on me and I didn't need to replace it immediately, I would be saving up some more for better components as well.  Alright, I think you should go and mow your neighbor's lawn for some money right NOW! :grin:

---

