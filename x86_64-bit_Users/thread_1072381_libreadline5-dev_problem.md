---
title: "libreadline5-dev problem"
date: 2009-02-17
forum: x86 64-bit Users
---

### Post by karenk on 2009-02-17
I'm new to Linux (using Ubuntu 8.10) so I don't even know what libreadline5-dev does, but I get error messages now whenever I try installing new packages.

I think it started when I tried installing GoogleEarth 4.3 (but it happens when attempting installation of others as well):
I get the following message from synaptic:
E: libreadline5-dev: subprocess post-installation script returned error exit status 1

Before GE 4.3, I had tried installing GE 5 but realized that wouldn't work.  But I forgot to uninstall GE5 first (How do I do that?  The uninstall script in the /opt/googleearth directory just says "Could not find a usable uninstall program. Aborting.")

I have tried reinstalling libreadline5-dev and libreadline5 but synaptic gives the same message as above.

Thanks for any help!

---

### Post by Yellow Pasque on 2009-02-17
> E: libreadline5-dev: subprocess post-installation script returned error exit status 1
That's a bit of a generic error message. See if you can coax more info out with the terminal. Try:
```
sudo dpkg --configure -a
```

---

### Post by karenk on 2009-02-17
I got this message, which I had seen while trying to install from the command line.  Still doesn't mean anything to me.

```
Setting up libreadline5-dev (5.2-3build1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing libreadline5-dev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libreadline5-dev

```

---

### Post by Yellow Pasque on 2009-02-19
Sorry I didn't get back to you sooner, I could've sworn I posted here the other day.
Can you post the output of this command:
```
ls -la /usr/share/info
```

---

### Post by karenk on 2009-02-19
Thanks for your response, but I actually gave up and retransferred my wubi installation.  Still can't get GE 5 or 4.3 to work, but at least I don't get that error on every installation attempt anymore.  GE will have to wait for another week at least.  Thanks for your help!

---

