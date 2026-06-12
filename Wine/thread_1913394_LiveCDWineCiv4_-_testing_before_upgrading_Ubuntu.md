---
title: "LiveCD/Wine/Civ4 - testing before upgrading Ubuntu"
date: 2012-01-22
forum: Wine
---

### Post by Sunships on 2012-01-22
Hello!

i am currently running Ubuntu 10.10, and have Civ4 running perfectly in Wine. I would like to upgrade to the next LTS when it gets released, but don't want to go through the process of upgrading only to find that Civ4 etc don't work as well afterwards.

Is it possible to boot into the new LTS using a LiveCD, install Wine and then direct Wine to my current .wine directory (on /home of my existing installation) and run Civ4 from there, to see if it will run properly before I decide to go through with the installation?

A second idea I had was to move /home to its own partition. If I do this, would it be possible to install different versions of Ubuntu/other distros and see how Civ4 runs in Wine from the /home partition under those, without having to lose my existing OS?

Thanks for your help, all.

---

### Post by Sunships on 2012-01-22
*bump*

---

### Post by Sunships on 2012-01-26
*bump*ing this again.

---

### Post by Sunships on 2012-01-26
*bump*

---

### Post by Sunships on 2012-01-27
*bump*

---

### Post by Sunships on 2012-01-29
*bump*

---

### Post by Sunships on 2012-01-30
bumping to the top again....

---

### Post by Sunships on 2012-01-31
One last time, and then I'll call it a day with this crazy idea.

Or I'll just test it anyway.

---

### Post by Soulcage on 2012-01-31
You would need to install video drivers which would require restarting, so no.

---

### Post by Sunships on 2012-02-02
> **Soulcage said:**
> You would need to install video drivers which would require restarting, so no.

Argh. Thanks soulcage!

---

### Post by Sunships on 2012-08-10
For anyone who comes across this now, I took the plunge into 12.04 and have got Civ4 Complete running perfectly :)

I'm using Wine 1.5.10, and have the following overrides:

d3dx9_26
d3dx9_31
d3dx9_32
d3dx9_33
d3dx9_34
msxml3
msxml3r

All are set to "Native, then Built-in", and I copied the DLLs from a Win XP virtual machine.

I also have Civ5 working - I gather that is less of a challenge, but if it helps anyone for that I have:

d3dx9_26
d3dx9_31
d3dx9_32
d3dx9_33
d3dx9_34

again set to "Native, then Built-in", and I installed d3dx9_36 and vcrun2008 as directed by the Wine DB instructions: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=21465](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21465)

I'm pretty clueless about overrides in Wine, so some of the above might not make sense, but hopefully this will help someone in the future :)

---

