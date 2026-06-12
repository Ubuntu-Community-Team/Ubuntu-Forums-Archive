---
title: "General Status of 64-bit Ubuntu?"
date: 2007-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by kragen on 2007-02-08
I just wondered what the pro's and con's of installing the 64-bit version was over the 32-bit version. Of the common programs, which have 64 bit versions, and which dont? Persumably its possible to install 32 bit versions of programs when the 64 bit ones arent available - is there any downside to this?
Also, all the downsides aside - most importantly - what is there to be gained from 64 bit Ubuntu? Is it significantly faster, or will I be struggling to notice any difference at all?

I know I can research / work out most of the above myself, and I can gues most of the answers anyway, but I also figured that it might be an idea to have an FAQ answering some of the above - updated as more gets developed. Nothing too fancy and in depth, just a quick overview of all the really important bits that do and dont work.

---

### Post by John.Michael.Kane on 2007-02-08
I so far have not had any issue with running ubuntu64. Most 32 programs have a guide or script to get it installed if you need it.

64bit being fast is an enduser perspective. Rember what is fast to one user maybe slow to you.

The best thing to do is setup a 64bit partition,and run it for a solid month.

---

### Post by incubus on 2007-02-08
I absolutely agree with SD.  I've been running 64bit for more than six months now and I never even thought of switching back.  The system is rock stable and the vast majority of things work out of the box.

Many people get annoyed with some proprietary programs (e.g., flash and the java plugin), but seriously it's not more than 10 minutes to set it up, if you follow a HowTo.

Besides, I think we have a very friendly community of 64bit users.  Questions are answered quickly and there's no RTFM-kind of thing.

I know of no better way of deciding this issue than trying it by yourself.  Again, I'm with SD: install it on a spare partition and give it a try for a month.

incubus

---

### Post by incubus on 2007-02-08
Regarding the advantages, you can search this section for previous discussions.

The first advantage of 64bit is not so appealing right now, which is the ability to deal with more than 4Gb of RAM memory.

If you do CPU-intensive work, there are also statistics favoring the 64bit platform.  I don't have the numbers, but it's fairly accepted that encoding, rendering, etc, get a good boost.

Now if you ask me, and perhaps many 64bit users will agree with me, the main issue is: since I bought a 64bit processor, why should I run it in 32bit mode?  I know that one day we all will.  Might as well start now.

incubus

---

### Post by Hendrixski on 2007-02-08
Eric Raymond had an article about this.  We can defeat MS if we rock the 64 bit platform before they do.  Right now we're on equal footing.
64 bit works great on Ubuntu, but it's just like Windows in that most programs are really only using 32 bit addressing.  Unix and Mac have almost finished their transitions to 64 bit platforms, Linux and Windows have to catch up, or else BOOM.

---

### Post by incubus on 2007-02-08
Kilz and other guys have championed that, by talking directly to the developers.  The problem is that they argue that:
1. The 64bit platform already works fine.
2. We should focus on the majority, which means 32bit users.
3. Complaints are usually just about proprietary software and in that case, they can't help.

It's understandable to certain point.  Then here at ubuntuforums, I have the impression that we have too much FUD about the 64bit platform.  The question of "advantages and disadvantages of 64bit" is by far the most common question raised in this section.  And we get a lot of answers of people who either just heard about it or tried it for a day (remember SD recommended trying for a month), gave up, and end up scaring other people away.

But with this process, we don't have so many people using 64bit.  Then because of point 2 above, 64bit receives less attention.  So people get frustrated/scared and don't use 64bit, so on ad infinitum.

incubus

EDIT: I forgot to mention that I agree with you: 64bit should be a marketing point, we should take advantage of it.

---

### Post by FrozenFOXX on 2007-02-08
So far my experience with 64-bit Ubuntu's been nice, minus one thing.

Wine.

It was more of an idle curiosity and took me a few minutes to figure out why it was showing up in Synaptic on my 32-bit machine but not on my 64-bit (honestly hadn't thought about it).

But then that only accents the fact that that has been the ONLY time so far that made me realize there was even a difference support-wise between the two platforms.

64-bit has greater potential for processing power.  Generally speaking unless you can seriously find a reason NOT to use it there's no reason not to install it.  If this was going to be a serious game machine I might think about reinstalling with 32-bit just to make it easier to upgrade Wine but since I've got a 360 gaming on the PC isn't so much of a concern anymore (well, minus the upcoming Warhammer:  Age of Recknoning, but that's it).

