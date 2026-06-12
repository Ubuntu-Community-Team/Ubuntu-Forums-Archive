---
title: "Do Not Upgrade Wine!!"
date: 2008-10-11
forum: Wine
---

### Post by david_kt on 2008-10-11
I have seen posts something like these:

```
- I updated wine with automatic update and now NONE of my apps work.
- WoW has worked perfectly for me until now when i updated wine to 1.1.6
```

Listen to me folks, _DO NOT UPGRADE WINE_ unless you are able to troubleshoot your problem, or at least you are willing to run regression test and feedback to wine developer. But even after you submitted the regression test result, you need to wait for sometime until there is a patch or future release (not necessarily subsequent release) with that patch.

If you are satisfied with any version of wine, lock it to refuse all future updates. That is your "stable version of Wine". I still have wine 0.9.43 on 10 computers to run office 97. It is very tedious to troubleshoot wine, especially for office 97 which not many people are using. And to continuously upgrade and downgrade wine on 10 computers definitely very boring and people would complain as their computers are frequently "breakdown".

Wine developers are very active, they release upgrade almost every week. But remember, those upgrades are development version, not stable release. So, do not treat it as stable release and start complaining to wine developers because those upgrades break many things. You could always feedback your problem, but that means you are "beta tester" and you should give sufficient information for the wine developers to work on, for example using regression test.

To lock wine version, open synaptic:

```
System >  Administration > Synaptic Package Manager
```
```

click on wine > click package on the menu > click lock version 
```

After this you will see a lock in wine package and updater will ignore wine upgrades.

But if you do not want to lock your wine version as you want to test latest wine, at least install your "stable wine" on custom directory, so as you will still have "your stable wine" when you upgrade your default wine. I saw some users even do not know when their application start to stop working as there are numerous wine upgrades before they realize that some of their applications stop working.

For this purpose, I have made an installer that help you to install many wine versions at the same time. I have not try regression test my self, but after I try it, I will make a script as well to make it easy to run regression test, and then report the result to wine developer. If I have completed this script, all of you could be beta tester for wine. But for now, please lock your wine version, or install multiple wine using below installer and instruction:

