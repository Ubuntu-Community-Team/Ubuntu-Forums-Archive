---
title: "Dual Boot 64 bit Ubuntu with 32 bit XP Pro"
date: 2009-07-21
forum: x86 64-bit Users
---

### Post by adempewolff on 2009-07-21
I am going to be upgrading to a larger hdd (250GB from 80GB probably) in the near future and was entertaining the idea of installing the 64 bit version when I switch over.  I will still be dual booting with my 32 bit version of XP pro for the odd .docx file and what not that I can't make work quite right in Ubuntu and was wondering if there would be any issue with the two operating systems exchanging files.  Will Ubuntu be able to read write files on the XP partition without making them unreadable for XP.  Furthermore if I made a shared partition would XP be able to read files written by the 64b Ubuntu?

Also I understand data will take up slightly more space in a 64 bit environment could anyone give an estimate of about how large this factor would be?

Thanks for any answers, sorry if these questions sound silly I have a tenuous understanding at best as to exactly what is different with a 64 bit architecture!

---

### Post by bacil on 2009-07-21
Yes you will have no problem reading standard files between your OSes . I am using this setup on my T400 laptop i have 80gb linux partition 80gb XP partition and 140 gb ntfs partiton for data that i can mount between both systems

anything i write in linux i can read in windows and wice versa .. well with exeption for binary files for 64bit os etc :-)

---

### Post by litspliff on 2009-07-21
well, mostly correct.


unless you install linux on a NTFS partition (which i don't know if it is even possible with ubuntu), you will not be able to read your linux partitions in windows without going through some bullsht.

keep a big NTFS partition (windows native), because both operating systems can read/write to NTFS with no problem. mounting an NTFS partition in ubuntu is as easy as point-n-click.

that memory size thing you mentioned has nothing to do with the HD. i'm not quite sure what you're talking about there unless you're talking about DWORD vs. QWORD.  that's something you'll never have to deal with. you can read up on it though. just do a google search, or check out a pinned topic.

---

### Post by adempewolff on 2009-07-21
Thanks for the responses, now I just need to decide if I want to move to 64 bit....


As for the memory thing, what I had heard was something about addresses being longer with 64b which causes data to take up more space.  I'm not sure whether this was taking about disk space or memory.

---

### Post by litspliff on 2009-07-21
on the 64 bit strings of data vs. 32 bit strings.....just do a little readiing...about a half hour should give you some enlightenment...or at least the illusion thereof...


64 is more work than 32, but if you're up to a little extra challenge, the performance is about 35% better in my situation (your may vary...i multi-thread a lot, and load balancing on the cores is much better in 64 - IMO). 


i'm writing this message in 64, i've had it installed for about a day, and i like it for my laptop.
i wouldn't put it into a production box yet though....not quite ready for prime time....

on that note...we need more people pushing the 64 bit envelope, and this is a kick-***** forum for tech support.

---

