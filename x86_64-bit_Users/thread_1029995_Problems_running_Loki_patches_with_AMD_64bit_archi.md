---
title: "Problems running Loki patches with AMD 64bit architecture"
date: 2009-01-04
forum: x86 64-bit Users
---

### Post by fuzzykitty on 2009-01-04
I tried posting this to the Games forum but to no avail.  I suspect this is more of a technical problem with running 32bit apps on a 64bit system.  If not please direct me to the appropriate forum.  My problem description is below:

Based upon a number of forum posts some people have had success with the following:

root@K4:/usr/local/games/Heroes3# export _POSIX2_VERSION=199209

I should add that the loki patch is residing in the program directory, although whether it is or is in my home directory it does not seem to matter. I get the following when trying three different commands:

root@K4:/usr/local/games/Heroes3# linux32 sh heroes3-1.3.1-x86.run
Verifying archive integrity...OK
Uncompressing Heroes of Might & Magic III for Linux: patch 1.3.1trap: 126: cd /tmp; /bin/rm -rf $tmpdir; exit $res: bad trap

root@K4:/usr/local/games/Heroes3# linux32 ./heroes3-1.3.1-x86.run
Verifying archive integrity...OK
Uncompressing Heroes of Might & Magic III for Linux: patch 1.3.1trap: 126: cd /tmp; /bin/rm -rf $tmpdir; exit $res: bad trap

root@K4:/usr/local/games/Heroes3# linux32 ksh heroes3-1.3.1-x86.run
Verifying archive integrity...OK
Uncompressing Heroes of Might & Magic III for Linux: patch 1.3.1heroes3-1.3.1-x86.run[126]: trap: condition(s) required

Unfortunately I have not been able to find any forum posts with this specific problem nor any related posts with how to fix it (being non root doesn't help either since "export _POSIX2_VERSION=199209" wont work) I've also changed the permissions of the patch to be executable and the Heroes program directory permissions to 0777.

My system is an Intrepid 64bit upgrade of Hardy. Running AMD X2 5600 and GForce 8600GT. Any help would be appreciated. Thanks

Fuzzy

---