---

### Post by Kilz on 2007-02-08
> **kragen said:**
> I just wondered what the pro's and con's of installing the 64-bit version was over the 32-bit version. Of the common programs, which have 64 bit versions, and which dont? Persumably its possible to install 32 bit versions of programs when the 64 bit ones arent available - is there any downside to this?
Also, all the downsides aside - most importantly - what is there to be gained from 64 bit Ubuntu? Is it significantly faster, or will I be struggling to notice any difference at all?

**I know I can research / work out most of the above myself, and I can gues most of the answers anyway, **but I also figured that it might be an idea to have an FAQ answering some of the above - updated as more gets developed. Nothing too fancy and in depth, just a quick overview of all the really important bits that do and dont work.

You know what your post says to me? "Im lazy, I dont want to read a few posts, or use the search feature" Just like you dont want to look up the information. The next newbie will bypass any FAQ's you may create and ask the same question. It happens over and over.

---

### Post by Kilz on 2007-02-08
> **incubus said:**
> Kilz and other guys have championed that, by talking directly to the developers.  The problem is that they argue that:
1. The 64bit platform already works fine.
2. We should focus on the majority, which means 32bit users.
3. Complaints are usually just about proprietary software and in that case, they can't help.

It's understandable to certain point.  Then here at ubuntuforums, I have the impression that we have too much FUD about the 64bit platform.  The question of "advantages and disadvantages of 64bit" is by far the most common question raised in this section.  And we get a lot of answers of people who either just heard about it or tried it for a day (remember SD recommended trying for a month), gave up, and end up scaring other people away.

But with this process, we don't have so many people using 64bit.  Then because of point 2 above, 64bit receives less attention.  So people get frustrated/scared and don't use 64bit, so on ad infinitum.

incubus

EDIT: I forgot to mention that I agree with you: 64bit should be a marketing point, we should take advantage of it.

The problem is that the Ubuntu developers dont want to work on something new that points the way to the future. They want to make an eye candy distro that Windows users can install on their old 32bit boxes.
You cant buy a 32bit computer any more, but watch, this is my prediction. After Fiesty, we will have yet another eye candy release focusing on the 32bit version. But there will be no wine in the official 64bit repositories. They will not make a solution for the plugins ( either a 32bit browser or an easy to use nspluginwrapper) available in the official 64bit repositories. The only way it will happen is if a user submits it.
Ubuntu has its back turned to the future and cant see the road ahead. But my o my doesnt it look pretty.

---

### Post by BIGtrouble77 on 2007-02-09
> **incubus said:**
> Besides, I think we have a very friendly community of 64bit users.  Questions are answered quickly and there's no RTFM-kind of thing.
Yeah, especially because the parent's question gets asked at least 4 times a day.  I was gonna say we're REALLY understanding until I read Kilz post, lol.

Reality is that ubuntu 64bit is supported really well.  So Kilz, why is it Canonical's responsibility to make sure the ndiswrapper works better, have a 64bit flash, have 64 bit codecs, have a 64bit wine?  Their job is to build a distro based on the best of what's out there.  They can't contribute to every project.  

I kinda hope that 64bit Ubuntu just gets better (easier) at running 32bit code.  Reality is that there's no need for a 64bit browser, or a 64bit flash.  There's no performance improvement.  64bit should be used for apps that actually need it, like graphics production, audio production, encoders, databases, servers, etc.

Getting pissed at ubuntu/debian developers because wine isn't 64bit is just silly- your running 32bit windows code!  And all that eyecandy you're so disappointed with works in 64bit too so I'm completely missing your point.

---

### Post by incubus on 2007-02-09
haha, good point!

I was going to say, so hey why don't we have a sticky thread on "32bit vs 64bit", but I bet it's not going to make much difference.

incubus

---

### Post by osaeris on 2007-02-09
I have been working on cleaning up and resizing very high resolution scans (16 megapixel) then making them into 1024x768 video 25fps Ogg Theora video for projection using gimp and cinelerra. I had been working on the 32bit version of Ubuntu up until the end of last year.  I decided to switch to AMD64 version (having followed all the great advice here :-) ) it made a really noticable difference in the speed and stability of the OS to be running 64bit. 

64bit. Voted best.

---

### Post by Kilz on 2007-02-09
> **BIGtrouble77 said:**
> Yeah, especially because the parent's question gets asked at least 4 times a day.  I was gonna say we're REALLY understanding until I read Kilz post, lol.

