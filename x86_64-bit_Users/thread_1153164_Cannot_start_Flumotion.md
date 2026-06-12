---
title: "Cannot start Flumotion"
date: 2009-05-08
forum: x86 64-bit Users
---

### Post by NDotter99 on 2009-05-08
I cannot get flumotion started.  When I select start a new manager and connect to it I get this error message

The command that failed was:
/usr/sbin/flumotion -C /tmp/tmpkqEJ1u.flumotion/etc -L /tmp/tmpkqEJ1u.flumotion/var/log -R /tmp/tmpkqEJ1u.flumotion/var/run start manager admin
The command exited with an exit code of 1.

Can anyone help.

---

### Post by jeff_14 on 2009-05-21
you juts need to change the permission by using the terminal..

---

### Post by qole on 2009-05-21
> **jeff_14 said:**
> you juts need to change the permission by using the terminal..

Can you be more specific? Change the permission of what?

I'm getting the same error (in 32-bit 9.04), and I can't figure out what the problem is.

---

### Post by wigren on 2009-06-30
I just experienced a similar problem. It fails because Jaunty uses python 2.6 by default. Flumotion uses python 2.5 and they're not compatible. You need to edit /usr/share/python/debian_defaults and set:
```
# the default python version 
default-version = python2.5
```
Then run:
```
sudo rm /usr/bin/python
sudo ln -s /usr/bin/python2.5 /usr/bin/python
```

From: [http://socialize.leeremenge.net/posts/8](http://socialize.leeremenge.net/posts/8)

---

### Post by qole on 2009-07-01
Flumotion still doesn't start; do I need to reboot?

I start from the Streaming Server Administration icon. I choose "Start a new manager and connect to it"; it warns me that this mode is only useful for testing Flumotion...

I get "Could not start manager" with the following error:

```

The command that failed was:
/usr/sbin/flumotion -C /tmp/tmpu5LvBD.flumotion/etc -L /tmp/tmpu5LvBD.flumotion/var/log -R /tmp/tmpu5LvBD.flumotion/var/run start manager admin
The command exited with an exit code of 1.

```

I type python at the command line and it says it is running "Python 2.5.4 (r254:67916, Apr  4 2009, 17:55:16)"

---

### Post by qole on 2009-07-01
Ok, two things might help:

First, add yourself to the flumotion group:

```

sudo adduser <username> flumotion

```

Secondly, make the /etc/flumotion directory readable:

```

sudo chmod a+x /etc/flumotion
sudo chmod g+r /etc/flumotion/*

```

---

### Post by qole on 2009-07-02
This may not be a good idea, as it impacts other packages that are expecting python 2.6.

> **wigren said:**
> I just experienced a similar problem. It fails because Jaunty uses python 2.6 by default. Flumotion uses python 2.5 and they're not compatible. You need to edit /usr/share/python/debian_defaults and set:
```
# the default python version 
default-version = python2.5
```
Then run:
```
sudo rm /usr/bin/python
sudo ln -s /usr/bin/python2.5 /usr/bin/python
```

From: [http://socialize.leeremenge.net/posts/8](http://socialize.leeremenge.net/posts/8)

---

