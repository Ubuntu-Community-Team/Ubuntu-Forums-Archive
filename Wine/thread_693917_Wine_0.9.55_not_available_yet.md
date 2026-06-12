---
title: "Wine 0.9.55 not available yet"
date: 2008-02-11
forum: Wine
---

### Post by cameran on 2008-02-11
is wine 0.9.55 available in the wine budgetdedicated repo yet?

 i've been trying to update my system all weekend but nothing comes up.

---

### Post by Kosimo on 2008-02-11
Take a seat, drink a tea and wait 'till wine maintainers make a nice free job for you ;)

---

### Post by bastiegast on 2008-02-11
I've been waiting too! :lolflag: Usually it's there within a day. I don't know why but I always get ridiculously  excited over wine releases. 

By the way. The Wine Weekly News is keeping me waiting too. I love reading it.

---

### Post by Zzzach on 2008-02-11
I want mah wine!! :)

---

### Post by FrozenFox on 2008-02-12
I found a .deb for the new version that worked fine for me on Hardy.

[http://www.mepislovers.org/forums/showthread.php?t=13883](http://www.mepislovers.org/forums/showthread.php?t=13883)

---

### Post by cameran on 2008-02-12
thanks, maybe i'll check out that version!

---

### Post by lvlo on 2008-02-13
Thanks! Works fine for me and [Live For Speed]("http://lfs.net").

:")

---

### Post by cameran on 2008-02-13
will that deb update an existing wine installation or do i have to remove wine 0.9.54?

thanks!

cameran

---

### Post by FrozenFox on 2008-02-13
> **cameran said:**
> will that deb update an existing wine installation or do i have to remove wine 0.9.54?

thanks!

cameran

It will update your current version to the newest one.

---

### Post by duncan_nz on 2008-02-14
Wow, still no official version? What gives?

---

### Post by IanW on 2008-02-14
Maybe their Ubuntu maintainer is on vacation?

That Mepis deb is no good for me, I need some 64bit goodness.

---

### Post by Sockerdrickan on 2008-02-14
Hardy has the debs

---

### Post by cameran on 2008-02-14
where do we get those debs for hardy?

will they work OK in gutsy?

---

### Post by FrozenFox on 2008-02-14
EDIT: Ignore the link below, it's broken, as several have pointed out to me. If youre on 32 bit, try the mepis one earlier in this thread and see if you have any luck. Would appreciate if someone tells me when this package is fixed. :)

[http://packages.ubuntu.com/hardy/otherosfs/wine](http://packages.ubuntu.com/hardy/otherosfs/wine)


The hardy packages are here for those not using hardy if they really want to download the .deb.. The mepis deb given earlier should work fine on gutsy.. it certainly works fine on hardy..

---

### Post by Crinos512 on 2008-02-14
use the hardy ones if you use x64 and don't want to force the architecture.

---

### Post by tghe-retford on 2008-02-14
> **FrozenFox said:**
> [http://packages.ubuntu.com/hardy/otherosfs/wine](http://packages.ubuntu.com/hardy/otherosfs/wine)


The hardy packages are here for those not using hardy if they really want to download the .deb.. The mepis deb given earlier should work fine on gutsy.. it certainly works fine on hardy..
That .deb appears to be broken, as confirmed by a number of posters on this thread:

[http://ubuntuforums.org/showthread.php?t=696882](http://ubuntuforums.org/showthread.php?t=696882)

I installed the deb from the link in your post and I get exactly the same "Segmentation Fault (core dumped)" message someone else got in that thread.

It's frustrating because I am hoping that the Direct3D improvements will help with a program I really need to run on Linux.

---

### Post by FrozenFox on 2008-02-14
Yes, I just confirmed your comment. It is indeed broken. However, for those of us on 32 bit machines, the mepis one does work for me on hardy and should work on gutsy.

---

### Post by FrozenFox on 2008-02-14
Hmm, is the "official" deb also broken on 64 bit machines? It doesn't seem so from the comment a few posts above me here.

---

### Post by kubug on 2008-02-14
Ditto. Segfault with wine 0.9.55

---

### Post by cameran on 2008-02-14
i tried the mepis package and it installed but my wine entry in the applications menu has completely vanished

what can i do to get it back?

---

### Post by Crinos512 on 2008-02-14
> **FrozenFox said:**
> Hmm, is the "official" deb also broken on 64 bit machines? It doesn't seem so from the comment a few posts above me here.

I cannot confirm this as of yet, (still workin hard... LOL.)

---

### Post by Sockerdrickan on 2008-02-14
Guys :KS

I don't see any reason NOT to go hardy, it's stable I tell you.

---

### Post by theShaggy on 2008-02-14
Yeah, but nearly a week after the fact, and Wine is STILL not in the repos?

What's taking so long?

---

### Post by cameran on 2008-02-14
well according to this page:

[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

there is a single person responsible for releasing a packaged version of wine for each distribution.  i assumed it was a team since wine is a very large and well-known project, but i guess it all boils down to one person without an apparent backup or alternate.  at any rate if you'd like to contact the maintainer for ubuntu/debian his email address is on that page

i always wondered how my friends with other distros would always get the latest version of wine before my ubuntu friends and myself (we seem to lag about 1-2 days behind other distros the last few months), and i guess it has to do with each maintainer's own schedule instead of something done with the wine team.

learn something new about linux and wine every day it seems! :)

---

### Post by KhaaL on 2008-02-15
Thanks a lot for the info cameran... I was quite puzzled why wine has been delayed so much, i think this is a record. 

@Tux0r: I'm going 64bit hardy next thursday, with the new alpha ;) Am also switching kde for gnome... my computer is going to experience some major changings! :D

But winehq dosen't supply repositories for hardy yet, do they?

---

### Post by Kosimo on 2008-02-15
Hey guys...
how about downloading the source and compile it?

It is too difficult?

Any how-to around?

---

### Post by kubug on 2008-02-15
Well, if any of you want to go back to a previous version (like me) and wait until this is fixed, just enter:

```


 sudo dpkg -i /var/cache/apt/archives/wine_0.9.54-0ubuntu4_i386.deb


```

Of course, this line only works if you are running i386.

Cheers

---

### Post by happyhamster on 2008-02-15
- Get rid of previous wine:

sudo apt-get remove wine

- Download source archive, double-click it to extract. It will extract to a "wine-0.9.55" folder. Open a terminal and navigate to that folder.

- Download all dependencies you need (this can be quite a huge amount of software). From within the source folder:

sudo apt-get build-dep wine

- Compile (takes ~ 30 minutes on my machine (AMD x2 3800+), so get yourself some tea):

./configure
make depend && make

- You'll need to install wine itself as root. Never *run* anything else wine-related as root though.

sudo make install

- Update your wine-install:

wineprefixcreate

- That's it. If you want to uninstall this compiled version; 

sudo make uninstall


N.B. What I recall from compiling  wine-0.9.55, it needed additional packages over the previous wine (other gcc version IIRC and some other stuff). Perhaps that's the reason the ubuntu packages are delayed (just guessing).

---

### Post by Crinos512 on 2008-02-15
> **Crinos512 said:**
> I cannot confirm this as of yet, (still workin hard... LOL.)

I can confirm that X64 doesn't work either.... :(

---

### Post by zebulon M on 2008-02-16
Thanks to happyhamster for his useful how-to! It was a lot of fun to compile that big fat pile of code. With the latest source in their git-repository, even Google Sketchup is functional. :D Now I'll go format my windows partition!

---

### Post by blackdragon1157 on 2008-02-16
Thanks to hamster, I now have 9.55 :)

How hard would it be for someone else to make a .deb, to save people from compiling it themselves?

---

### Post by Zzzach on 2008-02-16
I WAN MAH WINE!!!!1!!!!1111 :mad: :mad: :mad: :mad:

---

### Post by ChristosG on 2008-02-16
Hello, I recently have installed Wine 0.9.55 and I have a question. I installed Bitlord (torrent downloading) and now I uninstalled it but it remains: Applications->Wine->Programs->Bitlord. How can I dispose it for good? :p

p.s. This is my first post, I am happy to join such a useful forum :-)

---

### Post by happyhamster on 2008-02-16
> **ChristosG said:**
> Hello, I recently have installed Wine 0.9.55 and I have a few questions.

1) Is it compatible with all programs, or it doesn't work with some? I tried to install Bitlord (torrent downloading) and when I tried to execute the .exe it didn't run and there was a message that there is a problem with the program.
Hi. Wine is work in progress, so a lot of programs don't work, and some will probably never work. The number of applications that do work is steadily growing though.

First place you can look to see if some app may work is the application database:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

And here is an excellent thread on wine:
[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

It doesn't look to promising concerning Bitlord, I'm afraid: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4764&iTestingId=12531](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4764&iTestingId=12531)

Anyway, you can try one of several native linux bittorrent clients: ktorrent or deluge for example.

> 
2) Can Wine replace XP totally?
Well, wine isn't XP, so no. If you want a *complete* replacement for XP, you should use XP, not wine :) Most people use wine for a few windows apps they can't do without. I use it so I can still play all those windows games I bought over the years.

