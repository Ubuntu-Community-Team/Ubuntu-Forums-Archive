---
title: "Evolution crash"
date: 2005-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nadir on 2005-01-26
Yesterday I reported on Bugzilla a [bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=5870)  with evolution-data-server on Hoary/AMD64 which was causing a Floating point Exception. stopping me from accessing my contacts and calendars. Today, with the 2.1.4-0ubuntu1 version of evolution, this exception also happens when starting Evolution itself.

Anybody else have this problem ?

Tristan

---

### Post by styrke on 2005-01-26
Yes, I have this as well.  No solution though.

---

### Post by Nadir on 2005-01-27
Compiled evo 2.1.4 and evo-data-server 1.1.4.1 by hand and it works !

---

### Post by lean on 2005-01-27
Got it too. Please hurry fix :)
I gonna have a few thousand mails, when I can read it again.

---

### Post by djtansey on 2005-01-27
i downgraded to the following packages (some i had to find on ubuntu mirrors that seemed to keep more packages than most)

libebook1.2-3 1.1.3-0ubuntu1
libcamel1.2-1 1.1.3-0ubuntu1
evolution 2.1.3.2-0ubuntu3
evolution-data-server 1.1.3-0ubuntu1

I think that's it. if there are any more problems with dependencies then downgrade the packages that they say are needed as well

---

### Post by Tobu on 2005-01-28
I've got it too, I've downgraded for now, but the solution of building by hand doesn't work for me.
@Nadir: what gcc are you using? I'm using 3.4, and the crash is before any library is used, so it could be a compiler issue.
Also, did you build with dpkg-buildpackage, or did you run configure by hand? Possibly there's something wrong with how the debian scripts call configure.

---

### Post by Nadir on 2005-01-28
[QUOTE=Tobu]I've got it too, I've downgraded for now, but the solution of building by hand doesn't work for me.
@Nadir: what gcc are you using? I'm using 3.4, and the crash is before any library is used, so it could be a compiler issue.
Also, did you build with dpkg-buildpackage, or did you run configure by hand? Possibly there's something wrong with how the debian scripts call configure.[/QUOTE]
 Hi Tobu,
I used gcc version 3.3.5 (Debian 1:3.3.5-6ubuntu1) and I built and installed by hand because I fear it is a problem with debian build scripts. Do the build daemons default to a different compiler ?

I looked at /proc/version and it says that the kernel is compiled with the same version of gcc, so I believe that the build daemons use that.

---

### Post by Tobu on 2005-01-28
Using gcc-3.3 and running configure by hand didn't work for me. :sigh:

---

### Post by arx-lupus on 2005-01-29
Anyone got an update on this one?

---

### Post by lean on 2005-02-02
You know what people say:
No news is good news.
Except in this case. There are no news, and it doesn't work.

Anobody know if there is a bugzilla entry for this?

---

### Post by Nadir on 2005-02-02
[QUOTE=lean]You know what people say:
No news is good news.
Except in this case. There are no news, and it doesn't work.

Anobody know if there is a bugzilla entry for this?[/QUOTE]
 Check the post that started this thread. Do you think I should assign the bug to someone ?

---

