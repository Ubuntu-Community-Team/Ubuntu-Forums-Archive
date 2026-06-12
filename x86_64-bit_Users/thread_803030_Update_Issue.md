---
title: "Update Issue"
date: 2008-05-21
forum: x86 64-bit Users
---

### Post by wycito on 2008-05-21
Hey lads while attempting an upgrade it gave me this error:

[http://picasaweb.google.com/lestatt77/Stuff](http://picasaweb.google.com/lestatt77/Stuff)

Just wont let me update

Any help is appreciated

preconf packages...
dgkg: syntax error: unknows group 'mlocate'in statoverride file
E: Subprocess /usr/bin/dpkg returned an error code (2)
A package failed to install

Wycito

---

### Post by Sef on 2008-06-03
Someone on [Debian Help]("http://www.debianhelp.org/node/3037") has had a similar problem.

Partial From the Help:

> > dpkg: parse error, in file `/var/lib/dpkg/available' near line 2
> package `libkrb53':
> value for `status' field not allowed in this context

Personally I would go and explore the file mentioned and look for
corruption. It seems to imply line 2 so it should be near the
beginning. Perhaps there is a blank line or something near the
beginning.

Did you run out of disk space sometime recently?

There should be a /var/lib/dpkg/available-old file too (at least I have
one)

Partial Reply:

> Thanks, your suggestion basically did the trick, although I did end up
having to remove 3 lines from /var/lib/dpkg/available to get it to work.
It appears as though the file was corrupted.

Regarding your question about disk space, I have plenty, so it's
unlikely that was the cause of the corruption.

---

