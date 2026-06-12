---
title: "using jails for 32 bit apps"
date: 2007-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by skibrianski on 2007-05-02
I'm a bit surprised that the contents of this forum doesn't have anything (well, not much anyway) about creating a chroot for 32 bit applications. I did a quick install following the guides on this site, and everything worked, but I had files scattered all over the place, all sorts of files down /usr that weren't in any sort of packaging system, lots of 3rd party debs with no way to upgrade when security concerns are addressed, etc.

So, when I reinstalled I decided to put all my 32 bit apps in a jail, and it works like a charm. Skype, firefox+flash+java, nxclient (nonfree), wine+ies4linux, and opera+flash all work just fine. I did encounter a couple of snags along the way but nothing a few bind mounts couldn't solve... All in all, it only takes about 500M of space to have this parallel 32 bit system, which even on my laptop isn't that big of a deal...

So... is there some reason most people don't install this way? It seems a much cleaner solution - or am I missing something?

Thanks!

---

### Post by skibrianski on 2007-05-02
One problem with this setup that I've found in the past few hours - loading helper applications doesn't work because they live outside the chroot, so when I click on a pdf, for example, evince won't load.

Hmmm....

---

### Post by skibrianski on 2007-05-02
Apparently I'm not the only one to have wlaked down this road:

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Wish I had discovered that howto *before* I spent so much time discovering it myself! :)

---

### Post by Kilz on 2007-05-02
The main reason chroot's are not used is the amount of space that is wasted. You in effect have a double installation. For most people the amount of 32bit applications is small (under 5). The problem of them being in a jail is also an issue.
I am one of the people who packages a 32bit application. I realize that it takes a little bit of attention on the part of people installing the application to keep it up to date. But I do provide updated debs.
I think that a lot of people also replace their install with every version of ubuntu. This  helps. Because the installed application for them is no more than 6 months old. Before Dapper it was the only way to install 32bit apps. They would not run outside of a chroot. now there are options. That you like a chroot, great. But most new users see it as a reason to stay away from using a 64bit install if they "have" to install a chroot.

---

### Post by skibrianski on 2007-05-03
> **Kilz said:**
> The main reason chroot's are not used is the amount of space that is wasted. You in effect have a double installation. For most people the amount of 32bit applications is small (under 5). The problem of them being in a jail is also an issue.
I am one of the people who packages a 32bit application. I realize that it takes a little bit of attention on the part of people installing the application to keep it up to date. But I do provide updated debs.
I think that a lot of people also replace their install with every version of ubuntu. This  helps. Because the installed application for them is no more than 6 months old. Before Dapper it was the only way to install 32bit apps. They would not run outside of a chroot. now there are options. That you like a chroot, great. But most new users see it as a reason to stay away from using a 64bit install if they "have" to install a chroot.

Hi Kilz. I used your work extensively when I was first testing 64 bit ubuntu, and found it quite useful!

I see what you're saying about double installation, but I guess I don't find it to be much of a problem, since it's only about 500MB of "wasted" space, and you still need to "double-install" 64 and 32 bit libraries to run 32 bit ffox for example, so I don't think the wasted space is really appreciably different. If it is, the fact that I can use apt and I have everything partitioned off nicely more than makes up for it for me.

You know,  I'd be happy to use the non-chroot approach if there was an apt repository for all these 32 bit apps that used consistent naming scheme and all that. Many/most of these apps are proprietary, liike skype and flash, but I wonder if that could be worked around similar to how seveas's flashplugin-nonfree works. What do you think?

I think we need to make 64-bit linux "just work", falling back to 32 bit when necessary - windows vista and mac os x can/will soon be doing this, and an apt repository would get us on track to keep 64-bit ubuntu in the running as a viable 64-bit system. What think ye?

---

### Post by Kilz on 2007-05-03
> **skibrianski said:**
> Hi Kilz. I used your work extensively when I was first testing 64 bit ubuntu, and found it quite useful!

I see what you're saying about double installation, but I guess I don't find it to be much of a problem, since it's only about 500MB of "wasted" space, and you still need to "double-install" 64 and 32 bit libraries to run 32 bit ffox for example, so I don't think the wasted space is really appreciably different. If it is, the fact that I can use apt and I have everything partitioned off nicely more than makes up for it for me.

