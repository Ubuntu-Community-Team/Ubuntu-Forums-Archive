---
title: "Using ubuntu i86 and amd-64 version parallel"
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by walt+walt on 2007-08-09
Hello, I went through these threads here and couldn't find an appropriate answer to my query. 
I do have an pretty good equipped desktop with amd-64 dual. 4 gigs of Mem and a handful of harddrive gigs. Until know I used to run Kubuntu-32 and Kubuntu-64 in different partitions with an own /home for each of them. (there are other distros dumpling around - however I will eliminate those, cause it costs too much time to keep everything running and up-to-date).

Now, finally my question, strictly concerning KUbuntu 7.04 (or better, gutsy tribe 4):

-  can I make 3 Partitons: 1) Kubuntu-86 Root
                                         2)  Kubuntu-64 Root
                                         3)  one /home for both of them
It's a desktop, so I just could use either or of these systems. The idea is, if there are
apps which hesitate to run under the 64.bit version I could use the 32-bit-kubuntu. And for apps running on both versions I would spare time upgrading them twice.

Uff, I almost forgot, all my data like pics, music etc. are savely on usb-drives.

Many thanks for any ideas, tips and comments, walt

---

### Post by dabl on 2007-08-09
> **walt+walt said:**
> 
                                         3)  one /home for both of them


I'm sure the gurus can tell you how that could be made to work, but the short answer is, it's a bad idea for non-gurus.  A lot of your desktop settings are stored in /home, as well as your data, and that will be a cause of trouble if you don't run two identical desktops in your two different OSs.

However (and on a smaller size scale), you can safely make a single swap partition and let whichever OS is booted use it.

:)

---

### Post by david_2001 on 2007-08-10
Rather than dual booting between the two different environments, you could consider setting up a chroot.  The chroot would allow you to run 32-bit applications from the 64-bit environment using the same /home directory and would also save wasting disk space on two root partitions.

There are Ubuntu guides to setting up a chroot, e.g. [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575) but the [COLOR="DarkOrange"][Debian GNU/Linux AMD64 HOW-TO]("https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html")[/COLOR] is the best guide I've found.  (Hint: Use schroot rather than dchroot if you do go down this route, it has several practical advantages).

---

### Post by Cappy on 2007-08-10
You shouldn't even need a chroot to run your 32-bit apps. Post any problems making a 32-bit application run on 64-bit and we'll make it work ;)

I'm hesitant towards chroot because it takes up a lot of space and it requires work to setup.

---

### Post by dabl on 2007-08-10
> **david_2001 said:**
> 

and would also save wasting disk space on two root partitions.



Last night I installed my new WD7500 -- nominally a 750GB drive, but in reality more like a 700GB drive.  It cost $200, delivered. That's 28.5 cents per GB.  So, an 8GB root for the second OS will cost you exactly $2.28 USD.  That's the economic view of it.  How many hours of your own time would you invest to save $2.28?

Just a thought .....   :)

---

### Post by david_2001 on 2007-08-11
> **Cappy said:**
> You shouldn't even need a chroot to run your 32-bit apps. Post any problems making a 32-bit application run on 64-bit and we'll make it work ;)

I'm hesitant towards chroot because it takes up a lot of space and it requires work to setup.

A chroot is an absolute doddle to set up.  It took me less than an hour, uses a little over 400Mb and is the easiest way I've found of running the 32-bit only proprietary driver for my Epson Perfection 3170 Photo scanner.  (I cannot be bothered finding out whether the alternative of uninstalling 64-bit sane and force installing the 32-bit version is a feasible alternative in Ubuntu.)

---

### Post by david_2001 on 2007-08-11
> **dabl said:**
> Last night I installed my new WD7500 -- nominally a 750GB drive, but in reality more like a 700GB drive.  It cost $200, delivered. That's 28.5 cents per GB.  So, an 8GB root for the second OS will cost you exactly $2.28 USD.  That's the economic view of it.  How many hours of your own time would you invest to save $2.28?

Just a thought .....   :)

Look after the pennies and the pounds look after themselves...

---

