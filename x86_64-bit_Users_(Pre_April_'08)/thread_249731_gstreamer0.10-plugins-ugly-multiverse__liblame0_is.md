---
title: "gstreamer0.10-plugins-ugly-multiverse:
  liblame0 is not installable"
date: 2006-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by BlackTopBum on 2006-09-02
Hey there, A little system info is a good spot to start: kernel 2.6.15-26-amd64-k8, Dapper 6.0.6.

I want to add *lame* so *grip* will encode MP3. Then I can add them to my Nomad **MP3-only** player. However, while trying to install gstreamer0.10-plugins-ugly-multiverse the following message occurs: "Depends: liblame0 (>=3.96.1-1) but it is not installable".

Anyone know the status of this package? Have suggestions for installation success?

Currently, there are several gstreamer0.10* packages already installed.

Thanks for your time !
--
BlackTopBum

---

### Post by Kilz on 2006-09-02
> **BlackTopBum said:**
> Hey there, A little system info is a good spot to start: kernel 2.6.15-26-amd64-k8, Dapper 6.0.6.

I want to add *lame* so *grip* will encode MP3. Then I can add them to my Nomad **MP3-only** player. However, while trying to install gstreamer0.10-plugins-ugly-multiverse the following message occurs: "Depends: liblame0 (>=3.96.1-1) but it is not installable".

Anyone know the status of this package? Have suggestions for installation success?

Currently, there are several gstreamer0.10* packages already installed.

Thanks for your time !
--
BlackTopBum


Do you have the Multiverse and Universe repositories enabled? liblame0 is in the Multiverse. [Click here]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") if you need information on how to do it.

---

### Post by BlackTopBum on 2006-09-03
> **Kilz said:**
> Do you have the Multiverse and Universe repositories enabled? liblame0 is in the Multiverse. [Click here]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") if you need information on how to do it.

Thanks for answering. Yes, in fact I set them all just to be certain before trying to install it and updated.

--
BTB

---