You know,  I'd be happy to use the non-chroot approach if there was an apt repository for all these 32 bit apps that used consistent naming scheme and all that. Many/most of these apps are proprietary, liike skype and flash, but I wonder if that could be worked around similar to how seveas's flashplugin-nonfree works. What do you think?

I think we need to make 64-bit linux "just work", falling back to 32 bit when necessary - windows vista and mac os x can/will soon be doing this, and an apt repository would get us on track to keep 64-bit ubuntu in the running as a viable 64-bit system. What think ye?

The only problem with what you are suggesting , is that it would take Ubuntu wanting to make 32bit applications "just work" and with a consistent naming scheme on our 64bit installs. Something the developers seem to not want to do.  It has been brought to their attention a few times, I did it just before work on Edgy started. The only thing I accomplished is that the developers proved that they really dont want user ideas to me. Because right after that they made a closed mailing list that users cant join.
As it is right now, its a bunch of users who write howto's for other users. There is no group of them to make decisions. There is also no central place to host the apt repository. Id love to have a place for my deb's for firefox. But at this point it isnt possible for me to host them.

Edit: [I just found this in another thread]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/43324"), Im sure it will be interesting to you. Its from launchpad. Its about trying to get wine into Edgy for 64bit users. Notice it was regected at first. Even with Scott Ritchie, the person who makes the deb's you can download from the Wine website. We still have no wine package in the repositories. Not for edgy, not for Feisty. Why? Because the developers find reasons not to make it work because its "32bit". So they dont want to make it work.

---

### Post by qrdl on 2007-05-03
I think the reason not to make ia32 debs for amd64 is that debian does not have them. For example openSUSE 10.2 for 64bit has an option in installer called something like "32bit environment", selecting it results in installation of about 300 Mb of 32bit libs in your 64bit system. And that is not all of them. Compare it to 5 or 6 packages ia32*.deb in debian/ubuntu. This is not a hollywar provocation it's just an example of how can it be done without any harm to system or philosophy. The result is that opensuse's konqueror supports flash plugin without any need of nspluginwrapper.

---

### Post by Kilz on 2007-05-03
> **qrdl said:**
> I think the reason not to make ia32 debs for amd64 is that debian does not have them. For example openSUSE 10.2 for 64bit has an option in installer called something like "32bit environment", selecting it results in installation of about 300 Mb of 32bit libs in your 64bit system. And that is not all of them. Compare it to 5 or 6 packages ia32*.deb in debian/ubuntu. This is not a hollywar provocation it's just an example of how can it be done without any harm to system or philosophy. The result is that opensuse's konqueror supports flash plugin without any need of nspluginwrapper.

The thing is, 64bit suse is completely multiarch. Installing a 32bit application is as easy as selecting the 32bit version in yast. When searching for applications in yast, there is a version tab, and you can check the 32bit version of the application, it will then install it.
Ubuntu and Debian are not even close to suse's multiarch capability. [I brought this fact up to the developers 2 months before Edgy was released.]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-September/020552.html")
I know the Firefox in 64bit Suse is 32bit, I can bet that knoqueror is to. Thats may be why the Flash plugin works without nspluginwrapper.[ Seeing that it wasnt going to happen]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-September/020575.html")(Matt says there are no plans to implement it) I asked, [can we at least have a 32bit Firefox while we wait for multiarch?]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-September/020581.html") Guess what , its been 2 releases (Edgy and Feisty) and we still dont have the option to install a 32bit Firefox from the repo's.

