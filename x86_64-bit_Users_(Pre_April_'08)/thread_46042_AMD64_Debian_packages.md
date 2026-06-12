---
title: "AMD64 Debian packages"
date: 2005-07-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by ehsan on 2005-07-02
Hi all,

Lately Debian Sarge was released, and now it has a nearly complete unofficial AMD64 port.

I'd like to know if installing Debian AMD64 packages which are not inside the main Ubuntu repositories is supported or not.

I already have AMD64 Sarge DVD's, but I prefer to use Ubuntu because of its more frequent release cycles.  I just need to know whether I can use Debian packages in my Ubuntu system, since downloading lots of software on a 33.6kbps Internet connection is not really an option for me.

Thanks in advance,
Ehsan

---

### Post by rsw on 2005-07-03
[QUOTE=ehsan]I just need to know whether I can use Debian packages in my Ubuntu system, since downloading lots of software on a 33.6kbps Internet connection is not really an option for me.[/QUOTE]

you can install them, they should work.

whether this will break anything or lead to crazy dependency problems, dunno. give it a try and see how it goes. I've installed some debian packages before in ubuntu-amd64, no huge problems.

---

### Post by ehsan on 2005-07-03
Thanks a lot for your reply.

One more question: will Debian 32-bit packages also work or they need special handling?  Debian uses a special 32-bit chroot environment to run 32-bit applications, but I'm not sure how similarly Ubuntu handles that stuff.

Thanks!
Ehsan

---

### Post by dewey on 2005-07-03
32 bit apps need to be run in a chroot, just like debian.

Ubuntu is based off debian, but is straying very far from it's roots, package-wise.  Officially, you're not supposed to install any packages not contained under official ubuntu repositories.  The repositories listed in [www.ubuntuguide.org](www.ubuntuguide.org) should contain everything you need, and if not, you can request it on the backports forum.

I don't recommend installing a large amount of debian packages, but installing limited amounts where Ubuntu doesn't provide them, hasn't harmed my installation.  (I've only tried the Marillat debian repository.)

---

### Post by ehsan on 2005-07-03
My main problem is the lack of ability to download large amounts of packages over my dial-up connection, and the reason I need to install Debian packages is just this.

Also, as I understand it, Ubuntu does not provide DVD ISO images containing all of its software repositories (including main, universe, multiverse, and restricted.)  The nearest thing is the DVD image downloadable from BitTorrent, which is again not an option for me (I could manage to download a DVD ISO image from work but BitTorrent is prohibited by the company firewalls.)

Is there any hope left for me?  Or should I cross my fingers and start installing Debian packages?

Thanks!

---

