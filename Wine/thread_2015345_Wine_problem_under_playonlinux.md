---
title: "Wine problem under playonlinux"
date: 2012-07-03
forum: Wine
---

### Post by asharpham on 2012-07-03
I installed playonlinux as I wanted to run iTunes in Ubuntu. It installed fine and I installed iTunes 7 (iTunes 10 wouldn't install). When trying to run iTunes, I keep getting an error message - something about invalid parameters. iTunes doesn't work and eventually the computer locks up.

Any suggestions?

---

### Post by oldos2er on 2012-07-03
Moved to Wine.

---

### Post by Toz on 2012-07-03
> **asharpham said:**
> I installed playonlinux as I wanted to run iTunes in Ubuntu. It installed fine and I installed iTunes 7 (iTunes 10 wouldn't install). When trying to run iTunes, I keep getting an error message - something about invalid parameters. iTunes doesn't work and eventually the computer locks up.

Any suggestions?

What version of PlayOnLinux are you running?
Open a terminal window, run the following command, and post back the results:
```
apt-cache policy playonlinux
```
What version of Wine are you running?
Open a terminal window, run the following command, and post back the results:
```
apt-cache policy wine
```
And what exactly is the error message?

According to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10248&iTestingId=26269]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10248&iTestingId=26269"), iTunes v7 is rated as silver. The one time I installed it, it started up, but I couldn't really do anything with it. I had much more success running iTunes in a Windows vm, though I could never get it to sync.

---

### Post by asharpham on 2012-07-08
I think i uninstalled it but here's the results you asked for:
playonlinux:
  Installed: (none)
  Candidate: 4.0.14-1
  Version table:
     4.0.14-1 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/multiverse i386 Packages

wine:
  Installed: (none)
  Candidate: 1.4-0ubuntu4
  Version table:
     1.4-0ubuntu4 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages

I'll reinstall to get proper results if this will help. I uninstalled because the computer kept locking up.

---

### Post by buzzmandt on 2012-07-08
I highly recomend you update to the current playonlinux.  They've done some fabulous things with more recent releases.

go to [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html) and follow the instructions there or do the following commands which is the same as the link.

```
wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
```
```
 sudo wget http://deb.playonlinux.com/playonlinux_precise.list -O /etc/apt/sources.list.d/playonlinux.list
```
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

itunes in wine never got better than a silver on any test results turned in.  It doesn't look good I must say.  However, the most recent test was as far back as 1.2 rc7.

In playonlinux you can add current wine up to and including wine 1.5.8.  Under tools>manage wine versions.  once you've updated pol, click your itunes>configure> and change your wine version to some very recent wine versions and try.  You might get lucky.

---

### Post by asharpham on 2012-07-09
Well I followed all those instructions and it appeared okay but iTunes just doesn't work for long without freezing the computer.

The error message I get is "Wine Program Crash. Internal errors - invalid parameters received".

---