So we as 64bit users are told no to functionality (a working multiarch system that is common in other 64bit linux distro's) while they add Eye candy to the 32bit version.

---

### Post by qrdl on 2007-05-03
Ubuntu is very dependent on debian, so we will not see multiarch support in ubuntu until it shows up in debian, thats why developers say that there are no plans. It's a huge work and i don't think that ububntu (or canonical) can handle it alone without debian support. As I now debian's multiarch project is very far from completion.

Btw I was always looking at suse as an installation candidate, but i'm really disappointed  by its package management system (ZEN or Yast) it's so sloooowly. (I no there is Smart and somebody say it overcomes apt/synaptic, but I've never tried it). Also what scares me in suse is the lack of multimedia stuff. Of course there is pacman repo, but i'm not sure that using 3d party repo will not affect future update to 10.3 version.

Ok lets switch back to ubuntu :)

---

### Post by qrdl on 2007-05-03
More on multiarch and i386 jails...

I think that current amd64 version of ubuntu (and may be other amd64 distros) is quite buggy. A have two examples of bugs that I encountered:
1. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111690](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111690)
2. [http://ubuntuforums.org/showthread.php?t=427511](http://ubuntuforums.org/showthread.php?t=427511)
I must say there are no such problems in 32bit. Ok the second one can be fixed easily, the first one - i'm not sure. These two examples show that compiling source code that was developed and debugged on 32bit architecture for 64bit and not changing it to satisfy 64bit needs is not a good way. GCC cannot change code it just adds some optimizations and the resultant binary code is not always as good as it should be. It's a long way to go to really port all of those thousands of packages on amd64 (not just gcc ... -m64).

So I don't know is there any reason to switch to 64 bit or not, I will stay with i386 for a couple of years. I must say it's my personal opinion, everyone is free to make decision on his/her own I don't force anyone.

---

### Post by Kilz on 2007-05-03
> **qrdl said:**
> Ubuntu is very dependent on debian, so we will not see multiarch support in ubuntu until it shows up in debian, thats why developers say that there are no plans. It's a huge work and i don't think that ububntu (or canonical) can handle it alone without debian support. As I now debian's multiarch project is very far from completion.


Thank you for proving something I have said for quite awhile now. Ubuntu is dependent on debian for almost everything. Imho we get very little from Ubuntu other than eye candy and funny animal names for releases.

> **qrdl said:**
> More on multiarch and i386 jails...

I think that current amd64 version of ubuntu (and may be other amd64 distros) is quite buggy. A have two examples of bugs that I encountered:
1. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111690](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111690)
2. [http://ubuntuforums.org/showthread.php?t=427511](http://ubuntuforums.org/showthread.php?t=427511)
**I must say there are no such problems in 32bit.** Ok the second one can be fixed easily, the first one - i'm not sure. These two examples show that compiling source code that was developed and debugged on 32bit architecture for 64bit and not changing it to satisfy 64bit needs is not a good way. GCC cannot change code it just adds some optimizations and the resultant binary code is not always as good as it should be. It's a long way to go to really port all of those thousands of packages on amd64 (not just gcc ... -m64).

So I don't know is there any reason to switch to 64 bit or not, I will stay with i386 for a couple of years. I must say it's my personal opinion, everyone is free to make decision on his/her own I don't force anyone.

[Lets take a look, shall we. ]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20") The page ( Bugs in linux-source-2.6.20 in ubuntu) lists 1  &#8594; 75  of 910 results. Dont even start to tell me that they are mostly 64bit bugs.

---

### Post by skibrianski on 2007-05-03
> **Kilz said:**
> The only problem with what you are suggesting , is that it would take Ubuntu wanting to make 32bit applications "just work" and with a consistent naming scheme on our 64bit installs.  Something the developers seem to not want to do.

If ubuntu devs won't make it "just work", then someone needs to make an apt repository that does. Ubuntu had crappy multimedia support, then automatix came along (breaking everything along the way), and the ubuntu devs had to make more of an effort to accomodate the features they were demanding (see: feisty's automatic codec download support).

This is what I'm suggesting. We've already got willingness from you (and other unofficial packagers) to make updates, so all we need is a mirror somewere with those 32 bit apps for 64 bit systems... Since we have a third party repo we can also incorporate things like flash9 (and seveas has done most of the work here, we just need to package if appropriately for 64-bit arch and add a depend on 32-bit ffox).

---

### Post by skibrianski on 2007-05-03
> **qrdl said:**
> I think that current amd64 version of ubuntu (and may be other amd64 distros) is quite buggy.

Interesting, on my c2d hardware I have had no problems, and (somewhat shockingly) all my drivers "just worked". Also, no offense, but it strikes me your post is a bit offtopic here, we're not discussing whether to use 64bit ubuntu, we're discussing how to best do it :)

---

### Post by nss0000 on 2007-05-03
SkiBri:

NOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO.

Having 32-bit apps in a x64 system is like the gent who married two gals: one young, to look after his body and one old to look after his soul. Well ... the ol'gal wrecked his body and the young one trashed his soul. 

Thus ..... better to have gone fishing.


nss
*******

---

