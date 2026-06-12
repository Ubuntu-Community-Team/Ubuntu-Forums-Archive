---
title: "Can't install Pidgin"
date: 2007-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by revchris on 2007-11-01
I'm trying to install pidgin through Synaptic but I keep getting this error:

[INDENT]pidgin:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed[/INDENT]

I do it from a terminal and I get: 
[INDENT]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages[/INDENT]

What do I need to do?

---

### Post by dewey on 2007-11-01
Does synaptic run an update automatically?  I'm sorry, I don't use it.

Try this in the CLI:
> sudo apt-get update
sudo apt-get install pidgin

---

### Post by earobinson on 2007-11-01
what version of ubuntu are you useing, I though pidigin came stock now :)

---

### Post by revchris on 2007-11-01
I'm on Gutsy.
and this is what I get when I run sudo apt-get install pidgin:

[INDENT]Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
pidgin: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages[/INDENT]

---

### Post by lildeb on 2007-11-01
> **earobinson said:**
> what version of ubuntu are you useing, I though pidigin came stock now :)
I agree, I'm on Gusty as well and Pidgin came stock

---

### Post by Yellow Pasque on 2007-11-01
If you still can't get it, you might try using the libpango from Debian sid: [http://packages.debian.org/sid/libpango1.0-common](http://packages.debian.org/sid/libpango1.0-common)

OR the entire pidgin package: [http://packages.debian.org/sid/pidgin](http://packages.debian.org/sid/pidgin)

---

### Post by revchris on 2007-11-01
I go to Applications->Add/Remove...  and I get this when I try to add pidgin

[INDENT]Cannot install 'pidgin'

This application conflicts with other installed software. To install 'pidgin' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/INDENT]

---

### Post by Sockerdrickan on 2007-11-01
remove pidgin in synaptic or download source and compile [www.pidgin.im](www.pidgin.im)
sounds like you ****** up your install in the first place because Pidgin comes with 7.10

---

### Post by revchris on 2007-11-01
> **Tux0r said:**
> 
sounds like you ****** up your install in the first place because Pidgin comes with 7.10

I think you and my ex-wife would get along great. :lolflag:

I disabled some 3rd party repositories and it installed like a dream.  Thanks everyone.

---

### Post by snaptwenty on 2008-03-16
Hi, I'm kind of new to ubuntu, and also kind of a slow learner, so...  Anyways, I accidentally uninstalled pidgin and am now having the exact same problem.  What did u so exactly to fix it?  Also, is there anyway u could give me the crucial command lines that u entered to do what u did?  Take care and thanks for any help you can give

---

