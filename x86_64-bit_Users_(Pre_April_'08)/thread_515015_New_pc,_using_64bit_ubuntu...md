---
title: "New pc, using 64bit ubuntu.."
date: 2007-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by mattixtech on 2007-08-01
OK, so I just got a new computer.
Intel Q6600 quad core processor, 8800gts, and 4gb of ram.

I want to get the full 4gb of ram so It looks like I'm stuck using the 64bit version of ubuntu 7.04.

I am going to be mainly using this computer to play games and do web development.

It looks like Wine will work on the 64bit version and the games I play the most also look like they are going to work (WoW and Steam games).

However I need to be able to use applications like dream weaver and flash and I'm not sure how well they will work in Wine so I was going to virtualize windows XP and run them that way. Will this work well? What would I use to virtualize them?

Also do the nVidia drivers work well in 64bit ubuntu? Will games and 3d desktop effects work?


Oh and is there anything fancy I need to do with ubuntu for the quad core support? Like is there a specific kernal or something?

---

### Post by Cappy on 2007-08-01
All that stuff is exactly the same as the 32-bit including wine .. the games .. 3d desktop .. nvidia drivers .. etc.

You can find out about wine and applications on the appdb:
[http://appdb.winehq.org/appview.php?iVersionId=7694](http://appdb.winehq.org/appview.php?iVersionId=7694)
newest version of dreamweaver .. can't install it but it will run if copied into wine.
the older versions seem to install/run fine, you can look them up here:
[http://appdb.winehq.org/appview.php?iAppId=183](http://appdb.winehq.org/appview.php?iAppId=183)

Flash:
[http://appdb.winehq.org/appview.php?iAppId=23](http://appdb.winehq.org/appview.php?iAppId=23)

As for virtualization .. you can use something like VirtualBox (which I like a lot) or VMWare. Not sure how well it will work with memory/processor heavy apps though, never tried.

No idea about quad core support.

---

### Post by John.Michael.Kane on 2007-08-01
> **mattixtech said:**
> However I need to be able to use applications like dream weaver and flash and I'm not sure how well they will work in Wine so I was going to virtualize windows XP and run them that way. Will this work well? What would I use to virtualize them?

Either of these should get you going

[virtualbox]("http://www.virtualbox.org/")

Or 

[Deluxe Beginners Guide HowTo: Install VMware Server in Ubuntu 7.04]("http://ubuntuforums.org/showthread.php?t=491852&highlight=virtualbox")


> **mattixtech said:**
> Also do the nVidia drivers work well in 64bit ubuntu? Will games and 3d desktop effects work?

Yes the drivers work the same as they would under 32bit ubuntu.


> **mattixtech said:**
> Oh and is there anything fancy I need to do with ubuntu for the quad core support? Like is there a specific kernal or something?

No. the standard kernel ubuntu installs with is smp enable, and will see your quad fine.


For any other issues such as codecs flash-plug check this thread.:
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by mattixtech on 2007-08-01
> **Cappy said:**
> newest version of dreamweaver .. can't install it but it will run if copied into wine.
the older versions seem to install/run fine, you can look them up here:
[http://appdb.winehq.org/appview.php?iAppId=183](http://appdb.winehq.org/appview.php?iAppId=183)



Does this mean I can install it in windows and then launch it from Wine? Or.. what do you mean copy it into wine.

---

### Post by Cappy on 2007-08-01
Well I meant that you could install it in Windows and then you would need to copy all the DLLs that it installed, the files it installed in C:/Program Files/ and the registry keys it inserted from the registry. Not very plug and play =P

---

### Post by nxt on 2007-08-01
I'am running VMWARE for XP x64 for Flash and Photoshop etc.

with for 4gb of ram you have plenty of ram to spare for virtual machine

---

### Post by univremonster on 2007-08-02
This post only covers the topic of flash while web browsing:  You can install a 32-bit version of Firefox, which is much more functional at least for now.  There are more directions for getting all the plugins working [here]("http://ubuntuforums.org/showthread.php?p=1174435").

---

### Post by dabl on 2007-08-02
I'm getting very satisfactory results with the free VMWare Player, running a Win XP Pro virtual session. Seems very stable, has ethernet, USB, and sound (sometimes, if I don't use sound in Linux first). :popcorn:

---

### Post by Kilz on 2007-08-02
> **dabl said:**
> I'm getting very satisfactory results with the free VMWare Player, running a Win XP Pro virtual session. Seems very stable, has ethernet, USB, and sound (sometimes, if I don't use sound in Linux first). :popcorn:

I just have a question or two, Why? Why would you want to run XP? Isnt the purpose of running Linux that you dont have to use Windows and Windows applications? What is holding you back from removing Windows completely? I could see using a vm as you transition from Windows. When do you think you will be able to?

---

### Post by dabl on 2007-08-02
> **Kilz said:**
> I just have a question or two, Why? Why would you want to run XP? 

Fair question!

It's not really "wanting" to run XP, it's "having" to run XP.

I have 10 years of hard work invested in a genealogy database that is a MS Visual FoxPro app named "The Master Genealogist".  It is close to 70,000 individuals, with a lot of source documentation.  There's nothing close to it in Linux.  So, to preserve and use my previouse work, while converting to Linux, I have to have a way to run Windows XP.  VMWare Player provides that capability.  Everything else I need appears to be available in Linux, so nothing else needs to be dragged along from Win-World.

:)

---

### Post by univremonster on 2007-08-02
Kilz, 

While I happen to agree with you, not everyone may be using Linux for the same purposes.  I am one of the few who don't think Windows is completely evil... matter of fact there are some stats out there that say Google is [even worse]("http://news.bbc.co.uk/2/hi/technology/6740075.stm").  If people want to dual-boot Ubuntu and XP, we should try to help them out.

btw, excellent post you made regarding installing the Flash application for 64-bit, as I referenced above.  That was my first encounter with Ubuntu Forums :-)

---

### Post by Cappy on 2007-08-02
That link about google privacy is ballony. Google are the MOST concerned about privacy (google it [or not if ur paranoid] and you'll learn why). That study was supposedly paid for by microsoft ...

Their actions speak much differently than a wrong report ...
[http://www.iht.com/articles/2006/01/20/technology/web.0120google.php](http://www.iht.com/articles/2006/01/20/technology/web.0120google.php)

---

### Post by univremonster on 2007-08-03
The report says "Google’s privacy failures include: retaining large quantities of user information, often for an unstated or indefinite length of time and without an opportunity to delete or withdraw it; failing to follow generally accepted privacy practices and elements of EU data protection law, and logging search queries in a way that makes them personally identifiable."  Which part of this is untrue?

In the site you linked, the reasons for not handing over data was the request was "unnecessary, overly broad, would be onerous to comply with, would jeopardize its trade secrets and could expose identifying information about its users".  I guess one out of five ain't bad... though trade secrets may have more to do with their reluctance.

I googled "Google worst on Privacy" and "google worst privacy paid for Microsoft" and got nothing about Microsoft funding Privacy International.  Actually, if you go to the Privacy International web page, you'll find under the "funding PI" page the following:

"The majority of our funding comes on a project-level basis from foundations and grant-making bodies.  Our core work is currently done on an entirely voluntary basis."

At any rate, this topic is not what the post was about.

---

