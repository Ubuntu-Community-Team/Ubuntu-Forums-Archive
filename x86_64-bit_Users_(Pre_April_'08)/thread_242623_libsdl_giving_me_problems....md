---
title: "libsdl giving me problems..."
date: 2006-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chrono86 on 2006-08-23
Hey guys~
Been trying to compile Zsnes on my amd64 system. It tells me about how libsdl 1.2 files aren't there, so when I try to install it it gives me this error message 

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev

I've tried manually installing those in the package manager but it tells me they're dependant on something else, and THOSE are dependant on something else, and so on in a never endling line of dependancies.

This is what keeps me from permenatley switching to linux everytime I've tried it over the past 4 years. Dependances, dependancies, dependancies...always a problem for me. It's one of the few cool things Windows does better...it says 'hey, you don't have this required file? well let me include it in the installation, or point you where to download it!'...Linux doesn't seem to work this way.

Anyways sorry about the rant but does anybody know what I can't seem to install the dev files for libsdl?

Thanks
Adam

---

### Post by RAOF on 2006-08-24
You probably should post your /etc/apt/sources.list file here.  You're probably either:
1) missing one of the dapper-updates repositories, and one of the dependent packages depends on something in there, or
2) have some crazy debian repository in there, and the dependencies of the package from there can't be met by Ubuntu packages.

**I** have libsdl1.2-dev installed from the repositories just fine.

---

### Post by Chrono86 on 2006-08-24
Thanks...I got it installed!

---

