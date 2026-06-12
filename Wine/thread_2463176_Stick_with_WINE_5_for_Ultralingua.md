---
title: "Stick with WINE 5 for Ultralingua"
date: 2021-06-05
forum: Wine
---

### Post by Tom_ZeCat on 2021-06-05
I reinstalled my Kubuntu 20.04 LTS and am in the process of reinstalling all my applications.  I've had success in the past (since about 2012) running Ultralingua 6.0 under WINE.  This time around, I installed WINE and Q4WINE via PPAs to get the latest versions.  My WINE version was 6.0.  However, for the life of me, I could not get Ultralingua 6 to run, with or without help from Q4WINE.  I therefore uninstalled both WINE 6 and Q4WINE.  I then installed WINE from Kubuntu's Discover repository, as well as Q4WINE from that same source.  After that change, I was able to get Ultralingua 6 running.  

Should I be concerned that when Kubuntu eventually goes to WINE 6 in its repository that it could break Ultralingua for me?  Can I keep using WINE 5 indefinitely if I download it somewhere?  I would really hate to have to run Ultralingua under VirtualBox with Windows.  As of yet, it runs flawlessly under WINE.  I just couldn't get it to work in WINE 6.

---

### Post by deadflowr on 2021-06-05
Wine will almost certainly never get to wine 6 for 20.04 in the normal repositories.
An exception to that would be a high-level security issue that the Ubuntu wine maintainers cannot backport the fix for it.
(and even that would be rare as wine almost never gets updates in the repos)

---

### Post by Tom_ZeCat on 2021-06-05
> **deadflowr said:**
> Wine will almost certainly never get to wine 6 for 20.04 in the normal repositories.
An exception to that would be a high-level security issue that the Ubuntu wine maintainers cannot backport the fix for it.
(and even that would be rare as wine almost never gets updates in the repos)

Thanks.  I appreciate the help.  I guess I don't have to worry about it for a while.  I did check to see if Ultralingua had finally come out with a Linux version, but they haven't.  They do have an Android version (which I use on my phone), so there could be the option of running that on my PC.  I've heard of running Android apps under Linux, but have never really looked deep into it.  For now, at least, the Windows version will work.  

In future *buntu distros, when WINE 6.0 does become standard, am I able to install an old version of WINE to keep Ultralingua working?  It's the only program I run under WINE regularly.  It's really a good app, and it would be tough to give up.  I found a Linux equivalent in GoldenDict, and that one is even better in some ways, but Ultralingua is best when you just want the very basic and most used translations of words.  I would hate to have to give it up.

---

### Post by CatKiller on 2021-06-06
> **Tom_ZeCat said:**
> In future *buntu distros, when WINE 6.0 does become standard, am I able to install an old version of WINE to keep Ultralingua working?
Being able to use a particular version of Wine for a particular Wine prefix is a standard feature of Wine helpers like q4wine, Lutris, or Proton.

You'll want to report the regression to the Wine devs so that they can fix future versions for everyone.

---

### Post by mastablasta on 2021-06-09
> **CatKiller said:**
> Being able to use a particular version of Wine for a particular Wine prefix is a standard feature of Wine helpers like q4wine, Lutris, or Proton.
.
i use play on linux for that and manage various wine version for different widnows games & apps.

there are also paid for solution such as CrossOver if you need business grade support.

---

