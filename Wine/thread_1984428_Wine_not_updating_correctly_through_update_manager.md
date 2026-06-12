---
title: "Wine not updating correctly through update manager"
date: 2012-05-21
forum: Wine
---

### Post by Strebenherz on 2012-05-21
I'll load update manager, and this error message will load.  How do I update the repository indexes it mentions?

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://wine.budgetdedicated.com/archive/source/dists/ubuntu/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/archive/source/dists/ubuntu/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://wine.budgetdedicated.com/archive/source/dists/ubuntu/main/source/Sources.gz](http://wine.budgetdedicated.com/archive/source/dists/ubuntu/main/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

---

### Post by Enigmapond on 2012-05-21
That PPA you have listed is gone. Delete those from your sources and if you want to use a PPA...use this:

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by Strebenherz on 2012-05-22
Thank you.  The site mentions....

Step 1: On the PPA's overview page, look for the heading that reads Adding this PPA to your system. Make a note of the PPA's location, which looks like:

ppa:gwibber-daily/ppa

Step 2: Open a terminal and enter:

sudo add-apt-repository ppa:user/ppa-name

Replace ppa:user/ppa-name with the PPA's location that you noted above

I'm not sure what the PPA for wine would be.  This site yes, but I'm not sure what to put into the terminal line after
sudo add-apt-repository

---

### Post by thatguruguy on 2012-05-22
> **Strebenherz said:**
> Thank you.  The site mentions....

Step 1: On the PPA's overview page, look for the heading that reads Adding this PPA to your system. Make a note of the PPA's location, which looks like:

ppa:gwibber-daily/ppa

Step 2: Open a terminal and enter:

sudo add-apt-repository ppa:user/ppa-name

Replace ppa:user/ppa-name with the PPA's location that you noted above

I'm not sure what the PPA for wine would be.  This site yes, but I'm not sure what to put into the terminal line after
sudo add-apt-repository

The page also says the following:
> You can update your system with unsupported packages from           this untrusted PPA by adding **ppa:ubuntu-wine/ppa**           to your system's Software Sources.
As such, the command you would type in the terminal would be as follows:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
Follow the on-screen prompts, and then type:
```
sudo apt-get update && sudo apt-get upgrade
```

---

