---
title: "thunderbird 2"
date: 2007-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by jamesford on 2007-05-27
i got the tbird2 tarball from mozilla and just extracted and run but it looks odd, it doesent take on the murrine theme look that im using. is this because its not 64 bit? where are the 64 bit tarballs and or debs hiding?

---

### Post by atlfalcons866 on 2007-05-27
you have to compile it

---

### Post by jamesford on 2007-05-27
how do i do that? thers no ./configure stuff

edit:nevermind i found a deb deb [http://gnomefreak.youmortals.com/mozilla-testing](http://gnomefreak.youmortals.com/mozilla-testing) feisty main

---

### Post by firecat53 on 2007-05-27
Kilz also posted a 64-bit compilation of Thunderbird on this forum a month or so ago. Worked great!!

Scott

---

### Post by Kilz on 2007-05-27
> **firecat53 said:**
> Kilz also posted a 64-bit compilation of Thunderbird on this forum a month or so ago. Worked great!!

Scott

[Yes, this one ]("http://www.filecrunch.com/file/~li7z9p")

---

### Post by jamesford on 2007-05-28
hey thats brilliant
thanks firecat53 and kilz

---

### Post by StratosL on 2007-05-28
Kilz, once again you are a life saver!
 
I would just like to push my luck a little and see what happens....  need advise on this one:

Since I installed the 64 bit version, the lightning extension does not work (integrated calendar). This was very useful for me, as I had set it up to use my Google calendar (through another extension, "provider for Google calendar"). This was extremely useful.

I should probably contact the person who makes the extension, I suppose.

---

### Post by StratosL on 2007-05-28
will give it a shot at compiling lightning.

the source is >>  [here]("/pub/mozilla.org/calendar/lightning/releases/0.3.1/source") <<

---

### Post by StratosL on 2007-05-28
Wow! that took some time! Gathered info from all over google and mozilla, here's the story:

1) Ok, so I downloaded the >> [source code]("http://pub/mozilla.org/calendar/lightning/releases/0.3.1/source") <<. 

2) extracted to a new directory

3) made a file .mozconfig in that directory, with contents:
(not sure if this step was needed at all, but it doesn't hurt)

```
ac_add_options --enable-optimize --disable-debug
ac_add_options --disable-tests
ac_add_options --enable-application=mail
mk_add_options MOZ_CO_PROJECT=mail,calendar
ac_add_options --enable-extensions=default,lightning
```

and run

```
export MOZCONFIG=~/{whatever}/source/mozilla/.mozconfig
```

4) run configure
```
./configure --enable-application=mail --enable-extensions=default,lightning
```

5) run make

```
make
```

6) go make a cup of coffee

7) you'll find the lightning.xpi file in the directory dist/xpi-stage

I also tried downloading the 64bit xpi from >>[mozilla contrib]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.3/contrib/")<<, but although it installed, it wouldn't run at all.

I even tried this trick >>[from debian etch]("http://eccentric.cx/wordpress/2006/11/22/icedovethunderbird-lightning-calendar-extension-on-debian-etch/")<<, but still no luck. 

Had to compile from scratch.
I'm sure one day we'll look back at these posts and laugh. I would have thought Tb 2.0 with everything on it would be in the repos by now.

PS
enigmail has  [a 64bit version]("http://enigmail.mozdev.org/download.html")

---

### Post by Kobalt on 2007-05-28
Thanks a bunch Kilz for that 64bit compilation of yours.... ! ;)

---

### Post by Kilz on 2007-05-28
> **KARINA123 said:**
> i got the tbird2 tarball from mozilla and just extracted and run but it looks odd,

If you got a tarball from mozilla, it is a 32bit version, mozilla doesnt build 64bit builds. Most of the time they will run, but wont look as nice as a 64bit version.

---

