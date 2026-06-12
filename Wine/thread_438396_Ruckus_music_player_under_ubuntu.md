---
title: "Ruckus music player under ubuntu"
date: 2007-05-09
forum: Wine
---

### Post by kryrinn on 2007-05-09
My school is effectively blocking out every download option that they can, but giving students the option of using the Ruckus Music.  However, their player is win only.

I installed Wine, hoping that that would let it work, but the install freezes midway, saying that it cannot update Win media player.  I managed to find a Win media player 6.4 for linux, but it doesnt make a difference in the install.

I'd really like to be able to use this, for the speed of it if nothing else.  Anyone got a clue?

---

### Post by freehunt on 2007-05-10
I know Ruckus uses the PlaysForSure DRM, which requires WMP9. I have gotten WMP7.1 installed, but when I try to upgrade, it says I have the most up to date version, which is incorrect obviously. WineHQ has some interesting suggestions, but I am short on time right now. Try going there and playing around with some of the stuff they've posted under WMP9. I would really love to get this working as well.

---

### Post by mengfei on 2007-09-13
Not just WMP9, but Ruckus requires WMP11.

I'd say forget it. Ruckus is horribly designed.

Use eMusic.com, jamendo, magnatune, etc.

Or just buy the CDs on Amazon or something. Work hard to earn what you want.

---

### Post by jmetal88 on 2007-10-29
Well, no, Ruckus is lying if it says it needs WMP11. I've been using it under Windows with WMP10 for quite a while. It also installed fine on Wine with WMP10's failed install, except its 'Apple Bonjour' wouldn't install so I can't actually log in or play any songs.

---

### Post by vertexoflife on 2007-11-02
Okay, with Wine I can get WMP10 running, and I can get Rukus running, but the only problem is getting Apple Bonjour to actually work so I can login.

---

### Post by DouglasAWh on 2007-11-02
WMP 11 is required for the neighborhood feature.  Mine dies when I try to open it.  I'll report back as things change.  My school newspaper, The Daily Tar Heel, is doing a story on file sharing and contacted me about open source alternatives, so I'd like to say it's possible to get Ruckus going since UNC heavily supports Ruckus use.

---

### Post by DouglasAWh on 2007-11-03
I've gotten it installed, but I get an error when trying to log in: [http://www.ils.unc.edu/~whitdoug/Screenshot-ruckus.png](http://www.ils.unc.edu/~whitdoug/Screenshot-ruckus.png)

This appears to happen whether WINE is set to 2000, XP, Vista or 2003.

Appears to be a brief discussion of the issue at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5320&iTestingId=7359](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5320&iTestingId=7359), but no solution.

---

### Post by MaindotC on 2007-11-14
I thought bonjour was just so you could share files within those in the same network or domain?  For example, those that are on the same campus as me.  Is Bonjour used for authentication?

I think what I'll do is just host an XP box and allow you to RD into it.  It's made of school parts so there's no way to trace it back to me.  I'll set it up so you can RD into it, d/l what you need, then extract the music files to your linux box so you can remove the DRM.  I'll let you know when I have this complete.

---

### Post by DouglasAWh on 2007-11-14
Whatever bonjour is used for, Ruckus doesn't work...

---