### Post by dfreer on 2007-05-04
The idea of a 32-bit repo for AMD64 users is really good. Aren't we linux users, after all? Why do we need to wait for some developers to make it for us when we have the power to do it ourselves? Sounds a bit like Ubuntu has become more like Microsoft to me. 
Anyways, having one repo that has repackaged 32-bit .debs would be great, and I would love to support it. I do have a small webserver with hard drive space, unfortunately it has small bandwidth so if this idea takes off it will eventually need to be moved. For now it should work IMO. I've already repackaged pSX and ZSNES, and I've been setting my eyes on wine/mplayer/firefox and all of it's plugins for awhile now. Basically, once we get some software and repository up, we could put a sticky in the 64-bit thread and a note on ubuntu guide that invites users to use the 64-bit repository. Who knows, maybe the developers will take notice?

EDIT: sorry for posting off-topic, probably should create a new thread :D

---

### Post by ronocdh on 2007-05-04
I really like the idea of a separate 64-bit repository. I can see how it would make a statement to the developers, which would hopefully lead to greater 64-bit support in the future (I mean, c'mon, aren't almost all processors sold today in mid-level computers 64-bit?), but OTOH I can see the devs saying, "Good, good riddance to 'em."

I guess it just comes down to the politics. Are our intentions likely to be misinterpreted? Next question: if the devs take offense from the creation of his hypothetical 64-bit repo, would that be a misinterpretation?

---

### Post by dfreer on 2007-05-04
i don't think it's as bad as all that. Probably the developer's just don't want to spend the time doing it themselves, not so much that the developer's hate 64-bit users. I would think they would welcome the help, my point is that we shouldn't sit around waiting for them to do it for us. Perhaps if we get a repo up, they would set up an official one to be included in all default /etc/apt/sources.lists, so that something similiar to SuSE's "Click on which version of the package you wish to install" could be implemented for 64-bit users.

---

### Post by qrdl on 2007-05-04
Nice idea. The first candidate for repackaging - Mozilla! I can help somehow (I think), if you decide to create such a repo please let me now. I have some experience in backporting apps from debian unstable.

---

### Post by qrdl on 2007-05-04
> **skibrianski said:**
> Interesting, on my c2d hardware I have had no problems, and (somewhat shockingly) all my drivers "just worked". Also, no offense, but it strikes me your post is a bit offtopic here, we're not discussing whether to use 64bit ubuntu, we're discussing how to best do it :)

Well I'm not so lucky, I really face this problems. I've posted a bugreport to bugzilla.kernel.org on the kernel's bug, I hope it will be fixed soon and patch will be backported to ubuntu's kernel. Ok finally you're right, we should talk of best ways to use 64bit :)

---

### Post by dfreer on 2007-05-04
> **qrdl said:**
> Nice idea. The first candidate for repackaging - Mozilla! I can help somehow (I think), if you decide to create such a repo please let me now. I have some experience in backporting apps from debian unstable.

Well, let me look into the specifcs for creating a repository, I'll do some searching on my own but in the meantime, if anyone would want to post any links to creating one might save me some time (preferably with a signed gpg key), and also we would need to get some people on board that would be willing to repackage the 32-bit programs, repackage any needed libraries as well (very important!), and then somehow get them to me. I'm all for creating a repo but I'm not exactly keen on opening up a ftp-upload site just yet. If there are any .deb's out there already, just let me know.

EDIT: well that was quick, the link in my own signiture has a guide for creating a repository. duh!

---

### Post by RAOF on 2007-05-04
In case you haven't already seen it, **falcon** from Seveas' repository is extremely good (it's what I use).

[quote=qrdl]I must say there are no such problems in 32bit. Ok the second one can be fixed easily, the first one - i'm not sure. These two examples show that compiling source code that was developed and debugged on 32bit architecture for 64bit and not changing it to satisfy 64bit needs is not a good way. GCC cannot change code it just adds some optimizations and the resultant binary code is not always as good as it should be. It's a long way to go to really port all of those thousands of packages on amd64 (not just gcc ... -m64).
[/quote]
That's not how programs are written.  The **vast** majority of the source code in Ubuntu (in fact, **everything** that's not inline assembler) is neither 32bit nor 64bit code.  **Source code has no inherent word size**.  Gcc doesn't "port" 32bit source code to 64bit object code, it compiles the **same** source code into either 32- or 64-bit object code.

