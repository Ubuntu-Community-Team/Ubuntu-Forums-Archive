---
title: "Hardy 64bit flash10 strange video crashes firefox hulu"
date: 2009-05-05
forum: x86 64-bit Users
---

### Post by Fanless_Puppy_Fan on 2009-05-05
I've got a strange problem. I have flash for 64bit alpha 10.0r22 pretty much working on my up to date 8.04LTS 64-bit installation.

If I go straight to youtube firefox crashes. If I click a youtube address from video.google.com, youtube functions flawlessly. If I go to hulu, it will start the show and crash during the transition from commercial to the program.

I can go to the official adobe flash test site and all seems to work flawlessly. Some webpages also crash the firefox browser.

I have confirmed there are no other flash versions and can't reinstall firefox through the "add/remove applications" because of some dependency. therefore, I am afraid I will break something if I force the reinstallation. Any advice or tips appreciated.

I am using a nvidia 8400gs video card if that matters.

---

### Post by atownley on 2009-06-08
Also have the same issue, but only started recently.  Pretty serious problem for me as it also affects internal embedded browser application.

Load of this page: [http://mashable.com/2009/06/08/twitter-local-2/](http://mashable.com/2009/06/08/twitter-local-2/) will crash FF like clockwork.  Also, any page with the twitter flash app (like [http://atownley.org](http://atownley.org)) will also cause immediate crash.

Temporary workaround is to disable flash plugin, but this isn't practical in modern Web.

Anything we can do to fix this?  Noticed that there was also a Jira ticket at adobe, but has no priority.

Anyone else have this issue?  Is there a preferred way of collecting the relevant info (installed package list), stacktrace, etc. that will help solve it?

Cheers,

ast

---

### Post by udippel on 2009-06-09
Yes, I have a lot of crashes of Firefox, agreed.
Though not on the mashable.com link as above.
I did install the original 64-bit Flash-Player on Jaunty.

But I couldn't point to any specific site, at times it crashes when I open a new link in this forum.  :(

I guess, we need better references on exactly what happens when it dies. I for one had the impression, taking too much memory at a time could be the reason; like fast scrolling.

---

### Post by udippel on 2009-06-09
Fanless_Puppy_Fan, have you considered it had to make with the Nvidia card? Here I was fighting with a 8300, IGP.
Maybe some incompatibility of Nvidia and Firefox on 64 bit?

---

### Post by seamuso on 2009-06-09
by any chance did you upgrade to amarok 2.1? I noticed that if I had that running in the background, any youtube vids I tried to play killed firefox.

---

### Post by bedhead75 on 2009-09-22
I also had a problem with 64-bit flash causing Firefox to crash with a segmentation fault when I try to view videos in Hulu.  Firefox always closes a few seconds after clicking on a video in Hulu, but it seems fine in Youtube.  I am back to using 32-bit flash in Jaunty now.  I guess 64-bit flash is simply not yet as fine and dandy as many people on here would like you to believe.

---

### Post by sadahalli on 2009-09-25
I also had this problem. The problem was that there were different versions for firefox and the links were everywhere. I removed all firefox versions (If necessary delete the firefox directory at at /usr/lib). I also removed all the flash palyers that had been installed. 
 Installed firefox again and installed adobe flash and it works perfectly. No crashes now..

---

