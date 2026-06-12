---
title: "Adobe reader in 64bit"
date: 2007-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by PmDematagoda on 2007-08-29
I was wondering if there is any way to install Adobe reader on ubuntu 64 bit?

---

### Post by Kilz on 2007-08-29
Perhaps in your need to get Adobe working you didnt notice the Sticky posts. You might even try a search of this section as I know this is a common topic.

---

### Post by funrider on 2007-08-29
use KPDF, it is in the repository and comes with "hand tool"

---

### Post by John Jason Jordan on 2007-08-29
> **funrider said:**
> use KPDF, it is in the repository and comes with "hand tool"
KPDF can't handle editable PDF files, among its other problems.

---

### Post by Kilz on 2007-08-29
> **John Jason Jordan said:**
> KPDF can't handle editable PDF files, among its other problems.

How about [pdfedit?]("http://sourceforge.net/projects/pdfedit") I just compiled it last week, it was easy and it allows you to edit pdf files. You can also use it to read them.

---

### Post by funrider on 2007-08-29
> **John Jason Jordan said:**
> KPDF can't handle editable PDF files, among its other problems.

i learned a new thing today......thanks man

---

### Post by PmDematagoda on 2007-08-29
Thanks for the help, and sorry Kilz you are right, I just checked out the first sticky thread and it answered almost all my problems, sorry for disturbing you.

---

### Post by Kilz on 2007-08-30
Your not disturbing me. I was just pointing out that the information you wanted was easy to get.

---

### Post by serendib on 2007-08-30
Would like to take advice and install pdfedit and get away from the Adobe syndrome. How do I get hold of qt3, boost and xlib as stated in the README of pdfedit files and install them? Running feisty. Please advice.

---

### Post by nss0000 on 2007-08-30
Adobe reader problems ? Mine "just works" on DAPPERx64 -- always has, never an issue. Maybe Festering_Faun is the issue ... as in so many other cases .

---

### Post by kuja on 2007-08-30
serendib:

"sudo apt-get install libqt3-mt-dev libboost-dev xlibs-dev"

Might need more, hard to say

---

### Post by serendib on 2007-08-31
kuja, thanks for your help.

---

### Post by kuja on 2007-08-31
> **serendib said:**
> kuja, thanks for your help.

You're welcome.

---

### Post by ipina on 2007-09-01
Hi, there's also a direct way to install pdfedit, without compiling hence without taking care of dependencies. Download from here [http://www.getdeb.net/download.php?release=1002&fpos=0](http://www.getdeb.net/download.php?release=1002&fpos=0) and install with gdebi package installer. After installation, create a launcher. Crjackson advised me and it works. Greetings.

---

### Post by John Jason Jordan on 2007-09-01
> **ipina said:**
> Hi, there's also a direct way to install pdfedit, without compiling hence without taking care of dependencies. Download from here [http://www.getdeb.net/download.php?release=1002&fpos=0](http://www.getdeb.net/download.php?release=1002&fpos=0) and install with gdebi package installer. After installation, create a launcher. Crjackson advised me and it works. Greetings.
Hey! That worked. Thanks!

But how do I print from it? No print function?

---

### Post by crjackson on 2007-09-01
> **John Jason Jordan said:**
> Hey! That worked. Thanks!

But how do I print from it? No print function?

Glad it worked out.

---

