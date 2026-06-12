---
title: "Hard drive space rapidly depleting"
date: 2006-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by nate_2001 on 2006-07-10
Hi.  I have Ubuntu installed on a 200 gig ide hard drive.  It appears that 120 gigs of this is already used, but I can't find anything that would be that large.  My music collection is about 35 gigs, I don't keep movies on the hard drive.  I've been using dvd shrink a lot to backup my movies, but I delete the files when it's finished running.  Does anyone have any ideas as to what all of this space might be used for?

Thanks!

---

### Post by Ptero-4 on 2006-07-10
/var and /tmp are two good places that hide tons of temporary crap that can be safely deleted, also there's the debs left behind everytime you download something through synaptic/adept/apt-get/aptitude.

---

### Post by nate_2001 on 2006-07-10
Oh, I forgot to mention the thing that is confusing me the most.  When I look in nautilus, each individual folder appears to be the correct size.  When I do edit-select all then right click and choose properties, then the size of all of the files equals 120 gigs.  When I look at them all individually, they don't add up to more than 60.

---

### Post by nate_2001 on 2006-07-10
Ah.  When I delete files from the DVDshrink program, I had to do it as root because the directory it uses was owned by root.  I just found the root .Trash directory and emptied it.  My space is free again. I also changed the permissions on that directory so that I can use the regular trash from now on.  I see why using root too much can be a bad habit.

---

