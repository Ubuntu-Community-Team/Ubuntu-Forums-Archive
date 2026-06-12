---
title: "Problems with graphical browsers"
date: 2006-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sutur on 2006-10-25
Hello,

I am running Dapper Drake on an AMD 64. I recently installed nvidia's display drivers although the problem I am about to explain popped up long before this.

After a given amount of time (say, 2-3 minutes) while browsing only graphic web browsers, I experience deadlock. Music keeps looping and I cannot communicate with the system in any way forcing me to restart via the tower's reset button. I am able to download data any other way, I downloaded 70MB worth of updates the other day and gaim works perfectly. Strangely enough, there are no problems when I'm using lynx, only graphical browsers like opera and firefox.

Any help on this matter would of course be greatly appreciated.

P.S. It may also be of some use that I am using ndiswrapper for my network adaptor, which is a Netgear WG111v2, and it should also be known that this particular driver has a history of being unstable, but it doesn't explain how only graphic web browsers should set about a lock up.

Thank you.

---

### Post by Sutur on 2006-10-26
Bump for help.

Once again if I turn off images in Opera (do not load images) it doesn't lock up the entire system and is completely stable, please - any ideas?

---

### Post by juicemansam on 2006-10-27
I'd run memtest+ just to make sure that the system memory is not the problem. I've had times where bad RAM timing or bad memory sticks caused similar crashes. I've also had bad video drivers (as well as bad USB drivers) cause similar lock-ups; I'd check the video drivers as well. I'd also try running the problem apps via the command line while redirecting all output to a log file. That way there'd be some evidence after the reset.

---

