---
title: "Anyone load OpenOffice 2.4 yet?"
date: 2008-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by modestmelody on 2008-03-31
The .debs are i386, of course...
I really could use the equations for linear regressions in Calc...

So what are your experiences with OO2.4 thus far?  Anything tricky worth knowing about?

---

### Post by tighem on 2008-03-31
2.4 RC1 has been in Hardy and so far so good. Much better MS Office 2007 file support, although it's not perfect.

---

### Post by calc on 2008-03-31
I will be uploading OpenOffice.org 2.4.0 (final release) debs in the next day or so.

---

### Post by modestmelody on 2008-03-31
> **calc said:**
> I will be uploading OpenOffice.org 2.4.0 (final release) debs in the next day or so.

Excellent

---

### Post by calc on 2008-04-02
In the process of uploading openoffice.org_2.4.0-3ubuntu1_source.changes as I type this, hopefully no major bugs will be found. :)

---

### Post by be4truth on 2008-04-20
> **calc said:**
> In the process of uploading openoffice.org_2.4.0-3ubuntu1_source.changes as I type this, hopefully no major bugs will be found. :)

Where is the upload?

---

### Post by calc on 2008-04-20
> **be4truth said:**
> Where is the upload?

Its been in Ubuntu hardy for about 3 weeks now.

---

### Post by smileyme on 2008-04-20
I have been using it in Hardy for a week or so, but not frequently enough to report on, except that I haven't seen any anomalies. But boy does it open quickly.

Rick :)

---

### Post by be4truth on 2008-04-20
I extracted the 2.4 files (64bit) from Hardy and tried to install them in Gutsy with dpkg -i *.deb.

First problem:


dpkg: regarding openoffice.org-base-core_1%3a2.4.0-3ubuntu5_amd64.deb containing openoffice.org-base-core, pre-dependency problem:
openoffice.org-base-core pre-depends on dpkg (>= 1.14.12ubuntu3)
dpkg is installed, but is version 1.14.5ubuntu16.

Well, I tried to install dpkg ([http://packages.ubuntu.com/hardy/dpkg](http://packages.ubuntu.com/hardy/dpkg)) but it says it wants [http://packages.ubuntu.com/hardy/libc6](http://packages.ubuntu.com/hardy/libc6). Not a surprise. I install libc6 new version and then tried to install dpkg but now it wants [http://packages.ubuntu.com/hardy/dpkg-dev](http://packages.ubuntu.com/hardy/dpkg-dev) which doesn't install because it wants quite some other stuff.

Any idea how to install OPenOffice 2.4 whichout install hardy.....:)

---

### Post by calc on 2008-04-20
> **be4truth said:**
> I extracted the 2.4 files (64bit) from Hardy and tried to install them in Gutsy with dpkg -i *.deb.

First problem:


dpkg: regarding openoffice.org-base-core_1%3a2.4.0-3ubuntu5_amd64.deb containing openoffice.org-base-core, pre-dependency problem:
openoffice.org-base-core pre-depends on dpkg (>= 1.14.12ubuntu3)
dpkg is installed, but is version 1.14.5ubuntu16.

Well, I tried to install dpkg ([http://packages.ubuntu.com/hardy/dpkg](http://packages.ubuntu.com/hardy/dpkg)) but it says it wants [http://packages.ubuntu.com/hardy/libc6](http://packages.ubuntu.com/hardy/libc6). Not a surprise. I install libc6 new version and then tried to install dpkg but now it wants [http://packages.ubuntu.com/hardy/dpkg-dev](http://packages.ubuntu.com/hardy/dpkg-dev) which doesn't install because it wants quite some other stuff.

Any idea how to install OPenOffice 2.4 whichout install hardy.....:)

You can use the debs from [http://openoffice.org/](http://openoffice.org/) but they lose a lot of features including proper font hinting and Office 2007 support. Other than that, no you would need to upgrade to hardy, Ubuntu 8.04 (hardy) will be released in about 4 days.

---

### Post by FredB on 2008-04-21
OpenOffice.org 2.4 is working wonderfully here on my Hardy 64 bits installation.

So, use hardy ;)

---

