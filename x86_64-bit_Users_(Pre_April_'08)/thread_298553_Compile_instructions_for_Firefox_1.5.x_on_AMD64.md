---
title: "Compile instructions for Firefox 1.5.x on AMD64"
date: 2006-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by cogitordi on 2006-11-12
I am using 6.10 for AMD64. I do not like the performance of Firefox 2.0 and some extensions do not work. I decided to build Firefox 1.5.8. Here are the steps

Collect the source tarball from ftp.mozilla.org:
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases)

Expand the tarball. Add a file named ".mozconfig" in the root directory of the resulting structure on disk. Use these lines for the content of the file:

. $topsrcdir/browser/config/mozconfig
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/ff-opt-static
ac_add_options --enable-optimize
ac_add_options --disable-debug
ac_add_options --disable-tests
mk_add_options MOZ_CO_PROJECT=browser
ac_cv_visibility_pragma=no

The option "--enable-static" appears to be broken on this platform so I do not use it.

Build Firefox with the command:
$ make -f client.mk build

Create a tarball with the command:
 make -C ff-opt-static/browser/installer/

This creates a tarball in the following location:

ff-opt-static/dist/firefox-1.5.0.8.en-US.linux-x86_64.tar.gz

Expand the tarball somewhere and double-click the "firefox" file to run the application.

---

### Post by kaminix on 2006-11-29
I found this thread via the search engine, this was the only one I found about compiling Firefox, that's why I used it.

Anyway, I realise that you might not be able to help me, but I thought I'd ask and try.

I'm on a Pentium M processor, and followed this small guide all the way to:
make -C ff-opt-static/browser/installer/
When I type this I get:
kaminix@kaminix-laptop:~/mozilla$ make -C ff-opt-static/browser/installer/
make: Entering directory `/home/kaminix/mozilla/ff-opt-static/browser/installer'
Makefile:69: *** you need a "--enable-static --disable-shared" build to create an installer.  Stop.
make: Leaving directory `/home/kaminix/mozilla/ff-opt-static/browser/installer'

Any idea how to solve this, even though it's on the wrong platform?

EDIT:
I'm compiling it because SCIM doesn't work with the one I got from Mozilla's homepage.

---

### Post by cogitordi on 2006-12-01
The Pentium M is a 32-bit CPU, yes? If so, use a regular .mozconfig.
Try adding **--enable-static --disable-shared** to the .mozconfig file.

---

### Post by kaminix on 2006-12-02
> **cogitordi said:**
> The Pentium M is a 32-bit CPU, yes? If so, use a regular .mozconfig.
Try adding **--enable-static --disable-shared** to the .mozconfig file.
Yes, it is. :)
I'll try that, I'll get back if I get any problems. Thank you. :)

---

