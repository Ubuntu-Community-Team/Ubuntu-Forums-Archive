---
title: "f@h cant download work with 7.10 64bit"
date: 2007-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Henrythe9th on 2007-11-14
hello, I.ve installed gusty 7.10 on a server board and cant get it to down load F@H work units, I can ping the server ok and think its something to do with my netgear routor.. here's the log file 
01:07:12] - Ask before connecting: No
[01:07:12] - User name: henrythe9th (Team 37766)
[01:07:12] - User ID: 2579D6730F544A33
[01:07:12] - Machine ID: 1
[01:07:12] 
[01:07:12] Work directory not found. Creating...
[01:07:12] Could not open work queue, generating new queue...
[01:07:12] - Preparing to get new work unit...
[01:07:12] + Attempting to get work packet
[01:07:12] - Will indicate memory of 3025 MB
[01:07:12] - Detect CPU. Vendor: AuthenticAMD, Family: 15, Model: 5, Stepping: 10
[01:07:12] - Connecting to assignment server
[01:07:12] Connecting to [http://assign.stanford.edu:8080/](http://assign.stanford.edu:8080/)
[01:07:12] - Autosending finished units...
[01:07:12] Trying to send all finished work units
[01:07:12] + No unsent completed units remaining.
[01:07:12] - Autosend completed
[01:07:13] Posted data.
[01:07:13] Initial: 40AB; - Successful: assigned to (171.64.65.56).
[01:07:13] + News From Folding@Home: Welcome to Folding@Home
[01:07:13] Loaded queue successfully.
[01:07:13] Connecting to [http://171.64.65.56:8080/](http://171.64.65.56:8080/)
[01:07:17] Posted data.
[01:07:17] Initial: 0000; - Receiving payload (expected size: 3151221)
[01:08:18] - Downloaded at ~50 kB/s
[01:08:18] - Averaged speed for that direction ~50 kB/s
[01:08:18] + Received work.
[01:08:18] + Closed connections
[01:08:18] 
[01:08:18] + Processing work unit
[01:08:18] Core required: FahCore_a1.exe
[01:08:18] Core not found.
[01:08:18] - Core is not present or corrupted.
[01:08:18] - Attempting to download new core...
[01:08:18] + Downloading new core: FahCore_a1.exe
[01:08:18] Downloading core (/~pande/Linux/x86//Core_a1.fah from [www.stanford.edu](www.stanford.edu))
[01:08:18] - Error: HTTP GET returned error code 0
[01:08:18] + Error: Could not download core
[01:08:18] + Core download error (#2), waiting before retry...

I can surf the web ok can't see any other problems other than gettting to stanfords servers..
Ideas where to start ??
Thanks for the time
Henry

---

### Post by chewearn on 2007-11-23
Your message is a week old, not sure if you have solved it?

But looking at your fah log; I faced the same problem as you did.  Basically, it is not that you cannot download the work unit, but rather, you cannot download the core file (FahCore_a1.exe, in your case).

Fyi, this problem is not related to 64bit ubuntu.  I ran FAH in 32bit, and faced the same issue: the core file always failed to download automatically.

I'm not sure about the cause, but the workaround is to download the core manually.  Here is the link to help you out:
[http://fahwiki.net/index.php/Downloading_FAH_Core_files_manually](http://fahwiki.net/index.php/Downloading_FAH_Core_files_manually)

---

