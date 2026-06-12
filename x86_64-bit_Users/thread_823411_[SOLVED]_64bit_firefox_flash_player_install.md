---
title: "[SOLVED] 64bit firefox flash player install"
date: 2008-06-09
forum: x86 64-bit Users
---

### Post by michael_mallett on 2008-06-09
Hi there,
I am new to ubuntu (although having just finished my cmp degree!) and I am having trouble with some package dependencies.
I followed the guide ( [http://www.linuxheadquarters.com/howto/64-bit/flash64.shtml](http://www.linuxheadquarters.com/howto/64-bit/flash64.shtml) ) located there up until point 2. 

"Install the RPMs as the root user with the rpm -Uvh nspluginwrapper-0.9.91.4-1.x86_64.rpm nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm command. You will see the following messages as it finds compatible 32-bit plugins: "

(all went fine up to this point) but the given expected output was not the same, instead I got the following:

"
mjm@mjm-ubuntu:~/Desktop$ sudo rpm -Uvh nspluginwrapper-0.9.91.4-1.x86_64.rpm nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm

error: Failed dependencies:
	/bin/sh is needed by nspluginwrapper-0.9.91.4-1.x86_64
	bash is needed by nspluginwrapper-0.9.91.4-1.x86_64
	libc.so.6()(64bit) is needed by nspluginwrapper-0.9.91.4-1.x86_64
	libc.so.6(GLIBC_2.2.5)(64bit) is needed by nspluginwrapper-0.9.91.4-1.x86_64
	libdl.so.2()(64bit) is needed by nspluginwrapper-0.9.91.4-1.x86_64
	libdl.so.2(GLIBC_2.2.5)(64bit) is needed by nspluginwrapper-0.9.91.4-1.x86_64
	libglib-2.0.so.0()(64bit) is needed by nspluginwrapper-0.9.91.4-1.x86_64
	libpthread.so.0()(64bit) is needed by nspluginwrapper-0.9.91.4-1.x86_64
	libpthread.so.0(GLIBC_2.2.5)(64bit) is needed by nspluginwrapper-0.9.91.4-1.x86_64
	libX11.so.6()(64bit) is needed by nspluginwrapper-0.9.91.4-1.x86_64
	libXt.so.6()(64bit) is needed by nspluginwrapper-0.9.91.4-1.x86_64
	/usr/bin/linux32 is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	bash is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libc.so.6 is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libc.so.6(GLIBC_2.0) is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libc.so.6(GLIBC_2.1) is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libc.so.6(GLIBC_2.1.3) is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libdl.so.2 is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libdl.so.2(GLIBC_2.0) is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libdl.so.2(GLIBC_2.1) is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libgcc_s.so.1 is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libgcc_s.so.1(GCC_3.0) is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libgcc_s.so.1(GCC_3.3) is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libgdk-x11-2.0.so.0 is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libglib-2.0.so.0 is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libgobject-2.0.so.0 is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libgtk-x11-2.0.so.0 is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libpthread.so.0 is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libpthread.so.0(GLIBC_2.0) is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libpthread.so.0(GLIBC_2.1) is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libX11.so.6 is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
	libXt.so.6 is needed by nspluginwrapper-i386-0.9.91.4-1.x86_64
 "
(sorry for length of output)

I understand the concepts of the dependency errors but cannot find the relevant package to rectify the problem.
Any help would be much appreciated. 

Note: I have read elsewhere that the /bin/sh error can be caused by an sh entry missing from /etc/shells but that folder does not exist on my system!

Many thanks in advance,
Michael.

---

### Post by Sef on 2008-06-09
Ubuntu, being based on Debian, uses .deb, not .rpm.  To install flash on 64-bit Ubuntu, read [Kliz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490").

---

### Post by jespdj on 2008-06-09
You're making it much more difficult than necessary.

You should preferrably install software via Ubuntu's package management system, Synaptic. The package for Adobe Flash is called **flashplugin-nonfree**. Find it and install it with Synaptic, or in a terminal window with the following command:
```
sudo apt-get install flashplugin-nonfree
```
If you are using 64-bit Ubuntu 8.04, this will install Adobe Flash and the necessary surrounding stuff to make it work in 64-bit Firefox.

---

### Post by michael_mallett on 2008-06-09
Many thanks both of you, flash is working now (at least on most websites).
What sort of plugin do I need to view videos online i.e. googlevideo or youtube?

---

### Post by Sef on 2008-06-09
> What sort of plugin do I need to view videos online i.e. googlevideo or youtube?

If you need java, then download OpenJDK.  Click on my 'Java On 64-Bit Systems' for more information.

```
sudo apt-get install OpenJDK
```

or install from Applications > Add/Remove.

---

### Post by jespdj on 2008-06-09
> **michael_mallett said:**
> Many thanks both of you, flash is working now (at least on most websites).
What sort of plugin do I need to view videos online i.e. googlevideo or youtube?
These should just work with Adobe Flash (they do work on my 64-bit Ubuntu 8.04). You don't need Java for those websites.

---

### Post by michael_mallett on 2008-06-10
> **jespdj said:**
> These should just work with Adobe Flash (they do work on my 64-bit Ubuntu 8.04). You don't need Java for those websites.

That's what I thought, but no videos work. I get the thumbnail when searching, but once clicked - the area where the display appears is plain white.

(This is why I thought flash wasn't installed properly, but having tested on Adobe Flash Test page it appears it is)

Any ideas?

Thanks.

---

