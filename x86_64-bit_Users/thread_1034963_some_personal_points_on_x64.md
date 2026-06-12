---
title: "some personal points on x64"
date: 2009-01-09
forum: x86 64-bit Users
---

### Post by tbj61898 on 2009-01-09
Hello there,
please excuse this (for some) pointless post, it contains just a fan point of view, substanstially:
- website didn't tell me that x64 is a pain in the (head) about software availability
- other troubles with x64

Some days ago I decided to replace VISTA with UBUNTU, on my main PC at home. So I went to UBUNTU website (actually ubuntu-it website, click Get UBUNTU, then I read "What kind of PC do you have?": I got a AMD64. I'm no expert here and since UBUNTU is meant to be just simple I couldn't imagine what would happen then. Little difference with english UBUNTU site, which states, before downloading UBUNTU x64: "May provide additional capabilities to computers that are able to use 64bit software"

Now please excuse my point but, when a normal user go for UBUNTU... he probably wants the simple thing, 32bit version. Compatible, simple, plain. There may be additional features, but you also get additional issues like software availability. 
Remember this is a simple user point of view: I know there are solutions, ia32 emulations and stuff but they just aren't out-of-the-box solutions like UBUNTU seems to have in plans.
How does it went with UBUNTU 64? I started FIREFOX, go Youtubbing, "hell I don't have flash player, let's get it!", Adobe website and... voilà: no 64 bit support. I googled a bit and find out there was two solutions: non-adobe players, non 64 bit browsers (with 32bit emuls). Sounds fine, let's go on.

Troubles with 64 bit?
Well I was using a laptop in living room and I decided to configure my system to let me remote login, so I used Remote Desktop Ubuntu standard solution, I got a VNC viewer in my win32 box. Well I got two clients: tightVNC and an old RealVNC. IT happened that remote desktop connection frozen after a bunch of minutes, and it happened again and again. So.. may that be a VNC-vinagre compatibility issue. But I didn't find a vinagre porting to win32 so I tried XDCMP solution and, at last, X tunnelling via SSH but there were both too slow. Too bad.

I told myself: too difficult, let's try out FEDORA. :-)

Ok.. after a couple of minutes with fedora I was downloadgin UBUNTU 32bit to give it a try. Definitely better, simpler. I just got some issues but I'm working on that.

And, guess what? VNC viewers (both) was working very good with remote desktop. At that time I realized there must be some compatibility issues with drivers/software in 64bit version,
which are not in the 32 bit version.

For the record, if it can be of some help to a dumb user like me, I suggest to just download 32bit version and let power users pick 64bit. 

My HW setup:
MB ASUS M2V
CPU Athlon64 X2
2 GB RAM (or 4? I don't remember)
WIRELESS USB WL-113
WEBCAM Lifecam VX1000 (not working yet)
PCTV 2000i Pinnacle (not working, never)
NVIDIA 7300

:popcorn: now my ubuntu 32bit rocks!

---

### Post by Kilz on 2009-01-09
Just one minor little question.


Can you provide us with a link(s) to the bug(s) reports you have either filled out or commented on for the issues you experienced?

---

### Post by tbj61898 on 2009-01-09
> **Kilz said:**
> Can you provide us with a link(s) to the bug(s) reports you have either filled out or commented on for the issues you experienced?

Sorry, my english is probably too bad for this. I didn't file a bug report 'cause I can't say this was a bug or my fault.

All this post just to say: 
1)64 bit ubuntu require extra knowledge, IMHO a bit more than a simple user (and that could be a suggestion for web descriptions of packages)
2) Same hardware and different results with remote desktop, that sounds like an issue to me but surely require extra investigation.

While point 1 is just a personal opinion I wanted to share with You, point 2 is an observed "feature" :-).

If you think this is a bug, We could join the effort and, if you know how, I can produce plenty of log files, interactions and all stuff needed to file bugs. First step could be "understand if it's due to hardware, drivers or remote desktop server", but I don't know how to make such distinction. Maybe I'm a little old-school on that but to file bug-reports one is required to provide logs, tries and stuff. 

To me it sounded like a trouble but I'm not sure if it depends on some 64 bit specific set-up (like for the flash player) and why it didn't came out on 32 bit.

Anyway if You, or others, wants to investigate on that, I'm totally available to help with time and (all my little) knowledge.

