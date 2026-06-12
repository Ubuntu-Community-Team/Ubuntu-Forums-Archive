---
title: "apt-get upgrade"
date: 2004-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by corleone on 2004-10-12
I tried apt-get upgrade and apt-get dist-upgrade, and it downloads everything, tells me this will take up so much room do you want to coninue?  I say yes and get the blue screen asking for keyboard setup, language, do I want to participate in the popularity contest?... then after that back to terminal and I see this:

Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: warning, architecture `amd64' not in remapping table


What does that mean?

---

### Post by froust on 2005-01-18
I get the same error doing a dist-upgrade... Any takers?

---

### Post by Pani on 2005-02-16
I'm getting the same error - followed by:

dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `ubuntu-desktop':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)

Did anyone find a solution?

---

### Post by Dylanby on 2005-02-16
Are you guys running Warty or Hoary?

---

### Post by rwillmer on 2005-02-23
I'm getting this message too. I installed warty and am attempting to dist-upgrade to Hoary when I get the message

Rachel

---

### Post by dallen on 2005-10-13
*dpkg: warning, architecture 'amd64' not in remapping table.*

Check  whether gcc is installed.  ("gcc --version" and "dpkg -l gcc")

I got exactly this error, and recreated it by stepping through the /var/lib/dpkg/info/sun-j2re1.5.postinst  file and running each command in turn.  

The bad one turned out to be:

"dpkg --print-architecture"

man dpkg says it gets that info from gcc.  When I installed gcc, the error went away.

---

