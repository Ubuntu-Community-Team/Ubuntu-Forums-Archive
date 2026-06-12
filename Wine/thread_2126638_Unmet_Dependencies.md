---
title: "Unmet Dependencies"
date: 2013-03-17
forum: Wine
---

### Post by ShaneRitz on 2013-03-17
I'm having a lot of trouble installing Wine 1.5.  It's listing these unmet dependencies when I try...

> The following packages have unmet dependencies:

wine1.5: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.5-amd64 (**= 1.5.25-0ubuntu1**) but **1.5.25-0ubuntu1** is to be installed
         Depends: wine1.5-i386 (= 1.5.25-0ubuntu1) but it is not going to be installed

Some of those don't even look like they make sense, especially the one I bolded. I've gone to Synaptic to see what I can do, but that doesn't accomplish much since everything is already upgraded. Anybody know anything else I can do?

---