Reality is that ubuntu 64bit is supported really well.  **So Kilz, why is it Canonical's responsibility to make sure the ndiswrapper works better, have a 64bit flash, have 64 bit codecs, have a 64bit wine?**  Their job is to build a distro based on the best of what's out there.  They can't contribute to every project.  

I kinda hope that 64bit Ubuntu just gets better (easier) at running 32bit code.  Reality is that there's no need for a 64bit browser, or a 64bit flash.  There's no performance improvement.  64bit should be used for apps that actually need it, like graphics production, audio production, encoders, databases, servers, etc.

Getting pissed at ubuntu/debian developers because wine isn't 64bit is just silly- your running 32bit windows code!  And all that eyecandy you're so disappointed with works in 64bit too so I'm completely missing your point.

Because the purpose of Ubuntu is to make it easier for the first time user to install Ubuntu. To do that job some things have to "just work". What new user doesnt want flash or other plugins running? Its probably the number one question on the 64bit section. The second is wine. Most new users coming over from Windows have one or 2 Windows applications they need working to transition. The excuse the developers use is "but what are they going to run with these applications. Isnt it going to be proprietary ?" Well yes it is, but that is no excuse as to why 2 of the most common open source applications asked about on the 64bit section dont work out of the box.
Imagine how many posts they would have if the same were true of the 32bit version. How many new users would Ubuntu have if the 32bit version had a browser that didnt let you use the plugins, and wine wasnt available.
The solution to the #1 asked question is to make the 32bit browser available to us. 64bit Suse defaults to the 32bit browser. Why doeesnt Ubuntu, a distro that is suposed to be easier for the first time user. But instead, the new user must jump through hoops. It isnt like they are not already making those same packages for 32bit. What or make the nspluginwrapper work, or even **available** in the repositories, it isnt
Lastly dont hold your breath waiting for the developers to make running 32bit code easier, in fact they have made it harder since Dapper. They have also told me point blank not to rely on it continuing to work.

But my o my doesnt everything look pretty.

---

### Post by mogulike on 2007-02-09
I was using ubuntu 64 for about 3 weeks and it didn't agree with my set-up. I did get most things working eventually, but it was such a pain in the butt that I decided to just go back to my XP install. (Boooo hisssss)

Keep in mind that I've only used *nix on and off over the last few years, but I am a software engineer graduate, so I'm not completly usless with computers. (or at least I hope so)

The main problem I had was getting my graphics card to work. It's an Nvidia 7600GT and at the time was a fairly new card/chipset. So there was no driver support built into Ubuntu. I realised very shortly after the install, being that the nice and shinny Ubuntu login screen didn't appear. I had to skip back and forth between my windows boot and ubuntu to find out what was going on. It took me about 3 days (between work, life etc) to find and download 3rd party drivers using wget, which I hadn't used before. The drivers worked (sort of, bit flakey) well enough to run at level 5. Another epic trial was when I tried to get my wireless card working, which I didn't manage in the end. It's a linksys pci card I can't remember the model, but it's 54g. I looked high and low and no matter what I tried I couldn't get it working. I had  Ethernet, but I was soon moving and didn't want to run wires all over the place, well not yet anyway.

In the end any thing I came to install became a hurdle and I tried of all the effort just to get a small task done. And some apps feel over queit regularly. I feel my problems are as much my fault as it is ubuntus, me choosing my config and all, but if I can't get it working what chance does a normal user have? I know for some people the config is completly compatible, but mine sadly isn't (yet).

I do plan to get Ubuntu 64 back on soon though. I think ubuntu is brilliant and worth the effort, but not at the time.

---

### Post by BIGtrouble77 on 2007-02-09
Ok, I actually think we're on the same page, Kilz.  I think there's competing trains of thought and ideologies here... The first is the Purest that only wants to support open standards and open software.  The second is the Realist that wants to support commercial software and *popular* proprietary standards.  The suprising thing is that the ubuntu developers seem to be liberal as far as proprietary standards go (planning to include proprietary video drivers and codecs int he next release).

My frustration with all 64bit distros (except maybe gentoo) is that it should be stupidly easy to run 32bit code.  In many cases it is somewhat easy, but it's never stupidly easy.  I also have absolutely no clue why Ubuntu defaults to the 64bit browser.  It's so limited that i'm sure almost no one uses it.  I agree that if there was actually a well developed ndiswrapper it would be usable, but why aren't they defaulting to the 32bit version in the mean time?

