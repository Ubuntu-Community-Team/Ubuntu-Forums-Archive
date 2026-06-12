---
title: "The long, long wait... for 64bit programs"
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ispmarin on 2005-12-16
Hello everybody. I have now for six months a amd64 running ubuntu 5.10 (previosly hoary) and some little things really annoy me. Some are ubuntu's, others are from third party companies. Here is my list:
1. Browser plugins. Flash, quicktime, NOTHING is working nicely. Or working.
2. OpenOffice 2 is buggy. Really buggy.
3. (TP)Opera is not avaliable yet. I really enjoy Opera.
4. (TP)Skype.
5. (TP) Games in general...
6. Java?
I think that there is enough public with amd64 processors for the companies and even ubuntu development community to think more seriously about this architecture. I am not a very good programmer, and I am always filling bug reports and posting when something gets to work. But how can we (or I) put more pressure on the companies or help more to get better software and support? And...
Chroot. Don't talk to me about chroot...

See ya!

---

### Post by Casey on 2005-12-16
I have java working, what problems are you having?

There's no java 1.5 plugin for the AMD64 from sun, although I hear that blackdown has one if that's actually what you want.

---

### Post by azcrumpty on 2005-12-16
[QUOTE=ispmarin]Hello everybody. I have now for six months a amd64 running ubuntu 5.10 (previosly hoary) and some little things really annoy me. Some are ubuntu's, others are from third party companies. Here is my list:
1. Browser plugins. Flash, quicktime, NOTHING is working nicely. Or working.
2. OpenOffice 2 is buggy. Really buggy.
3. (TP)Opera is not avaliable yet. I really enjoy Opera.
4. (TP)Skype.
5. (TP) Games in general...
6. Java?
I think that there is enough public with amd64 processors for the companies and even ubuntu development community to think more seriously about this architecture. I am not a very good programmer, and I am always filling bug reports and posting when something gets to work. But how can we (or I) put more pressure on the companies or help more to get better software and support? And...
Chroot. Don't talk to me about chroot...

See ya![/QUOTE]
Do you favorite apps really have to be compiled for 64 bit?  I mean I downloaded opera static as a .deb and --force-arch'd it, and it works fine.

I use the blackdown JAVA so I can have plug-in support on Firefox.   What I really need are our favorite 32 bits statically compiled.  I just need to get mplayer working and I am set.

I get a feeling from you that some things are not w orking in 64 bit ubuntu?  I can't get cfs, amorok, and a few things in the packaging system to work, as well.  Anyone else notice problems like that?

---

### Post by ispmarin on 2005-12-16
I will see about this java, thank you. Well, amarok is working fine here in the Breezy 5.10 on amd64. And yeah, is a little bit disapointing to use 32 bits apps on a 64bits... someone remember the old days of 16bits/32bits on, say, win3.1?? :-)

---

### Post by ispmarin on 2005-12-28
News: finally Sun leashed the java for amd64 platforms. Strange, there is a java for sparc64 for long time... but my list is a little short now. 
Cheers!

---

### Post by skylark on 2005-12-28
[QUOTE=ispmarin]I think that there is enough public with amd64 processors for the companies and even ubuntu development community to think more seriously about this architecture. I am not a very good programmer, and I am always filling bug reports and posting when something gets to work. But how can we (or I) put more pressure on the companies or help more to get better software and support? And...
Chroot. Don't talk to me about chroot...[/QUOTE]
I completely agree ispmarin, there are still numerous problems with certain Linux applications on amd64. I think if more developers had AMD64 machines most of these issues would be resolved. The lack of 64-bit drivers/codecs from certain companies though would still be a big stumbling block. I believe some of these problems plague windows on AMD64 too though!

However, I disagree with your views on a 32-bit chroot. Yes, it is a small hassle to setup and maintain and in the long term is not ideal... but I believe it does have some hidden advantages. For example I use firefox/flash/totem/xine from a chroot - if any of these applications have security issues the chroot provides an extra layer of protection against attackers.

It would be great if a the setup of a 32-bit chroot was an option in the AMD-64 ubuntu install with tools provided to easily manage it... I think it would be an acceptable short-term solution.

---

### Post by olivierp on 2005-12-28
[quote=ispmarin]News: finally Sun leashed the java for amd64 platforms. Strange, there is a java for sparc64 for long time... but my list is a little short now. 
Cheers![/quote]

