---
title: "Find Command"
date: 2006-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by confusimo on 2006-11-05
What happened to the Find Gui in Edgy like there used to be in DD?  The utility to search my hard drive for local files?

Thanks,
Confusimo

---

### Post by kuja on 2006-11-05
I'm not sure, why not install the gnome-find package?

---

### Post by confusimo on 2006-11-06
If I goto Synaptic all I see is "gnome-utils" and "findutils" which already claim to be installed.  Be I see them nowhere.

Thanks,
Confusimo

---

### Post by kuja on 2006-11-06
Interestingly enough, gnome-find is in the [universe repository](https://help.ubuntu.com/community/Repositories).

The locate command in the terminal works well also.

---

### Post by confusimo on 2006-11-06
I downloaded that from.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Funiverse%2Fg%2Fgnome-find%2Fgnome-find_1.0.2-1.1_amd64.deb&md5sum=72d17a56eeb73c75cc8271745fbcb4ab&arch=amd64&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Funiverse%2Fg%2Fgnome-find%2Fgnome-find_1.0.2-1.1_amd64.deb&md5sum=72d17a56eeb73c75cc8271745fbcb4ab&arch=amd64&type=main)

But it says 

Error: Dependency is not satisfiable: gdk-imlib1.

Thanks,
Confusimo

---

### Post by kuja on 2006-11-06
If you want to do it that way, rather than using apt, then you have to *tediously* download every single dependency, **one. by. one.** 

I recommend first enabling the universe repository, (see the link in my last post), and then using [insert apt frontend of choice here] to install it.

---

### Post by confusimo on 2006-11-06
I see nothing about enabling anything at that link.  And what I saw covered 6.06 not 6.10.

Thanks,
Confusimo

---

### Post by kuja on 2006-11-06
Sure it does, there should be three links on that page regarding "managing repositories". Click the one that seems pertinent to you.

Anyhow, the only difference between managing repositories in Edgy 6.10 and managing them in Dapper 6.06 is just that - whether you write in dapper or edgy on the line.

---

### Post by confusimo on 2006-11-06
Not exactly.  There is no X buntu mentioned either.  And I have no Kbuntu as of right now.

Anyway, if I use the first link.  It says Goto Administration and Software Properties.  In 6.10 I have no Software Porperties.  Ony Software Sources.  And that has no installation Media tab.  So that's 6.06 being covered, not 6.10.

Thanks,
Confusimo

---

### Post by kuja on 2006-11-06
If you can't figure out how to do it from the GUI, then you can't go wrong with [a terminal](https://help.ubuntu.com/community/Repositories/CommandLine).

---

