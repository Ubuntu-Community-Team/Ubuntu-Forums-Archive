---
title: "bug blocks 8.10 desktop install or updates"
date: 2009-04-10
forum: x86 64-bit Users
---

### Post by ken78724 on 2009-04-10
thanks. Ken):P

---

### Post by Kareeser on 2009-04-10
```
ubuntu-bug apt-get
```

And copy&paste every error message you see.

---

### Post by dcstar on 2009-04-11
> **ken78724 said:**
> can't bring in 466 updates nor can I install 8.10 desktop-AMD64. am running Ubuntu 8.04.2 and the following notice shows up after I clicked on auto up date: "Can't install 'ubuntu-desktop'

It was impossible to install a required package. Please report this as a bug."

Yes, I planned to cure this by installing a newly downloaded 8.10 but have not had time. originally I downloaded Ubuntu Studio 8.10 [1.2 giB. burned it on a DVD and used an external loader].
.......

What's wrong with just installing the ubuntustudio-desktop package?

---

### Post by ken78724 on 2009-04-14
> **Kareeser said:**
> ```
ubuntu-bug apt-get
```

And copy&paste every error message you see.

essentially solved

---

### Post by ken78724 on 2009-04-14
an ubuntustudio-desktop forum specialist for studio, said there are problems in ubuntustudio  developers had not overcome. forums suggest to get around the problem, do a ubuntu 8.10 desktop install then update ubuntustudio update. I gave up and installed 9.04 jaunty 64 and did without ubuntustudio

---

### Post by ken78724 on 2009-04-15
could not do updates. TheLasko U Studio often ends/causing a bug... whatever

---

### Post by ken78724 on 2009-04-24
puzzle resolved following: deb [http://ubuntu-bug](http://ubuntu-bug) apt-get

The message pretty well tells you what is wrong, to repair the problem press Alt-F2 and type:
Code:  gksu gedit /etc/apt/sources.list
Enter your password when prompted.

---

