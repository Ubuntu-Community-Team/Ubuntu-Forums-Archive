---
title: "Keeps showing updates"
date: 2008-06-06
forum: openSUSE and SUSE Linux Enterprise
---

### Post by sayakb on 2008-06-06
Sorry for the awful thread title!
Anyway, I just installed Suse and let Yast update all my packages and rebooted many times.
Now I still have one update showing up in the Online updater.
It shows:
[ATTACH]73107[/ATTACH]

After I press Install, it again searches the OSS, non OSS and KDE repos and shows me the same window again. This goes on indefinitely and it doesn't actually download this package.
I tried updating all installed libqt4 components from Yast package manager but still the update manager seems keeps showing this update.

Any suggestions?

---

### Post by 67GTA on 2008-06-06
There was a bug for 10.3 that caused this. I think you have to run the online updates in Yast (not the panel updater). There is a bug fix for the panel updater. I think it had something to do with an endless update loop with amarok.

---

### Post by quickshade on 2008-06-07
Really should just run 11.0. It's much nicer and all these problems with updating and the repos being slow are all fixed in 11 (the entire update system was rebuilt)

---

### Post by 67GTA on 2008-06-07
> **quickshade said:**
> Really should just run 11.0. It's much nicer and all these problems with updating and the repos being slow are all fixed in 11 (the entire update system was rebuilt)

That's what I'm waiting for :) It is supposed to be final the 19th. Mint needs a buddy to play with.

---

