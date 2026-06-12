---
title: "apt-get update doesn't work,  Could not open lock file... unable to lock list dirctry"
date: 2008-05-13
forum: x86 64-bit Users
---

### Post by Tsukasah on 2008-05-13
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

The terminal brings that up if I type in apt-get update. I'm trying to get a few programs to work in WINE, on Gutsy. 

and for the programs i try to install:

fixme:ntdll:NtLockFile I/O completion on lock not implemented yet

the terminal brings that up. Any help will do. Also, if I simply right click on the setup file and click oepn with WINE, nothing happens

---

### Post by flaggh on 2008-05-13
Sounds like you have a couple of different problems going on here.  

To solve the medibuntu GPG key problem, in the terminal type:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Sounds like you are not preceding apt-get with sudo or running it as root?  Type this into the terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

