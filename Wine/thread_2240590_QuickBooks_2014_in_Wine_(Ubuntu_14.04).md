---
title: "QuickBooks 2014 in Wine (Ubuntu 14.04)"
date: 2014-08-21
forum: Wine
---

### Post by em3raldxiii on 2014-08-21
First off, I want to give this a good solid try - I don't want to just throw up my hands and give up.

Okay here's the background:  My co-worker has made the plunge to use Ubuntu, partly out of hatred for Win8.  Everything is great, but he needs to be able to use Quickbooks.  Alternatives will not suffice at this time.

1.  Ubuntu 14.04 is working fantastically as the sole OS on his machine.
2.  The most recent repository version of WINE is installed, and aside from a few minor hiccups appears to be running fine.  I have tried configuring WINE to emulate Vista, Win7, and Win8.
3.  The QuickBooks installer begins to run, and I can successfully enter the obnoxious security code thingie that all Win software seems to have.
4.  The Quickbooks installer fails on installing **msxml6_x64** with an invalid handle error (1604)
5.  Using WineTricks, I identified the **msxml6_x86 **as the only optionso instead I went to the MS website and acquired msxml6_x64.msi.
6.  **msxml6_x6**4 appears to have installed fine, with no errors.
7.  Running the QuickBooks installer *still fails* with the same error.

So my guess is that we need to somehow convince QuickBooks that xml6 is actually installed and/or give it the right location.  Of course, there might be a different Windows library or some such that will also fix this error.

The most recent entry for QB in the AppDB is pretty old, but gives THAT version a platinum rating.

Finally, we might have to try using a virtual box, but I have no experience with that.  I have installed virtualbox, but he may not have a Windows disk.

---

### Post by mastablasta on 2014-08-21
no, actually all the latest version have Garbage rating on appdb. I wonder what is so essential about these quickbooks everyone in north America is using?

for example we use accounting software that is web-based and system agnostic. but it is probably tailored to my country.

also is the app 32bi or 64 bit is the wineprefix set correctly? it seems you got further than some "testers" at wine db. so, kudos for that. :P

---

### Post by em3raldxiii on 2014-08-21
@mastablasta:  Hmm, it appears I read the appdb ratings backwards.  Thanks for that.  As to the whole 32/64 bit stuff, err, to be honest I didn't really spend a lot of time looking at that.  I just assumed (probably erroneously) that 64 bit Ubuntu would automagically configure it to be 64 bit Wineprefix for 64 bit Quickbooks.  I'll keep working with it, but I may have to go the virtualbox way.

As to the prevalence of QB ... I don't know.  I've never used it, LOL.  It's probably just a marketing thing, in the same way that Windows had an iron grip on the OSs, so too does QB have an irongrip on Nort American finances.

---

### Post by mastablasta on 2014-08-23
yes 64 bit Ubuntu it automaticly creates 64 wineprefix. if app is 64bit then the 64bit prefix should be the right one. but make sure the correct librarires (64bit) are isntalled as well after you add them. still in this case i doubt you will make it work.

the virtualbox/vm seems to be the only way then. some light windows version+the QB software. virtualbox is not really an issue as long as there is enough CPU power and RAM to run it.

---

### Post by em3raldxiii on 2014-08-29
Update:  Attempted to install via VirtualBox.  We successfully installed a version of Win7 onto the VirtualBox, and can boot into it.  However, the install of QB fails partway in due to some oddball error (I am not at that machine right now, so I cannot say precisely what the error was).  Upon further investigation (Googling), it appears the problem is actually with the QB software, not anything else.  As a work-around, I have attempted to convince my co-worker to use the online version of QB in his browser.  It actually may end up being a better solution all-around, actually ... I asked him to text me if his book-keeper (daughter) has any trouble with the online version.  If everything works as planned, then he's just going to go that route.  The QB software cost something like 600 bucks, whereas the online version that will do what he needs costs something like 20 bucks a month.  AND it can be written off against his company's taxes.  So this might be a win-win.  No more storing local files, either, which was always a source of anxiety for him.

---

### Post by pete37 on 2015-02-28
I have been usingQuickbooks loaded inot Ubuntu with Windows XP (and now 7) in Virtual Box for  a couple of years now.  There is nothing better;Windows runs much faster in VB as well.

---

### Post by alamo2 on 2016-01-26
The chains of habit are too weak to be felt until they are too strong to be broken.
—Samuel Johnson

---