> 
p.s. This is my first post, I am happy to join such a useful forum :-)
Welcome, welcome :)

---

### Post by happyhamster on 2008-02-16
> **ChristosG said:**
> I installed Bitlord (torrent downloading) and now I uninstalled it but it remains: Applications->Wine->Programs->Bitlord. How can I dispose it for good? :p
Right-click the main menu on your top panel and choose Edit Menus.

---

### Post by ChristosG on 2008-02-17
happyhamster, thank you for your reply, it was all very useful :-)

---

### Post by SoulSmasher on 2008-02-17
it's been 10 days :S hope it is released asap. thanks for the deb btw :)

anyone had an issue about 3d games ? i'll use team fortress 2 on it..

---

### Post by SATA on 2008-02-18
HOPEFULLY this version will allow me to install CNC3 without the installer claiming it had failed. We'll See.
:guitar:

---

### Post by justin whitaker on 2008-02-18
I tried compiling Wine, and it exited early.

I grabbed the tarball, unzipped it, and used the ./tools/wineinstall tool to find out what was missing. There are three files missing on Hardy...I don't know what it is for Gutsy, but it should be similar.

1. Get the wine tarball, and extract it somewhere. 
2. If you haven't installed build essential, then get it. 
3. You need Flex. So, grab a terminal, and type: 

