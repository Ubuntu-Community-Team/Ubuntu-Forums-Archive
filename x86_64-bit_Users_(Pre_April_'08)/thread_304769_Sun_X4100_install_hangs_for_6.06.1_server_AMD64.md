---
title: "Sun X4100 install hangs for 6.06.1 server AMD64"
date: 2006-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by ke han on 2006-11-22
This is partly a repost from a week ago.
Its pretty important stuff since Ubuntu has announced they now support Sun's X4100 and X4200 servers.
The trouble is, Ubunutu 6.06.1 server AMD64 install CD hangs when it gets to the partitioning part of the install.
There is very little info on how to get around this and none from official Ubuntu sources.
When I posted a week ago, I did receive 1 reply (thanks) which involves manual tricks way above my experience level (building your own kernel and such).

Here's the details of the original post:

I am trying to install Ubuntu 6.06.1 server AMD64 on a Sun X4100. The two 73 GB SAS drives are configured standard as RAID-1 by the LSI MPT card. This config is recongnized by both Solaris 10 and Centos 4.4 installers.
When I try installation with the Ubuntu 6.06.1 server AMD64 ISO, the install "locks up" when it tries to start the partitioning process.
Any ideas?
thanks, ke han

---

### Post by syscon411 on 2006-12-06
Yup! Same problem here, I would love to deploy Ubuntu acrost the server farm (all 28 sun x4200's) but it hang on install. I love ubuntu and want to make life grand for me at work! Can someone help?

-Justin B

---

### Post by dimmer on 2008-03-03
I realize it's been a long while since you first posted these, and I wonder if you ever found a solution?

If not, my experiences are that the preseed needs to be pointing at /dev/sdb for the partitioning to work.  Further, you then should use a preseed late_command to download script and replace the devices in fstab with UUIDs, otherwise you might have problems booting.

---

### Post by ke han on 2008-03-04
ubuntu 7.04 doesn't have the problem.
Never fixed the 6.06 problem.

---

