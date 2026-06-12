---
title: "Problem with updates"
date: 2008-08-13
forum: x86 64-bit Users
---

### Post by xphil9 on 2008-08-13
Hey I ran a shellscript before I understood what exactly they do, I am new to linux. Anyways, when I run

sudo apt-get update

I recieve the error

'E:Type 'wget' is not known on line 50 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Any help would be awesome

Update manager is hanging out in the tray with an error icon and the error message

"An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'wget' is not known on line 50 in source list /etc/apt/sources.list, E:The list of sources could not be read.'    "

---

### Post by xphil9 on 2008-08-13
Synaptic package manager says

E: Type 'wget' is not known on line 50 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by ibutho on 2008-08-13
You could download wget from [here]("http://packages.ubuntu.com/search?keywords=wget&searchon=names&suite=hardy&section=all") and then use the dpkg command to install it.

---

### Post by xphil9 on 2008-08-13
there are major errors going down now, just going to reinstall ubuntu

watchout

---