And why not include automatix with the distro (or easyubuntu)?  It solves so many problems that novice users would have to spend a couple weeks to figure out.  I think the developers train of thought is that we should be further developing the Linux ecosystem and the propegation of OSS standards rather than conforming to proprietary standards that have historically hurt interpolarity.  

It's a difficult arguement... I can see the issues from both sides ad I'm still not sure which I support more.  But I think what disappointsments there are in 64bit Ubuntu mainly boil down to interpolarity problems with proprietary, closed source software only compiled in 32bits.  I have a feeling we're going to be debating this issue for a very long time.  Don't forget Canonical is a company too, so it's silly to think they aren't looking out for their financial interests as well.

---

### Post by JAPrufrock on 2007-02-09
As previously mentioned in this thread, the best way, and maybe only way, that distros like Ubuntu have a chance of competing against Microsoft is by winning the race to support the 64 bit machine (see the link below).  Without the slightest doubt, 64 bit machines are the future of computing.  Ubuntu has already lost the software battle for the 32 bit machine.  So why isn't it fully supporting 64 bit Ubuntu?  Only one word comes to mind -  shortsightedness.  

[http://www.catb.org/~esr/writings/world-domination/world-domination-201.html](http://www.catb.org/~esr/writings/world-domination/world-domination-201.html)

---

### Post by Kilz on 2007-02-09
> **BIGtrouble77 said:**
> Ok, I actually think we're on the same page, Kilz.  I think there's competing trains of thought and ideologies here... The first is the Purest that only wants to support open standards and open software.  The second is the Realist that wants to support commercial software and *popular* proprietary standards.  The suprising thing is that the ubuntu developers seem to be liberal as far as proprietary standards go (planning to include proprietary video drivers and codecs int he next release).

My frustration with all 64bit distros (except maybe gentoo) is that it should be stupidly easy to run 32bit code.  In many cases it is somewhat easy, but it's never stupidly easy.  I also have absolutely no clue why Ubuntu defaults to the 64bit browser.  It's so limited that i'm sure almost no one uses it.  I agree that if there was actually a well developed ndiswrapper it would be usable, but why aren't they defaulting to the 32bit version in the mean time?

And why not include automatix with the distro (or easyubuntu)?  It solves so many problems that novice users would have to spend a couple weeks to figure out.  I think the developers train of thought is that we should be further developing the Linux ecosystem and the propegation of OSS standards rather than conforming to proprietary standards that have historically hurt interpolarity.  

It's a difficult arguement... I can see the issues from both sides ad I'm still not sure which I support more.  But I think what disappointsments there are in 64bit Ubuntu mainly boil down to interpolarity problems with proprietary, closed source software only compiled in 32bits.  I have a feeling we're going to be debating this issue for a very long time.  Don't forget Canonical is a company too, so it's silly to think they aren't looking out for their financial interests as well.

Wait a second, lets look at a few things. [LIST=1]Ubuntu is all set to incorperate the proprietary binary blobs that are the video drivers.
[*]They have for a long time done this with other drivers
[*]They make avilable the proprietary 32bit code (proprietary plugins) in the 32bit version. 
[*]The 64bit version is capable of running the code.[/LIST]
But the developers wont make that same code available in the 64bit version for what reason? Is it just me or do others see that they are talking out of both sides of their mouths?

You also mention that Canonical is a company. That they are out to make money. Exactly how does a business continue to pour money into old technology and ignore the real world? Exactly how do they ignore that 32bit processors are no longer being made?
I know people will still be using the 32bit hardware for a few years. But isnt the 32bit OS good enough to last out the life of said hardware? 
People keep pointing out that the work they are doing kind of sort of helps the 64bit version. Wouldn't that be true in reverse?

---

### Post by tomdkat on 2007-02-10
> **Kilz said:**
> Exactly how does a business continue to pour money into old technology and ignore the real world?Well, in the real world lots of people are still running 32-bit OSes and apps on 32-bit hardware and on 64-bit hardware.  One could argue continuing to support 32-bit environments is actually paying attention to "the real world".  Of course, this doesn't support advancement or transition to a 64-bit world but I doubt that "movement" will come from the Linux community.  When 64-bit native Windows environments become the norm, the transition to 64-"bitness" will gain more momentum. Why?  Simply because Windows is so ubiquitous.

> Exactly how do they ignore that 32bit processors are no longer being made?Because processor production has nothing to do with the current install base.  The fact 32-bit processors aren't being made doesn't convert my mom's old Pentium Celeron based machine to a 64-bit beast.  :)    There are a ton of 32-bit machines still installed and each of those can be a candidate for running Ubuntu.

> I know people will still be using the 32bit hardware for a few years. But isnt the 32bit OS good enough to last out the life of said hardware? 
People keep pointing out that the work they are doing kind of sort of helps the 64bit version. Wouldn't that be true in reverse?I do agree with you that the Ubuntu developers certainly do need to do more to make the 64-bit environment easier for end users.  The various scripts and other tips & tricks to get 32-bit proprietary apps, like Flash, running which are posted on this forum should be incorporated (in some fashion) to at least give the appearance of things "just working".  The harder it is for people to get the apps they need running without second thought, the more challenging it will be for people to be open minded about computing in a native 64-bit environment.

Peace...

---

### Post by JAPrufrock on 2007-02-10
> Of course, this doesn't support advancement or transition to a 64-bit world but I doubt that "movement" will come from the Linux community.

Actually it might.  MS, Linux and Apple are all in the race.

---

### Post by Kilz on 2007-02-11
> **tomdkat said:**
> Well, in the real world lots of people are still running 32-bit OSes and apps on 32-bit hardware and on 64-bit hardware.  One could argue continuing to support 32-bit environments is actually paying attention to "the real world".  Of course, this doesn't support advancement or transition to a 64-bit world but I doubt that "movement" will come from the Linux community.  When 64-bit native Windows environments become the norm, the transition to 64-"bitness" will gain more momentum. Why?  Simply because Windows is so ubiquitous.

Because processor production has nothing to do with the current install base.  The fact 32-bit processors aren't being made doesn't convert my mom's old Pentium Celeron based machine to a 64-bit beast.  :)    There are a ton of 32-bit machines still installed and each of those can be a candidate for running Ubuntu.



While your grandmothers old pentium celeron _may be_ a candidate, it may not run Ubuntu at all. I have quite a few old 32bit compters and have tried Ubuntu on some of them. They dont run well. That is , if you could convince someone who has been running Windows for 5-7 years on a machine to switch its OS.
Right now a lot of 64bit hardware is sold with a 32bit Windows. There is a greater chance imho to get those people to switch , if we had a good 64bit OS to offer them.

---

### Post by illogical on 2007-03-10
> Right now a lot of 64bit hardware is sold with a 32bit Windows. There is a greater chance imho to get those people to switch , if we had a good 64bit OS to offer them.
Now that's the nail hit hard and squarely on the head.
I've been fighting to get the 64 bit AMD version to run on my machine for a week now, I think I'll crack it today, but what a battle!](*,)
For weeks I've been trying to persuade people to try UBUNTU rather than Vista, but it needs to be much easier and work out of the box 99.9% of the time on a 64 bit platform.
If this was achieved I have little doubt that it would become the mainstream op system of now and future.
Someone needs some very strong coffee methinks.:cool:

