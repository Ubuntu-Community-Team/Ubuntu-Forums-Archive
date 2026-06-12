---
title: "Setting locale failed - ZA.UTF-8"
date: 2006-12-29
forum: Za Team - South Africa
---

### Post by sindile on 2006-12-29
Could you please assist with this error - was setting up LTSP

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_ZA.UTF-8",
        LC_ALL = (unset),
        LANG = "en_ZA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

onething I have noticed is that ZA Translation on synaptic fails

---

### Post by Roque on 2007-01-04
I have the same problem, after installing libc. 
Try 
```

locale -a

```
and see if your locale (en_ZA.UTF-8 ), is included. Mine is not.

I have edited /etc/environment but nothing changes, not even perl's complaint.

---

