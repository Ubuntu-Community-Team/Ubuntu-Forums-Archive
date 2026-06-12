---
title: "can't run synaptic's ECLIPSE !?"
date: 2006-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by sha_man on 2006-11-29
Hello,

i tried to install *eclipse* via Synaptic - but whenever i want to launch it, it says: ```
Could not launch Eclipse Platform: the custom VM you have chosen is not a valid executable
```

:confused: 

I have Sun's java installed and working correctly (I think), and it's also set as the *default java*.
BTW, when i download the eclipse binary from the website, i CAN RUN IT without problems, except it's **terribly SLOW and CPU intensive**:( .

What else could I try!?

---

### Post by zcrar70 on 2006-12-12
You probably figured this out by now, but for anyone else having this problem, it is caused by the fact that the /etc/eclipse/java_home file isn't set up correctly, and gets the path of the default Sun JVM installation in Ubuntu wrong - as mentionned in that file though, it can be overridden by creating an  "eclipserc" (without quotes) file in ~/.eclipse with the following content:

```
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
```

Where "java-1.5.0-sun" is the name of the major release of the Java platform.

HTH,
Elie

---

### Post by BIGtrouble77 on 2006-12-13
I've had so many issues with eclipse in the repos that I just download it from the eclipse project website.  It's really easy to get going and it's much faster.

---