---

### Post by revleo on 2007-06-05
first off i appoligise in advance if i offend anybody sencond i am not a novice i am a pc tech and am familiar with both os,es and hard ware  now to the meet we are all dancing around the subject  to 32 or to 64  is it easy enough can i as a user install with just a point and a click will the future architecture be supporrted 
         it won,t be an easy point and click if it is not debugged
          this means someone has to be using it to find the bugs 
                    BTW that means us 


                the future hardware will be supporrted 
                  if we don,t the other guy will
                    for the world is not flat 
                   and telephones work
                      and 64 is comming 
                        so is terabyte 
                           lets go

---

### Post by JAPrufrock on 2007-06-06
> **illogical said:**
> Now that's the nail hit hard and squarely on the head.
I've been fighting to get the 64 bit AMD version to run on my machine for a week now, I think I'll crack it today, but what a battle!](*,)
For weeks I've been trying to persuade people to try UBUNTU rather than Vista, but it needs to be much easier and work out of the box 99.9% of the time on a 64 bit platform.
If this was achieved I have little doubt that it would become the mainstream op system of now and future.
Someone needs some very strong coffee methinks.:cool:

The first time I installed a 64 bit ubuntu OS, it was extremely difficult- a real struggle.  The last time (1 month ago) it was extremely easy, for two reasons- 1) I have a lot more experience with 64 bit programs/files and with Ubuntu in general and 2) Feisty is more 64 bit "friendly" than previous OSs.

---

