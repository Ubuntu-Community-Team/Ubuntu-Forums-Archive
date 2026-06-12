---
title: "[SOLVED] Software sources error (software-properties-gtk)"
date: 2009-01-04
forum: x86 64-bit Users
---

### Post by runner09 on 2009-01-04
Hello all

This weekend I updated from 8.04 to 8.10 Ubuntu (amd-64). Things went relatively smoothly with the exception that the packages numpy and matplotlib did not update. So I manually downloaded numpy and matplotlib packages and followed the build-install instructions. (I used the package manager to remove the old numpy and matplotlib packages). After a few issues getting these packages installed, I was having a look around to make sure things worked okay when I noticed that I could not access the software sources dialog (after entering my password). Similarly, I could not get the repository listing through the Synaptic Package Manager. The /etc/apt/sources.list file is readable through a text editor, so I tried to open the software manager via:

gksu /usr/bin/software-properties-gtk

The result was:

 File "/usr/bin/software-properties-gtk", line 27, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /var/lib/python-support/python2.5/gtk-2.0/gtk/_gtk.so: undefined symbol: gdk_window_remove_redirection

I am not a power-user of Linux, and I have tried searching for help on this issue but with no luck. If anyone can point me in the right direction, it would be greatly appreciated.

Thanks

---

### Post by jts0803odon on 2009-01-05
[This thread]("http://ubuntuforums.org/showthread.php?t=990852") helped me when I had that problem. 

At the terminal, type: 

```
lsb_release -a
```

You might see a Debian release listed instead of Ubuntu. If so, try editing /etc/lsb_release by replacing the text there with:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
```

Be sure to thank OP if it works. I noticed a few problems that were associated with the kernel upgrade, but I was also trying Amarok nightly builds at the same time, so I don't know what really is at the root of issues I was having. Good luck.

---

### Post by runner09 on 2009-01-05
> **jts0803odon said:**
> [This thread]("http://ubuntuforums.org/showthread.php?t=990852") helped me when I had that problem. 

At the terminal, type: 

```
lsb_release -a
```

You might see a Debian release listed instead of Ubuntu. If so, try editing /etc/lsb_release by replacing the text there with:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
```

Be sure to thank OP if it works. I noticed a few problems that were associated with the kernel upgrade, but I was also trying Amarok nightly builds at the same time, so I don't know what really is at the root of issues I was having. Good luck.


Thanks **jts0803odon** for the suggestions.

```
lsb_release -a
```

does not appear to give any clues, as the output was:

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
```

I also tried the diagnostic suggested by **fooman** in the linked thread that you provided:

```
sudo apt-get update
```

which appears to run fine (it hits all of the repositories). However, software sources still fails, and I also notice that when I get an alert about a new update on the top toolbar, nothing happens when I click on the 'update' arrow.

If you have any other suggestions, please let me know.
Thanks for your help.

---

### Post by runner09 on 2009-01-10
I finally stumbled upon a 'fix', as suggested from this link:

[https://bugs.launchpad.net/ubuntu/+source/fusion-icon/+bug/268577](https://bugs.launchpad.net/ubuntu/+source/fusion-icon/+bug/268577)

Looks like a conflict with libs in /usr/local/lib/

Everything works after removing the libs in that location.
I hope this info helps someone else.

Cheers

---