Sometimes, programmers make (stupid) assumptions about the size of various things (for a common example, assuming that an "int" is the same size as a pointer).  **This** is the (essentially only) source of bugs in 64bit builds that aren't also in 32bit builds.  These assumptions are bugs, even for the 32bit builds.  They're just only exposed by building a non-IA32 binary.

---

### Post by qrdl on 2007-05-04
> **RAOF said:**
> In case you haven't already seen it, **falcon** from Seveas' repository is extremely good (it's what I use).


That's not how programs are written.  The **vast** majority of the source code in Ubuntu (in fact, **everything** that's not inline assembler) is neither 32bit nor 64bit code.  **Source code has no inherent word size**.  Gcc doesn't "port" 32bit source code to 64bit object code, it compiles the **same** source code into either 32- or 64-bit object code.

Sometimes, programmers make (stupid) assumptions about the size of various things (for a common example, assuming that an "int" is the same size as a pointer).  **This** is the (essentially only) source of bugs in 64bit builds that aren't also in 32bit builds.  These assumptions are bugs, even for the 32bit builds.  They're just only exposed by building a non-IA32 binary.

You are absolutely right, but you just said yourself that programmers do stupid things. By the fact they always do :) And that is exactly how most of programs are written - with "bonus" bugs :) That is the reason to actually rewrite code regardless of the fact that these bugs are 64bit specific or not.

---

### Post by dfreer on 2007-05-04
I've used ubuntu.moshen.de before, and that's pretty much what I was aiming for with the signed gpg key and everything. So I am currently reading up on Falcon and it's .pdf, looks like it will do the job. Thanks!

---

### Post by RAOF on 2007-05-04
> **qrdl said:**
> You are absolutely right, but you just said yourself that programmers do stupid things. By the fact they always do :) And that is exactly how most of programs are written - with "bonus" bugs :) That is the reason to actually rewrite code regardless of the fact that these bugs are 64bit specific or not.

I suppose that what I'm trying to get at is: almost all the programs in the Ubuntu repository **don't** need to be rewritten for 64bit support, because Linux/Unix programs tend to be written with portability in mind.  Debian - the source of almost all Ubuntu packages - is available for a staggering range of hardware, from 32bit big endian system to mixed 32/64bit little endian systems.  This works because programmers are thinking about portability from the get go.

---

### Post by qrdl on 2007-05-04
I don't mean rewriting from scratch either, I mean that there are bugs scpecific to 64bit version, they shold be fixed (your example of sizeof(int*) for example). Of course it means rewriting **some** code (patching) - it's a part of porting process. 

Ok enough of that:)

---

### Post by RAOF on 2007-05-04
Ok, I think we have found the happy medium :).  There **are** bugs which are only exposed by using x86-64 binaries, just as there are (admittedly, fewer) bugs which are only exposed by IA32 binaries.

---

### Post by dfreer on 2007-05-04
well, I'm going to create a new thread in the 64-bit section once i get this repo up. It won't really have anything other than my pSX and ZSNES packages at first, but hopefully we can fix that. 

RAOF, I just configured falcon, and ran it for the first time. I got this error when running falcon update:
```
$ falcon update
Falcon repository builder 1.5.4 (C)2005-2006 Dennis Kaarsemaker <dennis@kaarsemaker.net>
*  Updating component 'feisty/main'
E: Package pSX in component main has unknown architecture amd64
```
the package/s in question can be found in here (i assume these are the packages it is hanging up on):
[http://packages.dfreer.org/pool/feisty/main/binary-amd64/P/](http://packages.dfreer.org/pool/feisty/main/binary-amd64/P/)

Not quite sure what the problem is, because I built them with the DEBIAN/control file stating the architecture as amd64, and they install just fine on an amd64 system. Maybe you've experienced this?

EDIT: hmmm seems like I needed to edit the /etc/falcon.ini file so that it defined the architectures, oops.

---

### Post by dfreer on 2007-05-04
The repository is up, although for some reason I can't get the HTML page to generate. RAOF, could you help me with this? I created a new thread in the 64-bit forum about it, and I describe the problem in that thread.
Here's the thread:
[http://ubuntuforums.org/showthread.php?t=432642](http://ubuntuforums.org/showthread.php?t=432642)

---

