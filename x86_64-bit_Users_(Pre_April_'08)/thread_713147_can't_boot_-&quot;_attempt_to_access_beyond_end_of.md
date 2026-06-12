---
title: "can't boot -&quot; attempt to access beyond end of device&quot;"
date: 2008-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by ceege on 2008-03-02
I've been using Mythbuntu 7.10 AMD64 for about a month.  Yesterday I noticed that things were running REALLY slowly, so I rebooted.  After that, my system would not start back up again.

If I reboot using the recovery mode, the system stops loading at the following screenshot.  Everything I've read here and from google points to a raid problem, but I am not using raid.

What can I do?

---

### Post by ceege on 2008-03-03
Nobody has any ideas?

---

### Post by fjgaude on 2008-03-04
Might be a drive going bad.

Try running from a LiveCD fsck on the drive and see if you get any errors.

---

### Post by ceege on 2008-03-04
Before your post, thinking all hope was lost, I loaded the live cd onto a spare HD and once up and running mounted the messed up drive and started moving files off of it and on to the temp drive.  I was pretty much finished when I got notice of your post.  

I did notice that there were files that were messed up while backing up all of my customized *.conf files and such, and now that I have run fsck they appear normal again.

But, I think when I get home I'll format and start over (things are always better the next time around, right?), but I'm curious: 

1) what would have caused errors in the first place? (The errors were mostly Illegal block [blah] in inode [blahblah] CLEARED)
2) and this is just a filesystem problem, not hardware?  The drive is only 3 months old....


Thanks,
Chris

---

### Post by fjgaude on 2008-03-04
Well, it hard to say what would cause such errors... the hard drive is likely the least reliable thing in our computers. And just because the drive is new doesn't mean is a solid one.

Keep with it but do run fsck often and from there you might get a feel if errors are continuing to be produced. If so, then it's likely the drive, one still under warrenty.

---

### Post by Ocxic on 2008-05-07
Your hard drive is fine, I get the exact same thing with my drive it's happening to me as well, I've gone through extensive testing of my drive an I assure you it not that. everything is fine. this is starting to get on my nerves, as I cannot get anything to work after i get this error, I can't unmount the drive the error you get is all dmesg will spit out, and my CPU usage skyrockets to 100%, and I end up haveing to do a hard reboot. 
I'm offering a $50 dollar reward to anyone who can sove this

---

