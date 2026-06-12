---
title: "64bit Searchmonkey crash"
date: 2008-08-19
forum: x86 64-bit Users
---

### Post by PeterBBB on 2008-08-19
I have found the Searchmonkey crash (on trying to select from the results frame) 100% reproducible with all recent versions of the package. One click on the results, and crash to desktop every time.

[http://bugs.launchpad.net/ubuntu/+source/searchmonkey/+bug/178701]("http://bugs.launchpad.net/ubuntu/+source/searchmonkey/+bug/178701")

A selection of 64bit Searchmonkey 'results'....

```
Aug 19 00:17:27 peter-desktop kernel: [ 3836.158590] searchmonkey[8930] trap stack segment rip:424a22 rsp:7fff2311a580 error:0
Aug 19 00:18:30 peter-desktop kernel: [ 3870.280999] searchmonkey[8953] trap stack segment rip:424a22 rsp:7fff99314770 error:0
Aug 19 00:31:41 peter-desktop kernel: [ 4285.518867] searchmonkey[9580]: segfault at 361 rip 422ad8 rsp 7fff6cbe1ba0 error 4
Aug 19 00:47:20 peter-desktop kernel: [ 4797.548096] searchmonkey[10221] general protection rip:7f6b0824f060 rsp:7fff143d6698 error:0
Aug 19 00:48:13 peter-desktop kernel: [ 4832.491035] gvfs-fuse-daemo[8869] general protection rip:7fda25cee423 rsp:7fff2f919030 error:0

```

I had some suspicions after compiling some unrelated C source in 64bit and getting buckets of 'incompatible pointer type' and 'cast .... of different size' warnings. Downloaded a 32bit package and installed it using

 ```
sudo dpkg -i --force-all searchmonkey_0.8.1-6_i386.deb
```

and it works perfectly!  This is the first real issue I have found with 64bit though. Everything else seems solid enough.


Pete.

---

### Post by Jhongy on 2009-05-25
Thanks for this, I didn't think of forcing the 32-bit version -- I've just been putting up with the crashes :o

SearchMonkey is great. I'm using RapidSVN + gedit + meld + SearchMonkey, and they all work together beautifully. SearchMonkey crashing was the last piece of the puzzle.

---