Umm... it's been around for quite some time.
Real news will be when the Browser footnotes here change:
[http://java.sun.com/j2se/1.5.0/system-configurations.html#browsers]("http://java.sun.com/j2se/1.5.0/system-configurations.html#browsers")
And upvote this, if you can:
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695")

---

### Post by poofyhairguy on 2005-12-29
[QUOTE=ispmarin]Hello everybody. I have now for six months a amd64 running ubuntu 5.10 (previosly hoary) and some little things really annoy me. Some are ubuntu's, others are from third party companies. Here is my list:
1. Browser plugins. Flash, quicktime, NOTHING is working nicely. Or working.
2. OpenOffice 2 is buggy. Really buggy.
3. (TP)Opera is not avaliable yet. I really enjoy Opera.
4. (TP)Skype.
5. (TP) Games in general...
6. Java?
I think that there is enough public with amd64 processors for the companies and even ubuntu development community to think more seriously about this architecture. I am not a very good programmer, and I am always filling bug reports and posting when something gets to work. But how can we (or I) put more pressure on the companies or help more to get better software and support? And...
Chroot. Don't talk to me about chroot...

See ya![/QUOTE]

Everything you mention (even OpenOffice) sucks in 64 bit Ubuntu because of lack of third party support.

The Ubutnu devs do a GREAT job for the things they can control. For the rest.....thats your deal.

---

### Post by Ribs on 2005-12-29
I disagree with your list here...
Skype static works okay, so I've been told, not checked this myself tho.
Java. Blackdown 1.4 java has a working browser plug-in. I actually installed Blackdown, and then Sun Java afterwards. With this I get blackdown 1.4 in firefox, and Sun's Java 1.5 for everything else.
OpenOffice is improving, honestly. They are working on getting it 64-bit clean. If you can't wait for that, consider using Abiword.
Browser plugins... Well, I've got Java going, as I said. mplayer-plugin works pretty well for movies, only wmv version 9 files appear to have problems. Totem has issues...
Games. Well, I've got Cedega working just great, so that's Windows Games okay. UT2004 has native 64-bit support.

Only issue I have is Flash. Current open source stuff doesn't cut it. And dispite CrossOver claiming it supports 64-bit plugins for browsers, I couldn't get it working...

I don't blame you for not chrooting. I don't either, I really don't feel it's the soultion to our problems. Things will get better, it's just a matter of time now, I know the wait is frustating, but things have already come a long way in the past year.

---

### Post by MagicNo14 on 2005-12-29
I have to agree that a lot of things are a real pain on Ubuntu 64-bit. I have been struggling for weeks to get things up and running a bit, and I am a programmer, so I know my way around computers a bit. Making the switch to linux is hard enough without having to recompile your kernel, build 32-bit packages and so on to get the functionality you need.

It is true that most of the problems are caused due to the unavailability of third party libraries, however the average user does not make that distinction. I find it incomprehensible that there is so little available for 64-bit linux.

I came upon this thread looking for help on installing the java plugin. I have managed to install firefox 1.5 32 bit (on ubuntu 64 bit). Will this cause problems if I try to install the plugin of either sun or the blackdown version? I can safely say I will run into several problems, as everything else I tried to install did. I'm not giving up though.... :p 

However I will leave this for later, because thanks to this thread i found out ut2004 should work on ubuntu. That will be my first priority... ;)

---

### Post by JuanC on 2005-12-29
[QUOTE=olivierp]
And upvote this, if you can:
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695")[/QUOTE]

In this link i saw this :
> 
State  : In progress, request for enhancement

What does it mean?

Sun is working on amd64 java plugin?

---

