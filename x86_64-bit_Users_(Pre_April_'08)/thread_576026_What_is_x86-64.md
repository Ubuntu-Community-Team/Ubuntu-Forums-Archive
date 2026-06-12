---
title: "What is x86-64?"
date: 2007-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Yes on 2007-10-14
I was looking into building a computer, and I would like to use an Intel Core 2 Duo processor.  It has "x86-64", and I was wondering what that meant.  I asked about it a few weeks ago, and someone told me that it means that it can run both 32 and 64 bit applications.  But then I found this forum, and I assume that if it has it's own forum, it's not that simple, is it?

Thanks.

---

### Post by Tyche on 2007-10-14
Yes,

I'm running a Core Dual (Dell Inspiron 530n).  It came installed with Feisty Faun, 32 bit.  I'm currently running Gutsy Gibbon Beta 64 bit.  So yes, it can handle both.  The thing you might want to consider is that not all applications are ported to 64 bit, and some of them don't respond well as a 32 bit app in a 64 bit environment.  This is getting better, and I haven't had any trouble, but you might want to look around the forums for further information.

Hope this helps.

---

### Post by Sef on 2007-10-14
> The thing you might want to consider is that not all applications are ported to 64 bit ....

For that reason, I would recommend that you start with the 32-bit Ubuntu.  Once you get comfotable with it, or the 64-bit apps come out, then switch.

---

### Post by Yes on 2007-10-14
Thank's, that helps a lot.  So basically it can run both, but not all 32 bit apps run well in a 64 bit environments, and vice-versa?  How would you set what environment you used?  Would it be determined on what bit the operating system is?

---

### Post by Tyche on 2007-10-14
It depends on what you install.  The normal i386 distribution is 32 bit.  There is an AMD64bit distribution (which is what I am running as Gutsy) that is the 64 bit environment.  So your environment is pretty much dependent on the distribution.  Why don't you try the 32 bit first, and get used to how it handles.  Then, if you have another partition that you can load the 64 it distro on, you can play with it and see what differences there are.  I haven't noticed a lot of difference between them (I think the speed difference is too small for me to measure by eye).  But there are times when I can see that both processors are working.

---

### Post by John.Michael.Kane on 2007-10-14
@Yes you will get varying views on what architecture you should run. Some feel 64bit has no merit or offers little advantage over running 32bit etc. What is usually suggested in this part of the forum to users who are new to 64bit Ubuntu Is to run it for 30days on a separate partition, and make use of the guides made for this architecture.

IMHO both software architectures have their upsides, As well as their downsides. In the end the user will have to make the choice of what is right for them,and their needs.

---

### Post by Kilz on 2007-10-14
> **Sef said:**
> For that reason, I would recommend that you start with the 32-bit Ubuntu.  Once you get comfotable with it, or the 64-bit apps come out, then switch.

If you think that there are applications missing you may have been misinformed. At present,  according to launchpad there is no difference in available packages between i386 and AMD64 for Feisty and Gutsy. There was a difference in Edgy, but that information is out of date.
Also there is no real difference in the installation of the 2, nor are there more problems. Every new user will have a learning curve. Advising them in this way leads to misinformation that there are difficulties where none exist.

> **Tyche said:**
> It depends on what you install.  The normal i386 distribution is 32 bit.  There is an AMD64bit distribution (which is what I am running as Gutsy) that is the 64 bit environment.  So your environment is pretty much dependent on the distribution.  Why don't you try the 32 bit first, and get used to how it handles.  Then, if you have another partition that you can load the 64 it distro on, you can play with it and see what differences there are.  I haven't noticed a lot of difference between them (I think the speed difference is too small for me to measure by eye).  But there are times when I can see that both processors are working.
I386 is not the "normal" distribution, neither is 64bit the abnormal. You are making it sound like there is some problem with the amd64 bit version. While this may not be your intent, you may end up scaring away users based on that.

---

### Post by Tyche on 2007-10-14
> **Kilz said:**
> 
I386 is not the "normal" distribution, neither is 64bit the abnormal. You are making it sound like there is some problem with the amd64 bit version. While this may not be your intent, you may end up scaring away users based on that.

Kilz,

You have a valid point, and I may have used a poor choice of words.  64 bit is certainly not abnormal, and I don't consider it as such (especially as it saved me from a mess when I had a problem with my Feisty partition that ran 32 bit.  Long story, and not apropos to this situation.)  My intent was for Yes to start with what he was familiar with, and on another partition set up 64 bit for comparison.  I regularly have an "active" partition (being the partition that I use as a stable base) and a "playground" partition, where I can try new things.  Very often "active" and "playground" end up trading places, as I become more comfortable and confident with them (that will be the case with Gutsy final).  It also gives me a way to get in and fix things when they go wrong, by simply booting to the other partition.  Last resort is booting off of a LiveCD and going from there (which is what I did, yesterday).  :-)

---

### Post by Kilz on 2007-10-14
> **Tyche said:**
> Kilz,

You have a valid point, and I may have used a poor choice of words.  64 bit is certainly not abnormal, and I don't consider it as such (especially as it saved me from a mess when I had a problem with my Feisty partition that ran 32 bit.  Long story, and not apropos to this situation.)  My intent was for Yes to start with what he was familiar with, and on another partition set up 64 bit for comparison.  I regularly have an "active" partition (being the partition that I use as a stable base) and a "playground" partition, where I can try new things.  Very often "active" and "playground" end up trading places, as I become more comfortable and confident with them (that will be the case with Gutsy final).  It also gives me a way to get in and fix things when they go wrong, by simply booting to the other partition.  Last resort is booting off of a LiveCD and going from there (which is what I did, yesterday).  :-)

Thats just it., imho the differences between the 64bit and 32bit are not that significant that someone familiar with Linux would have a problem. Sudo is the same, the file system is the same, commands are the same, they both use deb files, ect. Those that dont know linux would not know enough to recognize a difference. 
What people install is most often what they keep using, add to that the fact that you need to do a complete reinstall to move from a 32 to a 64bit install it may be easier and more efficient to start with 64bit. Since the world is moving to 64bit (either slow or fast) I think its time we stop recommending people take a step backwards.
Since both have their problems (32bit and 64bit) and there are advantages to 64bit. I think we should recommend 64bit from the start. If someone has a stable install they should keep it as you suggest, but those starting out should bypass the problems that can happen to 32bit installs. 32bit is not perfect. There is no guarantee that the new user or even the experienced user on new hardware will have a problem free 32bit install. because a lot of the time after working hard to install one version few are going to be willing to do the same thing again.

---

### Post by Keith_Beef on 2007-10-14
> **Tyche said:**
> The thing you might want to consider is that not all applications are ported to 64 bit, and some of them don't respond well as a 32 bit app in a 64 bit environment. 

I'll be building a system round an Intel Q6600 SLACR as soon as the parts arrive (looks like being Tuesday 16 October 2007).

I am sure that some commercial apps that I have are going to cause problems in the 64 bit world. I don't need Applixware much these days, and SimCity 3000 Unlimited stopped working again a couple of kernel releases ago.

[SIZE="1"](I don't remember when it got obstinate again... It stopped working once before, I found a fix for it, but this fix no longer works)[/SIZE]

But some other commercial apps will fail. Adobe products (Flash players, PDF viewers, whatever else Adobe buys up) will probably not get ported for a long time. And then, the ports will be buggy and have no support. So no change there, then, on Adobe's part.

Chase the big market share, that's all... And Adobe doesn't even get *that* simple goal right all the time, as FrameMaker users know to their despair.

It's a big shame Adobe never supported FrameMaker on Linux past the limited trial version (I think it was FM 5.2beta). That would have been an opportunity for Adobe to completely re-write the app from the ground up, building in a more modular, expandable way. That would have made Unicode a possibility years ago... until having to wait until this year's FM 8 to finally go to Unicode.

But I'm drifting off topic.

32 bits good, 64 bits good also. But if you use many commercial apps, keep a 32 bit system installed, too, as a (hopefully) temporary fallback.

Beef.

---

### Post by Kilz on 2007-10-14
> **Keith_Beef said:**
> I'll be building a system round an Intel Q6600 SLACR as soon as the parts arrive (looks like being Tuesday 16 October 2007).

I am sure that some commercial apps that I have are going to cause problems in the 64 bit world. I don't need Applixware much these days, and SimCity 3000 Unlimited stopped working again a couple of kernel releases ago.

[SIZE="1"](I don't remember when it got obstinate again... It stopped working once before, I found a fix for it, but this fix no longer works)[/SIZE]

But some other commercial apps will fail. Adobe products (Flash players, PDF viewers, whatever else Adobe buys up) will probably not get ported for a long time. And then, the ports will be buggy and have no support. So no change there, then, on Adobe's part.

Chase the big market share, that's all... And Adobe doesn't even get *that* simple goal right all the time, as FrameMaker users know to their despair.

It's a big shame Adobe never supported FrameMaker on Linux past the limited trial version (I think it was FM 5.2beta). That would have been an opportunity for Adobe to completely re-write the app from the ground up, building in a more modular, expandable way. That would have made Unicode a possibility years ago... until having to wait until this year's FM 8 to finally go to Unicode.

But I'm drifting off topic.

32 bits good, 64 bits good also. But if you use many commercial apps, keep a 32 bit system installed, too, as a (hopefully) temporary fallback.

Beef.

Flash works just fine on 64bit, in fact in Gutsy its a new "Just Works" feature that can be installed from the repositories. It will work in feisty, and [there is a install script that will take 30seconds]("http://ubuntuforums.org/showthread.php?t=476924"). [Acrobat (32bit) works on 64bit also]("http://ubuntuforums.org/showthread.php?t=571506").
We as 64bit users fight a constant battle of disproving the things dont work misinformation.  In fact all 32bit linux applications should run fine on a 64bit install. Some may require setup. But the number the average user may need can be counted on the fingers of one hand, remember thats may, because they may not need them. Evince is a great pdf reader. Lots of people never install acrobat because there is a great free application that works.
As for SimCity3000, thats a windows game. It should run under wine. But thats another issue as windows applications sometimes have problems even under 32bit linux.

So no, users do not need to keep or install a 32bit install.

---

### Post by magikx21 on 2007-10-15
While I prefer 64-bit over 32-bit I will not call them equal. With 64-bit you may have to search a little harder for things not included in the OS automatically. 64-bit packages can be difficult to find at times since 64-bit hasn't been adopted by the majority yet. Also while yes there are workarounds for compatibility issues such as those with Java and Flash the fact is they are workarounds and yes they are simple but doing them without a workaround is easier. The way I see it though is if your adventurous enough to use Linux then you are adventurous enough for 64-bit. If you got the processor use it. :)

---

### Post by rsambuca on 2007-10-15
> **magikx21 said:**
> While I prefer 64-bit over 32-bit I will not call them equal. **With 64-bit you may have to search a little harder for things not included in the OS automatically. 64-bit packages can be difficult to find at times since 64-bit hasn't been adopted by the majority yet**... 

Might I ask what "things" are not included with the 64bit installation that are not included in the 32 bit OS?

Also, what specific 64bit packages have been difficult to find?  I know there are some, but I have never had a problem.

---

### Post by magikx21 on 2007-10-15
The packages that I spoke of are not in either 32-bit or 64-bit but are harder to find for 64-bit. Such as the new version of Pidgin. I found a number of repositories for the 32-bit version before find one for the 64-bit version.

---

### Post by Kilz on 2007-10-16
> **magikx21 said:**
> The packages that I spoke of are not in either 32-bit or 64-bit but are harder to find for 64-bit. Such as the new version of Pidgin. I found a number of repositories for the 32-bit version before find one for the 64-bit version.

One of the best things about Ubuntu is the large amount of packages (20k+)in the repositories. While there may be some things you cant find, if they are popular they get added. Pidgin is now available in the Gutsy repos.
Even so, while it sometimes scares new users one of the strengths of open source is the ability to compile applications. A simple ./configure, then make, then sudo make install and you have the latest version installed. Most of the time in less time than it takes to look for a package.

---

### Post by Keith_Beef on 2007-11-03
Well, I take back my assertion that there would be many broken apps in the 64-bit version.

I got my AMD64 Desktop CD from [The Linux Store]("http://www.thelinuxstore.ca/") and booted from it.

The live version worked fine, and I was using that to post to a few websites while the install was going on.

Everything worked "straight out of the box"... except for a few "extras" that I needed to hunt down so I could play DVD movies.

I've still not tried out everything, but what I have tried works.

Beef

---

### Post by LavianoTS386 on 2007-11-03
> **magikx21 said:**
> The packages that I spoke of are not in either 32-bit or 64-bit but are harder to find for 64-bit. Such as the new version of Pidgin. I found a number of repositories for the 32-bit version before find one for the 64-bit version.

Really? Cause I found the opposite. I'm still waiting for 2.2.2 for my 32-bit laptop.

---

### Post by s_spiff on 2007-11-03
Well, with all the talk of x64 not being for newbs and all...proud to say that I started off with x64 ...and still am on x64, learnt everything I know about linux on x64. 
Like Kliz says, almost everything is there in the repo's, although, not always the latest versions, but you can find the source online, and just do the ./configure ( like the latest BFWesnoth , damn that game rules! )

---

### Post by dcstar on 2007-11-05
> **rsambuca said:**
> Might I ask what "things" are not included with the 64bit installation that are not included in the 32 bit OS?

Also, what specific 64bit packages have been difficult to find?  I know there are some, but I have never had a problem.

I have a problem with some Brother printer i386 debs that don't seem to work on my 64 bit system (even when installed with the "force" option), and the Java issue is still not fully resolved with the Icedtea alternative, but other than that the issues are very minor for me now.

---

### Post by PmDematagoda on 2007-11-05
> **dcstar said:**
> I have a problem with some Brother printer i386 debs that don't seem to work on my 64 bit system (even when installed with the "force" option), and the Java issue is still not fully resolved with the Icedtea alternative, but other than that the issues are very minor for me now.

I could say the same thing, I did mess up my first 64 bit install of Ubuntu, but I have learned loads during that brief time and now I am pretty happy except for the fact that I am missing Skype but I don't really care about that. And Java iced tea is not perfect but is rather satisfactory and it would improve, but one thing, Iced Tea cannot be used to run other Java applications properly other than Firefox for which I have to switch to another JRE. And the installation of Flash has been improved on 7.10.

---

### Post by rsambuca on 2007-11-05
> **PmDematagoda said:**
> I could say the same thing, I did mess up my first 64 bit install of Ubuntu, but I have learned loads during that brief time and now I am pretty happy except for the fact that I am missing Skype but I don't really care about that. And Java iced tea is not perfect but is rather satisfactory and it would improve, but one thing, Iced Tea cannot be used to run other Java applications properly other than Firefox for which I have to switch to another JRE. And the installation of Flash has been improved on 7.10.

Skype works perfectly on the 64bit version.  [Details.]("http://ubuntuforums.org/showthread.php?t=432295&highlight=skype")

---

### Post by PmDematagoda on 2007-11-05
Yes, that was one of the tutorials I read, but I get a warning from Synaptic that linux32 can be harmful, is this true? I would have done it anyway if it wasn't for the fact that I want my Ubuntu 64 one as stable as possible.

---

### Post by rsambuca on 2007-11-05
I never received that warning message.  Are you sure you have all of your keys for the repos?  Anyways, it is from the standard Ubuntu repos, so you don't have to worry.

---

### Post by veritas366 on 2007-11-05
I find this discussion interesting.  I can't get Java plugin to work with Firefox on my AMD64...even with Blackdown.  I don't have a dog in this hunt but java isn't trivial, so how can someone say that amd64 is not harder to use?  I just hate when requests for assistance turn into little debates like this.  Evidently, at least for the java plugin for firefox, the 64 bit is harder to use...so let's admit that and move on to some (easier) solutions.

---

### Post by rsambuca on 2007-11-05
> **veritas366 said:**
> I find this discussion interesting.  I can't get Java plugin to work with Firefox on my AMD64...even with Blackdown.  I don't have a dog in this hunt but java isn't trivial, so how can someone say that amd64 is not harder to use?  I just hate when requests for assistance turn into little debates like this.  Evidently, at least for the java plugin for firefox, the 64 bit is harder to use...so let's admit that and move on to some (easier) solutions.

Just run [Kilz's script]("http://www.ubuntuforums.org/showthread.php?t=202537&highlight=java") to get everything working.  Not too hard.

---

### Post by veritas366 on 2007-11-05
Well, I think I mentioned that the original post about the script was confusing...it appears, for example, to bring in Flash which is no longer needed for Gutsy.  And all the other stuff on there...I just want Java.  And with 116 pages of responses, I'm guessing it's not as straightforward as it is supposed to be.

---

### Post by rsambuca on 2007-11-05
> **veritas366 said:**
> Well, I think I mentioned that the original post about the script was confusing...it appears, for example, to bring in Flash which is no longer needed for Gutsy.  And all the other stuff on there...I just want Java.  And with 116 pages of responses, I'm guessing it's not as straightforward as it is supposed to be.

Look, no one can help you if you aren't willing to even try.  

There is also the icedtea java that people are having success with.

---

### Post by Kilz on 2007-11-05
> **veritas366 said:**
> Well, I think I mentioned that the original post about the script was confusing...it appears, for example, to bring in Flash which is no longer needed for Gutsy.  And all the other stuff on there...I just want Java.  And with 116 pages of responses, I'm guessing it's not as straightforward as it is supposed to be.

The script, and post have existed since Dapper Drake, thats 4 versions of Ubuntu. That 116 pages is a lot of the same post over and over. 

In case no ones told you, or you are just like everyone else and resurrect ancient posts to ask the  same questions everyone else does.
There is NO 64bit java plugin that "just Works" for everyone. Doesnt exist, cant be installed, etc. If you choose to ignore this, have fun.

---

### Post by veritas366 on 2007-11-05
> In case no ones told you, or you are just like everyone else and resurrect ancient posts to ask the same questions everyone else does.
There is NO 64bit java plugin that "just Works" for everyone. Doesnt exist, cant be installed, etc. If you choose to ignore this, have fun.

The point I was replying to was whether 64 bit had disadvantages.  I was suggesting that the java difficulties were an example of that difficulty. I've posted for help elsewhere on this issue and wasn't expecting help here.  

Thanks for the warm and fuzzy comments though.

---

### Post by Kilz on 2007-11-05
> **veritas366 said:**
> The point I was replying to was whether 64 bit had disadvantages.  I was suggesting that the java difficulties were an example of that difficulty. I've posted for help elsewhere on this issue and wasn't expecting help here.  

Thanks for the warm and fuzzy comments though.

Your quite welcome, I hope you find the help you need.

---

### Post by saru411 on 2007-11-05
> **veritas366 said:**
> The point I was replying to was whether 64 bit had disadvantages.  I was suggesting that the java difficulties were an example of that difficulty. I've posted for help elsewhere on this issue and wasn't expecting help here.  

Thanks for the warm and fuzzy comments though.

I'm sure all of us have read the sticky about the advantages and disadvantages of 64 bit. thanks for proving not everyone has though. we really need more people to restate the obvious. oh, and using sarcasm towards one of the most helpful members here isn't winning you any warm feelings from me either.

im not trying to flame you here, just get with the program please. those who keep restating the obvious misinformation are getting a little annoying. i don't blame kilz for his reaction. try answering a question and then getting misinformation pushed down your throat. then think about hw hard it is to get newbies to even trust anyones information around here. i would recommend you try helping in a 32 bit forum if you want to contribute to this community because what you are doing here is just attempting to scare off newbies.

---

### Post by PmDematagoda on 2007-11-05
Forgive me rsambuca, I wasn't very clear with what I said about "the warning message", it was actually a notice that it was going to remove the following packages:-

ubuntu-minimal

util-linux

util-linux-locales

Is it ok if those particular packages are removed?

---

### Post by veritas366 on 2007-11-05
Saru 411 said 

> I'm sure all of us have read the sticky about the advantages and disadvantages of 64 bit. thanks for proving not everyone has though. we really need more people to restate the obvious.

But I was responding to this:


> If you think that there are applications missing you may have been misinformed. At present, according to launchpad there is no difference in available packages between i386 and AMD64 for Feisty and Gutsy. There was a difference in Edgy, but that information is out of date.
Also there is no real difference in the installation of the 2, nor are there more problems. Every new user will have a learning curve. Advising them in this way (i.e. that 64 bit is less newbie friendly)  leads to misinformation that there are difficulties where none exist.

Kilz made it sound as if there were no extra problems for 64 bit and that newbies have no reason to worry about using it.  And yet, we need a script to get functionality out of the java plugin.

I'm not putting down 64 bit...in fact, I find it bizarre that people are taking this personally.  My point is that I don't know much about it but ran into trouble, trouble which a newbie needs a script to solve.  Therefore, it has issues that might make it less newbie friendly.

And I'm pretty sure the sarcasm didn't start with me:

> In case no ones told you, or you are just like everyone else and resurrect ancient posts to ask the same questions everyone else does.

I had actually searched but I had explained that sometimes too MUCH information was as difficult as too little.  There was kilz's thread but also I've seen one suggesting iced tea would work.  I saw one suggesting that blackdown would work (and I saw both of those before I found Kilz's thread).  And I tried those things.  Meanwhile, I found Kilz's thread a little confusing...it didn't seem simple to me. 

I understand you guys spend a lot of time here and read all the threads and follow all the wrinkles.  Someone who just checks into the forum just for a particular problem is likely to ask a question that may have been answered.  Maybe they didn't search.  Maybe they searched but couldn't get the wording quite right to get a helpful answer  or maybe, as in my case, they came up with a variety of different posts all advising different approaches.  

I read recently in a PC magazine an editorial that discussed how one of the things holding Linux back was the condescending attitude of SOME longtime users to newbies or people looking for help.  That's for proving THAT point, saru.

I'm glad you've found some meaning in your life.  Sorry it's a brand of computer processor.

---

### Post by Kilz on 2007-11-05
> **veritas366 said:**
> Saru 411 said 
Kilz made it sound as if there were no extra problems for 64 bit and that newbies have no reason to worry about using it.  And yet, we need a script to get functionality out of the java plugin.
Because one java plugin (sun's proprietary, non open source) isnt available, you think the 64bit version is missing something? There is icedtea, Blackdown, and the 32bit plugin setup.
> **veritas366 said:**
> I'm not putting down 64 bit...in fact, I find it bizarre that people are taking this personally.  My point is that I don't know much about it but ran into trouble, trouble which a newbie needs a script to solve.  Therefore, it has issues that might make it less newbie friendly.
O heaven forbid that a new user have to double click on a file and type in a series of 1's or 2's and type in your login and password. That is just to difficult for any mere human!
> **veritas366 said:**
> I had actually searched but I had explained that sometimes too MUCH information was as difficult as too little.  There was kilz's thread but also I've seen one suggesting iced tea would work.  I saw one suggesting that blackdown would work (and I saw both of those before I found Kilz's thread).  And I tried those things.  Meanwhile, I found Kilz's thread a little confusing...it didn't seem simple to me.  Yes, that thread just has to much information on it. How can anyone be expected to (gasp) read it.
> **veritas366 said:**
> I understand you guys spend a lot of time here and read all the threads and follow all the wrinkles.  Someone who just checks into the forum just for a particular problem is likely to ask a question that may have been answered.  Maybe they didn't search.  Maybe they searched but couldn't get the wording quite right to get a helpful answer  or maybe, as in my case, they came up with a variety of different posts all advising different approaches. Variety is the spice of life. Isnt it wonderful to have so many answers to what you said was missing, just a few lines up
> **veritas366 said:**
> I read recently in a PC magazine an editorial that discussed how one of the things holding Linux back was the condescending attitude of SOME longtime users to newbies or people looking for help.  That's for proving THAT point, saru. Here  are a few more things holding linux back IMHO:
1. When the same question is asked 5 times in different posts on the top page of some forums. 
2. That some users have difficulty understanding what that strange box with GO beside it is used for. 
3. There is also the problem of reluctance to read howto's.
4. What sticky posts?
6. [Isnt this Windows?]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by veritas366 on 2007-11-06
> 
Variety is the spice of life. Isnt it wonderful to have so many answers to what you said was missing, just a few lines up

Except none of them worked.

What's the deal with this forum?  Or is it just the AMD 64 crowd that is so obnoxious?  Seriously, this much hostility over a processor?  

Anyway, I get the message. If you have any reservations about using 64 bit ubuntu, stay off the forums.

Will do...you can have the sandbox all to yourself, big guy.

---

### Post by PmDematagoda on 2007-11-06
Please don't use that tone of voice on Ubuntu forums, no one is shouting at you, everyone is just trying to help, it is rather true that Ubuntu 64 requires a little more work, but it all pays off in the end since 64 performs much better than 32 bit, especially when memory is considered. 

The thing about 64 bit is that Java needs to be improved as there is no proper 64 bit plugin, if you believe that Ubuntu is responsible for that, then you are terribly wrong because as Kilz said, Sun's Java plugin is closed-source. And the same applies for Flash, there is still no proper plugin for 64 bit, but there are ways of installing the 32 bit one to work on 64 bit. But keep in mind that many ways of installing 32 bit software on 64 bit has been very much simplified in Ubuntu 7.10, especially Java and Flash.

---

### Post by Kilz on 2007-11-06
> **veritas366 said:**
> Except none of them worked.

What's the deal with this forum?  Or is it just the AMD 64 crowd that is so obnoxious?  Seriously, this much hostility over a processor?  

Anyway, I get the message. If you have any reservations about using 64 bit ubuntu, stay off the forums.

Will do...you can have the sandbox all to yourself, big guy.

If you think my post was hostile, Im sorry. It was honestly an attempt at humor and answering your questions/statements. 

Are you suggesting that none of the methods worked for you? Please tell me , what 32bit browser are you using for those 32bit plugins? [You know the one I told you was necessary ]("http://ubuntuforums.org/showthread.php?t=603707")to use the plugins you said you installed. the 32bit browser setup is normally the most easy, fool proof way of getting java working. If you have a 32bit browser installed how are you starting it? Is the 64bit one closed when you start it?

---

### Post by veritas366 on 2007-11-06
Let me unpack that last post of mine, Kilz.  Your script may very well work, I haven't finished with it yet.  What I was referring to was how you said that it's wonderful what a variety of answers I found.  

My point was that, yes, there were a variety of answers and all the OTHER answers (assuming your script works) worked for me.  In other words, it's not a real variety for my own particular needs.

I'm writing this on my laptop that is not 64 bit.  I have the compiz goodies turned up beyond what this video card should really support and it is still 3 times faster than XP and much nicer to look at...so I'm very excited about my latest attempts with Ubuntu.

But as for your script, that's on my main computer which I share and haven't been able to get back to using your script yet.  I had gotten as far as installing the base script and then I mentioned how I mistakenly thought it crashed to desktop because it asked for a user name and not a password and then the terminal went away.  

I will try to finish the process later today and I'll let you know what happened.  I will say that I personally found some elements of the instructions confusing. I'm actually not stupid, so it may be that others found them confusing and I'll give you that feedback if you want it.  I can give one example....when presented with the various browser choices, it says choose one 1 - 5.  Yet the selection for the base install is number 6.  It wasn't impossible to figure out what was going on...but it made me scratch my head.

I appreciate that you created this script...and envy your ability to do so.  But let me explain something I think is important.  The repetitive posts you find annoying are likely the results of lots of new people coming here.  Some may just be new to Linux and some may be relatively new to computers and the lovely world of forums in general.  

There is a big picture here....the better for all of us.  

There's a forum I went to once that had a special term for people posting something that was repetitive.  They wanted a special term because they wanted to show respect to the poster and welcome him or her but also to explain that the post offered nothing new or the question had been answered.  For some funny reason, they chose "trout".  If someone posted something that had already been dealt with, you'd simply say, "Trout, you might want to see this thread" or "Trout.  No time to find it for you but searcing will easily locate info on this."  An odd word was chosen so that the newbie would have no doubt that no sarcasm or ill will was intended.

Glad we could get back on the right foot here...I'm really happy Ubuntu is looking so "ready for prime time."

---

### Post by veritas366 on 2007-11-06
PMDematagoda said:

> if you believe that Ubuntu is responsible for that, then you are terribly wrong

This has been the oddest experience.  I never blamed Ubuntu for this.  The issue was whether 64 bit is an extra hassle and therefore, not as newbie friendly or friendly to those who are pressed for time.  That was it.  No blame.  

As for my tone...why key on mine and not that of Kilz...though he has since said that it was meant to be humorous, and I didn't read it that way.

Anyway, final update and I will no longer be on this thread....I tried the script and it didn't work.  I'm perfectly willing to believe it was totally my fault.  I managed to get the 32 bit firefox going...but there were no plugins showing at all.  There was a particular file that needed to have the permissions changed and Kilz had an explanation of that but when I followed his instructions it said that file did not exist at all.  I'm sure I missed a step somewhere.

So, I reinstalled with the 32 bit.  Went to hushmail, chose the plugin...worked on the first try.  Went to weather.com, chose the flash plugin...worked immediately.

That's not to say these things can't be made to work on 64 bit or that I'm not sacrificing something by going back to 32, but for me, I got no other solution to work.  

However, since that is possibly going to be seen as a vicious attack on AMD64 I'm going to hide under a table now.  

Carry on.

---

### Post by Kilz on 2007-11-06
> **veritas366 said:**
> PMDematagoda said:



This has been the oddest experience.  I never blamed Ubuntu for this.  The issue was whether 64 bit is an extra hassle and therefore, not as newbie friendly or friendly to those who are pressed for time.  That was it.  No blame.  

As for my tone...why key on mine and not that of Kilz...though he has since said that it was meant to be humorous, and I didn't read it that way.

Anyway, final update and I will no longer be on this thread....I tried the script and it didn't work.  I'm perfectly willing to believe it was totally my fault.  I managed to get the 32 bit firefox going...but there were no plugins showing at all.  There was a particular file that needed to have the permissions changed and Kilz had an explanation of that but when I followed his instructions it said that file did not exist at all.  I'm sure I missed a step somewhere.

So, I reinstalled with the 32 bit.  Went to hushmail, chose the plugin...worked on the first try.  Went to weather.com, chose the flash plugin...worked immediately.

That's not to say these things can't be made to work on 64 bit or that I'm not sacrificing something by going back to 32, but for me, I got no other solution to work.  

However, since that is possibly going to be seen as a vicious attack on AMD64 I'm going to hide under a table now.  

Carry on.

The firefox32 script has worked flawlessly on lots of computers. That you chose not to install an option (the browser) is your own fault. Enjoy having your 64bit hardware running in 32bit mode.

---

### Post by veritas366 on 2007-11-06
> That you chose not to install an option (the browser) is your own fault

I did install a browser...or that is to say I thought I did.  And when I typed "firefox32" in a command line, lo and behold a browser popped up.  So if I chose not to install a browser then what was it that I was broswing on?

What didn't happen was the installation of plugins.  However, I admitted I was likely at fault for this but why you would assume it was some deliberate choice, I have no idea. Are you suggesting that I got part way through and then, just to spite you, I deliberately omitted a step so I could glory in your failure?

Or do you just assume anyone who doesn't understand your instructions must be stupid?

I've had a look at other of your threads, Kilz, including the one linked to in the sticky about comparing 32 and 64 bit...and the complaints are there as well.  If someone hints at dissatisfaction about 64 bit you take it very personally.  Did you design that chip or something?  Are your initials "A.M.D?" Are you 64 years old?  

Good luck in your continued quest to run people off who don't agree with you.  You might want to get a teddy bear or a puppy or something because you can get kinda lonely that way.  Well, you'll always have your silicon wafer to keep you company.

---

### Post by Kilz on 2007-11-06
> **veritas366 said:**
> I did install a browser...or that is to say I thought I did.  And when I typed "firefox32" in a command line, lo and behold a browser popped up.  So if I chose not to install a browser then what was it that I was broswing on?

What didn't happen was the installation of plugins.  However, I admitted I was likely at fault for this but why you would assume it was some deliberate choice, I have no idea. Are you suggesting that I got part way through and then, just to spite you, I deliberately omitted a step so I could glory in your failure?

Or do you just assume anyone who doesn't understand your instructions must be stupid?

I've had a look at other of your threads, Kilz, including the one linked to in the sticky about comparing 32 and 64 bit...and the complaints are there as well.  If someone hints at dissatisfaction about 64 bit you take it very personally.  Did you design that chip or something?  Are your initials "A.M.D?" Are you 64 years old?  

Good luck in your continued quest to run people off who don't agree with you.  You might want to get a teddy bear or a puppy or something because you can get kinda lonely that way.  Well, you'll always have your silicon wafer to keep you company.

You didnt install one, per your own words. 
> **veritas366 said:**
> 

I was able to chose which version of ubuntu.
I was able to choose "6" when it asked which browser you want to install. That was a little confusing because six options were listed but it said choose 1 - 5.  6 was what I thought** I was to choose as it was the one that said I'll install a browser later.**


[When I asked how you were running it]("http://ubuntuforums.org/showpost.php?p=3716162&postcount=37") your next post was a rant.

---

### Post by veritas366 on 2007-11-07
> I was able to choose "6" when it asked which browser you want to install. That was a little confusing because six options were listed but it said choose 1 - 5. 6 was what I thought I was to choose as it was the one that said I'll install a browser later.

Well, first off, I repeated the process and selected firefox.  Secondly, your instructions kept saying you had to do the "base install" first...then install the browser.

Are you telling me that you have option 6 there in case people just wanted to watch all the text go by? 

I assumed...obviously erroneously, that when you said you have to install the base package first and then a browser that I was to choose number 6, which would be the base package and then choose one of the browsers you had listed separately.  You even included those files.

To be honest, the instructions didn't make any sense to me as no package you provided was called "base install" and I didn't know what that meant.  But really, once you offered six choices and told me to pick an option  from 1 - 5, I knew I was out of my depth intellectually anyway.  Clearly it was a zen koan...."Why is option six here?  Answer this, and you will have wisdom my son."


But then again, we know that I'm stupid and unworthy of the glorious AMD 64 chip.  I am going to stick to the Firefox for dumb people and that should keep both of us happy.

---

### Post by Kilz on 2007-11-07
> **veritas366 said:**
> Well, first off, I repeated the process and selected firefox.  Secondly, your instructions kept saying you had to do the "base install" first...then install the browser.

Are you telling me that you have option 6 there in case people just wanted to watch all the text go by? 

I assumed...obviously erroneously, that when you said you have to install the base package first and then a browser that I was to choose number 6, which would be the base package and then choose one of the browsers you had listed separately.  You even included those files.

To be honest, the instructions didn't make any sense to me as no package you provided was called "base install" and I didn't know what that meant.  But really, once you offered six choices and told me to pick an option  from 1 - 5, I knew I was out of my depth intellectually anyway.  Clearly it was a zen koan...."Why is option six here?  Answer this, and you will have wisdom my son."


But then again, we know that I'm stupid and unworthy of the glorious AMD 64 chip.  I am going to stick to the Firefox for dumb people and that should keep both of us happy.

There are 6 options, and one typo that says choose 1-5. So you chose 6? The one that doesnt install a browser, that was spelled out it doesnt install a browser? Methinks thou dost protest to much.

---

