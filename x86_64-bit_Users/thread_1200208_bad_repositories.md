---
title: "bad repositories"
date: 2009-06-29
forum: x86 64-bit Users
---

### Post by smallmouth sam on 2009-06-29
I am having a problem when updating I am getting a message

gusty repository x64 not available 

Amd 64 running HH

How do I fix?

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Some index files failed to download, they have been ignored

---

### Post by hansdown on 2009-06-29
Hi smallmouth sam.

The gutsy repositories are no longer available.

Have you considered trying a newer distro?

8.04 is solid. 8.10 and 9.04 are options also.

---

### Post by smallmouth sam on 2009-06-29
I am running 8.04 HH
/
That's what I don;t get

---

### Post by deanjm1963 on 2009-06-29
Hardy Heron is not Gusty Gibbon - you need to change your repositories to access "hardy"

---

### Post by hansdown on 2009-06-29
If you click system> administration> software sources> updates,

does it look sort of like this?

Did you do a distibution upgrade?

---

### Post by cariboo on 2009-06-30
You can always open /etc/apt/sources.list in a text editor, and use search & replace to replace gutsy with hardy. to do this press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

This will open as root the sources.list file and allow you to edit it.

---