### Post by JuanC on 2005-12-29
Another issue about Flash :
[http://www.kaourantin.net/2005/12/flash-player-8-for-linux-update.html](http://www.kaourantin.net/2005/12/flash-player-8-for-linux-update.html)

> 
Instead of releasing a 8.0 version we will directly move to 8.5 on Linux .... 64bit versions will take a little longer, there are no definite plans just yet. Just recompiling will not work unlike what you might think. The main issue here is the x86 JIT in the virtual machine and the mark&sweep garbage collection which are not 64bit aware right now, work on 32bit pointers only.


---

### Post by olivierp on 2005-12-30
[quote=JuanC]In this link i saw this :

What does it mean?

Sun is working on amd64 java plugin?[/quote]

Look a few lines lower on the page, at the evaluation, and most importantly, when that evaluation was updated...

---

### Post by nrayever on 2005-12-30
might be that some of those programs are needed, but still without them you can survive.

but have them for 64 bits will be great!!

---

### Post by nothreat33 on 2005-12-31
After readin this I tryed installing Skype and I got it working.

Heres how I did it:

Installed gcc

```
sudo apt-get install gcc-3.3-base
```

```
sudo apt-get install libstdc++5
```

Downloaded the i386 libraries skype needs.

```
wget http://ftp.us.debian.org/debian/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.4-3_i386.deb
```

Installed them as 32-bit

```
dpkg --force-architecture -i libqt3c102-mt_3.3.4-3_i386.deb
```

Go here: [http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/) and download the debian package of skype

Install Skype

```
sudo dpkg --force-architecture -i skype_1.2.0.18-1_i386.deb
```

---

### Post by ispmarin on 2006-01-02
Well, u usually uses latex for text papers, but for something quick and dirty (or even to do a more sofisticated document), a WYSWYG editor like openoffice is the best solution, but it's still sucks. I did not had the time to install the java from sun and the blackdown to see how it is working (holidayes and etc), but i will test as soon i get to the lab. And yeah, ut2004 is very well supported in ubuntu64(was running like a charm, well, more or less like a charm ;-) )
Well, after complaining a lot, what can we do, in the open source community, to improve this condition? Send tons of emails to the companies, what? I cannot see how can we emphazyse more that the amd64 community is already very large, large at least for a 64 bit version of a flash player of a decent media player (sorry, but mplayer is not working very well, and totem really has it issues.) Maybe we should start a campaign or something like that? Post here the numbers of amd64 desktops sold in the last year? I am open to sugestions... and willing to embrace a good idea!

Ivan

--Happy new year to everyone.

---

### Post by ispmarin on 2006-01-02
I really don't know why, but the static compiled skype does not work very well, at least not like the shared version on a 32bit machine... and install the 32bit version on a amd64 is just the point of this post, that is, does NOT install the 32bit version, but has the 64bit version...

Third Parties, HEAR US!! (didn't resist, maybe the new year spirit... :-) )

Ivan

--Happy new year to everyone.

---

### Post by Aphorism on 2006-01-03
Once again -- the problem isn't with 64bit Linux.  

For the time it takes you to post, you could be persuading these companies to provide some documentation and specifications so that we aren't relying on them to provide their crappy software.  If they ignore us, ignore them -- switch to alternatives and plod onwards. 

Just a few cents...

---

### Post by ispmarin on 2006-01-03
[QUOTE=Aphorism]Once again -- the problem isn't with 64bit Linux.  

For the time it takes you to post, you could be persuading these companies to provide some documentation and specifications so that we aren't relying on them to provide their crappy software.  If they ignore us, ignore them -- switch to alternatives and plod onwards. 

Just a few cents...[/QUOTE]

This would be the best of all worlds, but I don't think that this companies will be willing to give away the documentation and specifications. They developed the applications, so, right or wrong, is their choice to give or not. But I agree with you: things that are so widespread HAVE to have the documentation avaliable to others be able to develop better software. But this is a paradigm shift for that companies, and sometimes we need a fast solution. So I think that we can do both things: put pressure to get their crappy but sometimes necessary software while ge fight to get the specifications. 

Ivan

-- Happy new year to everyone.

---

### Post by Aphorism on 2006-01-03
> put pressure to get their crappy but sometimes necessary software while ge fight to get the specifications.


I don't believe that their software is necessary at _all_.

The reality is that in the early going we as a computing population made some poor and ill informed choices on how to run *publically* controlled areas, such as the internet, our personal music, etc.

If we as a public spread the truth about these silly decisions (Read:  Java, Flash, MP3, etc) we can help to educate the rest of the folks who have yet to see the problems inherent with such technology choices.

And yes, there *are* alternatives to each of these (Read:  HTML, Ruby-on-Rails, etc).

Personally I have done the following since switching entirely to an open source based computing environment and I would encourage everyone to at least do the same via email:

[LIST]
[*]Notified the BBC of their closed source choice for broadcasting radio.  I pointed out that the wonderful information they have is being limited now to a new breed of 'haves' and 'have nots'.
[*]Sent email to both Nvidia and ATI while I waited for their drivers to catch up to 64 bit.
[*]Sent letters of thanks to companies for supporting ogg vorbis, etc, and stated that ogg was the sole reason I chose their products.
[*]Similar actions such as this...
[/LIST]

Speak with your money and your voice.

---

### Post by kurushi on 2006-01-04
Hi

I wrote a manual some days ago, about how to use Firefox 1.5 with Flash and Java support in Ubuntu Breezy for amd64. I hope it will help you.  This is the link :

:KS  [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

See you soon

---

### Post by Aphorism on 2006-01-04
The problem here is Kurushi is that you are trying to help out a company that chooses to restrict its software use.  Why help a company that doesn't want to have its software used everywhere?

Get the point?

If it were truly a 'standard' and had no alterior motives, it wouldn't be bound up with end user license agreements and such.


Question why the software needs a eula and what a company might have as an ultimate goal.  I think that we, as the earlier generation of amd64 bit operating systems can forge a healthy fresh start by *avoiding* kludges and supporting open software with open standards.

---

### Post by kurushi on 2006-01-04
Mmmm, Interesting reply.

I'm not helping any company, just helping users to go to 64 bits missing very few things from other systems.

In my opinion the ones who develop software must change their politics, and use starndard and open technologies. I do, and is not a big deal.

I also wrote mails to Macromedia, Adobe, Ati, Sun, Google, and many other companies, asking explanations about their software for linux 64 bits systems (for Ubuntu exactly), but I can't force them to develop products, I understand than their job is make money and the amount of 64 bits linux users is too few. But I invite everyone to mail these companies too (respecting everyone of course).

Still now, we are very few users using 64 bits linux, and in my opinion there will be more users with 64 bits installations if they have solutions for Flash, Java and the things they need.

What I can do for the users is try to help them, when they have non covered needs by third party companies. In this case, I found the way to use Flash and Java in Ubuntu 64 bits distributions, all of us know than actually these technologies are everywhere (for example my goverment's web site : [www.gencat.es](www.gencat.es)).

If I want to be a 'full time' linux user, I have to use these technologies in my default system, otherwise I'll be obligated to use other systems when a website uses these technologies.

My tutorial is for the "humanity to others" idea. I hope than with my tutorial, some users of 32 bits systems owners of 64 bits computers, will jump to 64 bits Ubuntu, making bigger the "free software" idea.

Thank you very much for your attention, see u soon, kisses

Albert

---

### Post by Aphorism on 2006-01-04
First, the open source community does *not* want these companies to support a particular operating system at all!  We do want them to fully disclose their specifications and documentation so that *we* can write the software *we* want, without EULAs and the rest of it.  If they want to truly 'compete' -- they should compete against everyone.

What if there is an exploit in Realplayer?  Must we wait for them to 'fix' it with some half assed coding effort that led to the flaw in the first place?  What about Java(TM) in this vein?  Flash?

You see my point?

You are better off telling the limiting sites that are using this technology why it is an awful choice, and that you will no longer support them.

It's pretty simple, but if we keep giving into them, they will keep flogging their ways.

---

### Post by kurushi on 2006-01-04
Ok

In my opition these companies can do whatever they want with they money, if they want to develop software and close the source for their programmers, then its ok for me. I understand than people doesn't work for free, and they have to win money somehow. I respect their decisions even if I'm not agree.

What I think is than the open source sofware is the best choice for end users, specially the use of open standards, because everyone can develop and improve everything. In my opinion clients must feel free all the time, and they only have this sensation if the source is available, and there's a lot of information about the products. The most part of clients only will install and use the software without look at the insides, but they will feel better if you don't keep hide things.

Hei, I'm using Ubuntu! This is a great system, we know it, but still know is difficult to use like desktop, because 'normal' users doesn't know how to manage it. But if I'm using Ubuntu is because is the easier UNIX like system since OSX. I tried with Fedora, Debian, Mandriva, Knoppix, ... , and I always came back to Windows. Except with Ubuntu, for me Ubuntu is the best system actually. But when I was telling it to my friends, they only said things like: Your .pdf viewer sucks, and you don't have flash, looking to me like if I was crazy.

Ubuntu pretends to be for desktops, for everyone's desktops. Ubuntu developers are doing a great job, but still now it must be improved. Maybe one day it will be enough easy and I will say :

- Hey mum, I changed your computer's system, come here I teach you how to use it, we only need half a hour because is really simple. You'll love it.

That day there will be a lot of people using Ubuntu, and software companies will have to develop programs for Ubuntu, maybe open source or maybe not. But everyone will have the choice to choose a good and free system for their desktops.

Of course I'm asking for "free software", but I'm a programmer and if my contract says everything must be closed, then I've nothing to discuss. Do you really think than Mark Shuttleworth arrived at the ISS for free? Use or sell software doesn't means than somebody is a good or a bad person, is just an option.

I ask for "free software" for everyone, and for "free medical help" also. But I continue buying software when I need it, like I continue buying medicines when I'm flu. And it is not a moral conflict for me, what's a moral conflict is to see people without resources because of they don't have money, that's what makes me feel upset. 

And that's why I want to help people start using Ubuntu if this is the point. With more Ubuntu users, there will be more resources. With the idea of, you just have to stop using propietary software, people only will think than you are appart of the world and the amount of linux users won't grow up. And we all now the result of this, the 80% of people using the worst operating system (at least now with Windows XP). The most part of people doesn't know than computers can be something different than Windows, for them these concepts goes together. 

Well, I think than now my opinion is clear, thanks for this chating time.

---

### Post by Aphorism on 2006-01-04
A) You can sell hardware and make money and keep your source open.  You can sell software and keep your source open and make money.

B) Computer literacy doesn't equate with 'simple' or 'easy'.  In fact, it is computer illiteracy that has gotten us into this problem in the first place.  Learning how to read and write doesn't happen with a point and a click on your iPod(TM), but it is perhaps one of the most valuable, albeit difficult, things you will ever learn.

---

### Post by Jave27 on 2006-01-04
Kurushi, thank you for explaining to everyone how to complete these tasks.  There are people on this forum that would like to accomplish the same things, regardless of politics, and your work will help them do that.  Aphorism has some good points as well, but the fact remains that you have contributed to Ubuntu, and for that we're all grateful.  Until someone comes up with a competitor to Flash that is as easy to use and design stuff for your everyday Joe Web-Designer, Macromedia holds all of the cards.  The great part about Open Source software is that you can *choose* whether or not to install their Flash player on your computer.  

Until now, installing their available player on an AMD64 machine was exceptionally difficult.  Now that you've helped, it's only marginally more difficult than installing other apps.  Personally, I'm not a big fan of Flash sites, but I can see their uses.  Anyway, just wanted to add a "thank you" to the thread instead of just attacking your philosophy.  If another user disagrees with you, they can just stick to the standard repos and live with them.

---

### Post by kurushi on 2006-01-04
Think easy doesn't mean illiteracy

Thank you very much for this last comment,  is very nice and I'm really appreciating.

---

### Post by ispmarin on 2006-01-05
Wow, never imagined that this thread will spread so much when I started it. Nice to see that different points of view are discussing and maybe together heading to a common goal and a way to do it. 

The way I see it, we have both needs and wishes. Every company is free to use a non-standart software, like flash. We are free, also, to do not access the site of that company. But, what do do when we need to? Second point: Open standards are much better for everybody, not just for some. But they need the colaboration of everybody. And sometimes, we just don´t have the time or will or the money to develop our own. Sometimes closed software is just what we need in the situation. And of course, programmers have to be paid (and hardware or support sometimes just can´t pay everybody). Here is the distinction: closed software does not mean closed standard. I agree that the standards must be open to everyone, and you can close or not your source code. And we should not enforce closed standards. Point.

But we have to be practical: some closed standards, we like it or not, are very widespread, like flash. And we must have a solution to the open source community to deal with this kind of problem. Workarounds maybe works for some time, but not for so long or the way it should work while the companies does not make the "official" software to the platform. This is not the point. And, like was said before, workarounds are not for the faint of heart usually (and I think that read and write is basic, while patch a kernel is not.) So, what can we do? First, we should not endorse, of course, this kind of company. The iniative to tell the companies and everybody how nice they are is a good one, and should work also with the hardware department (I think that in the hardware department the things have improved a lot in, say, the last 5 years).Second, we can put some pressure on the companies buying or not theirs products. (Everytime I call a support team or try to buy some soft or hard, I ALWAYS ask about linux support, linux compatibilities, linux drivers, etc... ALWAYS. And also fill complaints when the support does not have linux capabilities).

And what else? Maybe we should sinthetyze or arguments posted here, even with the different points of view (in the same or different documents), and send it to some major hardware (like AMD) and software (like Macromedia) companies, and even to the Ubuntu and linux community, and, why not, some media vehicles (like slashdot). 

Are you up to the task?

Thank you everybody.

Ivan

---