[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

DK

---

### Post by asdfoo on 2008-10-11
> **david_kt said:**
> I have seen posts something like these:

```
- I updated wine with automatic update and now NONE of my apps work.
- WoW has worked perfectly for me until now when i updated wine to 1.1.6
```

Listen to me folks, _DO NOT UPGRADE WINE_ unless you are able to troubleshoot your problem, or at least you are willing to run regression test and feedback to wine developer. But even after you submitted the regression test result, you need to wait for sometime until there is a patch or future release (not necessarily subsequent release) with that patch.


The more people who use the development releases the better.  If everyone tests their "must-run" software with these releases and reports the problems that is the best way they can help Wine.

> **david_kt said:**
> 
If you are satisfied with any version of wine, lock it to refuse all future updates. That is your "stable version of Wine". I still have wine 0.9.43 on 10 computers to run office 97. It is very tedious to troubleshoot wine, especially for office 97 which not many people are using. And to continuously upgrade and downgrade wine on 10 computers definitely very boring and people would complain as their computers are frequently "breakdown".


If you lock your version of Wine to an old release and do not test with a development release you are not helping the Wine project.  If an application breaks and goes unnoticed because everyone sticks to an old version then that is not good for anyone.

> **david_kt said:**
> 
Wine developers are very active, they release upgrade almost every week. But remember, those upgrades are development version, not stable release. So, do not treat it as stable release and start complaining to wine developers because those upgrades break many things. You could always feedback your problem, but that means you are "beta tester" and you should give sufficient information for the wine developers to work on, for example using regression test.


Yes, as soon as any user notices that a regression has occurred they should file a bug report at [http://bugs.winehq.org](http://bugs.winehq.org) with the results of their regression test

> **david_kt said:**
> 

To lock wine version, open synaptic:

```
System >  Administration > Synaptic Package Manager
```
```

click on wine > click package on the menu > click lock version 
```

After this you will see a lock in wine package and updater will ignore wine upgrades.

But if you do not want to lock your wine version as you want to test latest wine, at least install your "stable wine" on custom directory, so as you will still have "your stable wine" when you upgrade your default wine. I saw some users even do not know when their application start to stop working as there are numerous wine upgrades before they realize that some of their applications stop working.

For this purpose, I have made an installer that help you to install many wine versions at the same time. I have not try regression test my self, but after I try it, I will make a script as well to make it easy to run regression test, and then report the result to wine developer. If I have completed this script, all of you could be beta tester for wine. But for now, please lock your wine version, or install multiple wine using below installer and instruction:

[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

DK



In summary, if you want to help Wine development then it's a good idea to test the new development releases and file bug reports.

---

### Post by TransitMan on 2008-10-11
I updated Wine from the auto updater, reran winecfg, reset all my apps to their previous settings and my apps work.

So where does it go wrong?

---

### Post by asdfoo on 2008-10-11
> **TransitMan said:**
> I updated Wine from the auto updater, reran winecfg, reset all my apps to their previous settings and my apps work.

So where does it go wrong?

As more features or fixes get added to Wine, some may cause regressions, one example is with 1.1.5 to 1.1.6 some preliminary support for USB was added which broke an old version of the SafeDisc copy protection.  This was discovered quickly with people testing the development release and a fix is being worked on.

---

### Post by david_kt on 2008-10-12
> **TransitMan said:**
> I updated Wine from the auto updater, reran winecfg, reset all my apps to their previous settings and my apps work.

So where does it go wrong?

Nothing, until your application stop working.
If you run "easy" applications that "just run", it should be no problem. But those applications require some tweaks such as native dlls and dlloverrides would most likely to break after wine upgrade, even after you run winecfg or even doing fresh install.

DK

---

### Post by RealG187 on 2008-10-12
0.9.46 is the best I think. It was the one I used in Ubuntu 7.10.

I remember once I went to 8.04 I had problems...

---

### Post by david_kt on 2008-10-13
> **RealG187 said:**
> 0.9.46 is the best I think. It was the one I used in Ubuntu 7.10.

I remember once I went to 8.04 I had problems...

You could have wine 0.9.46 in Hardy, no kidding. See how you could do it on below thread, I just updated to include workaround installing older wines:

[http://ubuntuforums.org/showthread.php?p=5933396](http://ubuntuforums.org/showthread.php?p=5933396)

And you could have as many wines version as you want.

DK

---

### Post by Dark9204 on 2008-10-13
David_kt, are you dumb?

Just think about it. If no one would test the betas then nothing would improve.

You should always use the latest wine. In case anything stops working, then send them the console output.

Seriously, you cant just start a thread with "Do Not Upgrade Wine!!". What kind of support would that be?

If the newest wine cuses problems for you, then report them.
If wine X.X.X works best for you. Then install mutible wine versions.

---

### Post by RealG187 on 2008-10-13
> **Dark9204 said:**
> David_kt, are you dumb?

Just think about it. If no one would test the betas then nothing would improve.

You should always use the latest wine. In case anything stops working, then send them the console output.

Seriously, you cant just start a thread with "Do Not Upgrade Wine!!". What kind of support would that be?

If the newest wine cuses problems for you, then report them.
If wine X.X.X works best for you. Then install mutible wine versions.

Do you upgrade to the latest Ubuntu beta version on productivity machines? Because it should be for productivity machines so stay, and then maybe have a "test" machine (or even a VM) for testing/improving new versions.

Personally, I don't think I have the knowledge to improve wine.

Where may I post the output, [Mall Tycoon]("http://ubuntuforums.org/showthread.php?t=941261") doesn't run, but Roller Coaster Tycoon Deluxe (RCT1 with expansion packs on the same disk) and RCT 2 (with and without expansion packs) do.

---

### Post by david_kt on 2008-10-13
> **Dark9204 said:**
> David_kt, are you dumb?

Just think about it. If no one would test the betas then nothing would improve.

Yes, may be. At least I am not smarter than wine developers that say:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

[COLOR="Red"]Warning: These are development packages

The packages here are development packages. This means they will periodically suffer from regressions, and as a result an update may break functionality in Wine. If the latest stable release of Wine (currently Wine 1.0) works for you, then you may not want to use the development packages.[/COLOR]

I just want to explain further that the "stable release" for some individual might not wine 1.0. For my case, it is wine 0.9.43. The reason is I put many native dlls and overrides that prevent me from upgrading to later wine. If I upgrade it, I must remove some of the dlls and overrides, which is troublesome for me. 

> **Dark9204 said:**
> 
You should always use the latest wine. In case anything stops working, then send them the console output.

Seriously, you cant just start a thread with "Do Not Upgrade Wine!!". What kind of support would that be?

Well, that is depend on how you run your application. If you run it without any tweak and without any native dlls, yes I am 100% agree with you. But if you run your applications with tweaks and native dlls, you could hinder wined evelopers job instead of helping them. And at one time they even got irritated by people giving feedback about problems but fail to inform special setting they had done like using winetools:

[http://www.winehq.org/?issue=304#WineTools%20&%20Wine](http://www.winehq.org/?issue=304#WineTools%20&%20Wine)

[COLOR="Red"]Wine developers are arguing that WineTools is doing more harm than good. It's unclear which of the additional libraries are needed. WineTools also messes with Wine's default configuration by changing the default overrides for every library to be native Windows ones over Wine's internal ones. That tends to break a lot of things.[/COLOR]

More debates about winetools [here]("http://www.winehq.org/?issue=308").

> **Dark9204 said:**
> 
If the newest wine cuses problems for you, then report them.

Agreed, BUT.......
So far I do not know how to report it as I do not know how to do regression test yet. And workaround DO NOT HELP wine developers at all:
[COLOR="Red"]http://www.winehq.org/pipermail/wine-devel/2005-January/032918.html

I'm not trying to dismiss WineTools, it's just that I'd much prefer
people working on improving the "real" thing rather than distribute
workarounds for a specific combination of Windows software and Wine
release.[/COLOR]

And according to wine developers, we need to do the following in order to help them:

[COLOR="Red"]http://bugs.winehq.org/
Before you report a bug, please make sure you have completed the following steps:

   1. Create a login account
      Click the Create Account link to get access to the system. Then Login. Your login info will be stored in a browser cookie so you will not need to login until the cookie expires.
   2. View the Available bug list
      This list shows the submitted bugs that have not been assigned to anyone yet. If you want to work on a bug, this is the place to start looking.
   3. Make sure you are using the latest stable version or a build from Git, if similar bugs have recently been fixed and committed.
   4. Read our tips on Bug hunting and support.
   5. Read the FAQ to be sure your issue is not listed there.
   6. Submit only unknown bugs
      Before you submit a bug, please make an attempt to see if it already exists, The Find a Bug link will perform advanced queries.[/COLOR]

So, do not think that sending terminal output to wine developers will give them a helping hands, it might confuse or even annoy them.

> **Dark9204 said:**
> 
If wine X.X.X works best for you. Then install mutible wine versions.

Fully agree, but again, may be I am so dumb so that I create a multiple wine installer, so that if I want to install any wine version I just need to click and click and ..... Viola .... I got as many wine versions as I want. I even do not want to see a rubbish out put in the terminal when wine is compiling, so, I convert it to nice progress bar GUI as I do not understand what the rubbish writing in the terminal when I am compiling wine. And I share that script [here]("http://ubuntuforums.org/showthread.php?t=942269") for dumb people like me to use.

Having said that, you might be right, wine developers and I may be are dumb so as we think that user should not use beta version, but use "stable version" instead.

DK

---

### Post by asdfoo on 2008-10-13
> **david_kt said:**
> 

Agreed, BUT.......
So far I do not know how to report it as I do not know how to do regression test yet. 


if you do not know how then all you need to is ask... there are instructions [http://wiki.winehq.org/RegressionTesting](http://wiki.winehq.org/RegressionTesting) - if you have trouble with this either ask on irc #winehq or [http://forum.winehq.org](http://forum.winehq.org)

> **david_kt said:**
> 


And according to wine developers, we need to do the following in order to help them:

[COLOR="Red"]http://bugs.winehq.org/
Before you report a bug, please make sure you have completed the following steps:

   1. Create a login account
      Click the Create Account link to get access to the system. Then Login. Your login info will be stored in a browser cookie so you will not need to login until the cookie expires.
   2. View the Available bug list
      This list shows the submitted bugs that have not been assigned to anyone yet. If you want to work on a bug, this is the place to start looking.
   3. Make sure you are using the latest stable version or a build from Git, if similar bugs have recently been fixed and committed.
   4. Read our tips on Bug hunting and support.
   5. Read the FAQ to be sure your issue is not listed there.
   6. Submit only unknown bugs
      Before you submit a bug, please make an attempt to see if it already exists, The Find a Bug link will perform advanced queries.[/COLOR]

So, do not think that sending terminal output to wine developers will give them a helping hands, it might confuse or even annoy them.


No, it won't confuse anyone.
It is important for all bugs to be reported on bugzilla.

---

### Post by david_kt on 2008-10-13
> **asdfoo said:**
> if you do not know how then all you need to is ask... there are instructions [http://wiki.winehq.org/RegressionTesting](http://wiki.winehq.org/RegressionTesting) - if you have trouble with this either ask on irc #winehq or [http://forum.winehq.org](http://forum.winehq.org)


Well, actually I know that links, and I even had read it before. But looks like it is not easy for me, may be Dark9204 is right I just dumb. Anyhow, if I have time, I would try to study how to do regression test, and if I have time, I will make a script with GUI so that every time I want to run regression test, that script will help me to do it automatically.

And I will share that script so that other dumb people like me could run regression test easily, no need to spend time to study.

DK

---

### Post by YokoZar on 2008-10-14
Basically, the advice in the OP is good: only upgrade Wine if something is broken or you want to help us test.

---

### Post by Espryon on 2008-10-17
The new wine update is as buggy as running something in windows or mac yes i said the w and the m word, it has been nothing but a problem dont upgrade unless your testing.

---

### Post by RealG187 on 2008-10-19
Is there a program that can run Mac OS apps in Linux?

---

