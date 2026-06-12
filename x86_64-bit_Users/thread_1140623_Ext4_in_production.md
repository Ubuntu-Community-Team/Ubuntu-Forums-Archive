---
title: "Ext4 in production?"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by esdaniel on 2009-04-27
Hi, just wondering how everyone's getting on with ext4 and whether you've got it running in production... I'm nervous about going there myself after I [read this]("http://www.heise.de/english/newsticker/news/134483").

---

### Post by huntzire on 2009-04-27
> **esdaniel said:**
> Hi, just wondering how everyone's getting on with ext4 and whether you've got it running in production... I'm nervous about going there myself after I [read this]("http://www.heise.de/english/newsticker/news/134483").


Well I use it for my own personal experience however from what I heard ubuntu merged a patch to set commit time to 5 secs instead of 15 secs and changes to make it more stable. To be honest I used Ext4 ever since itcame out and did some massive data moving and writing (15 gigs on a good day) and i havent lost integrity, i think people blow it out of proportion.

---

### Post by Simian Man on 2009-04-27
I've been using it with Fedora for several months now without incident.  Knowing Fedora, they didn't apply any changes to make it safer either.  I'd say it's perfectly safe by now.

---

### Post by Slim Odds on 2009-04-27
> **huntzire said:**
> Well I use it for my own personal experience however from what I heard ubuntu merged a patch to set commit time to 5 secs instead of 15 secs and changes to make it more stable.This would not make it "more stable", but would give it a smaller window of time when a crash or power outage would have chance to mess it up.

The problem never was "stability", it had to do the order and methods for writing data and meta-data. Crashes and power failures tend to be the times when bad things happen to files systems.

In the case of ext4, really bad things were happening in those cases.

---

### Post by brandon88tube on 2009-04-27
> **simian man said:**
> knowing fedora, they didn't apply any changes to make it safer either.

:)

Edit: forgot to mention that I've been using it without noticing any changes, but that doesn't mean anything as I don't always remember all of what I have.

---

### Post by Ericyzfr1 on 2009-04-27
I have been using it for a month, no problem.

---

### Post by Slim Odds on 2009-04-27
> **Ericyzfr1 said:**
> I have been using it for a month, no problem.

Just remember that there was no issue with "normal operation". It was only during catastrophic conditions (crashes and power outages) that there was a problem.

---

### Post by cariboo on 2009-04-27
If you are running production servers, I would wait until the next release. On my personal destop and my media center pc it works great, without any problems, but I would be a little nervous about putting on a production server until the program devs get the programs rewritten to work with ext4.

---

### Post by wfp on 2009-04-27
> **Slim Odds said:**
> Just remember that there was no issue with "normal operation". It was only during catastrophic conditions (crashes and power outages) that there was a problem.

One big Reason I am waiting to try Ext4, the Area I live is famous for power out's specially during the summer.

---

### Post by Arup on 2009-04-27
> **wfp said:**
> One big Reason I am waiting to try Ext4, the Area I live is famous for power out's specially during the summer.

Hi,

As long you have a UPS you got nothing to worry about, its like enabling write back cache on hdd in Windows world. I have been on ext4 since the release of Jaunty.

---

### Post by brandon88tube on 2009-04-28
> **Arup said:**
> Hi,

As long you have a UPS you got nothing to worry about, its like enabling write back cache on hdd in Windows world. I have been on ext4 since the release of Jaunty.

You could always use a car battery like Google.

EDIT: Just experienced a crash while files were being downloaded to my ext4 drive among other things. So far I haven't noticed anything wrong or missing, but that doesn't mean there isn't anything wrong.

---

### Post by whoop on 2009-04-29
I believe the data loss was caused by the delayed allocation. Some patches where backported from 2.6.30 to jaunty's kernel (2.6.28) to limit this allocation.

I have been running ext4 (I converted it from ext3 howto:[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)) since alpha6 on a production machine without data loss (I even forced some system crashes to test the issue).

---

### Post by Slim Odds on 2009-04-29
> **whoop said:**
> I believe the data loss was caused by the delayed allocation.That was exactly my point. Delayed allocation is NOT a problem unless something happens that causes some part of the change NOT to get written (partial data). That's when things go bad.

---

### Post by Linux&amp;Gsus on 2009-05-01
I heard/read in other posts that there might be a problem when accessing other file systems, like NTFS or ext3.
Is there any more experience by now about this issue?

Well, I have an old desktop and might do some tests with it, if I have the time. I hope 9.04 will run on it at all. It has a known problem with the video card (32MB ATI) and regular freezes are guaranteed :D
For tests it's more then enough, and for server tests (without GUI) it runs just fine. Slow but fine.

Cheers,
L&G

---

### Post by dcstar on 2009-05-01
> **esdaniel said:**
> Hi, just wondering how everyone's getting on with ext4 and whether you've got it running in production... I'm nervous about going there myself after I [read this]("http://www.heise.de/english/newsticker/news/134483").

I selected it for my 9.04 install, but from what I now know about how immature it is (including the resize bug in the 9.04 release notes) I would not make that choice again.

---

### Post by disabledaccount01 on 2009-05-01
Message removed by author.

---

### Post by Yashiro on 2009-05-01
> Ext4 in production?
No.

---

### Post by Yellow Pasque on 2009-05-01
> On my laptop, the combination 9.04/EXT4 Laptop seems faster than 8.10/EXT3
Apples and oranges, i.e. irrelevant comparison.

Personally, I wouldn't use ext4 in a production environment, unless I had a specific reason to.

---

### Post by old_geekster on 2009-05-03
Just installed 9.04 with "Ext4" this evening.  For the past few days, I have been using Ext3, but didn't like the setup.  So, I figured as long as I was doing a new clean install I would try Ext4.  I find everything is a bit faster.  It is working great so far.

---

### Post by Arup on 2009-05-03
> **old_geekster said:**
> Just installed 9.04 with "Ext4" this evening.  For the past few days, I have been using Ext3, but didn't like the setup.  So, I figured as long as I was doing a new clean install I would try Ext4.  I find everything is a bit faster.  It is working great so far.

Always good idea to do a fresh install, that way all your files are in ext4 format. I have been using ext 4 since my fresh install of Jaunty and have never looked back.

---

