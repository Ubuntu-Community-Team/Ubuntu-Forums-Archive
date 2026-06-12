---
title: "OpenSUSE 11.0 is snappier... why?"
date: 2008-09-04
forum: openSUSE and SUSE Linux Enterprise
---

### Post by cisforcojo on 2008-09-04
Hey all --
I was running OpenSUSE 11.0 with KDE4 and it was a LOT snappier than Hardy with GNOME. That being said, I'll never use another RPM-based distro again... From everything I've read, KDE4 is supposedly a lot more resource intensive than GNOME. However, everything ran much faster, wine opened almost immediately which never happens with Ubuntu... I'm wondering what would cause this? I definitely prefer Ubuntu and don't quite get where the difference lies. I'd considered rebuilding the kernel to be specific to my architecture (Pentium M) but I've also read that this is pretty ineffective on modern generic kernels. 

My system is a 1.7GHz laptop with 512MB RAM (1.5G as of tomorrow :)) and an ATI Mobility Radeon X600 (128MB) gfx card. 

I know this is very vague and posts like this come up all the time. 
I've also seen a lot of posts saying Ubuntu is faster than OpenSUSE for other people... 

Any ideas on how I could boost Ubuntu's performance? The tips for tweaking Ubuntu I've seen are all about 2 years out of date. Thanks for your support!

---

### Post by bodhi.zazen on 2008-09-04
OpenSUSE has come a long way since 10.2 ;)

10.3 and 11.0 are both a lot snappier, it is nice.

Speed and performance is subjective as you know. There are many things that go into performance from file system, to window manager, to applications, to compilation options, to bloatwere.

In terms of KDE and speed, do not confuse KDE with Kubuntu-desktop  ;) KDE can be light weight or bloated depending on how many additional apps you install on the top of it.

---

### Post by cisforcojo on 2008-09-04
Right, I know saying it's snappier is really subjective and I wish I could give concrete information/benchmarks but I can't. What would make apps like WINE load so much faster? I actually really like what KDE is doing with KDE4 and would like to support it but like I said, I'll be damned if I ever use RPMs again. I tried Gentoo and really like Portage but things just took too long. I don't have that much time to commit to getting things to work ;) I tried Sabayon and liked it but had a lot of problems with equo (equo and China don't play nice) and it's not recommended to use emerge in Sabayon over equo.  

Would you recommend recompiling the kernel or is it a waste of time (minimal performance gains)? Will this break the updater?  

I might start trying to compile most things manually and install with checkinstall.

When it all comes down to it, I've found no suitable substitute for Ubuntu's community, brainstorm website and innovation, etc. So! I'm making an effort to get Ubuntu's speed up to par. :) Btw, I wasn't confusing KDE with Kubuntu btw. I, personally, don't like Kubuntu. Always seems to be 6 mos. behind Ubuntu in terms of innovation (ex: PulseAudio)

---

### Post by RedDwarf on 2008-09-06
> **cisforcojo said:**
> From everything I've read, KDE4 is supposedly a lot more resource intensive than GNOME.
You have read any benchmark that uses numbers instead of "lots" for his measures? Or just messages from unknown users in forums like this?
There are good sources and not so good sources.

The numbers said something different about KDE3 vs Gnome -> [http://ktown.kde.org/~seli/memory/desktop_benchmark.html](http://ktown.kde.org/~seli/memory/desktop_benchmark.html)


> **cisforcojo said:**
> I'll never use another RPM-based distro again...
If your problems have nothing to do with some reported bugs* already being fixed from a new package resolution stack and you know for sure they are caused because of an intrinsic limitation of RPM (both the one from [http://rpm.org/](http://rpm.org/) and the one from [http://rpm5.org/](http://rpm5.org/)) that affects all distros and will never be fixed then your decision makes a lot of sense.
](*,)

About openSUSE being snappier... compare package patches and build options.


* [https://bugzilla.novell.com/show_bug.cgi?id=408675](https://bugzilla.novell.com/show_bug.cgi?id=408675)
[http://lists.opensuse.org/opensuse-softwaremgmt/2008-08/msg00012.html](http://lists.opensuse.org/opensuse-softwaremgmt/2008-08/msg00012.html)

---

