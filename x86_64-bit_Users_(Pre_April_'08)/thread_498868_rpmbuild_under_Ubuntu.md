---
title: "rpmbuild under Ubuntu"
date: 2007-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by daniel_summers on 2007-07-11
Back when I ran White Box Enterprise Linux (a Red Hat EL rebuild), I maintained x86_64 versions of xine that people could download.  I now have Ubuntu Feisty Fawn AMD64 loaded on my laptop.

Under WBEL, I would download the xine source rpm, then enter "rpmbuild -ta [source tarball]".  This created a main library rpm and a development rpm.  I would also build xine-ui, the default user interface.  People could then download the two primary (and the devel, if they thought they needed it), and I know that it worked on other RHEL-based distributions.

What would I need to do to set up a build environment to allow me to continue to provide this service?  Would a chroot environment with -EL libraries be necessary?  Could I install rpmbuild and do the same thing from Ubuntu?

Thanks...

---

### Post by jespdj on 2007-07-12
There's a program named [alien](http://linux.die.net/man/1/alien) that can convert between different packaging formats; it can also create rpm's. (You might need to install it: sudo apt-get install alien).

---

### Post by daniel_summers on 2007-07-21
Well, the answer to this was pretty easy (once I exhausted all the other hard things that didn't work).  :)  I typed "rpmbuild" in a terminal, and it came back and said something "rpmbuild is not installed - it's part of the rpm package."

```
sudo apt-get install rpm
```voila!  rpmbuild is there!

(Now, the source tarball is missing a spec file - but that's not an Ubuntu problem...)

---