> sudo apt-get install flex

4. Next, you need bison. Again, in a terminal:

> sudo apt-get install bison

5. You need the xorg-server-dev package to get the headers if you want X support. Install that the way you did everything else. 

6. execute the ./tools/wineinstall command. With any luck, a bunch of compilation gibberish will fill your terminal, and you can go get a coffee. 

7. Once the compile is done, type wine notepad to make sure it works. If you see notepad, then it worked. :)

---

### Post by Twitch6000 on 2008-02-18
Well I got wine 0.9.55 by compiling it *ughhh* and well it seems the games and apps I need wine for(Starcraft,DevoC++,and a few random tools) are still the same bugs :(.

Although after compiling I noticed no icon in the program list.Why is that =[?

---

### Post by SATA on 2008-02-18
> **justin whitaker said:**
> 
5. You need the xorg-server-dev package to get the headers if you want X support. Install that the way you did everything else. 



I think you mean xserver-xorg-dev

---

### Post by stuart.crouch on 2008-02-19
> Although after compiling I noticed no icon in the program list.Why is that =[? 

Icons on lists, file associations and stuff are defined by the package maintainer in the .deb file.

All compiling yourself does is give you an executable file on your filesystem somewhere.  You then need to do everything the .deb does yourself as well.

---

### Post by SATA on 2008-02-19
YAY 0.9.55 is in the repo's! w000t

---

### Post by Crinos512 on 2008-02-22
I can confirm that the Repo version of the x64.deb does work.

---

### Post by arigram on 2008-02-22
> **SATA said:**
> YAY 0.9.55 is in the repo's! w000t

About time for version 0.9.56! :P

---

### Post by Spydr4590 on 2008-02-22
February 22, 2008: Wine 0.9.56 Released, You can compile wine yourself though it's very easy.

---

