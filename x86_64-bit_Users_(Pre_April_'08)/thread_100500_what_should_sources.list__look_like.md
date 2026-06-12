---
title: "what should sources.list  look like?"
date: 2005-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by joepotter on 2005-12-07
I am confused.

It looks like a 64 bit install leaves one with the exact same repositories as a 32 bit install.

What should the sources.list look like, and is it 64 bit software?

Thanks.

---

### Post by aysiu on 2005-12-07
It's the same sources.list for all versions.

---

### Post by joepotter on 2005-12-08
[QUOTE=aysiu]It's the same sources.list for all versions.[/QUOTE]



If it is the same sources.list, then you should get the same binaries. That means that only the kernel is 64 bit, but all else is 32 bit.

This can not be right. I must be missing something here. But what?

---

### Post by Suger on 2005-12-08
Well no, a source compiled with a 64 bits compiler won't give the same binary as the same source compiled with a 32 bits compiler.

---

### Post by joepotter on 2005-12-08
[QUOTE=Suger]Well no, a source compiled with a 64 bits compiler won't give the same binary as the same source compiled with a 32 bits compiler.[/QUOTE]



The sources.list refers to /etc/apt/sources.list which is a file that tells apt where to go to get the binaries from a repository. If the repositories are the same with a default install of Breezy or Breezy-64-bit than something is odd.

We are *not* talking about compiling from source.

---

### Post by kaffeine on 2005-12-08
yes, the default deb packages in your repos are 32-bit, and AFAIK there is no official amd64 repo for ubuntu/debian. one way to do it is to use deb-src (which would be in your default sources.list) to get the source and build it yourself on the amd64 kernel. there are quite a few unofficial (and hence  incomplete) amd64 repos, the one i know is 

deb [http://lukeplant.me.uk/debian](http://lukeplant.me.uk/debian) ./
deb-src [http://lukeplant.me.uk/debian](http://lukeplant.me.uk/debian) ./

but there may be better and bigger ones...if you know of any, pls post - let's use this thread to build a list!

---

### Post by RAOF on 2005-12-08
As Aysiu said, the sources.list will look the same for **every** architecture.  This includes the Mac/PPC.  This is because apt-get automatically includes the architecure in the packages it shows.  (This is what you're missing, joepotter ;) )

Everything you get through apt is a 64bit binary.  With the specific exceptions of: OpenOffice, & the ia32-lib-* packages to support it.  There's no need to break your ubuntu by adding extra repositories, or compiling everything from deb-src.  Everything that can be 64bit already is.

---

### Post by joepotter on 2005-12-09
[QUOTE=RAOF]As Aysiu said, the sources.list will look the same for **every** architecture.  This includes the Mac/PPC.  This is because apt-get automatically includes the architecure in the packages it shows.  (This is what you're missing, joepotter ;) )

Everything you get through apt is a 64bit binary.  With the specific exceptions of: OpenOffice, & the ia32-lib-* packages to support it.  There's no need to break your ubuntu by adding extra repositories, or compiling everything from deb-src.  Everything that can be 64bit already is.[/QUOTE]


You are saying that apt will see 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted


in the sources.list and go the repository. Then apt will ask for *only* 64 bit apps somehow on one of the boxen I own, but not on the others that has exactly the same entry in /etc/apt/sources.

Hmmmm. I am having a little trouble seeing how apt can do this voodo. Are all apps for all architectures sitting in the repository? How does apt know to ask for the correct one if all are sitting in the *same* repository.

On a side note --- why have different repositories if apt is so smart?

---

### Post by BoyOfDestiny on 2005-12-09
[QUOTE=joepotter]You are saying that apt will see 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted


in the sources.list and go the repository. Then apt will ask for *only* 64 bit apps somehow on one of the boxen I own, but not on the others that has exactly the same entry in /etc/apt/sources.

Hmmmm. I am having a little trouble seeing how apt can do this voodo. Are all apps for all architectures sitting in the repository? How does apt know to ask for the correct one if all are sitting in the *same* repository.

On a side note --- why have different repositories if apt is so smart?[/QUOTE]

Well different repo's carry different software. 
Go for what aysiu showed. I'm not sure why you aren't grasping this. 
Try this analogy, there is a car dealership (with a lot with minivans and a lot with cars). If someone goes and buys a minivan and someone else buys a car... How can they get something different at the same place? As far as I can tell, this seems to be what you are asking.

Anyway, I may be totally off here, so here are some links to take a look at:

[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

[http://www.debian-administration.org/articles/286](http://www.debian-administration.org/articles/286)

This might give you some insight into how it works... I'm pretty sure Ubuntu just has things pooled together (this is a guess), since a lot of the source and docs across platforms are almost the same...

---

### Post by bonzodog on 2005-12-10
if you were to look at the structure of a .deb package filename, you will notice it includes the arch in it. Apt-get is very clever and will only show you packages with your arch in them.

---

