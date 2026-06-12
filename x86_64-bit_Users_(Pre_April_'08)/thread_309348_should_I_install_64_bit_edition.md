---
title: "should I install 64 bit edition?"
date: 2006-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by clapton on 2006-11-29
I buy a laptop with a core 2 duo (T5500) should I install 64 bit version?

---

### Post by John.Michael.Kane on 2006-11-29
There should not be an issue running the 64bit version of ubuntu. Most of the 32bit add-on's  that one would want have scripts written for them to make installing them as smooth as possible.

---

### Post by xopher on 2006-11-29
If this is your first Ubuntu install (maybe even first Linux install?), then I higly recommend installing the 32-bit version first. You won't have as much problems installing eg. Flash player and stuff.

Just my 3 cents, it's still your decision ;)

---

### Post by Kilz on 2006-11-29
> **xopher said:**
> If this is your first Ubuntu install (maybe even first Linux install?), then I higly recommend installing the 32-bit version first. You won't have as much problems installing eg. Flash player and stuff.

Just my 3 cents, it's still your decision ;)

Installing Firefox/Flash/java isn't a problem on the 64bit version. There are multiple install scripts and applications for that.

> **clapton said:**
> I buy a laptop with a core 2 duo (T5500) should I install 64 bit version?
Yes, if you want to run 64bit on your 64bit system install it. For those that tell you to install a 32bit os, that isnt a perfect "easy" solution some people make it out to be. There is always a chance that something in an install be it 32 or 64 bit that you will have to deal with. Linux is not a guaranteed click - click install. But there is nothing on either version you cant learn to do if you ask questions and are willing to read and follow instructions.

---

### Post by RAOF on 2006-11-29
The 64bit version is basically unsupported by evil, non-open-source vendors :p.  That means: Flash and Java, mainly, but also Skype, Wine, etc.

It's not difficult to work around the lack of support and install these things, but you do have to work around it :).

Running the 32bit version will unquestionably be less effort.  But not a lot less effort.

The reason you might want to run the 64bit version is that some applications (particularly multimedia encoding/decoding) run substantially faster (~30% faster).

Edit: This should be the subject of a sticky thread "Pros and Cons of 64bit install".  If we could just agree that the cons exist :p.

---

### Post by fabertawe on 2006-11-30
> **RAOF said:**
> Edit: This should be the subject of a sticky thread "Pros and Cons of 64bit install".  If we could just agree that the cons exist :p.

That would be great as we're getting so many of these threads lately. One problem though... we also get repeated threads about Flash, Java etc., which indicates that people don't read stickies! ](*,) 

Paul

---

### Post by Malikith on 2006-11-30
I'm running 64-bit Ubuntu without any issue, the only thing that I've had to deal with is wine, but that can be solved by getting the wine deb package and doing a sudo dpkg -i --force-architecture winepackagename.deb . It all depends on what you require, everything will run, but some things like wine require just a different approach at the moment. But its not that bad at all. Its not hard though, and if you need any help getting something up and running, well, you know where to go ;).

---

### Post by xopher on 2006-11-30
> Installing Firefox/Flash/java isn't a problem on the 64bit version. **There are multiple install scripts and applications for that.**

Exactly my point - you can get everything working - with a bit of tweaking. The average user doesn't want to use third party script to get simple things (that should be installable with one click or less) working.

---

### Post by ByeByeBill on 2006-11-30
I agree,we need a sticky for this.I asked these same questions not long ago,and a proper place to find the answers is needed.The biggest ones are about flash and java,and folks need a simple solution.Most people I know who use Ubuntu,either version,use it for its simplicity,and the great forums.Not everyone wants to go to a command line to solve their problems,heck,not many folks even know how to do that.It seems easy to some here to do that,and they keep saying how easy it is,but it is above some folks heads to do it.All most folks want to know is how to get flash and java,and how to do it as easily as posible.For the longest time in 32 bit Ubuntu,there has been Automatix(and now Automatix2).It also works very well in 64 bit Ubuntu.The latest version dosent even need you to cut and paste anything in a terminal anymore,just click on one link on there website,and its installed.I feel that this is the solution to this problem everyone seems to be having with getting 32 bit programs up and running in 64 bit Ubuntu.I know that Ive said this before in this forum,and I dont mean to undermine anyones hard work getting java and flash,and other programs for that matter,to work in 64 bit,but users want and need the simplist solution to a problem,and I believe this is it.