For what matters other hardware (but I'm now on 32bit ubuntu):
- MS lifecam vx1000 which should be supported but doesn't work, support request [here]("http://ubuntuforums.org/showthread.php?t=1034988")
- Pinnacle PCTV 2000i (dual dvbt), not supported.

Thank you for your answer!

Andrè

---

### Post by Thelasko on 2009-01-09
> **tbj61898 said:**
>  "hell I don't have flash player, let's get it!", **Adobe website** and... voilà: no 64 bit support. I googled a bit and find out there was two solutions: non-adobe players, non 64 bit browsers (with 32bit emuls).

[LIST=1]
[*]Going to the Adobe website is the wrong way to install software in any version of Ubuntu.  [You are supposed to use the repositories.]("http://www.psychocats.net/ubuntu/installingsoftware")  Using the repositories would install the 32-bit flash on your 64-bit browser.

[*]There is a [64-bit version of Flash]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html") that is in Alpha (testing), but it's still very good.
[/LIST]

---

### Post by phlembob on 2009-01-09
Hi tbj61898,

64 bit has not met its worth in any OS because it is still new.--- as in time.  8 bit was new at one time too.  You can look in these forums and download the 32 bit libraries under the Hardy 64 bit kernel. That will take care some of the undesired mentioned. I have all flash and have no problems watching Utube, but I'm not a junkie for it either.  Get use of your Terminal.  apt-get --- install --- sudo and bash commands are benefits not interferences and they are very useful.  Which country are you in?  Your English writing is very good so most terminal use requiring English only commands should be no problem for you.  Several little steps will get you complete with the Hardy updates available today and this should make your video viewing pleasurable.  64 bit is fine, but I have seen several persons of Pentium processors go to 32 bit.  You are AMD 64 bit so I would assume your processor is not the problem.  The AMD 64 patch should download in updates available.  Update manager in system>administrator will do the work, but you need to get the 32 bit libraries.

:guitar:  Keep jammin  --- English Slang

---

### Post by tbj61898 on 2009-01-09
> **Thelasko said:**
> 1-Going to the Adobe website is the wrong way to install software in any version of Ubuntu.  [You are supposed to use the repositories.]("http://www.psychocats.net/ubuntu/installingsoftware")  Using the repositories would install the 32-bit flash on your 64-bit browser.

That's a good advice, thanks. I probably got tricked by the adobe website and .deb file associations, which started automatically the packet manager! In that case I said to myself: whoa, that's friendliness!! :-)


> **Thelasko said:**
> 2- There is a [64-bit version of Flash]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html") that is in Alpha (testing), but it's still very good.


Yep, I knew that. I also saw a sticky post in forum but I didn't feel comfortable to start with something this early, plus I read other posts and it seems that some people got into troubles while trying to install that player version. It's all alpha disclaimer fault, I got scared! :-)


Thanks for your reply!

Andrè

---

### Post by Arup on 2009-01-09
From day one, I have used x64 Ubuntu as well as x64 XP, both from their early days, intially there were some glitches but by Hardy everything was just fine and same goes for XPx64, by SP2, it was rock solid in compatibility. x64 repos have almost everything thats needed and when on rare occasions, its not there, it can always be compiled. In case of x64 XP, WoW makes it possible to run any x32 program. Gelibs does the same for Ubuntu but one never needs them as everything thats in x32 Ubuntu is there in x64 Ubuntu. So if one has x64 CPU and 4GB+ ram, you have no choice but to run x64 OS and Ubuntu is as full fledged as they come, with Sun's latest Java, x64 Java plugin issue is gone, Adobe already fulfilled the x64 Flash issue, soon hopefully they would have x64 Shockwave as well, its inevitable, Windows and Linux world is turning x64, its high time one should come to terms with it. I remember the resilience in the days of x16, 32 bit transition was painful and a good CPU from Intel namely the P Pro suffered poor sales due to its compatibility issues with x16 OS and programs. Luckily x64 CPU runs x32 software and OS with ease. Right now I have not had to install anything out of the repos on my x64 Ubuntu except for Opera which is sadly and strangely ommited in the Ubuntu repos.

---

### Post by jespdj on 2009-01-09
> **tbj61898 said:**
> Hello there,
- website didn't tell me that x64 is a pain in the (head) about software availability
That's because it's simply not true. All software in the 32-bit Ubuntu repository is also available in the 64-bit repository. There are a few proprietary programs that are 32-bit only, such as Skype and Google Earth, but those aren't hard to install on 64-bit Ubuntu (use the [Medibuntu](http://www.medibuntu.org) repository).

Installing Flash on 64-bit Ubuntu is as easy as installing Flash on 32-bit Ubuntu: just install the package flashplugin-nonfree. On 64-bit Ubuntu, this will automatically install a wrapper to make 32-bit Flash work.

Which specific programs are you using that are not available for 64-bit?

You're making things more difficult for yourself than they need to be, and you're blaming problems on the 64-bit version while you have no idea if it's because it's 64-bit or because of something totally different.

