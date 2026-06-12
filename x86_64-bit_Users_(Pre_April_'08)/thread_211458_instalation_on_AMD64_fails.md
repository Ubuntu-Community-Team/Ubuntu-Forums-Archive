---
title: "instalation on AMD64 fails"
date: 2006-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by iniurb on 2006-07-08
Hi all

I,m trying to install "Drapper" but it fails after the step "configuring some drivers", I had no problems with "Hoary" I,m currently running FC 5, any idea? Thx.

---

### Post by loserboy on 2006-07-08
did you try the alternate install?  i hear that when something like that comes up most people try the alternate and it works

---

### Post by recupero on 2006-07-08
One could also try the dvd-live, under cdimage/ports

I keep having the same problem: Ubuntu cannot be installed on my AMD64

---

### Post by hajk on 2006-07-08
> **iniurb said:**
> Hi all

I,m trying to install "Drapper" but it fails after the step "configuring some drivers", I had no problems with "Hoary" I,m currently running FC 5, any idea? Thx.

I don't recall such a step in the installer... Does the Dapper liveCD boot up properly? Or is it the liveCD that won't boot? In that case you might try giving some additional boot options, like noapic.

---

### Post by recupero on 2006-07-08
It's in the system install phase.
Some packages result being corrupted.
It is not possible to go ahead: soon all packages are corrupted even
sed, so on..
I had this problem when installing the alternate version.
What's the option to boot a minimal set of packages when installing the system?

---

### Post by loserboy on 2006-07-09
so you're sure your burner isnt messing up?

---

### Post by iniurb on 2006-07-09
I tried this, boot: live noapic; and i have this, kernel panic-not syncing:VFS:unable to mount root fs on unknown-block(8,1)

---

### Post by recupero on 2006-07-09
It worked with the dvd-live install. 
You find it under [url]http://cdimages.ubuntu.com

---

### Post by AllenGG on 2006-07-09
Only the alternate install works, for me.
[64-bit PC (AMD64) alternate install CD]("http://ubuntu.cs.utah.edu/releases/6.06/ubuntu-6.06-alternate-amd64.iso")

---

