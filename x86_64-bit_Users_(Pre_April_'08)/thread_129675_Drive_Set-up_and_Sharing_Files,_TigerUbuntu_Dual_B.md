---
title: "Drive Set-up and Sharing Files, Tiger/Ubuntu Dual Boot"
date: 2006-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by archern on 2006-02-14
Greetings all!

I'm new to Ubuntu and am preparing to install it on an old sawtooth G4 running OS X 10.4.4.

Before I partition my disk I would like to know if I will be able to share files between OS X and Ubuntu installed on the same internal disk (dual boot) and, if so, how.

In one tutorial I found it suggestet creating a small HFS partion for sharing files but Disk Utility under Tiger doesn't seem to give me the option of creating an HFS (not HFS+) partition. I'm not even sure if this tactic is required - perhaps Ubuntu can now mound and read/write Mac OS Extended disks?

Going the other way, aparently there was a utility to read ext2/3 partitions that worked under Panther but not Tiger. Going back to Panther is not an option for me although I have it. I am just experimenting at this point and need the additional functionality/apps Tiger offers.

Any suggestions appreciated.

Thanks!

---

### Post by tmeier on 2006-02-14
Archern,

I have a G4 Tibook.  I have OS 10.4.2 installed on one partition and Ubuntu on another.  It works great to dual boot.  You can read your hfs+ partition from Ubuntu, you won't need to change anything, Mine works fine.  Search the forum on how to modify your fstab file to make it work.  That is where I figured it out.  I have not gotten the extension to read the ubuntu partition from os 10 to work yet.  Dual boot works great, as well as a program called Mac on Linux or MOL.  Go to the Wiki to learn how to set that up.  I can work in Ubuntu and boot up X without ever leaving ubuntu, and it works great.  I hope this helps.

---

### Post by archern on 2006-02-14
Thanks tmeier,

Your reply was very helpful. I proceeded with the install and it seems to have worked. I haven't gotten to the point of accessing files to/from OS X yet but look forward to trying.

Thanks again!

---