---

### Post by tbj61898 on 2009-01-09
> **phlembob said:**
> You can look in these forums and download the 32 bit libraries under the Hardy 64 bit kernel. 

I was just reading some reports about 64 bit ubuntu system, compared with 32 bit one, links on the sticky posts in this forum. I think I can shrink a bit the ubuntu32 partition and let an ubuntu64 fit in. That way I can introduce my girl to a stable and simple 32bit ubuntu, while I can practice myself with the 64bit stuff in spare time!

> **phlembob said:**
> Which country are you in?  Your English writing is very good so most terminal use requiring English only commands should be no problem for you.


Thanks, I'm from Milan, Italy! Online traslators help me a lot here... but some stuff are just tricky to explain in my original language! :-)

Andrè

---

### Post by Kilz on 2009-01-09
> **tbj61898 said:**
> Sorry, my english is probably too bad for this. I didn't file a bug report 'cause I can't say this was a bug or my fault.

All this post just to say: 
1)64 bit ubuntu require extra knowledge, IMHO a bit more than a simple user (and that could be a suggestion for web descriptions of packages)
2) Same hardware and different results with remote desktop, that sounds like an issue to me but surely require extra investigation.

While point 1 is just a personal opinion I wanted to share with You, point 2 is an observed "feature" :-).

If you think this is a bug, We could join the effort and, if you know how, I can produce plenty of log files, interactions and all stuff needed to file bugs. First step could be "understand if it's due to hardware, drivers or remote desktop server", but I don't know how to make such distinction. Maybe I'm a little old-school on that but to file bug-reports one is required to provide logs, tries and stuff. 

To me it sounded like a trouble but I'm not sure if it depends on some 64 bit specific set-up (like for the flash player) and why it didn't came out on 32 bit.

Anyway if You, or others, wants to investigate on that, I'm totally available to help with time and (all my little) knowledge.

For what matters other hardware (but I'm now on 32bit ubuntu):
- MS lifecam vx1000 which should be supported but doesn't work, support request [here]("http://ubuntuforums.org/showthread.php?t=1034988")
- Pinnacle PCTV 2000i (dual dvbt), not supported.

Thank you for your answer!

Andrè

After reading that through explanation, I have no fear that you could fill out a bug report. [I also recommend reading this page. ]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by Thelasko on 2009-01-09
> **tbj61898 said:**
> That's a good advice, thanks. I probably got tricked by the adobe website and .deb file associations, which started automatically the packet manager! In that case I said to myself: whoa, that's friendliness!! :-)
Yeah, This is something new that most of us old Ubuntu users (if you can call a year and a half old) don't realize.  Youtube now links to the Adobe site for the Flash plugin, and provides a nice .deb package that most people install.  It wasn't always this easy, but it's the wrong way to do it.  If you would have clicked the information bar that popped up at the top of your browser, Firefox would have installed Flash the correct way automatically.
> 
Yep, I knew that. I also saw a sticky post in forum but I didn't feel comfortable to start with something this early, plus I read other posts and it seems that some people got into troubles while trying to install that player version. It's all alpha disclaimer fault, I got scared! :-)
The alpha disclaimer is there for a reason.  Plus, it's significantly more difficult to install due to the fact it's not a .deb file.  You have to place the file in the correct directory and make sure it has the correct permissions.

I'm betting Jaunty will have the new 64-bit plugin in the repositories to make it easily available to everyone.

---

### Post by tbj61898 on 2009-01-09
> **jespdj said:**
> That's because it's simply not true. All software in the 32-bit Ubuntu repository is also available in the 64-bit repository. There are a few proprietary programs that are 32-bit only, such as Skype and Google Earth, but those aren't hard to install on 64-bit Ubuntu (use the [Medibuntu](http://www.medibuntu.org) repository).

Sorry to disappoint you. Powerpoint viewer is only 32bit, in repository. After selecting it for download it says: sorry, You can't install it because it's for 32bit version, check again soon.


> **jespdj said:**
> Installing Flash on 64-bit Ubuntu is as easy as installing Flash on 32-bit Ubuntu: just install the package flashplugin-nonfree. On 64-bit Ubuntu, this will automatically install a wrapper to make 32-bit Flash work. 

Thanks, some other users in this forum were pointing me to that solution, thanks. There's also an alpha version from adobe but I got a bit scared by the disclaimer!

> **jespdj said:**
> Which specific programs are you using that are not available for 64-bit?

Powerpoint viewer, as told. At first it seems that Adobe wasn't providing a stable 64bit flash player version (source: adobe flash player download page). My fault I didn't check repositories but I told to myself: "If it's not on official flash player provider... there's no official 64bit stable version!"


