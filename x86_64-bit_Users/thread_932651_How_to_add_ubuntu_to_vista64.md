---
title: "How to add ubuntu to vista64"
date: 2008-09-28
forum: x86 64-bit Users
---

### Post by robinhoodmp on 2008-09-28
Hello all, I was shown ubuntu by a friend at school and really liked what I saw. So I downloaded it and am trying to get it to load on my drive but I as of now have vista 64 on it with only the one partition. Now....can I get ubuntu to load and make a second partition for me, or.....do I have to do a whole LOT more work here? Thanks for any response, Mike.

---

### Post by Bakon Jarser on 2008-09-28
You've probably got some decisions to make.  Here is a link to some good installation guides.

[https://help.ubuntu.com/community/Installation#Other%20installation%20guides](https://help.ubuntu.com/community/Installation#Other%20installation%20guides)

---

### Post by Sef on 2008-09-28
1) Read[ Psychocat's Ubuntu]("http://psychocats.net/ubuntu").  

2) **Back up** your data before installing.

3) Use vista's partitioner to shrink the its partition.

---

### Post by Bakon Jarser on 2008-09-28
The only thing I don't like about psychocats is that he recommends fat32 for shared data partitions.  Don't use fat32, it is an outdated file system.

---

### Post by Jouke74 on 2008-09-29
If you are scared of partitioning you can also try the Wubi installer first. I have to admit that I have no experience with Vista 64, I am using this with Xp 32 at work. Wubi makes a sort of shell around your Ubuntu that makes it possible to install and use Ubuntu as a windows program (in principle). This method has disadvantages too, so read about it first.

---

### Post by Jive Turkey on 2008-09-29
I reccomend you add 3 partitions,
1. around 6-8 GB for the "/" or "root" directory
2. a swap partition the same or slightly bigger than the amount of RAM you have, cross your fingers and hope suspend and/or hibernate work
3. A large partition for your "/home" directory, use up all of the remaining disk space for this.
4. your Vista partition should be 20% larger than its used space so it can defrag properly.  I like to use the ifsdriver so I can read and write to my /home partition from Vista, and I have my userspace folders like "Documents" and "Music" etc linked to my corresponding Ubuntu folders in /home/<user> to save space on the ntfs partition.  
I keep all my files on my home partition including image backups of my Vista partition so I can reinstall windows and all my apps in less than an hour. In case of infection or corruption, I can just refresh the image.

---

