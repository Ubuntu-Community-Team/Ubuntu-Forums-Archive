---
title: "Any serious issues with 64bit Ubuntu?"
date: 2006-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by mmcmonster on 2006-07-10
Hi.
  I've been using Ubuntu on a couple machines for about a year now.  I'm getting my first 64 bit machine in a couple days, and was wondering it I should install 32 bit Ubuntu or 64 bit.  Any suggestions?

I presume that installing 32 bit Ubuntu is an option, right?

Are there any serious issues with running 64 bit Ubuntu?

P.S. I know about the firefox/Flash issue, and will probably end up with the 32 bit version of firefox.

---

### Post by jvictor on 2006-07-10
If u read pdfs u will miss the adobe reader
Some apps dont work well on 64 bit , eg_; when i tried a cpl of weeks back gnomebaker crashed.. i use bonfire.. 

To be honest I dont find any big perf difference in commonly used apps.. well in mulitmedia it maybe a different story :) 

Im waiting for the platform to mature to try and switch to it.. right now, IMHO hardware has outrun software on the 64 bit platform

---

### Post by mmcmonster on 2006-07-10
Thanks.
  I'll probably end up using a 32 bit installation.  I really don't want to hit oo many hiccups.  I want the system running without administration (outside of my administration, at least).  Besides, hardware is fast enough that I won't worry about the performance hit much.

---

### Post by dasyar613 on 2006-07-10
I just installed unbuntu amd64 on my acer 5002, and I have not found any serious issues at all. I still do not understand what the fuss is all about with the issue of running it in 64 bit. I figure if I have a 64 bit machine then I will use that. Although I have only been using for a couple of days now, maybe some of the longer users can jump in, and enlighten us. So far I am very pleased with the way the ubuntu amd64 is running on my machine.

---

### Post by Kilz on 2006-07-10
> **jvictor said:**
> If u read pdfs u will miss the adobe reader
Some apps dont work well on 64 bit , eg_; when i tried a cpl of weeks back gnomebaker crashed.. i use bonfire.. 
I have adobe acrobat installed, I even have the firefox plugin. What was the reason gnomebaker crashed? 

> To be honest I dont find any big perf difference in commonly used apps.. well in mulitmedia it maybe a different story :) You are right, encoders run 30% faster. 

> Im waiting for the platform to mature to try and switch to it.. right now, IMHO hardware has outrun software on the 64 bit platform
Persoanlly I run 64bit and have no problems at all, I didnt give up. Of the software avaiable 97% of the time its apt-get/synaptic. Another 2% needs a cut/paste howto. 1% needs some extra work. Nothing is impossible to use or is missing.

> **dasyar613 said:**
> I just installed unbuntu amd64 on my acer 5002, and I have not found any serious issues at all. I still do not understand what the fuss is all about with the issue of running it in 64 bit. I figure if I have a 64 bit machine then I will use that. Although I have only been using for a couple of days now, maybe some of the longer users can jump in, and enlighten us. So far I am very pleased with the way the ubuntu amd64 is running on my machine.
IMHO this is how it goes.
Some people have the idea that they need to have everything working with a few clicks or a few lines in the cli. For the most part that's true of the amd64 bit version. But there can be problems. Sometimes you have to follow a howto, sometimes you have to fix a problem application. Same as the switch from Windows to Linux.
Just like switching from Windows to Linux there are differences. There are differences when switching from 32bit to 64bit. You cant run automatrix to do all the setup for you. You have to follow a howto to get Firefox running right. You have to follow a howto for wine. Some people just don't want to, or cant.
The people who fail then go on to tell others how hard it is, or 64bit isn't ready yet. They think that if they fail, then everyone will. They don't realize that the one thing they think is a must have, isn't a must have to everyone else. That or the bug they experienced can be fixed, or other software can do the job.
The worst of the FUD comes from people who ran 64bit Breezy. I will admit, 64Bit Breezy was not ready, it had some major issues. But Dapper is a whole new ballgame.

---