### Post by jamesford on 2007-06-06
is it just me or is the tbird 2.0 icon really ugly?
is there a way to fix this?
[[img]http://bildr.no/thumb/73105.jpeg[/img]](http://bildr.no/view/73105)

---

### Post by capecove on 2007-06-06
> **Kilz said:**
> [Yes, this one ]("http://www.filecrunch.com/file/~li7z9p")
I tried getting this file three times but was told all times that it was corrupt. Maybe there is something wrong with the file on the server? I was able to get Thunderbird 2 going anyhow, just wanted to give a heads up on that. Thanks for your help!

---

### Post by ecs_pf5 on 2007-06-08
Yes looks like I'm getting the same here at the moment

```

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

I'm trying to extract it on Feisty 7.04, using File Roller 2.18.1

My Feisty was text-installered from the alternate CD

As a sidenote I was overjoyed and massively impressed that the 32-bit Thunderbird 2.0.0.0 I'm making do with at the mo, accepted my old profile folder from Windows XP! How's that for cross platform compatibility.

Looking forward to trying a 64 bit build though..

---

### Post by jonasback on 2007-06-09
Fetch the deb-packages instead. :) That'll work just fine. Did it myself earlier today.

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

---

### Post by michael37 on 2007-08-10
Lightning howto is now live [https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

---

### Post by cyb3rj on 2007-09-18
> **jonasback said:**
> Fetch the deb-packages instead. :) That'll work just fine. Did it myself earlier today.

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

That solved it for my needs.  Very nice indeed.

I'm still waffling about my x64 decision because of having to hunt harder to find packages.  I'm hoping Gutsy will offer more of my favorites readily available.

---

### Post by Kilz on 2007-09-18
Just to let everyone looking for Thunderbird 2 know. I asked Stickk to build a version of thunderbird. So [the Swiftweasel project ]("http://swiftweasel.sourceforge.net/")has released a version of Thunderbird called [Swiftdove]("http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=243203"). It is a build of the Thunderbird 2 source and it has deb files available. The application installs easily and will install to Dapper, Edgy, and Feisty.

---

### Post by FLCLFan on 2007-09-18
> **Kilz said:**
> Just to let everyone looking for Thunderbird 2 know. I asked Stickk to build a version of thunderbird. So [the Swiftweasel project ]("http://swiftweasel.sourceforge.net/")has released a version of Thunderbird called [Swiftdove]("http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=243203"). It is a build of the Thunderbird 2 source and it has deb files available. The application installs easily and will install to Dapper, Edgy, and Feisty.
Thats fantastic, I thought Swiftweasel was their only project. Swiftdove 2.0.0.6 x64 is much better then the Thunderbird 2.0 I had. :)

*Thunderbird just got apt-get removed* :D

---

### Post by crjackson on 2007-09-18
> **Kilz said:**
> [Yes, this one ]("http://www.filecrunch.com/file/~li7z9p")

Do I need to remove the older version b4 I install this, or can I just install over top of the old?

---

### Post by crjackson on 2007-09-19
> **crjackson said:**
> Do I need to remove the older version b4 I install this, or can I just install over top of the old?

Disregard.  I added the repository and let it do the automatic update...

---

### Post by crjackson on 2007-09-19
> **StratosL said:**
> Wow! that took some time! Gathered info from all over google and mozilla, here's the story:

1) Ok, so I downloaded the >> [source code]("http://pub/mozilla.org/calendar/lightning/releases/0.3.1/source") <<. 

2) extracted to a new directory

3) made a file .mozconfig in that directory, with contents:
(not sure if this step was needed at all, but it doesn't hurt)

```
ac_add_options --enable-optimize --disable-debug
ac_add_options --disable-tests
ac_add_options --enable-application=mail
mk_add_options MOZ_CO_PROJECT=mail,calendar
ac_add_options --enable-extensions=default,lightning
```

and run

```
export MOZCONFIG=~/{whatever}/source/mozilla/.mozconfig
```

4) run configure
```
./configure --enable-application=mail --enable-extensions=default,lightning
```

5) run make

```
make
```

6) go make a cup of coffee

7) you'll find the lightning.xpi file in the directory dist/xpi-stage

I also tried downloading the 64bit xpi from >>[mozilla contrib]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.3/contrib/")<<, but although it installed, it wouldn't run at all.

I even tried this trick >>[from debian etch]("http://eccentric.cx/wordpress/2006/11/22/icedovethunderbird-lightning-calendar-extension-on-debian-etch/")<<, but still no luck. 

Had to compile from scratch.
I'm sure one day we'll look back at these posts and laugh. I would have thought Tb 2.0 with everything on it would be in the repos by now.

PS
enigmail has  [a 64bit version]("http://enigmail.mozdev.org/download.html")

The page you listed for source code seems to be a broken link now.  I found a 64-xpi and installed it.  The calendar appears in Thunderbird but you can't edit or make any changes.  I removed it.

---

### Post by nanotube on 2007-09-20
you might also consider using the ubuntuzilla project to install the mozilla build of thunderbird. 

[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

for 64bit users, there's one outstanding issue in that audio notifications seem not to work, but besides that, there you are. :)

---

### Post by Kilz on 2007-09-20
The problem is, the mozilla build is only 32bit. Swiftdove provides an optimized 64bit build that is fast. I am currently helping test a Swiftdove 2.0.0.7pre build that is very fast, even faster than the 2.0.0.6 build.

---

### Post by nanotube on 2007-09-20
> **Kilz said:**
> The problem is, the mozilla build is only 32bit. Swiftdove provides an optimized 64bit build that is fast. I am currently helping test a Swiftdove 2.0.0.7pre build that is very fast, even faster than the 2.0.0.6 build.

that sounds pretty cool - if i were a 64bit user, i might give it a try myself. :)

i'm curious - in what way is it "fast"? i'm on 32bit, so i use the mozilla build of tb, and it seems plenty fast to me, it's not like it's hanging or lagging or anything... how do you measure that it's faster? maybe searching benchmarks?

---

### Post by Kilz on 2007-09-20
> **nanotube said:**
> that sounds pretty cool - if i were a 64bit user, i might give it a try myself. :)

i'm curious - in what way is it "fast"? i'm on 32bit, so i use the mozilla build of tb, and it seems plenty fast to me, it's not like it's hanging or lagging or anything... how do you measure that it's faster? maybe searching benchmarks?

Granted its just perception , I dont have benchmarks. But it seems to start up faster, it also seems to process things faster than the Ubuntu versions. [Swiftweasel and Swiftdove]("http://swiftweasel.sourceforge.net/") are available as 32bit builds if you want to test them or try thrm out. There are deb files, just double click on one and let gdebi install it.

---

### Post by nanotube on 2007-09-20
> **Kilz said:**
> Granted its just perception , I dont have benchmarks. But it seems to start up faster, it also seems to process things faster than the Ubuntu versions. [Swiftweasel and Swiftdove]("http://swiftweasel.sourceforge.net/") are available as 32bit builds if you want to test them or try thrm out. There are deb files, just double click on one and let gdebi install it.

i'll stick with what i have for now. no reason to rock a working boat. :)

by the way, how's swiftweasel different from swiftfox (getswiftfox.com) ? seems like they are the same thing? i have tried swiftfox before, and went back to regular mozilla build, because swiftfox didn't seem any faster. 

since you are the big proponent of swiftdove, i leave the benchmarking to you. :) one test i can think of is searching through a large mailbox - can be timed with a stopwatch, since it's a long enough process (given a large enough mailbox). other than that, i'm not sure what there is to actually measure, in terms of speed... for the browser, you could measure the speed of rendering some large complex website...

---

### Post by Kilz on 2007-09-20
> **nanotube said:**
> i'll stick with what i have for now. no reason to rock a working boat. :)

by the way, how's swiftweasel different from swiftfox (getswiftfox.com) ? seems like they are the same thing? i have tried swiftfox before, and went back to regular mozilla build, because swiftfox didn't seem any faster. 

since you are the big proponent of swiftdove, i leave the benchmarking to you. :) one test i can think of is searching through a large mailbox - can be timed with a stopwatch, since it's a long enough process (given a large enough mailbox). other than that, i'm not sure what there is to actually measure, in terms of speed... for the browser, you could measure the speed of rendering some large complex website...

Swiftfox and Swiftweasel are complete different projects. The main difference to me is how the project is done.
Swiftfox is a proprietary application. It has a restrictive license. There have been numerous posts and problems getting the person doing Swiftfox to give back the changes as the MPL requires. The optimizations that have been released have been minor. [The person doing Swiftfox has had problems with people.]("http://www.linux.com/articles/61334")
Swiftweasel is open source, even the artwork is under an open source license. The changes are posted with each version and whenever the person doing swiftweasel is asked to do something he seems real nice and tries to help. Looking at the changes it looks like a lot of improvements compared to what swiftfox does. Also Swiftweasel is both 32 and 64bit. Swiftfox is only 32bit, even the builds for 64bit processors.

An example is I wrote asking for an email client, stickk wrote back saying he would be glad to. He asked me to help test a release, so I did.

---

### Post by nanotube on 2007-09-20
> **Kilz said:**
> Swiftfox and Swiftweasel are complete different projects. The main difference to me is how the project is done.
Swiftfox is a proprietary application. It has a restrictive license. There have been numerous posts and problems getting the person doing Swiftfox to give back the changes as the MPL requires. The optimizations that have been released have been minor. [The person doing Swiftfox has had problems with people.]("http://www.linux.com/articles/61334")

i know they are different projects - i was asking whether what they are doing, in terms of the end result, is not the same. because if they are doing basically the same thing, and swiftfox is not any faster for me, then swiftweasel probably won't be, either. that was my thinking, anyway. :) 

hm, i have read the swiftfox license, and while it prohibits redistribution of the /binary builds/, the source code and the build configurations are all open and freely sharable. while that's not quite as nice as what we're used to, it still doesn't quite fall into the "proprietary application" category i'd say. it's still open source, just not open binary. :)

still, clearly it's nicer to have software under a fully open license, i agree.

> Swiftweasel is open source, even the artwork is under an open source license. The changes are posted with each version and whenever the person doing swiftweasel is asked to do something he seems real nice and tries to help. Looking at the changes it looks like a lot of improvements compared to what swiftfox does. Also Swiftweasel is both 32 and 64bit. Swiftfox is only 32bit, even the builds for 64bit processors.

An example is I wrote asking for an email client, stickk wrote back saying he would be glad to. He asked me to help test a release, so I did.

hm, well, i can't speak for developer personality for either of these guys, but you make a pretty strong case for that stickk guy. :) i suppose next time i want to try a custom-built mozilla binary, i'll be looking at weasel/dove, rather than fox. 

anyway, please post any test results if you ever get around to doing some - i'd be interested to see if there are any /measurable/ speed improvements. "feels faster" just doesn't qualify as evidence in my book. :)

---

### Post by Kilz on 2007-09-21
> **nanotube said:**
> i know they are different projects - i was asking whether what they are doing, in terms of the end result, is not the same. because if they are doing basically the same thing, and swiftfox is not any faster for me, then swiftweasel probably won't be, either. that was my thinking, anyway. :) 

hm, i have read the swiftfox license, and while it prohibits redistribution of the /binary builds/, the source code and the build configurations are all open and freely sharable. while that's not quite as nice as what we're used to, it still doesn't quite fall into the "proprietary application" category i'd say. it's still open source, just not open binary. :)

still, clearly it's nicer to have software under a fully open license, i agree.



hm, well, i can't speak for developer personality for either of these guys, but you make a pretty strong case for that stickk guy. :) i suppose next time i want to try a custom-built mozilla binary, i'll be looking at weasel/dove, rather than fox. 

anyway, please post any test results if you ever get around to doing some - i'd be interested to see if there are any /measurable/ speed improvements. "feels faster" just doesn't qualify as evidence in my book. :)

From what I have read, not all swiftfox source is shared. That any questions about it are /were deleted from its forum. [This link.]("http://www.linux.com/articles/61334") has a lot to say about that, especially in the comments. [This site has a little more.]("http://www.getswiftfox.org/"). So while the MPL may require it, they are not doing it. The Code for Firefox is available but since the code (or not all of it) for Swiftfox isnt shared, its proprietary imho.
The patch in the Swiftfox site is for one settings file. Looking at the same for swiftweasel it impacts lots of files. Im not much into testing so I dont have the data you want. I couldn't find any data on the net either. since its a ten meg download everyone can get it and try it if they want.

---

### Post by michael37 on 2007-09-21
> **Kilz said:**
> From what I have read, not all swiftfox source is shared. That any questions about it are /were deleted from its forum. [This link.]("http://www.linux.com/articles/61334") has a lot to say about that, especially in the comments. [This site has a little more.]("http://www.getswiftfox.org/"). So while the MPL may require it, they are not doing it. The Code for Firefox is available but since the code (or not all of it) for Swiftfox isnt shared, its proprietary imho.
The patch in the Swiftfox site is for one settings file. Looking at the same for swiftweasel it impacts lots of files. Im not much into testing so I dont have the data you want. I couldn't find any data on the net either. since its a ten meg download everyone can get it and try it if they want.

This is an extremely serious licensing infraction for Swiftfox.  My recommendation is definitely staying away from it.

Get Swiftweasel instead from sourceforge.

---

### Post by StratosL on 2007-10-24
> **crjackson said:**
> The page you listed for source code seems to be a broken link now.  I found a 64-xpi and installed it.  The calendar appears in Thunderbird but you can't edit or make any changes.  I removed it.

With Gutsy Tb2, install the lightning extension from synaptic and the google calendar provider will just work!

---

### Post by crjackson on 2007-10-24
> **StratosL said:**
> With Gutsy Tb2, install the lightning extension from synaptic and the google calendar provider will just work!

At the time of my original post I wasn't using Gutsy as it was not released for production systems yet.  As you can see, I now use Gutsy and TB2 works nicely.  Thanks...

---

