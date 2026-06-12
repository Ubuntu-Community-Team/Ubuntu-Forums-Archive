---
title: "Lost"
date: 2016-01-08
forum: Wine
---

### Post by jdevola on 2016-01-08
I am trying to clone partitions (already tried and failed with gparted), and was recommended to use EASEUS.  Great, except the site downloads an *.exe file -- cannot run on Linux.  So, suggested to install Wine.  Okay, go to software center and find multiple listings for Wine and Wine-related software.  I have no idea what I need and what I don't.  (Yes, I did read the sticky notes -- no help there.)  Can someone tell me what, specific, downloads I need to get the EASES software to work so I can clone HDDs?  I appreciate the help; I am pretty frustrated at this point.  THANKS!

---

### Post by sandyd on 2016-01-08
Easeus is for Windows only.

That being said, WINE is only a compatibility layer, and Easeus will not be able to manipulate partitions when running through WINE.

You can create a new thread if you want help with GParted, please include errors/etc encountered.

---

### Post by jdevola on 2016-01-08
Well, their website seems to indicate it will work with Linux.  I also read that you can create an ISO or USB boot (e.g., live CD) to run Easeus.  Why wouldn't it run through Wine (it's not on the list)?  Mind you, I don't plan to clone my booted drive.  I have like 5 drives on now:  booted on C and want to copy E to F.

I have another machine I can set up with XP.  I think I'll try that before trying to figure out gparted (I suspect AF is the problem).

Anyway, thanks for the info.

---

### Post by lisati on 2016-01-08
I'm not sure if I'm looking at the correct website, but the [page]("http://www.partition-tool.com/personal.htm") I was looking at for the free version indicates that it is designed to run on Windows. This means that it won't run on Linux-base systems without help. When dealing with things like partitions, it's often better (and safer) to look for something that will run on the OS you happen to be using.

---

### Post by Bucky Ball on 2016-01-08
Are you actually using Ubuntu or just wanting to use it to clone Windows partitions? Best to use Windows for that. There are plenty of tools in Linux you can use already without trying to install Windows apps using WINE, where some stuff will work, some won't, but WINE is really a bit of a kludge.

For Linux, [fsarchiver]("http://www.fsarchiver.org/QuickStart#How_to_extract_filesystems_from_an_archive"), [Clonezilla]("http://clonezilla.org/"), rsync ... among others. They will run natively. [SystemRescueCD]("http://www.sysresccd.org/SystemRescueCd_Homepage") includes fsarchiver. It is one line of code to clone your partition, or partitions, and one line to clone them back to a new target.

From what I can gather, though, you're probably best to install XP and use Windows tools unless you are ready and willing to jump on the learning curve and learn to do it with a native Linux app. Whether you use Wine or not, there will be a Linux learning curve.

---

