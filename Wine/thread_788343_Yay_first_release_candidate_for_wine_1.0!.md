---
title: "Yay first release candidate for wine 1.0!"
date: 2008-05-09
forum: Wine
---

### Post by oedipuss on 2008-05-09
With lots of bugfixes!

I hope they build the packages soon =D

[http://www.winehq.org/?announce=1.0-rc1](http://www.winehq.org/?announce=1.0-rc1)

What do you think v1.0 release will be like ? Major difference , or just another release, with new regressions etc ?

---

### Post by hikaricore on 2008-05-09
It's hard to believe the WINE is finally hitting 1.0 after such a long long run.

All of the wine devs and various contributors have done a fabulous job.

*cheers*

---

### Post by wingnux on 2008-05-09
Let's open a bottle of wine to celebrate! :)

---

### Post by DoktorSeven on 2008-05-09
They fixed one of the bugs I've been wanting to be fixed forever!!!

> 7800  Grand Theft Auto Series with a gamepad plugged in the protagonist will start running ahead immedeately[sic] 

---

### Post by Twitch6000 on 2008-05-10
I hope they fix the problems I am having if they do then I will be happy =].I think since they are not focused on making version every other week it will be a big difference.Plus they are focused on certain bugs aswell.

---

### Post by tayhe on 2008-05-10
fifteen years old to 1.0 release.:popcorn:
Celebration for all wine developers and various contributors.

---

### Post by doorknob60 on 2008-05-10
1.0 already? Wasn't expecting that, but makes me happy :D

---

### Post by z|x on 2008-05-10
has anyone been able to download the package through the repos?

---

### Post by schtufbox on 2008-05-10
it's in the budgetdedicated hardy repo's now, I just had an update and downloaded it :)

---

### Post by z|x on 2008-05-10
> **schtufbox said:**
> it's in the budgetdedicated hardy repo's now, I just had an update and downloaded it :)
It doesnt show up for me..

---

### Post by Sleaka J on 2008-05-10
Just used the Update Manager and it updated Wine 1.0rc1 from 0.9.61 (which I already had installed).

---

### Post by gameryoshi600 on 2008-05-10
yay. i am using wine 1.0 rc1 
i got dreamweaver 8 to work under it.

---

### Post by z|x on 2008-05-10
it still aint coming in the update list for me with or without the bugdedicated repos.

---

