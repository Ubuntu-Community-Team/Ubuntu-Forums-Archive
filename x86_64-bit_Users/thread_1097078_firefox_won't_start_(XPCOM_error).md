---
title: "firefox won't start (XPCOM error)"
date: 2009-03-15
forum: x86 64-bit Users
---

### Post by jmcarval on 2009-03-15
Hi. Sorry the newby, probably many times repeated, question...

Installed 8.04LTS x86_64 (server) a few weeks ago. Cool.

Now upgraded to 8.10 x86_64 (server). Seemed ok.
Also played with the Python packages, trying to compatibilize vpython, IDLE ipython and matplotlib. Not sure what I did or if this is related to the problem

Now firefox won't start. From a console it complaints that XPCOM couldn't start. The
export LD_LIBRARY_PATH=/usr/lib/xulrunner-1.9.0.7
workaround fixes this, more or less. But the firefox icon at the Gnome panel fails to work properly.

Can anyone give me a clue on this, please?

Thanks, João

---

### Post by jmcarval on 2009-03-25
Looking for a solution, found that this XPCOM thing is an old and relatively frequent problem which receives little effective help.

In my case ```
ls -d /usr/lib/xulrunner*
``` reveals that my most recent xulrunner lib is    /usr/lib/xulrunner-1.9.0.7
However ```
ls /etc/gre.d 
``` shows that there is no configuration file for it.

Just created a file there ```
sudo nano /etc/gre.d/1.9.0.7.system.conf
``` with the following content:

[1.9.0.7]
GRE_PATH=/usr/lib/xulrunner-1.9.0.7
xulrunner=true
abi=x86_64-gcc3

Just in case also renamed some older configuration files (like 1.9.0.5.system.conf)

This solved my problem.

---

