---
title: "Upgrading 32bit Feisty to 64bit one? Is it possible?"
date: 2007-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by bravemosquito on 2007-03-29
Mission impossible or there's already successful try to do that?
Any advices and opinions are welcome

---

### Post by Scheater5 on 2007-03-29
To my knowledge, Ubuntu has no way of doing this.  Although, you could fairly easily back up your data (to cds or another harddrive) and do a fresh install of 64 bit Fiesty.  Sabayon has a means of doing this (although it's still sort of experimental), so maybe there's one in the works for Ubuntu - but last I heard there was no automated means of turning a 32 bit into a 64 bit version

---

### Post by RS3York on 2007-03-29
I just moved from 32-bit to 64-bit but not in an automated fashion.  I had 64-bit then moved to  32-bit a while ago.  A couple weeks ago I decided to replunge into 64-bit computing and I'm loving it.  But to the point: I did a clean install.  

I have a separate /home partition.  So all of my settings & e-mail remained the same.  There's really little difference between some sort of 'apt-get  go-go-64bits' trickery and just downloading a new ISO of K/X/Ubuntu64 if you have a separate /home partition.  In both cases you need to (re)download the entire OS. 

Scheater5 is right, Sabayon does have an experimental 32bit to 64bit upgrade option.  But seeing as Sabayon is based on Gentoo, if any distro can do something it's going to be Gentoo or one of its derivatives.  I suppose one could manually do the same with Ubuntu if they knew the sequence in which to compile everything.  But that would take much longer than a clean install, so why even bother beyond proving to yourself that you can do it?

If you don't have a separate /home partition you could create a new partition and then copy your /home directory over before doing a clean install.  I've never tried that, but I don't see why it wouldn't work - but my ignorance here could be a big headache for you if you tried it.

---

