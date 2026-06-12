---
title: "Adobe reader install"
date: 2008-06-24
forum: x86 64-bit Users
---

### Post by fahd on 2008-06-24
Hi folks ...
Whenever i try to install adobe reader (i386) under kubuntu for intel 64bit (amd64) edition i get the next error message:

can not install the package (i386).

Thanks a lot.

Fahd
080624

---

### Post by kuja on 2008-06-24
install it with "dpkg --install --force-architecture somepackage.deb"

---

### Post by stchman on 2008-06-24
> **fahd said:**
> Hi folks ...
Whenever i try to install adobe reader (i386) under kubuntu for intel 64bit (amd64) edition i get the next error message:

can not install the package (i386).

Thanks a lot.

Fahd
080624

Yes, the i386 debs will not work with the amd64 installs.

To install Acrobat reader use the Medibuntu repos.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

Medibuntu software contains 64 bit debs.

I really do not see the need for Acrobat as Evince is a capable reader.  Now Acrobat does have the editable pdf like tax forms.  The only time I use Acrobat is during tax time when the state has fill out PDF forms.  I otherwise use Evince.

Hope this helps.

---

### Post by stchman on 2008-06-24
> **kuja said:**
> install it with "dpkg --install --force-architecture somepackage.deb"

The dpkg command will only work if there are no dependencies needed.

If dependencies are needed then you need to use the gdebi command.

He can man gdebi to get the syntax.

---

### Post by kuja on 2008-06-24
> GDEBI(1)                                                                                                                                                               GDEBI(1)

NAME
       gdebi - Simple tool to install deb files

SYNOPSIS
       gdebi [package.deb]

DESCRIPTION
       gdebi lets you install local deb packages resolving and installing its dependencies. apt does the same, but only for remote (http, ftp) located packages.

AUTHOR
       This manual page was written by Gustavo Franco <stratus@debian.org>, for the Debian project (but may be used by others).

                                                                                  Dec 23, 2005                                                                         GDEBI(1)

> $ man gdebi-kde
No manual entry for gdebi-kde
See 'man 7 undocumented' for help when manual pages are not available.

I see nothing with regards to that ...... at all.

---

### Post by cariboo on 2008-06-25
Go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

And follow the instructions. Once it is done use System-->Aministration-->Synaptic Package Manager to install it. Search for a file called acroread.

Jim

---

### Post by fahd on 2008-06-26
Thanks a lot for all people who replied my question as possible as they could. Thanks again.

Fahd

---

