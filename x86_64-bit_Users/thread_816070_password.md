---
title: "password"
date: 2008-06-02
forum: x86 64-bit Users
---

### Post by shipinomore on 2008-06-02
new to ubuntu. was trying to use a terminal and did a SU command then when i entered my password I got an error about authori failed.

I was trying to install Vmware tools and I also see that you cannot use rpm?

Does ubuntu use the SU command to do installs etc. ?

Larry

---

### Post by Joeb454 on 2008-06-02
**su** typically doesn't work. To get temporary root access, Ubuntu uses "**sudo**" so you would prepend your command with that.

And Ubuntu is based from Debian - hence it uses deb's not RPM's :)

---

### Post by drhpapagino on 2008-06-02
try sudo as administrator.  VMware tools must be installed with the tar command.  VMware manual has a how to section for Linux installs.  Follow it closely and all will work.  Good Luck

---

