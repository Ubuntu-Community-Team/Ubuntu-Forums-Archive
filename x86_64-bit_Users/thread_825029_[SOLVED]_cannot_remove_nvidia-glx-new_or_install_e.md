---
title: "[SOLVED] cannot remove nvidia-glx-new or install envy.. Error"
date: 2008-06-10
forum: x86 64-bit Users
---

### Post by jimmy the saint on 2008-06-10
I have an hp laptop with a GeForce go 6150 which requires a newer driver than the one that is provided with Ubuntu.  I am attempting to install envy, but nvidia-glx-new cannot be removed.  The error returned is 

```
E: nvidia-glx-new: subprocess post-removal script returned error exit status 2
```

The console output from the expanded details in synaptic is
```

(Reading database ... 114075 files and directories currently installed.)
Removing nvidia-glx-new ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx-new (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx-new
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

It appears to be looking for files in the lib32 folder that are not there due to the fact that this is a 64 bit install.  I found a thread that discusses a similar issue, but the solution of adding a sym link in the lib64 folder is not working for me. 

Any ideas?

Thanks

JTS

---

### Post by jimmy the saint on 2008-06-10
after doing more research it turns out that the sym link idea is terrible so I removed it.  anyway, I sure hope someone can help me with this.  I am about to file a bug at launchpad as it seems to be reproducable.  any help is appreiciated!!

---

### Post by jimmy the saint on 2008-06-10
workaround via launchpad bug #36625.  The bottom of the page.  sloppy but seems to have worked.

---

### Post by olobex on 2008-06-14
This is what solved it for me on x64 ubuntu 8.04:

sudo mkdir /usr/lib32
sudo touch /usr/lib32/libGL.so.1

and then run the regular installation/deinstallation procedures again.

Hope it helps.
Olobex

---

### Post by callit on 2008-06-26
This worked for me too!  Thanks!

---

### Post by zhougm on 2008-08-30
thanks!
&#36825;&#30830;&#23454;&#26159;&#19968;&#20010;&#22909;&#30340;&#35299;&#20915;&#26041;&#26696;

---

### Post by jmattille on 2008-08-31
Thanks so much for this solution. I have tried so many other suggestions and work arounds. Non have worked till now.. :):)

---

### Post by mercules2178 on 2008-08-31
Thanks, worked for me!!!

---

### Post by It'sSuperJeremy on 2008-09-05
Worked for me too!

---

### Post by cr01nk on 2008-11-06
Thanks .. Works for me tooo..  I cannot explain how greatful i m

---

### Post by eumakant on 2009-03-17
works like a charm thx buddy 

i wanted to have nvidia settings gui window i wonder how to install it

---

### Post by norwoods on 2009-03-17
> **eumakant said:**
> works like a charm thx buddy 

i wanted to have nvidia settings gui window i wonder how to install it

install nvidia-settings

you need to run with admin privileges to change /etc/X11/xorg.conf
run gksu nvidia-settings

---

