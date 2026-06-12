---
title: "kvm-79"
date: 2008-11-15
forum: x86 64-bit Users
---

### Post by rrm3 on 2008-11-15
Hello.  I compiled some debs for kvm-79, libvirt-0.4.6, python-virtinst-0.400.0, and virt-manager-0.6.0.  This is the first time I've tried to make debs.  I pretty much just used the prior version and commented out all the patches that didn't work.  Seems to work pretty well for me.  They're at:

[http://uoregon.edu/~mcmeekin/deb/](http://uoregon.edu/~mcmeekin/deb/)

for now.

---

### Post by rrm3 on 2008-11-15
hmm.  works pretty well for OpenBSD 4.4, but Windows Server 2008 doesn't want to install.  It just hangs after I tell it to speak to me in English.

---

### Post by rrm3 on 2008-11-15
Nope, just had to restart.  Everything works.

---

### Post by rrm3 on 2008-11-19
hmm.  moved to [https://launchpad.net/~rrm3/+archive](https://launchpad.net/~rrm3/+archive)
though, it doesn't appear that anyone is interested.

---

### Post by FarJumper on 2008-11-28
> **rrm3 said:**
> hmm.  moved to [https://launchpad.net/~rrm3/+archive](https://launchpad.net/~rrm3/+archive)
though, it doesn't appear that anyone is interested.

Thanks. I'm interested :)

I tried it and it works. But now I can't invoke kvm as user because of permissions of the /dev/kvm (I guess). The user is in kvm group.

It worked flawlessly with version 72 this day before upgrading.

Ubuntu: intrepid

---

### Post by ccube on 2009-01-15
Yeah, im interested too. 
Thanks for making the kvm-package. Please stay up to date! ;)

If you get the "Permission Denied" message, make shure you are really in that group. (You arent after updating)

Also make shure to start a new session (xterm, etc) for making changes to work.

If not shure, just reboot after adding user to group.

greetings,
ccube

---

### Post by Blaze1024 on 2009-02-12
> **rrm3 said:**
> Hello.  I compiled some debs for kvm-79, libvirt-0.4.6, python-virtinst-0.400.0, and virt-manager-0.6.0.  This is the first time I've tried to make debs.  I pretty much just used the prior version and commented out all the patches that didn't work.  Seems to work pretty well for me.  They're at:

[http://uoregon.edu/~mcmeekin/deb/](http://uoregon.edu/~mcmeekin/deb/)

for now.

any chance on seeing 32bit debs ?

---

