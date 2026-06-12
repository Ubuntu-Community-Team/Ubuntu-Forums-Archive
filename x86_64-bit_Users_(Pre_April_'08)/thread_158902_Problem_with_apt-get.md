---
title: "Problem with apt-get"
date: 2006-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Slurm on 2006-04-11
hello all, 

I have been running apt-get install and/or apt-get upgrade and I keep getting the following error..

Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz)  404 Not Found

I have uncommented this in my etc/apt sources.list to no avail.  I also commented it out to see if that helped and I get nothing.  

Any suggestions?

Slurm

---

### Post by Bergen on 2006-04-12
You need to run apt-get update (before upgrade) after updating sources.list.

---

### Post by Slurm on 2006-04-12
Thanks,  I did this and it still failed.

Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  404 Not Found
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  404 Not Found
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Fetched 221kB in 2s (99.8kB/s)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz)  404 Not Found


Still getting the same error

---

### Post by Mustard on 2006-04-12
Apparently the URL is down, so I would try browsing to the URL (remove the Packages.gz part of the link though) in your web browser and see if you can see it that way.  If its down in your web browser it could mean that the server is down, or that the URL is wrong (thats two possibilities anyway).

-edit-

I just browsed to the URL myself and I can't see anything in that repository under that directory.  Why this is so I have no idea.   It does add a possible option three for what the  problem might be though.  Options 3. The repository is set up incorrectly? :)

If you look in the 386 section of the repository you can see the Packages.gz file in there.  This is most definitely missing from the AMD64 section

---

