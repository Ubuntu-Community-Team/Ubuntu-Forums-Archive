---
title: "Active Sync installer says already installed, but it isn't"
date: 2008-01-07
forum: Wine
---

### Post by Robertjm on 2008-01-07
Hi all!

Today I tried to install Active Sync, but having a problem.

I downloaded and tried to install the new Windows Mobile Device Center 6 (I think that's the name), but when I try and run the installer it does absolutely nothing. WINE doesn't open.

Next I downloaded versions 4.1, 4.2 and 4.5 from some site called oldapps. A couple of them turned out to be msi files (Microsoft Installer). When I tried launching one nothing happened still.

Finally, I tried using the 4.2 .exe installer. It launches, asks me where to install it and starts installing. All of a sudden it tells me I already have a version of active sync installed on my computer.

After I click OK it asks me if I want to continue installing Active Sync and remove the currently involved version. When I click Next, it asks me where I want to install it. I chose the C: just to keep it simple. It starts doing its thing, but quickly flashes up a msg that "The Wizard was interupted before ActiveSync 4.2 could be completely installed..."

When I click Finish, the installer goes away and the WINE desktop closes.

Is there something in WINE akin to the Windows Registry that I need to clean up so that it doesn't think its installed? Its not on the list of installed apps so I have to assume its really not there. Correct?

Robert

---

### Post by hikaricore on 2008-01-07
ActiveSync doesn't seem to run very well under WINE: [http://appdb.winehq.org/appview.php?iAppId=622](http://appdb.winehq.org/appview.php?iAppId=622)

Looks like your best bet is 4.1 however.

Perhaps you could tell us more about what this software does so that we could try and offer you a native alternative if one exists?

---

### Post by Robertjm on 2008-01-07
Its for syncing between your computer and your WM devices. A lot of programs require installation via Active Sync, rather than simply copying them over. I have found no native applications that will allow syncing with my WM-based PDA cellphone (Samsung i730) and Linux. Believe me, if I found one that worked, I'd be VERY happy. 

I'll be inteerested in trying v4.1 provided I can get past this crazy "already installed" error msg I'm receiving. 

Robert

---

### Post by mike-laptop-dot-local on 2008-01-07
I haven't tried it, but [SynCE]("http://www.synce.org/") might be your alternative answer, though you might have problems with hardware compatibility. Good luck with it. [www.synce.org](www.synce.org)

---

### Post by Robertjm on 2008-01-07
I think I played around with their stuff prior on an older phone to no availe. When I check their website the only phones they list are the HTC brand.

> **mike-laptop-dot-local said:**
> I haven't tried it, but [SynCE]("http://www.synce.org/") might be your alternative answer, though you might have problems with hardware compatibility. Good luck with it. [www.synce.org](www.synce.org)

---

