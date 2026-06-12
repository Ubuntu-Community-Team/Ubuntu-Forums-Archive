---
title: "Do I need a key for za repositories?"
date: 2009-02-16
forum: Za Team - South Africa
---

### Post by afrodeity on 2009-02-16
Do these repositories work, and do I need a key?



deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy main restricted


deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy-updates universe


deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by drubin on 2009-02-16
Have you tried them? :)

Those are the same as mine and I do not need a key.

---

### Post by stefanor on 2009-02-17
> **afrodeity said:**
> 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

That all looked good. If you want, you can switch these security updates to za.archive as well. You'll get your security updates a few hours later that way, but over local bandwidth.

---

### Post by drubin on 2009-02-17
> **stefanor said:**
> That all looked good. If you want, you can switch these security updates to za.archive as well. You'll get your security updates a few hours later that way, but over local bandwidth.

Do they even mirror the security updates?

---

### Post by morgs on 2009-02-17
> **drubin said:**
> Do they even mirror the security updates?

Yes, TENET do that on mirror.ac.za (and hence za.archive.ubuntu.com).

---

### Post by drubin on 2009-02-17
> **morgs said:**
> Yes, TENET do that on mirror.ac.za (and hence za.archive.ubuntu.com).
> 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

I have never seen 
deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) hardy-security universe

---

### Post by afrodeity on 2009-02-20
I am having trouble getting the mirrors, because all of the above are .com,and the above sites are NOT actually mirrored.


[http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za)
[ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za)

are just the iso's and not LIVE reflection of the above international sites, so this is a problem for anyone downstream on local bandwidth, or am I doing something wrong and there is a rational to this?

---

### Post by drubin on 2009-02-20
> **afrodeity said:**
> I am having trouble getting the mirrors, because all of the above are .com,and the above sites are NOT actually mirrored.


[http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za)
[ftp://ubuntu.mirror.ac.za](ftp://ubuntu.mirror.ac.za)

are just the iso's and not LIVE reflection of the above international sites, so this is a problem for anyone downstream on local bandwidth, or am I doing something wrong and there is a rational to this?

[http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) is the same as [http://ubuntu.mirror.ac.za/ubuntu-archive/](http://ubuntu.mirror.ac.za/ubuntu-archive/)

so in your source list use deb [http://ubuntu.mirror.ac.za/ubuntu-archive/](http://ubuntu.mirror.ac.za/ubuntu-archive/) main restricted 

If you need to have a non .com domain for what ever reason. But they are both locally hosted. 

Hope this helps

---

