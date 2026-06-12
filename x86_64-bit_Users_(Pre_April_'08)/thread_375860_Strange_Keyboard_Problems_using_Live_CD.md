---
title: "Strange Keyboard Problems using Live CD"
date: 2007-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by floba on 2007-03-04
Hi,

I am trying to get Ubuntu 6.10 to install on this Dell Dimension 9200 PC (using the Amd64 LiveCD).

The Dell machine came with a wireless USB keyboard  (the thing does not even have PS/2 adaptors, so I'm stuck with USB anyway).

Now, the strange thing is that during the boot phase of the LiveCD the keyboard is functional (I can type letters in the console), but as soon as X takes over and the GNOME desktop starts, the keyboard is dead - I can't even switch to console anymore.  Of course, I can't run the "Install" utility either.

I tried a couple of kernel boot parameters such as acpi=off, usb=bios, etc., to no avail.  I'm beginning to suspect this isn't really a kernel issue but maybe has to do with X drivers or something like that.

So, instead of preparing database tables and working on web applications I spent a whole lot of time just trying to get my damn keyboard to work, without any success :(

Any ideas on where to go from here?

Thanks in advance.

---

### Post by incubus on 2007-03-04
Hmm... if nobody comes up with a good solution, I would suggest you to try the alternate installer instead -- since the keyboard works before X.  The non-graphical installer asks pretty much the same questions, so it should be straightforward to use.

But before taking that route, search around for people with similar problems.  It could be a matter of changing the keyboard driver in xorg.

incubus

---

