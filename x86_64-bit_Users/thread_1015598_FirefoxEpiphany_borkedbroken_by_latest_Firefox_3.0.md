---
title: "Firefox/Epiphany borked/broken by latest Firefox 3.0.5 Upgrade on Intrepid"
date: 2008-12-19
forum: x86 64-bit Users
---

### Post by gbutler69 on 2008-12-19
Firefox/Epiphany borked/broken by latest Firefox 3.0.5 Upgrade on Ubuntu 8.10 Intrepid Ibex!

Yes, the problem is back! Firefox and Epiphany were both broken by the latest Firefox upgrade on December 18, 2008 @ approximately 7:00 PM EST.
When try to run Firefox, would get the following:

```

gbutler@ubuntu:/etc/gre.d$ firefox
Couldn't load XPCOM.

```
and Epiphany would get the following:

```

gbutler@ubuntu:/etc/gre.d$ epiphany
** (epiphany-browser:10803): WARNING **: Could not startup XPCOM glue!

```

Now, after examining the contents of the /etc/gre.d I made a "leap of faith" and did the following:

The contents of the folder after the update were:

```

gbutler@ubuntu:/etc/gre.d$ ls -al
total 28
drwxr-xr-x   2 root root 4096 2008-12-19 00:01 .
drwxr-xr-x 153 root root 8192 2008-12-18 23:00 ..
-rwxr-xr-x   1 root root   76 2008-07-28 16:56 1.9.0.1.system.conf
-rwxr-xr-x   1 root root   77 2008-12-18 23:58 1.9.0.3.system.conf
-rwxr-xr-x   1 root root   77 2008-12-18 23:48 1.9.0.4.system.conf
-rwxr-xr-x   1 root root   76 2008-12-16 18:32 1.9.0.5.system.conf
gbutler@ubuntu:/etc/gre.d$ 

```

So, I edited the 1.9.0.3.system.conf and made it point to the 1.9.0.5 lib path as follows:

```

gbutler@ubuntu:/etc/gre.d$ cat 1.9.0.3.system.conf 

[1.9.0.3]
GRE_PATH=/usr/lib/xulrunner-1.9.0.5
xulrunner=true
abi=x86_64-gcc3

gbutler@ubuntu:/etc/gre.d$ 

```

Then, I did the same for the 1.9.0.4.system.conf as follows:

```

gbutler@ubuntu:/etc/gre.d$ cat 1.9.0.4.system.conf 

[1.9.0.4]
GRE_PATH=/usr/lib/xulrunner-1.9.0.5
xulrunner=true
abi=x86_64-gcc3

gbutler@ubuntu:/etc/gre.d$ 

```

This fixed the problem. This seems to be a problem with the packaging of Epiphany/XULRunner/Firefox for Intrepid x86_64.

I don't think this is the correct fix, merely a work-around to make Epiphany and Firefox work after the Firefox 3.0.5 upgrade.

The package maintainers are going to need to fix this I imagine.

---

### Post by Kuoi on 2008-12-19
I had to install epiphany to get me on the internet after Firefox did an update.
I guess it's the same update.
Firefox isn't working anymore , and earlier today I had the same with Firefox in Windows.
Still have to fix , but I guess no update will work because you can't start Firefox anymore (talking about Windows).
Will have to keep an eye on the mozilla website any minute .

Kuoi

---

### Post by ubernatural on 2008-12-19
Yeah, firefox just broke for me too with the latest update, but epiphany still works (thankfully).  I actually get an odd little "scrollbar" type thing in the center of the window when I try to load firefox, but there are no errors reported when I load from a terminal.  No sites will load in the window though.  Here's hoping for a quick patch for this one...

---

### Post by skeetre on 2008-12-19
The bottom 2 posts in this thread (at least as of this posting) have 2 possible solutions. One with reinstalling and one without reinstalling.

[https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/270303]("https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/270303")

I'm at work researching the same issue and found this, but I can't test to verify until I get off.

---

