---
title: "Sketchup not responding"
date: 2014-11-22
forum: Wine
---

### Post by asearle on 2014-11-22
Hi Everyone,

I followed the instructions posted here ...

[http://ubuntuhandbook.org/index.php/2014/06/install-google-sketchup-ubuntu1404/](http://ubuntuhandbook.org/index.php/2014/06/install-google-sketchup-ubuntu1404/)

... to install Sketchup (2015) under Wine (1.7.31) on my Lubuntu 14.04 laptop and was very pleased that the installation ran through successfully.

Yes, all the icons and components seem to have been correctly installed but there is absolutely no response when I click on anything.  However, notepad opens up OK so Wine seems to be working.

I'd love to know how to get Sketchup working under Linux but, more important than that, is how do I diagnose/trouble-shoot the non-opening and non-response of Windows programmes under Wine?

Or is the fact that I am running Lubuntu rather than Ubuntu the root cause of the problem.

Many thanks for any tips that you can give me.

Regards,
Alan Searle
Cologne, Germany

---

### Post by flaymond on 2014-11-22
Lubuntu is based on the Ubuntu engine, only Desktop Environment and default apps are the difference. Some of files cannot run by WINE even its a executable file because the system is not like Windows. Check here - [https://appdbs..winehq.org/]("https://appdb.winehq.org/"). Based on the thread, do you already set up your Ruby API? Because the following comments on the article are mostly about API problems and WINE bugs problem ( WINE cannot run all file)

---

### Post by Mark Phelps on 2014-11-22
The recent versions, as shown in the linked WineHQ web page, are rated Bronze -- which is the lowest rating an app can get if it installs: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=1815]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=1815")

In my experience, anything installed in Wine that you really need to use, requires at least a Gold rating to be useful.

---

### Post by asearle on 2014-11-23
Hi Mark,

Thanks for this tip.  Yes, if it looks like being flakey, then I won't investigate too much but will, instead, install VirtualBox and get it running in a Windows environment.

Thanks,
Alan

---

### Post by asearle on 2014-11-23
I had choosen the 64bit version.  That was the problem.  I switched to the 32bit version and Sketchup opened OK.  But when I tried selecting menu options (e.g. "File") to do things like print or save the application crashed and went to the "bug screen".

It seems to be too flakey at the moment but I will try again in a few weeks to see if it runs better.

Many thanks for the tips.

Yours,
Alan

---

### Post by Mark Phelps on 2014-11-23
> It seems to be too flakey at the moment but I will try again in a few weeks to see if it runs better.

You're welcome to do that, but in my experience using Wine, waiting does not improve the situation.  It's still going to work poorly in the future, not better.

---

### Post by vmt298 on 2014-12-29
asearle, you may want to try download "mfc100u.dll" library and paste to "system32" folder. 

My SketchUp 2015 on my Xubuntu 14.04 works just fine after doing that.

---

### Post by Troon on 2015-03-17
Yeah thanks, that worked for me!

btw im running ubuntu14.04 with MATE
i had to set windows version to win7 using winetricks to get install to happen and then set wine config for sketchup to win 7

cheers

---

### Post by michael286 on 2015-05-24
Hello!
I am using Ubuntu for 24 hrs now and love it already. Way simpler than I always thought.

But I've got a massive issue with Sketchup. I can not get it running at all! I installed the newest version of wine and several versions of Sketchup. But the problem is always the same: As soon as I try to open (the installed) Sketchup on the Desktop nothing happends anymore. I googed and tried everything I could find in forums (that would suit a 'newer' Sketchup version).
The only thing I haven't tried as I do not understand where and how to do it is this:

> **vmt298 said:**
> asearle, you may want to try download "mfc100u.dll" library and paste to "system32" folder. 

My SketchUp 2015 on my Xubuntu 14.04 works just fine after doing that.o, if someone 

I'd be happy to try that too, if someone could tell me how.
Any other idea what the problem could be?
I'd need Sketchup running somehow ...


Thank you so much! :-)

Michael

---

