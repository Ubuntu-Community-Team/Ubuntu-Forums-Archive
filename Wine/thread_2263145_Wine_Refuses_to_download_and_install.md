---
title: "Wine Refuses to download and install"
date: 2015-01-29
forum: Wine
---

### Post by jtmcc on 2015-01-29
I don't even know how to respond to this.

```
johnthomas@alternative-Satellite-L775:~$ sudo apt-get install wine[sudo] password for johnthomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Brand new machine, never had Wine installed.

---

### Post by ian-weisser on 2015-01-29
Try these two commands. Please post the entire output of both here. The output (and error messages) will help us figure out the problem.

```
apt-cache policy wine1.6
sudo apt-get install wine1.6
```

Is your new machine running 14.04, 14.10, or something else?

---

