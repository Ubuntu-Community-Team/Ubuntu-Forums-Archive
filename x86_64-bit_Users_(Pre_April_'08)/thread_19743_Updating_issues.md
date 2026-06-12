---
title: "Updating issues"
date: 2005-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Boomstickz on 2005-03-13
Hey, i'm pretty new to Ubuntu on the AMD 64 side, I never had this problem that i'm having now with apt, but heres whats going on. Basically, I am on a fresh install, got it up and running very quickly, thanks Ubuntu ;), but I went to go edit my sources.list to be able to download updates off the net, so I did it the usual way:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

uncommented those, since they are the mains, if I just have those uncommented, I do not get any errors. However, when I want to get into the universe, thats when things get a bit wierd...

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

So I uncomment them to get access to the applications, and other cool crap I can play with, and then I go to do a apt-get update, and heres what I get:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages [2051kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources [862kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
  404 Not Found
Fetched 2914kB in 9s (322kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz)  404 Not Found
Reading Package Lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Maybe i'm insane, but if i'm doing something wrong or if someone knows a fix, I would appreciate it ;)

---

### Post by Boomstickz on 2005-03-13
Hmm i'm all fixed up now, no worries, I just updated off the main, guess there must had been a bug or something that caused this previously.

---

### Post by c_dog on 2005-03-14
Hoary hasn't even been rleased yet, so the 'hoary-updates' repos probably won't work to well . Comment them out for now and you should get fewer errors.

---