---

### Post by clapton on 2006-11-30
This is not my linux first install, but is the first time that I've got a 64 bit processor.
I've got work to do on linux, I've been ask because I don't wanna lost time with a instalation with give no advantage.

---

### Post by ByeByeBill on 2006-11-30
If you dont have time to waste,then install the 64 bit Edgy version,and then Automatix2,at   [www.getautomatix.com](www.getautomatix.com)   ,download swiftfox from it(an optimized firefox),swiftfox codecs(includes flash,java,and more)and anything else you would like(there are many programs to choose from).You will be up and running in under an hour,all told,and have a fully functional 64 bit OS.Anything else you might need will be in Synaptic,nearly 20 thousand pieces of software,just waiting for you to point and click.WOW!:mrgreen:
Hows that for a sticky?!?

---

### Post by Malikith on 2006-11-30
> **ByeByeBill said:**
> If you dont have time to waste,then install the 64 bit Edgy version,and then Automatix2,at   [www.getautomatix.com](www.getautomatix.com)   ,download swiftfox from it(an optimized firefox),swiftfox codecs(includes flash,java,and more)and anything else you would like(there are many programs to choose from).You will be up and running in under an hour,all told,and have a fully functional OS.Anything else you might need will be in Synaptic,nearly 20 thousand pieces of software,just waiting for you to point and click.WOW!:mrgreen:

Yup, thats what I used as well. Even if you know how to do it manually like I do, Automatix saves ALOT of time, you can definately get a fully functional 64-bit Ubuntu installation with all the bells and whistles in under a hour with that. Its got alot of goodies in there you can install that aren't on the main repositories. Works like a charm. Its even extremely useful for 32-bit machines. I've used it on every install of Ubuntu I've ever done. You'll love it.

---

### Post by Kilz on 2006-11-30
> **clapton said:**
> This is not my linux first install, but is the first time that I've got a 64 bit processor.
I've got work to do on linux, I've been ask because I don't wanna lost time with a instalation with give no advantage.

Dont worry, you will still be able to play games like Monopoly, Trivial Pursuit, and Enemy territory. Steam will run with Cedega.

---

### Post by non-free on 2006-11-30
> **ByeByeBill said:**
> If you dont have time to waste,then install the 64 bit Edgy version,and then Automatix2,at   [www.getautomatix.com](www.getautomatix.com)   ,download swiftfox from it(an optimized firefox),swiftfox codecs(includes flash,java,and more)and anything else you would like(there are many programs to choose from).You will be up and running in under an hour,all told,and have a fully functional 64 bit OS.Anything else you might need will be in Synaptic,nearly 20 thousand pieces of software,just waiting for you to point and click.WOW!:mrgreen:
Hows that for a sticky?!?

If you prefer Free software dont recommend Swiftfox. It takes away freedoms that Firefox gives you. It cant be included in any distribution because it cant be redistributed.

---

### Post by PacShady on 2006-12-01
I wasn't aware that the Core Duo was a 64-bit processor??? I thought it was a dual-core 32-bit processor... in which case wouldn't it be better to install the 32-bit version of Ubuntu?

'Shady

---

### Post by ByeByeBill on 2006-12-01
> **PacShady said:**
> I wasn't aware that the Core Duo was a 64-bit processor??? I thought it was a dual-core 32-bit processor... in which case wouldn't it be better to install the 32-bit version of Ubuntu?

'Shady

Almost all of the processors you buy today are 64 bit,dual and single core(and soon,quad core!!).It just makes sense to support 64 bit OS's as they are the future of computing.Ubuntu64 isnt perfect,but it makes a good attempt at putting both 64 and 32 bit software together in one place.What they dont offer can be had easily by following some of the tutorials on this site and others.Both 32 and 64 bit OS's in linux arent perfect,but they are a far cry from where they were only a year ago.I say go 64,as its well put together,and you probably wont find much of a difference,useability wise,as its 32 bit conterpart.What you will get is the satisfaction of using a 64 bit OS on your 64 bit Computer,and not having to wait for Bill&Co. to get it right.....like thats ever gonna happen!:p

---