> **jespdj said:**
> You're making things more difficult for yourself than they need to be, and you're blaming problems on the 64-bit version while you have no idea if it's because it's 64-bit or because of something totally different.

Well I admit my knowledge is not this wide, but I'm running fine with the 32bit version, now. This means I lack some experience and knowledge in the gap between the two, but I didn't know I needed some extra experience here. So now I know and I'm planning a little ubuntu64 installation to see how things gets going with it.

Thanks for your reply!

Andrè

---

### Post by tbj61898 on 2009-01-09
> **Kilz said:**
> After reading that through explanation, I have no fear that you could fill out a bug report. [I also recommend reading this page. ]("http://linux.oneandoneis2.org/LNW.htm")

As soon as I get ubuntu64 back in the disk (shrinking a bit ubuntu32 partition) I'll sure do some research!

Thanks for the link!

Andrè

---

### Post by Arup on 2009-01-10
Some corrections here, Picasa, Google Earth and Skype are all x64 now.

---

### Post by hyperdude111 on 2009-01-10
To get ALL the codecs without any hassle (flash,mp3,divx,mp4) you just go to terminal and type 

sudo apt-get install ubuntu-restricted-extras 

Dont bother with adobe their website provides NO help with 64 bit flash.

---

### Post by Arup on 2009-01-10
> **hyperdude111 said:**
> To get ALL the codecs without any hassle (flash,mp3,divx,mp4) you just go to terminal and type 

sudo apt-get install ubuntu-restricted-extras 

Dont bother with adobe their website provides NO help with 64 bit flash.

If I am not mistaken, by doing so, it would also install x32 version of Flash, now that x64 Flash is out, no need for nsplugin and x32 Flash. To get all codecs, go to add/remove and enable all software and check everything marked with gstreamer, thats all.

---

### Post by steveneddy on 2009-01-10
Well, since you aren't actually asking a support question, I will say that you are the one who must choose to run either 32 bit or 64 bit Ubuntu. Running 64 bit Ubuntu is not any more difficult than running the 32 bit version of Ubuntu.

The web site didn't make you download and install the 64 bit version of Ubuntu and I believe that the 32 bit version is just as available as the 64 bit version.

I actually have been running 64 bit Ubuntu for over a year and I don't have any issues with software. If it's not offered in 64 bit and not in the repos I will compile it from source.

Ubuntu, and Linux of any flavor for that matter, isn't Windows. It doesn't behave like Windows and never will.

If you aren't happy with the 64 bit version and you think that the 32 bit will be easier for you then by all means install the 32 bit version.

The rest of us will run 64 bit and actually file bugs when issues occur.

With a little clicking around on this forum, namely the first few stickies at the top of this forum, you will find most of the instructions for installing software that you need.

Also check out the links in my sig. I hope they help you find what you are looking for.

And please don't make this harder than it has to be. Just read the instructions and pay attention. You are going to learn something new and you have to go into this new OS you want to run and embrace the learning process for a little bit.

---

### Post by xebian on 2009-01-10
> **tbj61898 said:**
> 
...
Yep, I knew that. I also saw a sticky post in forum but I didn't feel comfortable to start with something this early, plus I read other posts and it seems that some people got into troubles while trying to install that player version. It's all alpha disclaimer fault, I got scared! :-)

....
Andrè

You shouldn't be.  The 64-bit version is using the same code base as the stable 32-bit.  Only now it's compiled in 64-bit to run natively in 64-bit OS.

---

### Post by tbj61898 on 2009-01-10
Thanks everybody. I think this little thread has helped me to understand  and clarify the whole thing... and sorry if the initial post wasn't really.. 64-bit friendly!

---

### Post by jespdj on 2009-01-10
> **tbj61898 said:**
> Sorry to disappoint you. Powerpoint viewer is only 32bit, in repository. After selecting it for download it says: sorry, You can't install it because it's for 32bit version, check again soon.
Powerpoint viewer? Is this a special Linux PP viewer? You can open PowerPoint presentations with OpenOffice, so you don't need that program.

Also, if this is an open source program that's from the official Ubuntu repository and it's only available in the 32-bit version, you should [add a bug report](https://bugs.launchpad.net/ubuntu) to ask for a 64-bit version.

And note that 32-bit software also runs on 64-bit Ubuntu; if you have the *.deb package for that PowerPoint viewer, you can force it to install with a command like this:
```
sudo dpkg -i --force-architecture filename.deb
```
You might need to install 32-bit libraries after that to get it to work; the [getlibs](http://ubuntuforums.org/showthread.php?t=474790) script can make this easy.

---

