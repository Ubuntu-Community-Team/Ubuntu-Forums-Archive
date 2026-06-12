---
title: "Making a Home partition in an installed Feisty64bit?"
date: 2007-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Udibuntu on 2007-12-04
Hi,

I wish to make a Home partition in an installed Feisty64.

I read [Psychocats]("http://www.psychocats.net/ubuntu/separatehome") tutorial but find it a bit risky for me, being a novice.

Is there a dummy proof step by step?

I'd greatly appreciate your help as I'm beginning to understand the importance of a true Home partition, instead of Home folder.

Thanks,

Udi

---

### Post by perixx on 2007-12-04
Hello Udibuntu!


I've done that myself (Under Feisty 32bit), but it should work similarly under Ubununtu AMD64, I suppose. Note that I've altered the way the guys at psychocats did it slightly, so read along and look if you think you can handle it:

[http://ubuntuforums.org/showthread.php?t=575671&page=2]("http://ubuntuforums.org/showthread.php?t=575671&page=2")


perixx

---

### Post by Udibuntu on 2007-12-04
Hey Perixx, thanks for the reply.

Sorry, this seems to be waaay over my head.

I'll bump this a couple of times and drop it if no simpler, idiot proof method comes up.

Thanks again,

Udi

---

### Post by perixx on 2007-12-04
Why, what's it about? What is too hard for you, just ask....
Basically, you have to 

[B]a) copy your home folder onto another partition, while preserving your file permissions. Of course, you have to create such a home-partition first, if you don't have it yet.

b) tell Ubuntu where to look for the files from now on (the new partition is mounted to the /home folder in the /etc/fstab file with a new entry).

c) rename the old /home folder for backup and so you don't get confused - and create a new /home folder on which you mount your home-partition to. [/B]

That's it all about. You might only leave out the last step but you can't skip a) or b), from what I can tell (on a running system). It's maybe best to use your Live-CD for that purpose. Unless you'd specify an alternative /home folder directly at the (manual) installation of Unbuntu, I'm afraid you've got no other choices...

If you follow all of the steps I wrote, or on psychocats, if you prefer, nothing should go wrong. You don't have to go through the steps for /opt (that's OPTionally, as you may have already guessed :) ). 

It's a good idea to make a backup of your personal files in spite, of course.

> **EDIT:** Hi again, Udi! Despite to what I've written above (shouldn't be all wrong), stick to Psychocats. You can still use my method, but for PARTITIONING, please use your Live-CD! See also this:
[http://ubuntuforums.org/showthread.php?p=3901747#post3901747]("http://ubuntuforums.org/showthread.php?p=3901747#post3901747")

regards,


perixx

---

### Post by Udibuntu on 2007-12-07
Cheers Perixx, I'll give it a shot,I guess I need to go into deeper waters for this one...

Will update on results.

Thanks again,

Udi

---

### Post by perixx on 2007-12-09
Udi, 

unfortunately, I found some more bugs in my descriptions (I was having trouble getting everything up and running again, but now it REALLY should work! I've edited the HowTo on page 2 accordingly.

Along with that though, I've come up with some recovering hints I had to work out first...  

I hope you didn't let yourself scare off by this ;]

perixx

---