### Post by ByeByeBill on 2006-12-01
> **non-free said:**
> If you prefer Free software dont recommend Swiftfox. It takes away freedoms that Firefox gives you. It cant be included in any distribution because it cant be redistributed.

I never said I did,I actualy use Opera myself,because,IMHO,its the best browser on the planet.The reason swiftfox is mentioned is that it is included in Automatix2,along with its codecs,to help folks who want to use flash and java in Ubuntu64 get going fast.Also swiftfox works and uses all of firefoxs extensions and themes,so its just like using firefox,even if it isnt redistributable(Im questioning this,by the way,and am checking it out,as I downloaded a copy from their website,and it said nothing about not redistributing it,though I could be wrong)

Update:I checked and your right,I should read those licence agreements more often....but that makes it like Opera,as in its freely downloadable,just not free to redistribute or modify.I agree with his reasons for doing this,so I personaly have no problems with it.And no,I do not want to get into a disscusion about whats free or not,I believe that you should use whatever you want whenever you want to use it,and it should be up to whoever is using any piece of software to decide, for themselves,if they should use it or not.

---

### Post by Malikith on 2006-12-01
> **ByeByeBill said:**
> Almost all of the processors you buy today are 64 bit,dual and single core(and soon,quad core!!).It just makes sense to support 64 bit OS's as they are the future of computing.Ubuntu64 isnt perfect,but it makes a good attempt at putting both 64 and 32 bit software together in one place.What they dont offer can be had easily by following some of the tutorials on this site and others.Both 32 and 64 bit OS's in linux arent perfect,but they are a far cry from where they were only a year ago.I say go 64,as its well put together,and you probably wont find much of a difference,useability wise,as its 32 bit conterpart.What you will get is the satisfaction of using a 64 bit OS on your 64 bit Computer,and not having to wait for Bill&Co. to get it right.....like thats ever gonna happen!:p

Yeah, 64-bit Linux is way ahead of 64-bit Windows its further ahead than Windows Vista and even after Vista I think its still ahead comparing today to that, so we'll just say, 64-bit Linux is ahead of even Vista+1 ;). And Beryl and Compiz are further ahead in the desktop graphic department than Vista+2, that will require Core 2 Duo X6800 minimum haha.

---

### Post by non-free on 2006-12-01
> **ByeByeBill said:**
> I never said I did,I actualy use Opera myself,because,IMHO,its the best browser on the planet.The reason swiftfox is mentioned is that it is included in Automatix2,along with its codecs,to help folks who want to use flash and java in Ubuntu64 get going fast.Also swiftfox works and uses all of firefoxs extensions and themes,so its just like using firefox,even if it isnt redistributable(Im questioning this,by the way,and am checking it out,as I downloaded a copy from their website,and it said nothing about not redistributing it,though I could be wrong)

Update:I checked and your right,I should read those licence agreements more often....but that makes it like Opera,as in its freely downloadable,just not free to redistribute or modify.I agree with his reasons for doing this,so I personaly have no problems with it.And no,I do not want to get into a disscusion about whats free or not,I believe that you should use whatever you want whenever you want to use it,and it should be up to whoever is using any piece of software to decide, for themselves,if they should use it or not.

No Its not like Opera. Because Opera cant be redistributed at all, nor is the source code available . Swiftfox takes the open source Firefox code that is itself redistributable as source and binary. Then just because Swiftfox compiles the free source code Swiftfox takes away the freedom the parent gives you.
Almost all browsers allow you to share the application with someone. Swiftfox is the only Firefox variant that prohibits redistribution. The reason that Swiftfox doesn't allow redistribution is pure FUD. The developer could just as easily post md5sum's of the application for those who are worried about "security".
But an important question comes to mind. Who is the developer of Swiftfox that we should place this trust in him? After all he has stopped the distribution of the application by the Linux distributions. Where many eyes would be available to check his work. If it were possible to include it in Ubuntu and you could get it from the Ubuntu repositories then it could be considered safe. As it is, its the work of one man who may or may not be trustworthy.
Secondly Linux is available to you because of the work of many people who kept the ideals of FOSS and its freedoms in mind. When you give away those freedoms you make future work harder. 
Granted if the application was important, with options found no place else it would make a difference. But the [less than a second]("http://www.apcstart.com/node/3097") speed improvements offered by Swiftfox are not something I personally would trade away a freedom for.

---

