---
title: "[SOLVED] seti optimized app install"
date: 2008-08-25
forum: x86 64-bit Users
---

### Post by csogilvie on 2008-08-25
Hello all, please accept my apologies for this rudimentary question as I'm very new to Ubuntu Linux (new to all linux in general)

I've built up a machine for crunching seti work units, and I have been scratching my head about trying to install an optimized app.  It took me a while to find out where it goes, but I don't know how to get the permissions to put the optimized app in the right folder.

It was installed using the "sudo apt-get install boinc-manger boinc-client"

I then manually connected to the seti project.

I'm running x86_64 8.04 Ubuntu (downloaded and installed today from ubuntu homepage)

Any help would be greatly appreciated!

---

### Post by LateNiteTV on 2008-08-25
you probably need to set the proper permissions with chmod.
read the chmod manpage.
```
man chmod
```

---

### Post by csogilvie on 2008-08-25
thanks for the suggestion...  I made a mess of it with chmod, then searched more and found that it would be easier for me (terribly visually oriented... neeeeed gui!) to use "gksudo nautilus" which I was then able to navigate to where I needed to go to install the files.

My machine is now happily crunching.

---

