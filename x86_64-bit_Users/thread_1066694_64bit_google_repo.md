---
title: "64bit google repo?"
date: 2009-02-11
forum: x86 64-bit Users
---

### Post by dougleduck on 2009-02-11
Can someone give me the address for this?

Google indicates that a 64bit repo is avialable but doesn't tell you where :(

---

### Post by darco on 2009-02-11
Hmm, Googling it may help !:)
You have to add to your source list....

[http://www.google.com/linuxrepositories/apt.html](http://www.google.com/linuxrepositories/apt.html)

darco

---

### Post by dougleduck on 2009-02-11
I did :P. This is the 32bit repo no?

---

### Post by Artemis3 on 2009-02-11
Did you know repositories can contain more than one architecture?

---

### Post by dougleduck on 2009-02-11
I take package manager doesn't know which architecture I'm using and I only get one result from the package manager, and it says

"to install Picasa from our 64-bit repository, the system's 32-bit libraries will be automatically installed if needed."

[http://picasa.google.com/linux/faq.html#2]("http://picasa.google.com/linux/faq.html#2")

I'll email them try find out where it is.

Thanks for advice. 

I'll post back here if I find it.

---

### Post by darco on 2009-02-11
> **dougleduck said:**
> I did :P. This is the 32bit repo no?

When I googled it, this site came up:

[http://www.google.com/linuxrepositories/yum.html](http://www.google.com/linuxrepositories/yum.html)

which shows x64. Clicking on the APT link does not specify x64, so not sure...

darco

---

### Post by inphektion on 2009-05-13
Any final word here?  I'd like to install picasa and google earth on my jaunty x64 and would rather use a repo when available.  Just want to make sure getting the x64 and not the 32 bit.

---

### Post by Skripka on 2009-05-13
> **inphektion said:**
> Any final word here?  I'd like to install picasa and google earth on my jaunty x64 and would rather use a repo when available.  Just want to make sure getting the x64 and not the 32 bit.

Google does not publish ANY of their apps as native 64bit code, not even Windows IIRC.  You can however force 32bit Google Earth to compile as a 64bit binary for any given Linux.

---

### Post by inphektion on 2009-05-13
yes you are right.  even their amd64.deb of picasa is really still 32bit picasa just knows what libraries to reference.  From their site:

> For Debian-based distributions, install the amd64.deb instead of the i386.deb. This is still 32-bit, but it knows to reference the system's 32-bit libraries. If you use apt-get to install Picasa from our 64-bit repository, the system's 32-bit libraries will be automatically installed if needed.

---