### Post by ByeByeBill on 2006-12-01
Um...you obviously didnt read the end of my post,I think for myself,and dont allow anyone to influence my thinking.Especially folks who think freedom is all there is to life.FOSS started it all,and I have respsct for that,I just dont care if my software is free as in beer,or free as in freedom.As long as its free,and usable,and needed.Swiftfox may not be needed,but it is an effort to bring firefox back to its roots,using the code that is free for all to use and modify to their wishes.If you dont like it,you dont have to use it.No one is forcing you to,but you think they are.A simple"I dont like swiftfox because it dosent meet MY STANDARDS"is all you needed to type.Dont go around pushing your standards on everyone else,no one realy cares.:rolleyes:

---

### Post by fabertawe on 2006-12-01
> **ByeByeBill said:**
> If you dont like it,you dont have to use it.No one is forcing you to,but you think they are.A simple"I dont like swiftfox because it dosent meet MY STANDARDS"is all you needed to type.Dont go around pushing your standards on everyone else,no one realy cares.:rolleyes:

Well said. I don't like being preached to. I think we're all mature enough to make up our own minds.

Paul

---

### Post by ByeByeBill on 2006-12-01
Amen to that.Im trying to get him off the forum,hes of no help to anyone.

---

### Post by jkroto on 2006-12-01
> **PacShady said:**
> I wasn't aware that the Core Duo was a 64-bit processor??? I thought it was a dual-core 32-bit processor... in which case wouldn't it be better to install the 32-bit version of Ubuntu?

'Shady

I assumed that when I got my new core 2 duo from the UPS guy the other day and it said it supports 64 that it does support that and 32...!!??

I'm also putting together a new computer with a core 2 duo today and can't decide whether to run 32 or 64.

Forgive the stupid question but if the 64-bit version is installed are all the programs in the repo's ready to go with that version (64)?  Tweaking only needs to be done on those 3rd party programs?

And I'll follow that up with the obligatory 'Dapper' or 'Edgy'??  I'm running Dapper on another PC right now and am starting to get comfortable.

---

### Post by Malikith on 2006-12-01
> **jkroto said:**
> I assumed that when I got my new core 2 duo from the UPS guy the other day and it said it supports 64 that it does support that and 32...!!??

I'm also putting together a new computer with a core 2 duo today and can't decide whether to run 32 or 64.

Forgive the stupid question but if the 64-bit version is installed are all the programs in the repo's ready to go with that version (64)?  Tweaking only needs to be done on those 3rd party programs?

And I'll follow that up with the obligatory 'Dapper' or 'Edgy'??  I'm running Dapper on another PC right now and am starting to get comfortable.


I'm running 64-Bit Edgy with zero issues, and to answer your question about the official repositories using only 64-bit binaries, that is indeed true, every program on the official repository in 64-bit Edgy is in 64-bit. And theres a ton of them, I haven't noticed anything on the official repository that isn't any different from the 32-bit counterpart. Everything is there and works great. And tweaking isn't required in most programs, even 32-bit, just some, mainly only some older 32-bit games. Or if you want flash you need to download a 32-bit version of Firefox and thats all.

---

### Post by non-free on 2006-12-01
> **ByeByeBill said:**
> Um...you obviously didnt read the end of my post,I think for myself,and dont allow anyone to influence my thinking.Especially folks who think freedom is all there is to life.FOSS started it all,and I have respsct for that,I just dont care if my software is free as in beer,or free as in freedom.As long as its free,and usable,and needed.Swiftfox may not be needed,but it is an effort to bring firefox back to its roots,using the code that is free for all to use and modify to their wishes.If you dont like it,you dont have to use it.No one is forcing you to,but you think they are.A simple"I dont like swiftfox because it dosent meet MY STANDARDS"is all you needed to type.Dont go around pushing your standards on everyone else,no one realy cares.:rolleyes:

They are not my standards, they are the standards of the Free Software Foundation. As for Swiftfox taking Firefox back to its roots. Thats a bold faced lie. Swiftfox is nothing more than a recompile of the already existing Firefox code with no changes but the compiler flags. 
Go ahead and spit on FOSS, but remember if it wasn't for people looking out for your freedom. You wouldn't have an operating system today. Go ahead and use whatever you want, in fact why not try windows.

---