### Post by oedipuss on 2008-05-10
Thats weird ... 
I can see the deb here : [http://wine.budgetdedicated.com/apt/pool/main/w/wine/](http://wine.budgetdedicated.com/apt/pool/main/w/wine/)
Perhaps it has trouble that particular repo ?

---

### Post by afv on 2008-05-10
> **z|x said:**
> it still aint coming in the update list for me with or without the bugdedicated repos.

I got it using 'deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main'

---

### Post by cogadh on 2008-05-10
Holy crap! Great news! Now make an official Gutsy package, please! Don't leave the Ubuntu users who won't or can't update to Hardy behind on this, we've all been waiting too long for it.

On a side note, after the final 1.0 release, what is next for the Wine devs? Perhaps interface enhancements?

---

### Post by z|x on 2008-05-10
when i run sudo apt-get update, i get the following errors:

```
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com hardy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

---

### Post by Sockerdrickan on 2008-05-10
> **oedipuss said:**
> What do you think v1.0 release will be like ? Major difference , or just another release, with new regressions etc ?

Dude, foo.0 is for stability, not major differences. :mad:

---

### Post by Kinst on 2008-05-10
We're in code freeze so up until 1.00 only regressions will be fixed. After 1.00 I think they said there'll be an unstable version and a stable version or something.

---

### Post by CSMatt on 2008-05-11
> **cogadh said:**
> On a side note, after the final 1.0 release, what is next for the Wine devs? Perhaps interface enhancements?
Work on Windows programs written for AMD64, probably.

---

### Post by z|x on 2008-05-11
> **z|x said:**
> when i run sudo apt-get update, i get the following errors:

```
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com hardy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```
bump

---

### Post by RIchard James13 on 2008-05-11
> **z|x said:**
> when i run sudo apt-get update, i get the following errors:

```
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com hardy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

Is not that fixed by running?
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add - 
```
I just copied that from the how to get WINE sticky.

---

### Post by bastiegast on 2008-05-11
It's in the Gutsy repo's now too!

EDIT: Oh damnit nevermind, I forgot I tried to add the hardy wine repo to my gutsy install

---

### Post by beyboo on 2008-05-11
> **bastiegast said:**
> It's in the Gutsy repo's now too!

Where did you see that ? Am looking up for a few hours now - dont see it !!

---

### Post by z|x on 2008-05-11
damn.. it still aint appearing no matter how many times i click on the update button.

---

### Post by situz on 2008-05-11
yay! =D>

(I just had to post in this thread ):P )

---

### Post by oedipuss on 2008-05-11
> **Tux0r said:**
> Dude, foo.0 is for stability, not major differences. :mad:

Well I thought that was a given.. I meant difference compared to a standard release, in stability and polishing mostly.. As for new features, most of what would be perceived as such would be apps that now run better, due to bugfixes, anyway.

---

### Post by Sordelka on 2008-05-12
WOW one point zero lol The official 1.0 wine ... :guitar:

---

### Post by josedb on 2008-05-13
iam still wating for network support on IL2

---

### Post by stephenb on 2008-05-13
Well, I have nothing to cheer about. Wine worked fine for me with Feisty 64, but with Hardy 64 it falls in a heap.

Here's my experience with Wine now, no matter what version I try:

[120294.982045] wine[18423]: segfault at 4a6c3f68 rip 4a6c3f68 rsp ffef06cc error 15

If I run winecfg I get "Segmentation fault."

So, I'll be happier when a version is released that actually works for me.

---

### Post by cogadh on 2008-05-13
I wonder; now that a RC is out, will WineHQ continue with releasing new builds roughly every two weeks (RC2, RC3, RC4... RC12 etc.) or will they stick with this one for a long time and only put out a new RC once a large number of bugs have fixes?

---

### Post by YokoZar on 2008-05-13
> **CSMatt said:**
> Work on Windows programs written for AMD64, probably.
It all depends on the timeframe for the next Wine release.  We're still not sure whether to try a stable version every six months or year (hopefully in sync with new Ubuntus), or whether to target particular features instead (eg Wine 1.2 must include support for these apps)

---

### Post by YokoZar on 2008-05-13
> **cogadh said:**
> I wonder; now that a RC is out, will WineHQ continue with releasing new builds roughly every two weeks (RC2, RC3, RC4... RC12 etc.) or will they stick with this one for a long time and only put out a new RC once a large number of bugs have fixes?
The biweekly releases will continue.  The winehq APT repos will be updated with them.

Once 1.0 comes out, I'll backport it to Hardy and Gutsy through Ubuntu-backports, as well as push one last update to the Gutsy budgetdedicated repo.

---

### Post by oninjao on 2008-05-15
wicked

---

### Post by VMan on 2008-05-15
An amazing program.  I still think that this is the absolute best example of open source collaboration/programming.  I don't know of any other project that allows programs written for one OS to be run on another OS.  This single effort is what I believe will allow linux to dominate the desktop/personal user market within the next decade.:guitar:

---

### Post by Half-Left on 2008-05-15
Photoshop CS2 working fine for people if they have any fears.

---

### Post by Faud on 2008-05-15
> **YokoZar said:**
> The biweekly releases will continue.  The winehq APT repos will be updated with them.

Once 1.0 comes out, I'll backport it to Hardy and Gutsy through Ubuntu-backports, as well as push one last update to the Gutsy budgetdedicated repo.

Many thanks

---

### Post by VMC on 2008-05-16
For those in the previous pages that couldn't get Wine 1.0rc installed. I followed this
thread and it worked perfect. Remember to uninstall previous version first.

[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

---

### Post by cogadh on 2008-05-16
You should have kept reading down a few posts:
> **YokoZar said:**
> The biweekly releases will continue.  The winehq APT repos will be updated with them.

Once 1.0 comes out, I'll backport it to Hardy and Gutsy through Ubuntu-backports, as well as push one last update to the Gutsy budgetdedicated repo.

---

### Post by goggins on 2008-05-18
> **VMan said:**
> An amazing program.   <snip> ***  I don't know of any other project that allows programs written for one OS to be run on another OS.  <snip>:

DosBox.  I installed it last night and it has run everything I've thrown at it, including stuff wine wouldn't run, whilst wine, on pure windows programs, is only batting 500 for me ('Tripmaker 2000' runs, 'The Sky' installs but doesn't run).

Of course, that's the wine I downloaded last week or so, and probaly isn't 1.0.

---

### Post by tedallal on 2008-05-20
> **goggins said:**
> DosBox.  I installed it last night and it has run everything I've thrown at it, including stuff wine wouldn't run, whilst wine, on pure windows programs, is only batting 500 for me ('Tripmaker 2000' runs, 'The Sky' installs but doesn't run).

Of course, that's the wine I downloaded last week or so, and probaly isn't 1.0.

That's a little bit misleading! 

DOSBox is an MS-DOS emulator. I'm no expert, but it doesn't take a genius to note the big difference between the two!

---

### Post by goggins on 2008-05-22
[QUOTE=tedallal;5005957]That's a little bit misleading! 

DOSBox is an MS-DOS emulator. <SNIP>

Hmmm - I don't see any relevant difference.  "Emulator" or not, it allows programs written for one operating system to run on a different operating system.  The original statement dealt solely with that capability, and there have been plenty of others, now that I think about it.  I sit here, running ubuntu, and I can fire up all the dos programs on my XP partition while running ubuntu.  I am thereby running programs written for one os on a different one.

---

### Post by cogadh on 2008-05-22
I think he was just trying to make the point that Wine is not actually an emulator and that programs run with Wine are actually running in a semi-native fashion. Programs run with DOSBox are running in a virtual environment, as is how all emulators work. The goal of each is the same, to be able to run software written for one OS in a different OS, but their methods of accomplishing that are different.

---

### Post by Vinni3 on 2008-05-22
Yey! I've been eagerly awaiting Wine 1.0! :)

---

### Post by DoktorSeven on 2008-05-23
Wine 1.0-rc2 was released today.

[WineHQ](http://www.winehq.org/) | [Announcement and bugfixes](http://www.winehq.org/?announce=1.0-rc2)

Not in the budgetdedicated repository yet, but it will be soon, I'm sure.

---

### Post by OpposingForce on 2008-05-23
Wine 1.0 rc2 is out.

---

### Post by jack handy on 2008-05-23
> **OpposingForce said:**
> Wine 1.0 rc2 is out.

now we just need it to hit the repo

---

### Post by flapane on 2008-05-25
nothing for gutsy?

---

### Post by bastiegast on 2008-05-25
> **flapane said:**
> nothing for gutsy?

Just one page back:

> **YokoZar said:**
> 
Once 1.0 comes out, I'll backport it to Hardy and Gutsy through Ubuntu-backports, as well as push one last update to the Gutsy budgetdedicated repo.

---

### Post by flapane on 2008-05-25
yes, I already saw that, I tought that someone maybe compiled it using checkinstall.

---

### Post by DoktorSeven on 2008-05-30
Note that 1.0-rc3 should drop today.  According to a news post on winehq.org:

> According to [http://wiki.winehq.org/WineReleasePlan](http://wiki.winehq.org/WineReleasePlan), wine-1.0.0-rc3 will be due out Friday, May 30th, 2008. 

Just a heads up.  Of course, this is just the source, it will likely take a day or two afterwards to get the package in the budgetdedicated repository...

**Edit**: RC3 is now available as source.  As stated, Ubuntu package in budgetdedicated will come later.

---

### Post by Melcar on 2008-05-31
Using rc3 on Hardy and every time I try to launch the wine control panel the whole screen becomes corrupted.  The system still responds, but everything is so distorted that I have to restart my session.  Anyone experiencing a similar issue?  Only thing I can think of besides Wine is fglrx, but previous versions worked fine.

---

### Post by Alex Carroll on 2008-05-31
Kind of similar I guess: I use wine virtual desktop and when I move the winecfg window around, the window border disappears. It reappears when I change to another tab such as graphics, but with a distorted appearance.

Running wine 1.0 RC3 AMD64 with fglrx

**Edit:**
Just tried running CCleaner setup and found that moving the window around slowly eats away at the window borders.

---

### Post by Sordelka on 2008-05-31
> **Melcar said:**
> Using rc3 on Hardy and every time I try to launch the wine control panel the whole screen becomes corrupted.  The system still responds, but everything is so distorted that I have to restart my session.  Anyone experiencing a similar issue?  Only thing I can think of besides Wine is fglrx, but previous versions worked fine.

I am scared to try it now, b/c I am converting a gigantic file from ps to pdf. But you can go to winehq forums and try your problem there. They respond in a few seconds!

---

### Post by JoshuaRL on 2008-06-02
Just got an email from Wine and thought it would be fun to pass along:
> 
Wine needs you!
-------------------------------------------------------
The following message was sent to you by the AppDB admins:

Hello Application maintainers!

If you weren't already aware, Wine is doing release candidates for the lead up
to Wine 1.0

The current release candidate is wine-1.0-rc3

We would like to make sure that as many programs as possible are tested with
the latest version of Wine and we have selected you as an ideal candidate to
test the applications you maintain.

Please help us find regressions and problems in rc3!

If you find a problem and it has not been reported in bugzilla, please file a new report at [http://bugs.winehq.org](http://bugs.winehq.org)

If you are unsure, you are welcome to ask in the forum at [http://forum.winehq.org](http://forum.winehq.org)

We are also running a Platinum Regression Hunt and a Dogfood Challenge

 * [http://wiki.winehq.org/PlatinumRegressionHunt](http://wiki.winehq.org/PlatinumRegressionHunt)
 * [http://wiki.winehq.org/DogfoodChallenge](http://wiki.winehq.org/DogfoodChallenge)

According to [http://wiki.winehq.org/WineReleasePlan](http://wiki.winehq.org/WineReleasePlan), wine-1.0.0-rc4 will be due
out June 6th, 2008

Best regards.
The AppDB team
[http://appdb.winehq.org/](http://appdb.winehq.org/)


---

### Post by Cyberponcho on 2008-06-03
After many years is 1.0 finally here, hard to believe!! I hope i can finally run starsiege under Wine (knocking on wood!)
Congratulations Wine team, thanks for all your hard work and for sharing this excellent application with the world (taking off my hat and making a deep bow):)

---

### Post by OmniCloud on 2008-06-05
> **cogadh said:**
> I think he was just trying to make the point that Wine is not actually an emulator and that programs run with Wine are actually running in a semi-native fashion. Programs run with DOSBox are running in a virtual environment, as is how all emulators work. The goal of each is the same, to be able to run software written for one OS in a different OS, but their methods of accomplishing that are different.You have to have Windows still installed on your drive to use DOSbox?

That would cut me out lol...

---

### Post by cogadh on 2008-06-05
Nope, DOSBox doesn't require Windows. Besides, Windows hasn't actually had any real DOS in it since Windows 98.

---

### Post by OmniCloud on 2008-06-05
> **cogadh said:**
> Nope, DOSBox doesn't require Windows. Besides, Windows hasn't actually had any real DOS in it since Windows 98.hmm...ok, I'll have to try it out then and test the performance of apps using both Wine and DOSbox...

---

### Post by cogadh on 2008-06-05
Bear in Mind that DOSBox is only for running old DOS software, not Windows software. Wine can also run old DOS software, but DOSBox does it better.

---

### Post by gjoellee on 2008-06-15
They are up in the RC5 now! The have done a fantastic job!
WINE
IS
NOT
(an)
EMULATOR

---

### Post by Fox McCloud on 2008-06-17
1.0 has been released. :)

---

### Post by gordiemac on 2008-06-30
How does wine work with games?..do you have too have the original copy on cd of that game too run?

---

### Post by cogadh on 2008-06-30
Using Wine to run games in Linux is just like running games in Windows (basically). If you needed original media to install or run a game in Windows, then you will need it to do the same with Wine. As for how well it works, it really depends on the game. If you have a particular game in mind, you should look it up on Wine's [Application Database](http://appdb.winehq.org/) to see how well it will work.

---

### Post by connorh123 on 2008-07-06
One question. Say you're going to download 1.0. But do you have to uninstall the current wine you have? And by doing that, wouldn't you lose all your settings in wine? Can anyone explain this to me?

---

### Post by Alex Carroll on 2008-07-06
You can just install over the previous version. No uninstalling or removal necessary, and it'll retain your settings and files.

---

### Post by cogadh on 2008-07-06
> **connorh123 said:**
> One question. Say you're going to download 1.0. But do you have to uninstall the current wine you have? And by doing that, wouldn't you lose all your settings in wine? Can anyone explain this to me?
If you originally installed Wine from the repositories using the Ubuntu .deb package and you are going to upgrade using either a downloaded .deb package, the Ubuntu backports repository or the WineHQ repositories, then you will not lose anything. All of Wine's settings are stored in the .wine directory in your home folder which is not touched by an upgrade. After upgrading, you do need to run "wineboot -u" to update the .wine directory with any changes made in the new version, but that will not affect any existing settings.

If you upgrade by downloading the source and compiling it yourself, it still won't overwrite the settings, but it will install things in a different location that the .deb packages do, so you will actually end up with two different installations of Wine. In this situation, you do need to uninstall any previously installed version before compiling and installing the new version. Unless you need to compile it yourself for some reason, I really don't recommend going that route.

BTW - I highly recommend you just use the stable 1.0 version that is available from the Ubuntu backports repository. It is currently the best version for everyday use and is less likely to contain new or unknown bugs and regressions like the unstable versions available from the WineHQ repository.

---

### Post by connorh123 on 2008-07-07
Ok so I thought the new version of wine would fix my bug problems with running counter strike, but no. Im still having problems with freezing, and I thought the new version would fix it.:(

---

### Post by piousp on 2008-07-07
Check the output of wine in the teminal. Maybe you are missing some DLLs.

---

### Post by connorh123 on 2008-07-07
No wine works fine. It's just I thought it would fix the bugs in counter strike. Like for example freezing problems, lag problems.

---

### Post by Shinbu-Otaku on 2008-07-08
wow thats awesome, i wasnt expeciting Wine to ever get to 1.0 with all the increment updates, but im glad they made it. Cant wait to try it out and see if i can get a Star Wars: Jedi Knight 3 mod finally working :D

---

