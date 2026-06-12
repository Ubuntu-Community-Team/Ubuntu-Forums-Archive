---
title: "Problems compiling Tapioca (stuck at libjingle)."
date: 2006-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by phibxr on 2006-03-29
When I try compiling libjingle I get the text pasted in this post. What could be the problem?

Has anyone even been able to compile Tapioca and/or libjingle on a PPC, or is it using some low level x86 code?

This is frustrating, when I finally get my USB headset working like a charm, Tapioca won't compile. Is there any other way to access the GTalk voice functions yet?

```
phibxr@ubuntu:~/dev/libjingle$ autoreconf -i -f -v
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
autoreconf: `aclocal.m4' is created
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy --force
autoreconf: `aclocal.m4' is unchanged
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy
automake: configure.ac: installing `./install-sh'
automake: configure.ac: installing `./mkinstalldirs'
automake: configure.ac: installing `./missing'
talk/base/Makefile.am:1: bad macro name `libjinglebase_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/base/Makefile.am:28: bad macro name `libjinglebase_@LIBJINGLE_MAJORMINOR@includedir'
talk/base/Makefile.am:29: bad macro name `libjinglebase_@LIBJINGLE_MAJORMINOR@include_HEADERS'
talk/base/Makefile.am:73: bad macro name `libjinglebase_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/base/Makefile.am:1: invalid unused variable name: `libjinglebase_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/base/Makefile.am:73: invalid unused variable name: `libjinglebase_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/third_party/Makefile.am:5: else without if
talk/third_party/Makefile.am:3: SUBDIRS defined both conditionally and unconditionally
talk/third_party/Makefile.am:7: endif without if
talk/p2p/base/Makefile.am:1: bad macro name `libjinglep2pbase_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/p2p/base/Makefile.am:16: bad macro name `libjinglep2pbase_@LIBJINGLE_MAJORMINOR@includedir'
talk/p2p/base/Makefile.am:17: bad macro name `libjinglep2pbase_@LIBJINGLE_MAJORMINOR@include_HEADERS'
talk/p2p/base/Makefile.am:41: bad macro name `libjinglep2pbase_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/p2p/base/Makefile.am:41: invalid unused variable name: `libjinglep2pbase_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/p2p/base/Makefile.am:1: invalid unused variable name: `libjinglep2pbase_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/p2p/client/Makefile.am:1: bad macro name `libjinglep2pclient_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/p2p/client/Makefile.am:7: bad macro name `libjinglep2pclient_@LIBJINGLE_MAJORMINOR@includedir'
talk/p2p/client/Makefile.am:8: bad macro name `libjinglep2pclient_@LIBJINGLE_MAJORMINOR@include_HEADERS'
talk/p2p/client/Makefile.am:18: bad macro name `libjinglep2pclient_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/p2p/client/Makefile.am:1: invalid unused variable name: `libjinglep2pclient_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/p2p/client/Makefile.am:18: invalid unused variable name: `libjinglep2pclient_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/session/tunnel/Makefile.am:1: bad macro name `libjinglesessiontunnel_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/session/tunnel/Makefile.am:2: bad macro name `libjinglesessiontunnel_@LIBJINGLE_MAJORMINOR@includedir'
talk/session/tunnel/Makefile.am:3: bad macro name `libjinglesessiontunnel_@LIBJINGLE_MAJORMINOR@include_HEADERS'
talk/session/tunnel/Makefile.am:4: bad macro name `libjinglesessiontunnel_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/session/tunnel/Makefile.am:1: invalid unused variable name: `libjinglesessiontunnel_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/session/tunnel/Makefile.am:4: invalid unused variable name: `libjinglesessiontunnel_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/session/phone/Makefile.am:3: bad macro name `nodist_libjinglesessionphone_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/session/phone/Makefile.am:6: bad macro name `dist_libjinglesessionphone_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/session/phone/Makefile.am:10: bad macro name `libjinglesessionphone_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/session/phone/Makefile.am:17: bad macro name `libjinglesessionphone_@LIBJINGLE_MAJORMINOR@includedir'
talk/session/phone/Makefile.am:18: bad macro name `libjinglesessionphone_@LIBJINGLE_MAJORMINOR@include_HEADERS'
talk/session/phone/Makefile.am:28: bad macro name `libjinglesessionphone_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/session/phone/Makefile.am:6: invalid unused variable name: `dist_libjinglesessionphone_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/session/phone/Makefile.am:10: invalid unused variable name: `libjinglesessionphone_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/session/phone/Makefile.am:28: invalid unused variable name: `libjinglesessionphone_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/session/phone/Makefile.am:3: invalid unused variable name: `nodist_libjinglesessionphone_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/xmllite/Makefile.am:1: bad macro name `libjinglexmllite_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/xmllite/Makefile.am:9: bad macro name `libjinglexmllite_@LIBJINGLE_MAJORMINOR@includedir'
talk/xmllite/Makefile.am:10: bad macro name `libjinglexmllite_@LIBJINGLE_MAJORMINOR@include_HEADERS'
talk/xmllite/Makefile.am:19: bad macro name `libjinglexmllite_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/xmllite/Makefile.am:19: invalid unused variable name: `libjinglexmllite_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/xmllite/Makefile.am:1: invalid unused variable name: `libjinglexmllite_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/xmpp/Makefile.am:1: bad macro name `libjinglexmpp_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/xmpp/Makefile.am:12: bad macro name `libjinglexmpp_@LIBJINGLE_MAJORMINOR@includedir'
talk/xmpp/Makefile.am:13: bad macro name `libjinglexmpp_@LIBJINGLE_MAJORMINOR@include_HEADERS'
talk/xmpp/Makefile.am:31: bad macro name `libjinglexmpp_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
talk/xmpp/Makefile.am:1: invalid unused variable name: `libjinglexmpp_@LIBJINGLE_MAJORMINOR@_la_SOURCES'
talk/xmpp/Makefile.am:31: invalid unused variable name: `libjinglexmpp_@LIBJINGLE_MAJORMINOR@_la_LIBADD'
autoreconf: automake failed with exit status: 1
```

---

### Post by chele on 2006-05-02
There are now Tapioca binary's available for Breezy with support for gtalk's Voice chat.  [https://wiki.ubuntu.com/Tapioca]("https://wiki.ubuntu.com/Tapioca") They say that it also should be running on Dapper any day now.

---

### Post by phibxr on 2006-05-07
Unfortunately, there are only binaries for i386, and those won't run on PPC.

---

### Post by medication on 2006-05-18
[QUOTE=phibxr]Unfortunately, there are only binaries for i386, and those won't run on PPC.[/QUOTE]

No love for the AMD64 platform either

---

### Post by ssam on 2006-05-18
maybe try with some different versions of automake, ubuntu has 1.4 -> 1.9

---

### Post by jbrnd on 2006-05-20
[QUOTE=phibxr]When I try compiling libjingle I get the text pasted in this post. What could be the problem?

Has anyone even been able to compile Tapioca and/or libjingle on a PPC, or is it using some low level x86 code?
[/QUOTE]

I just compiled tapioca on Dapper/AMD64, starting with "autoreconf -i -f -v", so it's possible. Your problem is definitely related to the autotools - one thing I'd do is to make sure that automake1.9 is installed and that /etc/alternatives/automake points to automake-1.9 .

The whole compilation process is pretty daunting, though. I had to edit a few makefiles for everything to work, but apparently that's because I'm on amd64. Not sure if PPC would have the same problems.

---

