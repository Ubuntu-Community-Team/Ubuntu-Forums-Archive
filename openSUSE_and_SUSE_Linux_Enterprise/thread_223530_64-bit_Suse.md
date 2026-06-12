---
title: "64-bit Suse?"
date: 2006-07-26
forum: openSUSE and SUSE Linux Enterprise
---

### Post by hizaguchi on 2006-07-26
Anybody tried the 64-bit version of Suse 10.1?  I don't really have any problems with Ubuntu, but Suse seems so polished these days and 64-bit Dapper is a little sketchy.

---

### Post by RAV TUX on 2006-07-26
> **hizaguchi said:**
> Anybody tried the 64-bit version of Suse 10.1?  I don't really have any problems with Ubuntu, but Suse seems so polished these days and 64-bit Dapper is a little sketchy.

64 bit SUSE is even worse.

---

### Post by hizaguchi on 2006-07-28
I went against my better judgment, and your advice, and my experiences with Suse 10.0 and spent all night downloading the Suse 10.1 64-bit DVD.  I tossed it into my machine when I got to work and let it install.  About an hour later I was sitting at the Suse desktop.  It correctly detected my Turion X2 processor and is correctly scaling my speed up to 1.6 GHz when plugged in... which Ubuntu didn't do.  My synaptics touchpad is also working flawlessly.  It isn't even psycho touchy.  So all of the things Ubuntu 64 got wrong are working.

There are some down sides though.  My sound card isn't working right now, but I don't imagine it being too much trouble to fix.  Also, the upgrade utility, YOU, is kinda crappy.  It said there were 123 updates available, but when I told it to install them it couldn't resolve the dependencies.  So I fired up YAST and it's doing the updates right now without any problems.  They really should fix YOU though, since an error message on the first order of business after installation isn't very reassuring.

Overall though, I'm impressed.  Other than the sound, it looks like Suse 64 is every bit as polished as the 32-bit version, and the kinks I ran into with 10.0 are gone.  Can't wait for the updates to finish so I can give 64-bit XGL a try.

---

### Post by hizaguchi on 2006-07-29
Alrighty, so Suse is way more polished than Ubuntu and it handles 64 bit processors quite a bit better.  Problem is that hardware detection and support is absolutely terrible.  I've had to track down repositories for realtek sound and atheros madwifi wireless, and I had to build my own rpm for fglrx!  You'd think that with all of Novell's money they could at least include these well-established drivers in their repositories.  I can't imagine going straight from Windows to Suse.  But now that I've got most things working, I have to admit that I enjoy Suse's superior 64-bitification.  And Xgl was super easy to install and works flawlessly.

---

### Post by RAV TUX on 2006-07-29
Glad to hear you have had a better time then I did.

have you tried tried;

64 Studio

[http://64studio.com/](http://64studio.com/)

---

### Post by hizaguchi on 2006-07-29
Hmm, nope, hadn't tried that one yet.  Seems interesting, but probably not anything I'd use since I mainly just use my computer for OpenOffice, Kate (with Octave), and surfing the internet.  Cool to know about though.

I'm on the lookout for a really good 64-bit distro.  Ubuntu doesn't cut it since some multimedia codecs (like iTunes aac) and the synaptics touchpad driver don't work.  Suse is a little better since pretty much everything seems like it's working, but I'm going to get tired of rebuilding the fglrx module for every kernel since there's not a repo for it that I can find.  It is very pretty though, and Xgl works perfectly and shouldn't break with upgrades, so it's the best I've got right now.  Even if it was a pain to get things going.

Gotta figure one out by the 23rd though.  Can't be messing around with OSes once classes start up again.

---

### Post by RAV TUX on 2006-07-29
Take a look at the screenshots of Sabayon Linux RR64 version

This is the best 64 bit OS I have found yet:

[http://www.ubuntuforums.org/showthread.php?t=225374](http://www.ubuntuforums.org/showthread.php?t=225374)

---

### Post by hizaguchi on 2006-07-30
I saw your previous Sabayon post and thought it looked interesting, but I got sidetracked with Suse when I was planning to give it a try.  I'm interested in it and the other Gentoo derivitives though because they tend to be very up to date and I figure that having the latest software gives me the best chance of getting the most functionallity out of my 64 bit processors.  I also like having Xgl in an official repository of some kind, because that means upgrades are less likely to break it.

---

### Post by hizaguchi on 2006-07-30
3 days of using Suse and I have drawn my conclusion.  Suse is the perfect distro for people who don't do their own computer maintenance.  It is beautiful and has very nice tools for doing everyday stuff (wireless networking especially),  But man it makes installing software a pain.  You wouldn't believe the flaming hoops I jumped through to get Octave today.  I can't even imagine what upgrading is going to be like.  I'm not convinced 64-bit support is worth this.  I might just steal these sexy icons and run back to 32-bit Dapper with my tail between my legs.  After I try Sabayon and FreeBSD, of course. :)

---

