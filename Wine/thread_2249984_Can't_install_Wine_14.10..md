---
title: "Can't install Wine: 14.10."
date: 2014-10-25
forum: Wine
---

### Post by felgro on 2014-10-25
(got evicted from this thread - [http://ubuntuforums.org/showthread.php?t=2249847](http://ubuntuforums.org/showthread.php?t=2249847))

I can't get Wine installed after upgrading to 14.10 

```
sudo apt-get install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-amd64 (= 1:1.6.2-0ubuntu6)
           Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu6)
E: Unable to correct problems, you have held broken packages.
```

Check package state -

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
dpkg --get-selections | grep hold
```

There are no held packages.

---

### Post by Bucky Ball on 2014-10-25
*Post moved to own thread.*

Please don't post your support requests on other user's threads. It gets confusing and is unfair to the OP of the original thread. Post a new thread with a descriptive title in the appropriate forum section and include as much info as you think is relevant. 

Good luck.

---

### Post by felgro on 2014-10-25
It's the same problem - I thought it may be relevant. 

*E: Unable to correct problems, you have held broken packages*. 

- the **exact** end result I have.

 No pleasing anyone - post a new thread about another issue, get yelled at for not using similar existing thread.

---

### Post by Bucky Ball on 2014-10-25
I'm not yelling. ;)

We just don't deal with two posters posting support requests on the same thread. They are just about NEVER the same issue and it just causes confusion. Too many variables and cross-talk is inevitable. By all means, keep an eye on that thread and add any useful information you come up with in your research and try any relevant advice others post there.

Good luck.

> **felgro said:**
> ... post a new thread about another issue, get yelled at for not using similar existing thread.

Example, please. :-k

---

