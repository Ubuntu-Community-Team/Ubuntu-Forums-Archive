---
title: "Advice on partition setup for reformat"
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by foulmouth on 2005-11-22
Due to my ever increasing like for ubuntu over osx I have decided to repartition a little more efficiently this time. I have been trying to figure out what sort of format I should put on my hard drive so that linux can read from my osx partition and os x can read from my linux partition or is this even possible? I basically just want to be able to transfer files back and forth and not worry about and compatability problems.

btw: osx does need to stay installed on my computer due to airport issues.

---

### Post by ssam on 2005-11-22
linux reads almost any format including hfs+. mac os can read ext3 with a plugin [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) (does not work on mac os x 10.4 yet ( [http://sourceforge.net/forum/forum.php?forum_id=505228](http://sourceforge.net/forum/forum.php?forum_id=505228) ))

you may end up with permission problems if you mount one partition from the other operating system. there are a few methods around this (read some of the other posts in this forum).

there is also the possibility of doing some damage to the other operating systems files, as they wont be protected by the operating system. for example mac os x wont let you delete important files, but if you mount it in linux with full permissions you could remove anything.

you may want to set up some shared space in a seperate partition and let both systems access that. hfs+ would probably be best for this.

you do not need to keep mac os x. airport extreme will only work from within mac os x (unless you want to mess with the MOL hack). you need mac os x installed to run MOL. if you dont mind not using mac os x or airport extreme then you can delete mac os x.

---

