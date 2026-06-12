---
title: "installing from source"
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by tikal26 on 2007-06-06
Hello,
I have no idea if this is the right place, but I am trying to install the following kio in kubuntu 7.04 64.

[http://kde-look.org/content/show.php/KIO+Slave+sysinfo%3A%2B?content=58704](http://kde-look.org/content/show.php/KIO+Slave+sysinfo%3A%2B?content=58704)

I am using the kubuntu from source package snad Ig et the following error.

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
 Any help would be greatly aprecited

---

### Post by pbw on 2007-06-07
You don't need to compile it yourself since they offer a feisty deb on that page. 

But to answer your question, just install kde headers as it says.

ie. sudo apt-get install kdelibs4-dev

---

### Post by incubus on 2007-06-07
It sounds like they don't have an x86_64 version, am I right?

If you follow what pbw said, it should work.  The headers are in -dev packages.

incubus

---

### Post by pbw on 2007-06-07
> **incubus said:**
> It sounds like they don't have an x86_64 version, am I right?


Oops gapped what forum this was in, sorry.

---

### Post by tikal26 on 2007-06-07
that seemed to have work, but now I am running into make proble I ge tthe following error
Package hal was not found in the pkg-config search path.
Perhaps you should add the directory containing `hal.pc'
to the PKG_CONFIG_PATH environment variable
No package 'hal' found
rm: cannot remove `': Is a directory

any idea

---

