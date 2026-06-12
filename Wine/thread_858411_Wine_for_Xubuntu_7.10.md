---
title: "Wine for Xubuntu 7.10"
date: 2008-07-13
forum: Wine
---

### Post by Max* on 2008-07-13
Ok, well today is the very first day I have used Xubuntu - as I have just installed it on my PS3.  I have never used any sort of Linux distro or anything related to it so this is all very new to me.  

I want to start off installing Wine, but as I dont have an internet connection **(as the only two options in the network settings are: Wired and Modem - could someone relay or enlighten me as to how to set up a wireless connection?)**I cannot download it via add/remove.  So, I've been trying all day today to install Wine & Visual Boy Advance emulator by transferring things to my external HDD and then to Xubuntu on my PS3. I hope that is ok...

So after browsing through the web, I found a Wine installer (.deb?) and when I put it on Xubuntu and clicked on it, it came up with: Error: Wrong architecture '1386' So apparently this is not the right one for Xubuntu 7.10.  Would anyone be able to point me in the right direction as to where to find that particular version?  I've already checked the WineHQ site and I personally couldn't see that there was any downloads for Xubuntu. :(

Any help would be appreciated guys!

---

### Post by pytheas22 on 2008-07-13
On Xubuntu, you can install packages for Ubuntu, Kubuntu, Edubuntu or in some cases even just Debian...Xubuntu is just a front-end; the underlying system is the same for all of the *buntus.  So if you can find a wine package anywhere for any variant of Ubuntu or Debian, it should install.

You do, however, have to make sure that the architecture is correct.  I don't have any experience with Linux on the PS3.  Packages with i386 in their name are for regular 32-bit computers with Intel-compatible CPU's; amd64 is for AMD-compatible 64-bit machines.  I don't know where to find packages built for PS3's (do you know what kind of CPU they have?), but if you can find them, you'll be all set.

As for the wireless, it seems that you may need to do some extra work to get it going.  Take a look at [http://psubuntu.com/wiki/Setup](http://psubuntu.com/wiki/Setup) .

---

### Post by Max* on 2008-07-13
Thanks, I'll try out the different packages to test and see what I can get working.  If they're all one in the same like you say, one of the downloads on HQ are bound to work right? :) 

If I can get this working then I'll pass on the WiFi as that looks way too complicated for me haha.

By the way, do you think I should try one from each of the three columns here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
(For Ubuntu Hardy)

Ok, I just did this ^ and I have concluded that neither the i386, amd64, or lpia structures work - they all come up with the wrong architecture error. So what do I do now?  Or maybe it's just because I used Ubuntu Hardy .deb's?  Will another distro possibly work?

Nevermind, this is not possible. :(

---

### Post by pytheas22 on 2008-07-13
Yes, according to [these people]("http://answers.yahoo.com/question/index?qid=20080623120552AAstu6t") it doesn't work.  Actually it makes a lot of sense...wine is an implementation of the Windows API, Windows only runs on Intel-compatible chips, so wine also only runs on Intel-compatible chips.  Owners of PPC Macs face the same disappointment when it comes to wine.

Sorry it won't work, but I hope you can do something else fun with Linux and your playstation.

---