### Post by jkroto on 2006-12-01
> **Malikith said:**
> I'm running 64-Bit Edgy with zero issues, and to answer your question about the official repositories using only 64-bit binaries, that is indeed true, every program on the official repository in 64-bit Edgy is in 64-bit. And theres a ton of them, I haven't noticed anything on the official repository that isn't any different from the 32-bit counterpart. Everything is there and works great. And tweaking isn't required in most programs, even 32-bit, just some, mainly only some older 32-bit games. Or if you want flash you need to download a 32-bit version of Firefox and thats all.

Thanks Malikith, I think I'll give 64-bit a try.  I try to stay in the repo's, so other than the firefox/flash issue I should be good.  Does Automatix solve the flash problem for you?

---

### Post by Malikith on 2006-12-01
> **jkroto said:**
> Thanks Malikith, I think I'll give 64-bit a try.  I try to stay in the repo's, so other than the firefox/flash issue I should be good.  Does Automatix solve the flash problem for you?

Yeah it will, if you get swiftfox off it, but if you want to remain with free open source stuff or don't trust swiftfox, or just want Firefox, then i'd follow this howto:

[http://www.ubuntuforums.org/showthread.php?t=202537&highlight=32-bit+firefox+howto](http://www.ubuntuforums.org/showthread.php?t=202537&highlight=32-bit+firefox+howto)

That should get you on the right track. All you'll probably need out of that howto is just the 32-bit Firefox deb file they present there and the flash stuff. You might even be able to install flash just through the browser by going to a site like the nvidia site and clicking the click here to install plugin box, but I haven't tried this myself.

Easiest way would be the automatix way, but it all depends on what you want to do.

---

### Post by drezha on 2006-12-02
Cheers for all the posts guys. I was tempted into running 64bit on my 3500+ at some point and now seems like as good as time as any. I use Swiftfox and Opera (Opera seems to struggle with some sites which is a major shame...)
I prefer not to use Automatix, (Like to know I'm installing what I want etc etc) but I know if I have a problem, there's something that can help me out.

Oh jkroto, Core 2 Duo is 64 bit capable AFAIK, the Core Duo isn't. (Guess what one my laptop is :( )

---

### Post by slicker on 2006-12-02
> **ByeByeBill said:**
> Amen to that.Im trying to get him off the forum,hes of no help to anyone.

Are you going to try and get everyone who doesn't agree with you kicked off?

---

### Post by kcallis on 2006-12-04
Normally, I don't get into these types of debates, but I felt compelled to make a response.

The original topic was "should I install 64 bit edition?". A very simple topic, which was very black and white. There was no additional quesion of whether the inclusion of one package or another would detract from the successful function of a 64-bit installation.

Most of the posting were apropos to the topic, but talking about the merits of the fine print of a single package is not germane to the key topic. So I am not bothered if someone complains about that fact.

I am sure ByeByeBill was agressively giving his arguement in the heat of the moment. But the reality is that the direction of that sub-thread was way off base.

If someone wants to make a statement or observation about a package, it is relatively easy to start a new topic. At that point, a person as the right to go and read and respond to that topic. There is something wrong when someone goes out to left field, and detracts from those of us who are either adding to the original topic or getting some things from the useful responses.

I am glad that I didn't ask to be notified via mail to new responses or else I would have be slightly bothered.

---

### Post by ByeByeBill on 2006-12-05
> **kcallis said:**
> Normally, I don't get into these types of debates, but I felt compelled to make a response.

The original topic was "should I install 64 bit edition?". A very simple topic, which was very black and white. There was no additional quesion of whether the inclusion of one package or another would detract from the successful function of a 64-bit installation.

Most of the posting were apropos to the topic, but talking about the merits of the fine print of a single package is not germane to the key topic. So I am not bothered if someone complains about that fact.

I am sure ByeByeBill was agressively giving his arguement in the heat of the moment. But the reality is that the direction of that sub-thread was way off base.

If someone wants to make a statement or observation about a package, it is relatively easy to start a new topic. At that point, a person as the right to go and read and respond to that topic. There is something wrong when someone goes out to left field, and detracts from those of us who are either adding to the original topic or getting some things from the useful responses.

I am glad that I didn't ask to be notified via mail to new responses or else I would have be slightly bothered.
As would I.Im sorry about that.Dont usually let folks get to me,just like a useful response to a question,not aimless chatter.Again,Im sorry.

---

