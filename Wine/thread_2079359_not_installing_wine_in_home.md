---
title: "not installing wine in /home"
date: 2012-11-01
forum: Wine
---

### Post by opfeld on 2012-11-01
Is there a way to install wine to a partition other that /home?  My /home only has around 8gb so having wine installed there means I can't install any games.  Whereas I have an extra ~250gb on a seperate partition.

---

### Post by Tweak42 on 2012-11-01
> **opfeld said:**
> Is there a way to install wine to a partition other that /home?  My /home only has around 8gb so having wine installed there means I can't install any games.  Whereas I have an extra ~250gb on a seperate partition.

There's a few different ways to accomplish this.

You can symlink the default wineprefix directory that wine uses "/home/<usernane>/.wine" to a directory on your other partition.  Basically wine and any programs accessing that path are seemlessly redirected to the other partition (minus backup utilities or course).  

Or you can change the actual wineprefix to a different directory.  This may involve adding some extra command parameters when launching wine programs though.  Wineprefixes are handy to use if you are creating seperate prefixes for segregating individiual programs so they don't step on each others installations.

Or better yet, why not just move your /home to the larger partition.  This will involve changes to the /etc/fstab and some copy commands.

---

### Post by zuti on 2012-11-02
Or add a new drive letter in winecfg and point it to a mount point/directory where there is enough space. And install games on that drive.

---

### Post by opfeld on 2012-11-02
I tried adding a new wine drive but when installing games it doesn't ask me where to install them it just auto chooses C:

I like the idea of moving /home because I also have 100gb of unallocated space, how would I go about that?  Is it something I would do in gparted?

---

### Post by opfeld on 2012-11-02
I never created a /home partition just a / partition, so if I just create a /home partition from unallocated space would everything move there automatically?  Or would I need to copy it over?

---

### Post by Tweak42 on 2012-11-03
> **opfeld said:**
> I never created a /home partition just a / partition, so if I just create a /home partition from unallocated space would everything move there automatically?  Or would I need to copy it over?

You would need to move the files.
Here's a guide from the ubuntu documentation but it can apply to other linux distros:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by crazyg4merz on 2012-11-04
I symlink from my other partition mounted as media. Everything working as usual. But failed to install ms office 2010. It showed a mscorsvc.exe(forget the exact name, not using laptop right now) error. I don't know if this is caused by symlinking. I Don't know :-)

---

### Post by opfeld on 2012-11-07
I tried copying over my home to a new parition and something got lost along the way and I ended up just doing a reinstall creating a seperate /home partition then which has solved my problem.  Thanks for the help

---

### Post by Tweak42 on 2012-11-08
> **crazyg4merz said:**
> I symlink from my other partition mounted as media. Everything working as usual. But failed to install ms office 2010. It showed a mscorsvc.exe(forget the exact name, not using laptop right now) error. I don't know if this is caused by symlinking. I Don't know :-)

I don't believe that error would be caused by a symlink.  It sounds more like a wine or wine dependency issue.

---

