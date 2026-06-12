---
title: "Unable to launch StepMania on 64 bit Jaunty"
date: 2009-04-25
forum: x86 64-bit Users
---

### Post by Zeplyx on 2009-04-25
Since I recently bought 4gigs of new ram I decided to install 64bit Ubuntu when jaunty got released however when I try to ./stepmania I get "bash: ./stepmania: No such file or directory", this worked perfectly fine with 32bit jaunty though.
is there some other command to launch programs in 64bit?

---

### Post by dcstar on 2009-04-26
> **Zeplyx said:**
> Since I recently bought 4gigs of new ram I decided to install 64bit Ubuntu when jaunty got released however when I try to ./stepmania I get "bash: ./stepmania: No such file or directory", this worked perfectly fine with 32bit jaunty though.
is there some other command to launch programs in 64bit?

32-bit binaries will not run in 64-bit systems. If you do a file check you will probably see that the binary you are trying to run is 32-bit:

```
file stepmania
```

---

### Post by Zeplyx on 2009-04-26
you're right, the file command gave me this output "ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped". 
so unless there is some way to make it run on a 64 bit OS ill just go back to my 32bit Intrepid and do a distro upgrade.

---

### Post by NESFreak on 2009-05-21
> **Zeplyx said:**
> you're right, the file command gave me this output "ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped". 
so unless there is some way to make it run on a 64 bit OS ill just go back to my 32bit Intrepid and do a distro upgrade.

you could compile from source yourself, or get a deb here [http://www.getdeb.net/app/StepMania](http://www.getdeb.net/app/StepMania)

--edit--
the getdeb version is outdated.
Try downloading the svn 32 bit linux build here:
[http://sourceforge.net/project/showfiles.php?group_id=37892&package_id=30318&release_id=565571](http://sourceforge.net/project/showfiles.php?group_id=37892&package_id=30318&release_id=565571)

read this:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

run getlibs ./stepmania
run ./stepmania
enjoy

---

