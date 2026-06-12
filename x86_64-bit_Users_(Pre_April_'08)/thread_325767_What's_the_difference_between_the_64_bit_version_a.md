---
title: "What's the difference between the 64 bit version and the regular version"
date: 2006-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by thesteamboat on 2006-12-26
I have a laptop with an AMD 64 bit processor, on which I installed Drake about 5 months ago. 
At the time, I was not aware of the 64 bit version of ubuntu, and so I installed the standard version on my computer.  I have had no complaints except for being unable to get my wireless card working. 

Should I switch my system over to the 64 bit version of ubuntu? If so, what is the easiest way to changeover?

Also, where should I head for advice on getting my wireless card working? After following various tutorials I can get ndiswrapper to recognize that the drivers and hardware are installed, but the card won't operate.

Thanks

---

### Post by bruenig on 2006-12-26
I wouldn't use 64 bit. It doesn't have support for stuff such as flash and a variety of other things. You can get those things working but with far more effort than in 32 bit. And since there is not much in the way of performance boost, it isn't worth it, imo of course.

---

### Post by Kilz on 2006-12-26
> **bruenig said:**
> I wouldn't use 64 bit. It doesn't have support for stuff such as flash and a variety of other things. You can get those things working but with far more effort than in 32 bit. And since there is not much in the way of performance boost, it isn't worth it, imo of course.

While it may be slightly more work to get flash working, it isnt as hard as you make it out to be. The sticky links howto's to solve the problem. There is a performance boost , but the amount of boost depends on the application.

---

### Post by rplantz on 2006-12-26
> **Kilz said:**
> While it may be slightly more work to get flash working, it isnt as hard as you make it out to be. The sticky links howto's to solve the problem. There is a performance boost , but the amount of boost depends on the application.

Reminds me of my teaching days. Some students would complain that the programming assignment was unreasonable because it took them five hours to complete. Other students would say that they wished there was more to the assignment because they were all done in only eight hours. (I'm not making this up.)

It really depends on how you wish to spend your time. I've been running 64-bit since my first Ubuntu installation (5.06). I enjoy the challenges. But things like flash are not that important to me. (I have a Mac next to me it I really need it.)

As far as the easiest way to switch over, I'm pretty sure that you need to do a fresh install.

How much free space do you have on your disk? You might wish to create another partition and do a 64-bit install there. Then you could try it out for yourself.

---

### Post by JAPrufrock on 2006-12-28
Getting what you need to work on the 64 bit can be painful.  If your lucky, everything you need will be installed fairly easily.  I have three 64 bit machines running on the Ubuntu 64 bit kernal (all AMD64s).  Two of them work like a dream.  On the other one I still can't get stand alone mplayer to work properly.  Even so, I'm sticking with 64bit platforms.  Within the next decade everything will be 64bit.

---

### Post by Paulo Wageck on 2006-12-28
64 bit seens much more smooth for me....

many things on 32 bit are easier... 

but you can always use vmware... use another hdd or have another mobo box/notebook....


64 is the way to go on my home server....

---

### Post by thesteamboat on 2006-12-29
Thanks for all the input!
I'm going to hold off for now, as the performance boost isn't a compelling enough reason to move all my files and settings. If I had more space I'd dual boot and enjoy the challenge, but I got a cheap laptop with limited memory and I'm running out of room.

---

### Post by duff on 2006-12-29
I don't think it'll be worth the hassle of a reinstall.  I only noticed a performance boost when ripping DVDs.

---

### Post by mayhemt on 2006-12-30
check this 
Ubuntu: 32-bit v. 64-bit Performance

[http://www.phoronix.com/scan.php?page=article&item=616&num=1]("http://www.phoronix.com/scan.php?page=article&item=616&num=1")

I am having second thoughts on installaing 64 bit after reading this article..

---

### Post by tcnguyen on 2006-12-30
there isn't much advantage to go for 64-bit unless your application optimize/require of it. Especially, if you have more than 2.6G of memory in your system.

There would be an advantage if your application requires more memory than OS can provided.

---

### Post by pseudonym on 2006-12-30
My evidence is impressionistic, but since running 64-bit Xubuntu I do notice a significant performance increase in processor-intensive tasks like de/remuxing and encoding video, and kernel compilation, perhaps more so than the Phoronix article suggests.

In any case, at least one of those 'benchmarks' was nonsensical - the gaming test. He used a crappy video card (by current standards) and presumably a low resolution (though it wasn't specified) so that the task would fall mainly on the CPU. But if you play graphics-intensive games it's 99% certain you won't be doing so under those conditions.

I guess if you're happy to believe the reviewers, you're likely to stick with 32-bit for now. But if you're the sort who wants to try things out for yourself, you'll be tempted to give 64-bit a shot. ;)

I certainly know I'm no worse off for running 64-bit. Sure, there are still a couple of apps like flash and w32codecs which aren't properly supported yet. But the workarounds are trivial to set up, and may even improve your knowledge of Linux (I'm thinking chroot here).

I even more cretainly know that, after having taken the time to try both 32-bit and 64-bit, switching back now would be a complete waste of time. :)

---

### Post by marcw on 2006-12-30
> **mayhemt said:**
> check this 
Ubuntu: 32-bit v. 64-bit Performance

[http://www.phoronix.com/scan.php?page=article&item=616&num=1]("http://www.phoronix.com/scan.php?page=article&item=616&num=1")

I am having second thoughts on installaing 64 bit after reading this article..

That article was missing at least one benchmark that would highlight a very important difference between 32 and 64 bit processing - Kino exporting.

On a whitebox with an AMD 64 3500+ with 1GB ram and loaded with 32 bit Edgy, I would see something like 13 hrs to export a 2 hour .dv file to DVD mpeg.  This was about the same processing time that I saw on a slightly older 3200+ AMD 32 bit processor.  However, after I installed the 64 bit Edgy and made the fs XFS on the 3500+, that same 2 hour .dv file would export in about 3 hours.

That's 13 hours vs 3 hours.  I would call that a significant difference.  To be fair, XFS vs EXT3 might have played a part in that monumental performance gain.  But I'm fairly confident that the bulk of that performance gain was caused by the 64 bit OS.

That said, I'm not sure I would run Ububtu 64 on my desktop until I could get more desktop type apps in native 64 mode.  I'm thinking OOo, Macromedia, etc.  Aside from the video processing I mentioned, I see little to no performace gain in anything I normally do on my desktop.

---

### Post by kesman on 2006-12-30
> 
Thanks for all the input!
I'm going to hold off for now, as the performance boost isn't a compelling enough reason to move all my files and settings. If I had more space I'd dual boot and enjoy the challenge, but I got a cheap laptop with limited memory and I'm running out of room.


You only need about 2gigs of hd for this, since you can easily use shared /home -directory if you have it as a separate partition on the harddisk. That way all your settings and personal files are in every operation system that use that partition as theirs /home -directory.

---

### Post by meldroc on 2006-12-30
I just got a new laptop (Asus A8Js w/ 2.0GHz Core 2 Duo) and installed x86-64 Linux on it.

The vast majority of software works nicely on it, but of course, there are things like Flash, Java plugins for Firefox and Windows codecs that are only available in 32-bit, so getting them working is an unholy pain in the *** right now.

After reading the Phoronix article, I'm sorely tempted to go back to 32-bit Ubuntu.  As the Phoronix article mentions, you don't get much of a boost in performance.  You get 64-bit registers, and you get to address more than 4GB of memory without jumping through PAE hoops, and most users don't have use for that yet.  When Flash 9 and Java work in 64-bit Firefox, and mplayer can run complied in 64-bits, but has a wrapper built in so it Just Works with 32-bit codecs, then it'll be time to make the switch.  But right now too many things are broken.

---

