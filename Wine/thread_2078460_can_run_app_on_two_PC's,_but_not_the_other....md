---
title: "can run app on two PC's, but not the other..."
date: 2012-10-31
forum: Wine
---

### Post by Baldrick_NZ on 2012-10-31
Hi all, 

Using the experimental wine1.5.16, I can make a certain .exe work on two PC's, but not a third. The exe starts but then freezes a few seconds later, ending with a message that wine has struck an error and needs to close. It doesn't elaborate on what the error is.

This PC that won't work with 1.5.16 works with the stable 1.4.1, but takes ages to start up. It worked well up to version 1.5.11, but hasn't worked since.

I also have an Ubuntu USB which has 1.5.16 loaded, and this works fine (with the same exe) when booted into either of the other two PC's, but not the third one.

Would I be right in thinking that the wine devs made some changes to 1.5.12 onwards that seem to cause some conflict with my hardware on the third PC? How can I prove this (or not)?

It would be great to have the exe work across all three PC's using 1.5.16 if pos..

Any help would be very much appreciated!

---

### Post by Baldrick_NZ on 2012-11-01
Bump.. Anyone??

I have noticed winealsa.drv are default audio drivers in v1.4.1, but has changed to winepulse.drv in v1.5.16.

How can I change back to winealsa.drv in 1.5.16? Maybe winepulse has issues with my hardware, while winealsa doesn't?

Any help much appreciated!

EDIT: Nailed! Changed to pulsealsa driver as default using winetricks. Amazing what happens when you play with something long enough and find the solution. :-)

---

