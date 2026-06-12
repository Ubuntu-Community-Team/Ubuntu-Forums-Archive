---
title: "[SOLVED] RPM Package installation problems"
date: 2008-02-08
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Griff on 2008-02-08
Like the title says I'm having problems installing some of the rpm packages from the official opensuse repositories.  I checked to see if I have rpm support and I do.  In fact some rpm packages from the repos seem to install fine, but the ones I desperately need (the mysql packages and yum) fail with an rpm error.  Any idea what's going on?

Thanks,
Griff

---

### Post by Antman on 2008-02-08
> **Griff said:**
> Like the title says I'm having problems installing some of the rpm packages from the official opensuse repositories.  I checked to see if I have rpm support and I do.  In fact some rpm packages from the repos seem to install fine, but the ones I desperately need (the mysql packages and yum) fail with an rpm error.  Any idea what's going on?

Thanks,
Griff

What kind of error are you getting when you try to install yum?
What method are you using to install - Yast, Zypper ??

---

### Post by Griff on 2008-02-08
I'm using yast.  I'll try to install it again when I get back to the pc (in about 10 min) and report back.

---

### Post by Griff on 2008-02-08
Here's the error message I get under details:
Subprocess failed. Error: RPM failed:
---
-?-

Thanks,
Griff

---

### Post by Antman on 2008-02-08
hmm... YUM and Mysql installed fine for me using Zypper.
Here are my repos:
```

openSUSE-10.3-Updates
http://download.opensuse.org/distribution/10.3/repo/non-oss/
http://download.opensuse.org/repositories/openSUSE:10.3/standard/
http://ftp.skynet.be/pub/packman/suse/10.3/

```

As SU try running:

```
zypper ref
```
then
```
zypper install yum mysql
```

---

### Post by Incense on 2008-02-08
Acording to this page

[https://bugzilla.novell.com/show_bug.cgi?id=236812]("https://bugzilla.novell.com/show_bug.cgi?id=236812")

it a memory error. You can try closing come programs, rebooting, whatever to clear out some memory, and  trying again.
You can also just give it a manual try by downloading the RPM, and running (as SU)

```
rpm -Uvh rpmname.rpm
``` 

see how that goes. If you still have a problem, it wouldn't hurt to do a bit of house cleaning with.

```
rpmdb --rebuilddb
```

That will take a couple minutes, and try to install again. Good luck.

---

### Post by Griff on 2008-02-18
Thanks, it was a memory problem and a reboot fixed it.  This pc is headless and I connect to it remotely so I hardly ever reboot it.  Before the reboot I had about 2MB of memory free. :)

---

