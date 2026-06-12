---
title: "How well does SQL Server and .Net work in Wine?"
date: 2008-10-11
forum: Wine
---

### Post by tc101 on 2008-10-11
If you are doing some MS programming for a living, working by the hour at home on your own computer, is it worth the trouble to get .Net and SQL Server Express running on wine, or would it be easier just to spend $500 and order a cheap windows computer from Dell for the project?

Let's say you are getting $50/hour and it is an ongoing project, maybe 500 hours a year, will you save more than 10 hours time by getting a windows computer rather than using Wine?

---

### Post by asdfoo on 2008-10-11
> **tc101 said:**
> If you are doing some MS programming for a living, working by the hour at home on your own computer, is it worth the trouble to get .Net and SQL Server Express running on wine, or would it be easier just to spend $500 and order a cheap windows computer from Dell for the project?

Let's say you are getting $50/hour and it is an ongoing project, maybe 500 hours a year, will you save more than 10 hours time by getting a windows computer rather than using Wine?

Looking at the AppDB entry for just the MSDE version, it doesn't look like it works at all.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3610](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3610)

If you're intent on using SQL Server rather than something like sqlite then you're probably better off just using Windows.

---

### Post by tc101 on 2008-10-11
> If you're intent on using SQL Server rather than something like sqlite then you're probably better off just using Windows.
asdfoo is online now Report Post   

It's not my decision.  This is a legacy system that just needs maintenance.  It was built with SQL Server and ASP.

---

### Post by estamand on 2008-10-11
Why not use virtualbox and setup a windows xp virtual machine?

---

### Post by tc101 on 2008-10-11
Someone else suggested that.  I don't have a copy of XP but I guess I could get one.  How hard is it to set up virtual box?

The more I think about this project I really hate the idea of dealing with Microsoft and windows products again.  The money is good and I can work at home though, so I am tempted.  I am undecided right now.

---

### Post by asdfoo on 2008-10-11
> **tc101 said:**
> Someone else suggested that.  I don't have a copy of XP but I guess I could get one.  How hard is it to set up virtual box?

The more I think about this project I really hate the idea of dealing with Microsoft and windows products again.  The money is good and I can work at home though, so I am tempted.  I am undecided right now.

Using Virtualbox is as easy if not easier than having the actual hardware, it probably performs best (near perfect for me) on Intel core2 cpus or similar from AMD, if you have an older cpu you might find it less responsive.  It has useful features such as snapshotting, so incase you want to preserve the state of your system before trying an upgrade you can do so then roll back if something goes wrong.

---