### Post by capecove on 2007-06-06
Boy, I have to second this thought...

"2) Feisty is more 64 bit "friendly" than previous OSs."

I had zero trouble getting Ubuntu to function. In fact, it was fast for me. Now, I install Windows all day long and may be used to doing install procedures but I was really surprised by the simplicity of it. Plus, the ease of setup really put me in a good frame of mind for working with Ubuntu Feisty Fawn 64 bit. 

I don't have the most cutting edge hardware but am at a place that it better than most users so that may have something to do with it. It would be impossible to know if every setup would be as simple but I can vouch that mine went excellently.

---

### Post by dabl on 2007-06-06
> **JAPrufrock said:**
> Feisty is more 64 bit "friendly" than previous OSs.

Very true, indeed.  And I love that avatar, JA!

:D

---

### Post by brharri1 on 2007-06-06
64 bit feisty was just as easy for me to get running as 32 bit. I have not lost any functionality and I do notice better response. This is either due to 64 bit install or the fact that my 32bit feisty was an upgrade from edgy vs a fresh install of my 64bit. Either way, I couldn't be happier having switched.

---

### Post by bullsmack on 2007-07-08
i see alot of ppl saying that the 64 bit linux and 64 bit windows xp are on the same level but that mac and others are further along then linux and MS. well i just took the 64 bit xp out of my 64AMD because it was awful. i see that ppl are talking about programs  still running in 32 bit. well that would nevre be my reason for NOT installing 64 bit. the main reason i wanted to install it was...

1. my system is capable of running it. and 
2. contrary to what i have heard i do not belive that there is n o benifit because of the 32 bit programs, simply because even though my programs may be running in 32 bit, when i am running my server and playing in the game as well i will benifit greatly with less strain on the system as a whole if i want to go back to my desktop and surf the web or download other things. because that IS using the 64 bit when doing things of that nature. therefor putting less strain on the server and the ppl in the server stopped complaining of LAGGGGG when i left the game and looked around on the web. 

the only reason i took it out is because it was unstable. it would crash and do some really odd things. for no reason at all certain settings would change out of the blue. 

so what i am hearing about the ubuntu sounds far superior to me then the MS 64xp. i just cant wait to see if its true what you all are saying that are running linux 64 bit/

---

### Post by hendoc on 2007-07-08
I've been running 64 bit Feisty and 64 bit Edgy before that. Swiftfox takes care of plugin problems. Swiftfox is a little bit buggy, but, with the restore session option, it is minor. The 64 bit system itself gives me no problems whatsoever.

---

### Post by nss0000 on 2007-07-08
BigH:

Yep! There's lots of us running various versions of Ux64 without serious issue. Frankly, my Dapperx64/AMD5400+ system is so slick & trouble-free that I have a hard time visualizing the problems others are having ... except to blame "hardware". 

I understand, that does not help the poor usr stuck-in-a-bind. But the overall success is so great,  I feel the entire distro ought to SURGE into 64-bit-land --- devil take the laggard. 

And yep, I'm waiting for the INTEL pricedrop this month , so I can  snag  (underpriced) AMD6000+ kit.  Ought to be about $175 from the NEGG bloodsuckers.

nss
*****

---

### Post by bullsmack on 2007-07-09
makes me so mad that i biult my first pc before it went to am2. because now im stuck with a 4200+ wqith ddr400 ram and 939 socket.i do have two 7900 gt ocs in sli but man i should had waited a couple months then i could be at least in the running for hte new technology without haqving to redo everything!. i am syked cant wait to install this if i can get past the preinstall stuff. :)


my father just got a 6000+ and honestly im sold on the fact that video cards are far more important then cpu once you get up over 4200 because my system runs smoother then his does. and i think its  because of the cards. hes got one 7600. i have two 7900s. and he has all the newer ram and mobo.

---

### Post by RAOF on 2007-07-09
A couple of the Ubuntu developers run the amd64 version, too.  They don't find anything wrong with it.

---

### Post by dryder on 2007-07-09
> A couple of the Ubuntu developers run the amd64 version, too. They don't find anything wrong with it.
With ... what?

Example: is it the (64-bit) Ubuntu that should provide a way to run a 32 bit printer driver or do Ubutnu (and 64 bit proponents) say it is the manufacturer who should provide a 64 bit driver or a driver that will work under the 64 bit OS shell?

Remember the days when MS changed from 16 bit to 32 bit - as the 'lead' it was MS who were expected to enable as many as possible 16 bit programs to work - with many incompatibility issues at the time.