### Post by hajk on 2006-07-10
I second what Kilz said. I did install both 32-bit and 64-bit Dapper, fully expecting to use the 32-bit version as my main OS and the 64-bit version to play around with, because of the "many perceived problems with 64-bit". But, in practice, I only use the 64-bit version and am thinking of replacing the 32-bit with 64-bit Edgy. 

W.r.t. listening to streaming audio, I've switched to a choice of radio stations broadcasting in OGG (didn't know there were that many). The SWF flash plugin for 64-bit Firefox is good enough that it lets me do my banking on-line (where the bank's website warns that the site is optimized for Macromedia Flash). And as others have already said: Acrobat Reader runs in 32-bit compatibility mode (although Evince has improved quite a bit since the version included in Breezy, and is now almost on a par with acroread IMHO).

I will never install another 32-bit OS.:)

---

### Post by caravela on 2006-07-10
you can install a 32 bit dapper in a chroot inside the dapper 64bit for the applications that doesn't run or doesn't exist for 64 bit like allmost all comercial stuff. [http://www.ubuntuforums.org/showthread.php?t=24575]("http://www.ubuntuforums.org/showthread.php?t=24575")

---

### Post by Kilz on 2006-07-10
> **caravela said:**
> you can install a 32 bit dapper in a chroot inside the dapper 64bit for the applications that doesn't run or doesn't exist for 64 bit like allmost all comercial stuff. [http://www.ubuntuforums.org/showthread.php?t=24575]("http://www.ubuntuforums.org/showthread.php?t=24575")
Yes you can, in some cases it may be a good option. But it isnt as nessasary in Dapper as it was in Breezy. Dapper for the most part runs 32bit programs without a chroot. If you are going to set one up. [I reccomend this post]("http://ubuntuforums.org/showthread.php?p=904320"). The setup script will have one setup in minutes.

---

### Post by jvictor on 2006-07-11
> You cant run automatrix to do all the setup for you. 

Neither would I want to use stuff from some repo thats not official. Its easier but I may prefer to stick with the repos ubuntu gives. Its my choice. Im under no compulsion.

> 
You have to follow a howto to get Firefox running right. You have to follow a howto for wine. Some people just don't want to, or cant.

Which is exactly the same as patching and running your system over _UNWANTED_ layers, For me, I get the feeling of moving about with a trouser whose rear is torn and a kerchief is used to cover up ... I would prefer a system without half-baked patches , hacks and workarounds ...

> 
The people who fail then go on to tell others how hard it is, or 64bit isn't ready yet. 

Thats completely your perception.. 


> They think that if they fail, then everyone will. 

I strongly disagree.. I've been with Linux from the time redhat started off.. and things were much tougher to set-up ... its much easier on Ubuntu.. and u expect it to be easier since Linux has moved on quite a bit.

> 
They don't realize that the one thing they think is a must have, isn't a must have to everyone else. That or the bug they experienced can be fixed, or other software can do the job.

Which is why there exists something called as a **bug_report** which takes time to get resolved.. You cant wait till the bug gets resolved when you are using it as ur primary and sole OS.


> 
The worst of the FUD comes from people who ran 64bit Breezy. I will admit, 64Bit Breezy was not ready, it had some major issues. But Dapper is a whole new ballgame.

Is'nt it because you failed to run breezy, what about the ones who managed to run it ?!! 

What I meant was there wont be a seamless install like that of a 32 bit one .. and 64 bit is ***NOT_YET** ready to be a complete_seamless_replacement as your primary_and_sole OS. The reasons can be many though..including vendor apathy towards the 64 bit community .. Even MS 64 bit is not completely suitable as a desktop even though the have the strongest lobby with all hardware & software vendors...

---

### Post by dasyar613 on 2006-07-11
I had a chance to install and run Vista Beta 2 ... 64 bit version, I was somewhat impressed. I also had a chance to install XP 64 bit version, now that was a dog. As I have mentioned in other posts here, I really like ubuntu amd64, and I have to reiterate, I am quite pleased with it. 

I did notice one thing, in all the posts, the people that are trying to install and run the intel 64 bit chips, are having a tougher go of it. It may be just a coincedence. But, all in all, I have not seen the issues that are being posted here. I hope, after posting that, my system does not crap out on me.

---

### Post by Kilz on 2006-07-11
> **jvictor said:**
> Neither would I want to use stuff from some repo thats not official. Its easier but I may prefer to stick with the repos ubuntu gives. Its my choice. Im under no compulsion.
Automatrix doesnt use 100% official repositories. The howto's I have written use programs strait from the programs site, Like Firefox, or strait from Ubuntu mirrors.

> Which is exactly the same as patching and running your system over _UNWANTED_ layers, For me, I get the feeling of moving about with a trouser whose rear is torn and a kerchief is used to cover up ... I would prefer a system without half-baked patches , hacks and workarounds ... So you would prefer to run a 32bit OS on a 64bit system. Some of us would rather not. If you don't want to fine. But don't come here and spread misinformation. The howto's use Ubuntu packages. Not half baked hacks.

> That's completely your perception.. Thanks for continuing to prove me right.

> I strongly disagree.. I've been with Linux from the time redhat started off.. and things were much tougher to set-up ... its much easier on Ubuntu.. and u expect it to be easier since Linux has moved on quite a bit.So the hard setup and work arounds were fine back then, but now they are not. Right........

> Which is why there exists something called as a **bug_report** which takes time to get resolved.. You cant wait till the bug gets resolved when you are using it as ur primary and sole OS.Thats why there are howto's. To fix things while waiting for the developers to sort things out. You know, Howto's, they even have their own section of the forum.

> Is'nt it because you failed to run breezy, what about the ones who managed to run it ?!! 

What I meant was there wont be a seamless install like that of a 32 bit one .. and 64 bit is ***NOT_YET** ready to be a complete_seamless_replacement as your primary_and_sole OS. The reasons can be many though..including vendor apathy towards the 64 bit community .. Even MS 64 bit is not completely suitable as a desktop even though the have the strongest lobby with all hardware & software vendors...
Thanks for the long winded spiel. I never said Breezy was unusable. I said there was a world of diffrence between 64bit  Breezy and 64bit Dapper. On 64bit Breezy you could not run 32bit paalications without a chroot. On dapper it is entirly possible without a chroot.
The AMD64 version of Ubuntu Dapper is ready for use. You just had some problems. So now you are posting that it isn't ready, when lots of other people are running it just fine.
If you don't want to run it , fine, but don't come into the 64bit section and tell people that 64bit isn't ready based on your experiences. Don't compare 64bit Dapper to Windows, or 64bit Breezy. Because it is neither.
I'm not the only one who thinks 64bit Dapper is great. I'm not the only one with 64bit howtos to make things run. I'm not the only one helping people realize that they don't have to run a 32bit OS on their 64bit system.
Sadly you aren't the only one who thinks they know whats right for other people. Sadly you aren't the only one who wants to be negative. Sadly you aren't the only one spreading FUD.
But do all the people doing what they can to help others a favor. Go spread the FUD someplace else.

---

### Post by charlier653 on 2006-07-12
I just installed Ubuntu 64 on my box a couple days ago. I've never had any dealings with linux of any flavor before this, and an happy with the performance on my machine, although there is one thing that seems to have a small problem:

when i tried to add a repo to the list, the profgram hung on me.....totasl freeze. other thatn that and not knowing anything, it seems to be working just fine.

comp stats:

Gigabyte GA K8U ULi M 1689 MB
AMD sempron 64 3400+
EVA nVidia GeForce 5500
3x 512Mb ddr333 ram
:eek: :eek: :-? :-?

---

### Post by Kilz on 2006-07-12
> **charlier653 said:**
> I just installed Ubuntu 64 on my box a couple days ago. I've never had any dealings with linux of any flavor before this, and an happy with the performance on my machine, although there is one thing that seems to have a small problem:

when i tried to add a repo to the list, the profgram hung on me.....totasl freeze. other thatn that and not knowing anything, it seems to be working just fine.

comp stats:

Gigabyte GA K8U ULi M 1689 MB
AMD sempron 64 3400+
EVA nVidia GeForce 5500
3x 512Mb ddr333 ram
:eek: :eek: :-? :-?
Freezing, or a crash can happen on any version. I added a force quit icon to my taskbar in case it happens.

---

