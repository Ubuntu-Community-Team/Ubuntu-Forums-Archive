---
title: "Network printer in chroot32"
date: 2006-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by rainbowbuilder on 2006-11-06
I have a networked Brother MFC-420CN printer that has a vendor supplied driver for Debian 32 bit. I created a 32bit dchroot and while in that dchroot, I can print fine. 

I cannot get the driver to work in the 64bit world (and vendor states it doesn't work there) How can I create a printer in the 64 bit world to send to the dchroot 32 bit printer? I have seen many posts about the USB version of this printer, but I need to use as a Network printer. I am sure it is more than just linking the print queue folder (/var/spool/lpd/MFC420CN) across the dchroot.

---

### Post by kidders on 2006-11-06
Hi there,

Usually, printer sharing is done with things like CUPS. CUPS essentially lets you interact with your printer over HTTP, so it won't matter whether the driver is 64-bit or not :-) You'd run the CUPS server in your chroot-ed environment, and print to it from anywhere.

---

### Post by roberts3000 on 2006-11-22
has anyone got this to work? I have the same printer, been working on it for two weeks with no luck.

---

### Post by incubus on 2006-11-22
Did you disable the 64bit CUPS server (outside chroot) and invoked the 32bit one with the driver installed?

As kidders said, it should be transparent to the application that tries to print something.  In theory, all it has to do is to connect to the CUPS daemon (cupsd). 

What I would do outside chroot:
```

$ sudo invoke-rc.d cupsys stop

```

Inside chroot:
```

$ dchroot -d
$ sudo invoke-rc.d cupsys restart

```

But I confess I have almost no experience with this.

incubus

---