I have 64 bit Ubuntu - but I am not going to change (again) my printer because its 32 bit linux driver won't install (Canon LBP3000). Nor my scanner (again).

In these early days wrapping these 32 bit drivers / apps so they work is the only way people will change - or else we are all on the MS path of 'upgrade and upgrade' all over again.

I like the speed of 64 bit (yes I do notice it.). I don't like that my printer works in Feisty 32 bit but not 64 bit. That is a fairly good deciding factor in which I use.

JMHO

David

---

### Post by stmiller on 2007-07-09
Have you tried any of the Canon drivers in gimp-print (now called gutenprint?)

[http://gutenprint.sourceforge.net/p_Supported_Printers.php3](http://gutenprint.sourceforge.net/p_Supported_Printers.php3)

I have a Samsung that works with a different samsung driver. This is in Ubuntu 64, with the listed driver (a .ppd file). I don't think there is a different 32bit or 64bit ppd file. So perhaps a ppd file from foomatic or gutenprint could work?

There are some generic print drivers which should at least let it print text.

---

### Post by nss0000 on 2007-07-10
BigD:

My HP1300 laserjet got automagically configured when I installed Dapperx64 on AMD5400+ kit. I MAY have pushed a button that said "configure printer". That printer was already hooked and running with my AMD2600+/Dapperx32 system. I don't think printers (HP only?) give-a-darn.

But then yes, Ubuntux64 usrs seem to have wildly different experience depending on (trivial) hardware differences

NB:: LM-Sensors, onboard sound+Etherport  remain unsupported on my ASUS_m2n mobo.

nss
*****

---

### Post by dryder on 2007-07-10
Hi stmiller,

yes, I have looked there but I cannot find a driver that works the LBP 3000, despite Canon Australia releasing a 32 bit driver for it (in itself a victory for 'linux').

It still seems to me that 64 bit will be 'nice to have' but not 'functionally good to have' until users, developers (OS, s/w and h/w) embrace the need to get current things working.

A lot of people changed printers and scanners, for example, after being fully convinced linux was for them - they will not take kindly to yet again replacing h/w for the 64 bit appetite.

In 32 bit Feisty (as a minor s/w 'for instance'), Boinc races along.

In 64 bit Feisty the 64 bit version is not supported and does not work.

I suppose this means that linux is not yet fully accepted by the industry as a serious OS to spend money on nor do we hassle them enough to convince them otherwise. And I think the number of linux flavours complicates the issue. MS' monoploly makes development a 'one road' map for them.

JMHO

David

---

### Post by dabl on 2007-07-10
> **nss0000 said:**
> 
But then yes, Ubuntux64 usrs seem to have wildly different experience depending on (trivial) hardware differences
*****

Very true, according to the posts I read.  Being kinda cowardly, I bought an Intel motherboard and CPU, thinking the "standard" chipset and BIOS it would improve my chances of coping with a conversion from Windows to Linux.  It has -- the only hardware issue (that I know of) is some silly PCI bus message on bootup about memory allocation -- just a bug that doesn't do anything.

- Epson C-84 printer driver in Ubuntu "just worked" (in Kubuntu I had to go chase one down in linuxprinting.org)
- USB keyboard and USB Wheel Mouse just work
- Mix of IDE/PATA and SATA drives required some trickery, to get the dual-boot MBR onto a SATA drive, but it's possible
- Integrated Intel HDA sound system works really well for recording and playback, and justifies the extra cost of the motherboard IMHO
- lm-sensors just works -- and the Ubuntu xsensors panel is WAY better than Kubuntu
- Nvidia PCI x16 card (7900 GS) provided a "learning experience" in driver installation, but oh well, "suffering builds character"!

:guitar:

---

### Post by pyrofly on 2007-12-07
Perhaps this thread has died since the Gutsy release, but I thought I'd add my 2 cents.

I'm new to Ubuntu and decided to try it because I built a new computer about a year ago and have spent many wasted hours trying to get Windows to load - unsuccessfully I might add.  I tried XP64, XP Prof (32bit), and most recently Ubuntu 7.04 and then 7.10.  

My box has:
AMD 64  3800+
A8N-SLI Premium mobo
2 GB 400mhz RAM
80 GB sataII hard disk
nVidia 7600GTS x2 in SLI mode
and all the other basic stuff - optical drive, ethernet card, etc.

The list of problems I encountered with Windows is quite long and varied (after all, I spent a year working on it) and while I learned a lot about hardware and different quirks in Windows, at the end I had nothing to show for it.  
Then I discovered Ubuntu and life suddenly became much happier and easier.  First off, the 64 bit version loaded flawlessly right out of the box (I didn't even have to remove any hardware components).  Most programs load quickly and easily from the applications menu or from synaptic package manager.  Everything is simple and intuitive, even for a long time Windows user.  I had to read two "how-to's" to install Flash and Wine (took about 20 min. each), but compared to the blistering hell I walked through with Windows, this was a minor diversion at worst.  I am now a complete Linux convert.  And the best part of all is that it's free!!!  Suck on that Microsoft!!!  Mwah hah hah hah!!!  (But if you're here you already know about that great benefit.)

I'm sure I'll have more to add after I've used it longer.  After all, I'm *still* going through all of the available repositories to see what software is available and what I can do with it.  After reading through this thread, I can only hope that like myself, others will be able to see more of the great benefits and possibilities than the minor inconveniences.  I say keep using the 64-bit version and it can only get better.  After all, IMHO it's already pretty snazzy compared to the competition!

---

### Post by thekat on 2007-12-30
Well, I am getting ready to jump into the 64-bit arena..
My box is about 2 years old and I have been running Kubuntu (32) for several months without issue.. 
Ubuntu has come so far since I ran it last.. before Dapper.. 

So once I get my profile backed up then I am going to wipe and load with
64-bit Ubuntu..

tk

---

### Post by Keith_Beef on 2007-12-30
I took the plunge and went all 64-bit a couple of months ago.

Although I was expecting to have to jump through some hoops, install some extra 32-bit libraries and compatibility hack, I found that just about everything works out-of-the-box.

[SIZE="4"]Software[/SIZE]

The only real sticking point I've had so far has been SC3U (won't run at all) and RT2 (choppy sound, but otherwise perfectly playable).

Since I don't play many games, this is no big deal for me.

Encoding OGG files (or the occasional MP3 for the living-room hi-fi that reads no other format) is blazingly fast.

Encoding XViD files (to get the on a hard drive, so I don't have to start swapping DVDs when the kids want to watch one episode of Bagpus, then one episode of C'est pas sorcier) is fast, too.

Retouching photos in Gimp is much faster.

[SIZE="4"]Hardware[/SIZE]

No real hardware problems.

OK, so I haven't got my OM3 to work yet, but then I had the same problem in 32 bit Ubuntu.

My Canon PowerShot A610 shows up, the Gnome software imports photos without any problems.

My TomTom GO 920 shows up as an external disc, and I can go in and copy or modify files as I wish.

My wife's Cowon A2 media player also shows up as an external disc, and I can rip her audio CDs to it, or films, or put text files downloaded from Gutenberg.org to it for her to read on long flights.

My aging Epson Sylus Photo 890 works perfectly well, now on a USB cable (as opposed to the parallel cable it had been on for years).

I started out wary and skeptical, and I'm not a zealot.

Bite the bullet, install 64-bit Ubuntu. It's worth doing, since:
[LIST]
[*]it costs you nothing to go 64-bit, if you have the CPU for it,
[*]it adds to the 64-bit user base, so encourages development of 64-bit applications.
[/LIST]

Beef.

---

### Post by DevilHunterWolf on 2008-01-08
I've been running 64-bit Gutsy for a couple of weeks and I really haven't had much trouble. I followed the install guides on [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607) and pretty much everything I wanted to use (combined with Wine) was covered. I've only come across a couple instances where there wasn't a 64-bit version of a program and it hasn't really bothered me too much. I'd say 64-bit is well implemented these days on Ubuntu and Linux and I'm sure it will only increase as users find ways around those few 32-bit only programs. It feels good to finally be able to use my processor to it's full potential.

---

### Post by Elim_Garak on 2008-05-09
> **JAPrufrock said:**
> The first time I installed a 64 bit ubuntu OS, it was extremely difficult- a real struggle.  The last time (1 month ago) it was extremely easy, for two reasons- 1) I have a lot more experience with 64 bit programs/files and with Ubuntu in general and 2) Feisty is more 64 bit "friendly" than previous OSs.

For comparison, my first 64-bit install is Heron, and I got it right once, and immediately.  There were no hiccups.  In opposition to this was the old Windows 98, which I had installed several times for several people, including about four times for myself.  Each install was a painful, tedious, peril-filled procedure.

---

