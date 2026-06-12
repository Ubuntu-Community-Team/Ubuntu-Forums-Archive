---
title: "Folding@Home"
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by tardis on 2007-06-06
I get this error when I try running Folding at Home 64bit version.

[20:33:50] Verifying core Core_a1.fah...
[20:33:50] Signature is VALID
[20:33:50] 
[20:33:50] Trying to unzip core FahCore_a1.exe
[20:33:51] Decompressed FahCore_a1.exe (3624144 bytes) successfully
[20:33:51] + Core successfully engaged
[20:33:51] Deleting current work unit & continuing...
sh: ./mpiexec: not found
[20:33:51] - Preparing to get new work unit...
[20:33:51] + Attempting to get work packet
[20:33:51] - Connecting to assignment server
[20:33:51] - Successful: assigned to (171.64.65.56).
[20:33:51] + News From Folding@Home: Welcome to Folding@Home
[20:33:51] Loaded queue successfully.
[20:33:52] - Error: Attempt #1  to get work failed, and no other work to do.
             Waiting before retry.
Why is it saying ./mpiexec: not found when it is in the directory?

 client.cfg  FahCore_a1.exe  FAH_SMP_Linux.tgz     mpiexec.exe     queue.dat
fah5.exe    FAHlog.txt      machinedependent.dat  MyFolding.html  work

Any help?

Thanks...:p

I have no problem running the 32bit version....

---

### Post by bapoumba on 2007-06-08
Thread moved to the 64-bit forum.

---

### Post by Cappy on 2007-06-08
I am using [http://www.getdeb.net/release.php?id=906](http://www.getdeb.net/release.php?id=906)
(BOINC, 64-bit)

Copying it may work:
```
cp mpiexec.exe mpiexec
```

---

### Post by jpkotta on 2007-07-02
[https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

The wiki contains two methods to install the client, at least one of which (fah_install) works with x86-64 (finstall may work too, but I'm not sure).

You need ia32-libs to make it work.

---

