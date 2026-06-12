---
title: "Upgrade from 32bit system"
date: 2008-05-17
forum: x86 64-bit Users
---

### Post by carfield on 2008-05-17
I have a 64bit CPU but wrongly install a 32bit version of ubuntu, how can I update it back to 64bit ubuntu? May make a fresh 64bit installation? Will my setting persist?

---

### Post by Xiong Chiamiov on 2008-05-17
You'll have to do a fresh install from scratch if you want the 64-bit OS instead of 32-bit.

---

### Post by carfield on 2008-05-17
> **Xiong Chiamiov said:**
> You'll have to do a fresh install from scratch if you want the 64-bit OS instead of 32-bit.

Too bad... :-(

---

### Post by CptPicard on 2008-05-17
So you really can't just switch some repositories in sources.list and do a dist-upgrade? I suspect something would just crash along the way before you could get your machine again in a bootable state?

I'm thinking of "upgrading" to 64bit as well from my 32bit setup that has seen upgrades all the way from dapper, but would hate to do a fresh install...

---

### Post by Kilz on 2008-05-17
> **CptPicard said:**
> So you really can't just switch some repositories in sources.list and do a dist-upgrade? I suspect something would just crash along the way before you could get your machine again in a bootable state?

I'm thinking of "upgrading" to 64bit as well from my 32bit setup that has seen upgrades all the way from dapper, but would hate to do a fresh install...

You can mount a /home directory if you have a separate one, also if you have hard drive room you can 
1. Do a dual install
2. Mount the 32bit one inside the 64
3. Move over your media and other document files. Also the contents of home if its not a separate partition.
4. Once everything is as you like it, delete the 32bit install to reclaim space.

After so long running and upgrading, you would probably be better off cleaning out old unused files and other things you tried to customize that didnt upgrade. But its all up to you.

---

### Post by carfield on 2008-05-17
Actually I just run install from CD again and it will preserve most of the setting and data, exclude those made at /etc

---

