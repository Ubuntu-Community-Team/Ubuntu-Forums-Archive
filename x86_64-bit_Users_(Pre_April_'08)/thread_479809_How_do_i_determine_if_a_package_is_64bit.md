---
title: "How do i determine if a package is 64bit?"
date: 2007-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by litemotiv on 2007-06-20
i just installed 64bit kubuntu today (used 32bit before), though i'm not sure how i can determine if a package in the repositories is 64bit? the repos in sources.list seem the same as in the 32bit install, so how is determined which version of a program i get?

---

### Post by jamesford on 2007-06-20
you will only get 64 bit packages via synaptic/apt-get when ur using 64 bit (k)ubuntu

---

### Post by nss0000 on 2007-06-20
Big_LM

All Ubuntu x64 apps come with a dancing paper_clip icon that self-installs in /root/keyboard  ... er, I believe his name is " clippy". 

He promises x64UBUNTU will improve just-as-fast as ... jeepers I just can't catch that last name.

---

### Post by incubus on 2007-06-20
Just so you know, if you type this in the terminal:
```

$ arch

```

You see which architecture you're using.

Now as for the package, as jamesford said, you don't have to worry about it if you install through the Debian packaging system.  But you can check it with:
```

$ apt-cache show firefox | grep Architecture

Architecture: amd64
Architecture: amd64

```

In other words, you just have to look for the field Architecture in the package description.

incubus

---

### Post by litemotiv on 2007-06-21
thanks, that's useful to know. :-)

---

### Post by fakie_flip on 2007-06-25
dpkg --print-architecture package.deb

---

### Post by fakie_flip on 2007-06-25
try this.

sudo find / -name '*.deb' -exec dpkg -I {} \; | grep "Package\|Architecture"

or this.

sudo find / -name '*.deb' -exec bash -c "dpkg -I {} | grep 'Package\|Architecture'" \;

---

