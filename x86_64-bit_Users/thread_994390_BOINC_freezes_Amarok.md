---
title: "BOINC freezes Amarok"
date: 2008-11-26
forum: x86 64-bit Users
---

### Post by rileinc on 2008-11-26
I switched to 64 bit Ubuntu Intrepid on Nov 17th and noticed recently that BOINC 6.2.12 running Rosetta sometimes "stops" Amarok (v1.4.10; KDE 3.5.10) from playing. Amarok resumes playing when I suspend BOINC. 
I put stop in quotes because BOINC doesn't literally stop Amarok, more like temporarily prevents it from using any resource. 

For example, if Amarok freezes at the 10 second mark of a song and I suspend BOINC after 20 seconds, the song resumes playing at 0:30.
This problem was never encountered in 32bit Intrepid.

I have an Intel E6750 dual core CPU. One core is used to run Rosetta, the other is free. The project is set to take 100% of CPU time.
I've looked around in the forum and searched Google, but I haven't seen anyone with a similar problem. 

I know this is probably not enough information to diagnose the problem but I'm not sure which log file to check.
Any input is appreciated.

---

### Post by rumblered on 2008-12-09
This sounds very similar to a problem I've been having since 2.6.27 on AMD64: [Bug 279907]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279907")

If you occupy both cores with BOINC, then run Amarok or some other media player, then run some CPU-intensive task (such as bzipping a file), can you produce even worse freezes? I can make my machine completely lock up, then resume several minutes later.

---