### Post by MaindotC on 2007-11-15
What could I do to contribute to getting it to work?  Better yet, can we think of an open source program that would still authenticate with Ruckus but operate smoothly in Linux?  I know in some of the previous posts there was a discussion about DRM and its compliance or interoperability with WMP.  I'm willing to contribute what I can to troubleshooting this issue.  Perhaps we could start a site such as [http://free60.org](http://free60.org) where we establish a methodology for resolving this with a constantly updated changelog and documentation.  Let me know what you think and if its feasible.  I'll email Ruckus and see if they can figure why this is happening (which I sincerely doubt they'll reply).

---

### Post by MaindotC on 2007-11-23
I was using wine to run Ruckus, and I thought of something.  Ruckus wants to access a bunch of .dll's.  Is there a way to get wine to find those dll's when called upon?

---

### Post by DouglasAWh on 2007-11-23
That sounds like a question for the WINE forums.

---

### Post by MaindotC on 2007-11-24
> **DouglasAWh said:**
> That sounds like a question for the WINE forums.

Wow thanks for nothing. Don't post on here if you have no interest in helping.

---

### Post by DouglasAWh on 2007-11-25
The WINE guys are the people that know about dll's.  Unless someone knows something about dll's here, then that's who we should be talking to.  Hopefully anyone here that knows about dll's has already spoken up, but who knows.  I already posted one link to WINE here three weeks ago and it doesn't seem to have garnered much interest.  Unfortunately, nobody who can help seems interested in doing so.  I'd help if I could, but I don't know the first thing about how WINE works or what to do with dll's.  I'm happy to try something if someone has an idea though.  

So, I guess the real question is, how to get the issue out of this thread and into the eyes of someone who knows what they are doing.  I thought going to WINE was the answer.

---

### Post by MaindotC on 2007-11-25
Doug, I appreciate your thoughts.  I hope a mod will move this thread to any wine-specific areas of the forums, or hotlink it to winehq.

---

### Post by angryfirelord on 2007-11-26
Hmm, my university offers the service for free as well. If I have time, I'll sign up for the service and report back if it works or not.

---

### Post by t3h_h4ck3r on 2007-11-26
try going to [http://www.ban-itc.org](http://www.ban-itc.org) i beleive to be able to go around proxy blockers. then try the download again

---

### Post by MaindotC on 2007-11-26
> **t3h_h4ck3r said:**
> try going to [http://www.ban-itc.org](http://www.ban-itc.org) i beleive to be able to go around proxy blockers. then try the download again

Server not found.  Google doesn't seem to turn up anything specific, either.

---

### Post by DouglasAWh on 2007-11-26
wait, what does this have to do with proxy servers?

---

### Post by MaindotC on 2007-11-26
> **DouglasAWh said:**
> wait, what does this have to do with proxy servers?

I thought maybe ban-itc was some sort of work around patch or program.  Aside from that - god knows if he'll clarify.

---

### Post by DouglasAWh on 2007-11-26
Did anybody else notice we got moved out of the beginner talk and into the WINE section?  This is good news, I think.  I'm not sure when the move happened, but let's hope we see some progress on this.

I got on the WINE mailing list, btw.  So far, people have been helpful, but no conclusions yet.

I think the proxy server guy thought the issue was Ruckus was being blocked, but that's not the issue....it just doesn't work! :(

---

### Post by MaindotC on 2007-12-02
I don't understand the whole concept of moving threads to particular forums in the sense that the search tool for ubuntuforums is horrendous, and I usually just search by doing```
 ruckus site:ubuntuforums.org
``` in google.  Well, let's hope something comes of this move...

---

### Post by DouglasAWh on 2007-12-04
It's better for browsing.  I'll want to post in a certain sub forum and then I'll see others in the thread and sometimes answer a few.

I post to the WINE list and the thread pretty much died.  I posted the dll list, but nothing came of it.  It'll probably be the summer before I get to take a serious look at it again, unfortunately.  I'll keep my eyes on new versions of WINE and Ruckus though.

---

### Post by DouglasAWh on 2008-01-06
So, I recently came accross WINE tricks on the WINE listserv, and here's the latest post 

> 
> Awesome, that was helpful...except that now I get
>
> Usage: ./winetricks.sh [options] package [package] ...
> This script can help you prepare your system for Windows applications
> that mistakenly assume all users' systems have all the needed
> redistributable runtime libraries or fonts.
> Some options require the Linux 'cabextract' program.
>
> Options:
>  -q         quiet.  You must have already agreed to the EULAs.
>  -v         Verbose
> Packages:
>  art2kmin   Access 2000 runtime.  License required!
>  cc580      Install native common controls 5.80, override comctl32
>  corefonts  Install MS Times, Arial fonts
>  dcom98     Install native DCOM, override the Wine implementation
>  gdiplus    Install gdiplus.dll from pp viewer (got a better idea?)
>  gecko      Install the HTML rendering Engine (Mozilla)
>  jet40      Install Jet 4.0 Service Pack 8
>  liberation Install Red Hat's Liberation fonts (Sans, Serif, Mono)
>  mdac27     MDAC 2.7: Microsoft ODBC drivers, etc.
>  mdac28     MDAC 2.8.
>  mfc40
>  mono11     mono 1.1.13-gtksharp-2.8.2 (deprecated, use 1.2)
>  mono12     mono mono-1.2.5.2-gtksharp-2.10.2
>  msi2       Microsoft Installer 2.0
>  msxml3     (Note: install a bit squidgy; see
> [http://bugs.winehq.org/show_bug.cgi?id=7849](http://bugs.winehq.org/show_bug.cgi?id=7849))
>  msxml4     (Note: installing this requires fake c: to be named harddrive1!)
>  pdh        Install pdh.dll (Performance Data Helper)
>  tahoma     Install MS Tahoma font (not part of corefonts)
>  vbvm50     Visual Basic 5 runtime
>  vbrun60    Visual Basic 6 runtime
>  vcrun6     vc6redist from VS6sp4, including mfc42
>  vcrun2005  Visual C++ 2005 redistributable libraries
>  wsh51      Windows Scripting Host 5.1
>  wsh56      Windows Scripting Host 5.6 (install vcrun6 first)
>  wsh56js    Windows scripting 5.6, jscript only, no cscript
>  wsh56vb    Windows scripting 5.6, vbscript only, no cscript
> Pseudopackages:
>  fakeie6      Set registry to claim IE6sp1 is installed
>  native_mdac  Override odbc32 and odbccp32
>  winver=win98 Set windows version to win98
>  winver=winxp Set windows version to winxp
>  winver=      Set windows version to default (win2k)
>  volnum      Rename drive_c to harddiskvolume0 (needed by some installers)
>
> I'm using Ubuntu Gutsy.  I know what to do with the -q and the -v, but
> I don't understand what all this other stuff is.  Thanks!
>
>   
Douglas:

The packages are packages which originates from Microsoft as addons to Windows, with the exception of corefonts.   This package adds the Arial and Times New Roman fonts that are not included with Wine.  Gecko installs the Mozilla HTML rendering engine (as stated). The pseudopackages do not install anything but do the following: Fakeie6 package 'fakes' the installation of Internet Explorer 6 sp1 by adding a setting to Wine's registry.
The winver packages are what they are, they set the windows version to either windows98 or windowsXP.  The standard windows version identification that Wine comes with is windows2000.   volnum sets another registry setting that maps the ./wine/drive_c to harddiskvolume0 (which is what the C: drive looks like to WindowsNT type versions of Windows) so that several programs will install. One note:  Most of the packages DO NOT require a Windows(TM) license.  However the Access2000 runtime does require that you have an Office Professional or MSDN license or you are in violation of the license agreement and a license id is requested on install.
If you are having problems with gdiplus, it is suggested that you use ./winetricks gdiplus.  This will install a program that comes with the native gdiplus.dll file and changes the default settings to use this file.

Once a package is installed, any files needed for the package install are stored in ~/winetrickscache so they do not have to be downloaded for subsequent installs.  The only exception to this is the mdac2.7 and mdac2.8 packages as the downloaded file has the same name.

*name removed*


I don't think this helps us any with Ruckus, but I thought I'd go ahead and post and hope for additional comments on how something like this could be helpful for getting ruckus to work.

As a side note, Music and DRM and such came up again yesterday at work.  I suppose that's one of the reasons I was particularly interested in winetricks.

---

### Post by DouglasAWh on 2008-02-25
I just got this from the guys at Ruckus:

> 
Hi,

Actually we'll have streaming media coming in about 2 weeks or so, so anyone can listen to music for free.


I wonder if you'll be able to make playlists though like you can when you actually download the music.  Their response to not having a Mac or Linux client was that they use Windows DRM.  The issue of DRM isn't one we are going to win with a company like this, but why such a restrictive DRM?  Why not a DRM that is cross platform?

---

### Post by AndThenWhat on 2008-07-01
I am also very interested in getting Ruckus working before I go off to college, as I refuse to use Windows.  My Ruckus gets all the way through the installation and I can start it but when I try to log in it gives me the same firewall message and tells me that Bonjour did not successfully install.

If we can get this working it will open up a huge door for Ubuntu/Linux.  Ruckus is awesome and best of all legal and most colleges offer it for free.  I heard that Ruckus offers Mac/Linux users the alternative eMusic.com which is absolute crap because it limits to 15 downloads a month and costs extra.

Someone help please :confused:

---

### Post by DouglasAWh on 2008-07-01
> **AndThenWhat said:**
> I am also very interested in getting Ruckus working before I go off to college

Have you tried Pandora.com or Last.fm?  You can get some free downloads from Last, but both are mainly streaming.  I've resigned myself to using them, though I haven't tried Ruckus with 8.04.  What distro are you using?

We aren't likely to get much help from Fedora since they really hate DRM and such.  I don't know if there have been any advances in getting Windows DRM to work on Linux.  If there have been, someone please post.  Right now my hands are kinda tied as to really working on this, but hopefully in another week I will have some free time.

---

### Post by skoberlink on 2008-07-08
hey guys I've been trying to get ruckus to work in wine for quite sometime.  I came across this thread the first time a tried a few weeks ago and am now trying again.  

I've done some research and Bonjour is used in ruckus solely for the Zeroconf features as near as i can tell.  Someone had asked why bonjour was needed dunno if it ever got answered.  That's why.  I don't really know exactly what neighborhood features entail (neighborhood features is mentioned in the error message you get) but it apparently has something to do with zeroconf.  is there some linux alternative for this or a windows alternative that ruckus can use that does work in wine?  

just a thought i'm no expert and i'm a pretty new ubuntu (and linux in general) user so I'm kinda going on generic computer knowledge and even that's just stuff i've taught myself over the years so input from someone more knowledgeable would be good.

---

### Post by DouglasAWh on 2008-07-08
skoberlink, do you mind posting some links on zeroconf?  I don't know anything about it and I just moved and started a new job, so I'm kinda busy getting a new drivers license and bank and stuff like that.  Thanks!

---

### Post by skoberlink on 2008-07-09
alright sure.

like I said I'm no expert.  I'd never even heard of zeroconf until i did research into bonjour and what ruckus uses it for.  

to summarize I understand it to be a very simple way to network computers/printers/etc. Bonjour is used to "manage" a network usually between macs (bonjour is Apple freeware) and pcs with special attention to printers and file sharing.  Zeroconf in general is derived from Zero Configuration in that there's no mucking about with long strings of numbers and letters such as ip addresses and mac addresses or guess and check by selecting/pinging until you find the correct computer you were trying to share.

Here are some links:
[http://en.wikipedia.org/wiki/Bonjour_(protocol)]("http://en.wikipedia.org/wiki/Bonjour_(protocol)") <-wikipedia article about Bonjour/Rendezvous

[http://www.zeroconf.org/]("http://www.zeroconf.org/") <-zeroconf.org with a description of zeroconf and several detailed links.  I dunno if this is a company and Zeroconf is a particular software that bonjour implements or if the domain name just hadn't been used yet and someone used it to write this description

[http://en.wikipedia.org/wiki/Zeroconf]("http://en.wikipedia.org/wiki/Zeroconf") <-wikipedia article about zeroconf

I can't seem to find the article about how ruckus uses zeroconf (I did this research a couple weeks ago)  I'll post it as soon as I find it

EDIT: I should mention I found some zeroconf alternatives.  

1. [Howl]("http://www.porchdogsoft.com/products/howl/")  -- No longer supported; found a download through softpedia.com but couldn't get it to install

2. [Avahi]("http://avahi.org/") -- again couldn't get it to install but like I said I'm new to linux and hadn't quite figured out how to install a tar.gz or tar.bz2 file so I may be able to get it now (haven't tried again since then).  Still it would be installed in linux not on the C:\ drive created by wine so I'm not sure that would work.  I never found a windows version other than bonjour to try

---

### Post by DouglasAWh on 2008-07-09
> **skoberlink said:**
> 
I can't seem to find the article about how ruckus uses zeroconf (I did this research a couple weeks ago)  I'll post it as soon as I find it

Did you ask Ruckus help?  In my experience they are very responsive, if not very helpful.  If also might be worth seeing if anybody has gotten Ruckus to work on a Mac since Bonjour is an Apple product.  DarWine is the Apple equivalent to WINE, the last time I checked.  I've got a big project due July 21st, but after that I'll do some research on this Zeroconf stuff.

---

### Post by skoberlink on 2008-07-09
> **DouglasAWh said:**
> Did you ask Ruckus help?  In my experience they are very responsive, if not very helpful.  If also might be worth seeing if anybody has gotten Ruckus to work on a Mac since Bonjour is an Apple product.  DarWine is the Apple equivalent to WINE, the last time I checked.  I've got a big project due July 21st, but after that I'll do some research on this Zeroconf stuff.

actually trying it on mac is an excellent idea.  Unfortunately I've already tried.  I tried to get it going on a macbook pro running Mac OS X tiger.  It can't run in mac of course because it's .exe but I tried with Darwine (Mac port of Wine) and ran into the same problems. I mean exactly the same error message as well as some extra problems because Darwine isn't as developed as Wine.  I kind of gave up though without trying much because I tried during final exams so I was pretty busy.  I did get it to work using Parallels Desktop but it was just emulating a windows machine on a virtual machine and didn't run very smooth anyway.

I didn't contact ruckus about running it in wine or how it interacts with bonjour.  However I did ask them why it wasn't ported to mac or linux and it's because it's limited by the windows DRM (which is why it need windows media player as well).

Also I agree, excellent customer service.  They seemed sympathetic to the problem but just had no way to fix it because of the drm forced on them.

EDIT:  Haha now i feel stupid.  it actually mentions that ruckus uses zeroconf in the bonjour wikipedia article.  I must have inferred that it was only using zeroconf by how the paragraph was worded.  That may not be true then since it's a conclusion I came to on my own

---

### Post by DouglasAWh on 2008-07-09
> **skoberlink said:**
> However I did ask them why it wasn't ported to mac or linux and it's because it's limited by the windows DRM (which is why it need windows media player as well).

I mentioned a week ago about DRM seeming to be the real issue and hinted at that back in February in this thread.  If we could get WMP working in WINE, we'd be golden.  At this point, I'm no longer a student, so it doesn't really matter to me, except that I think it would be good news for the students at UNC.  I don't know what sorts of dll's, etc WMP needs, but I think that's the place for work to be done.

---

### Post by skoberlink on 2008-07-09
DRM is absolutely a problem but I think WMP 10 or 11 DRM works.  The program has issues doing what it's supposed to but that seemed to install fine for me anyway (have you tried the latest version of wine?).  And I even got ruckus to start up and everything but then it popped up and said that Bonjour hadn't installed and blah, blah, blah can't remember it exactly but basically it doesn't like running without the neighborhood features whatever those are.  

At this point I am of the opinion that DRM is no longer a problem, although it is still a possibilty.  I think if we can get this zeroconf/bonjour problem fixed we can at least find out if the DRM works and then tackle that problem.  I mean right now even if we get DRM working for sure, the program still doesn't run.

And even if you're no longer a student you can still use it if your e-mail address is still valid.  (I go to University of Illinois and I'm pretty sure it stays valid for at least a while after leaving)  Plus I know the local community college where I took a few classes has your e-mail address in there for years after you've left. 

Plus it's always fun solving a computer problem:-D

---

### Post by DouglasAWh on 2008-07-09
> **skoberlink said:**
>   I think if we can get this zeroconf/bonjour problem fixed we can at least find out if the DRM works and then tackle that problem.  I mean right now even if we get DRM working for sure, the program still doesn't run.

But bonjour just does the network shares right?  I wouldn't be using that.  Time for bed.  Don't plan on me helping too much until after the 21st

---

### Post by skoberlink on 2008-07-09
that's a good point.  I wouldn't be using it either.  Or even if I did I could certainly live without it.  It's hardly a necessary feature.  If there's someway to work around the neighborhood features (assuming that only means network sharing) and the DRM is fixed I'm cool with that.

I dunno...I'll continue to look into it during my spare time and we'll see what we can come up with.  Keep me up to date.

---

### Post by skoberlink on 2008-07-12
wanted to give this a bump in case anyone with new info on the problem is hanging around here.

Unfortunately haven't had much time for research. working tons of hours...

---

### Post by DouglasAWh on 2008-07-12
> **skoberlink said:**
> wanted to give this a bump in case anyone with new info on the problem is hanging around here.

Unfortunately haven't had much time for research. working tons of hours...

I doubt a bump this soon is really going to help.  The Linux community does not like DRM and thus does not like Ruckus.  Now, if there have been serious changes to Ruckus or WMP or WINE then posting that news could be helpful, but until such an event occurs I doubt we'll get a lot of new input.  My nose is also to the grind at least until July 21st.

---

### Post by MyR on 2008-08-05
from what I have read on winehq and understand about drm...

WMP will NEVER support DRM on linux using wine!

it's even the only app [used as an example for rating definitions]("http://appdb.winehq.org/help/?sTopic=maintainer_ratings"). that's how sure they are over at wine.

this of course means that ruckus in its current form will NEVER work on linux.

virtualbox however works quite nicely ;] and the [DRM can be removed from ruckus files]("http://www.unifyingtheory.net/ruckus.html").

peace

---

### Post by DouglasAWh on 2008-08-06
> **MyR said:**
> 
this of course means that ruckus in its current form will NEVER work on linux.


Which is why I said "if there have been serious changes to Ruckus or WMP or WINE then posting that news could be helpful"

I suppose by Ruckus here I meant Ruckus' DRM.  Internet Radio is serving my needs just fine.  I'm using Vista at work and with no plans to do anything differently (though certainly the desire to do so), so I'll just use Ruckus at work...where Internet Radio is against policy.

---

### Post by issueperson on 2008-08-14
This is a lot of trouble to go to just for music, but I use VirtualBox anyway to run MSOffice (don't give me crap, I'm a business student and have to have it).  So from there Ruckus was an easy install.

Listening to O.A.R. on my XP virtualbox right now with ruckus.

---

### Post by DouglasAWh on 2008-08-14
> **issueperson said:**
> This is a lot of trouble to go to just for music, but I use VirtualBox anyway to run MSOffice (don't give me crap, I'm a business student and have to have it).  So from there Ruckus was an easy install.

Listening to O.A.R. on my XP virtualbox right now with ruckus.

That's fine, but some of us don't want to pay a couple hundred dollars just to have access to listen to songs.  We could just buy some CDs for that cost.

And, I think you're kinda missing the point.  We all know we could do that (and we could pirate Windows), but we want to put our heads together and come up with something better.

For me, using Internet radio (Pandora and Lastfm) is better solution than giving Microsoft my money.

---

### Post by issueperson on 2008-08-14
> **DouglasAWh said:**
> That's fine, but some of us don't want to pay a couple hundred dollars just to have access to listen to songs.  We could just buy some CDs for that cost.

And, I think you're kinda missing the point.  We all know we could do that (and we could pirate Windows), but we want to put our heads together and come up with something better.

For me, using Internet radio (Pandora and Lastfm) is better solution than giving Microsoft my money.

whoa, a little harsh on the response there.  I thought you might just have a copy of windows laying around.  My laptop came with it installed, so I just used the old install disk.  I have to have at least a few Windows programs anyway, made this clear in my post.  No need to get all upset about it.

I have a working Ruckus, the thread is about using Ruckus while in Ubuntu.

Go ahead and put your heads together to come up with a better response.  Until then, I'm listening to my free, legal music.  I wanted to share a working solution with any of the people out there that wanted one, since in over a year no one has come up with a working solution in this thread.

So if you want to listen to Ruckus while in Ubuntu, I repeat: VirtualBox is a working option with very little hassle.  Look for a "better" solution if you want, but in my opinion the best solution is having a working Ruckus.

---

### Post by DouglasAWh on 2008-08-14
> **issueperson said:**
> 
So if you want to listen to Ruckus while in Ubuntu, I repeat: VirtualBox is a working option with very little hassle.  

This is where we disagree.  I think you are using Ruckus in Windows. 

I'm not sure why you thought I was angry.  Seems like English is your first language.  I suppose I was dismissive and perhaps I shouldn't have been so dismissive.  I suppose not everyone knows they could dual boot or have a virtual machine.  Maybe I am giving Linux users too much credit.  I assumed (and still do really) that Linux users know they can do this.

So, just to clear this up, I was never angry.  The suggestion simply is not going to work for me, and I think others feel the same as many.  Clearly not everyone feels that way though.

And let's also be clear about this.  This isn't really a moral opposition to Windows (I have one of those, but that's not my reasoning here).  I simply don't want to run a VM.  If I had to run it in Fedora I would want another solution because I use Ubuntu.  I realize sometimes VMs are needed and if you have the overhead/money to run Windows, go for it.  My Dell thankfully never came with a license for Windows.

---

### Post by MyR on 2008-08-14
eventually the music industry will move away from drm altogether.
read more on my site [here]("http://www.unifyingtheory.net/sharing.html").

peace

---

### Post by DouglasAWh on 2009-02-09
Looks like this is a non-issue now as Ruckus is dead: [http://www.ruckus.net/notice/final.html](http://www.ruckus.net/notice/final.html)

I thus promptly bought a subscription to Last.fm.  My only gripe with Last.fm is they won't let me download in .ogg.

[http://www.last.fm/user/DouglasAWh](http://www.last.fm/user/DouglasAWh)

---

