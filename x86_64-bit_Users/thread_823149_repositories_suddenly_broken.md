---
title: "repositories suddenly broken"
date: 2008-06-08
forum: x86 64-bit Users
---

### Post by Levant on 2008-06-08
I just installed 8.04 amd64 the other day, and everything up until now was getting along great. I've had no problems with networking or with software updates and installations. Just today however it seems every last repository has fallen off the Earth. I attempted an apt-get update today and every last one returned a 404 not found. I piped the string of errors to a text file, which I've attached to the post. Perhaps someone can tell me how to re-enable those repositories?

The only modification I made to the /etc/apt/sources.list was to uncomment the backports repos. I doubt that is the source of the problem, because that didn't kill my ability to install software yesterday.

---

### Post by uberlube on 2008-06-09
+1, just installed hardy and its returning a 404 on every attempt to download from repos   :confused:

---

### Post by Bubba64 on 2008-06-09
The main server is working I just checked.

---

### Post by Levant on 2008-06-09
I seem to have fixed the problem (at least for now) by switching from the Canadian server to the main server. This seems to me as if the folks at Ubuntu are having issues with their Canadian server. Perhaps another Canadian Ubuntu user can verify?

---

### Post by ZabiGG on 2008-06-09
Same problem here with the Canadian server :(

---

### Post by editrix on 2008-06-09
> **Levant said:**
> I seem to have fixed the problem (at least for now) by switching from the Canadian server to the main server.

Nice to see fellow Canucks on this site, but not for this reason :-(

Can you tell me what you did to switch to the main server?

Never mind--I explored a few other "broken server" threads and found out.

---

### Post by sluger1138 on 2008-06-09
> **editrix said:**
> Nice to see fellow Canucks on this site, but not for this reason :-(

Can you tell me what you did to switch to the main server?

Never mind--I explored a few other "broken server" threads and found out.
Hello From Canada,
My repos have been down for 2 days, same as my friend, that lives in Hamilton also, uses the Canadian servers, tried the main repo, still get this error.
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz:) 404 Not Found  >>>> Changed to alternative repo below :

ttp://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz: 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz:) 404 Not Found
[http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz:) 404 Not Found

Good luck with the fix

From Canada

---

