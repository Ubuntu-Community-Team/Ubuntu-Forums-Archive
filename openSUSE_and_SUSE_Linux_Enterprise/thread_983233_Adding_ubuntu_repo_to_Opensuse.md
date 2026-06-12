---
title: "Adding ubuntu repo to Opensuse?"
date: 2008-11-15
forum: openSUSE and SUSE Linux Enterprise
---

### Post by kelinu on 2008-11-15
Hi guys,

Is it possible to add the Ubuntu repository to Yast (Opensuse)?  The Opensuse repo seems so small compared to that of ubuntu...

Any Help is Greatly appreciated.

Thanks.

Beef.

---

### Post by Neostar on 2008-11-15
Sorry but this is not possible as Ubuntu uses a completely different packaging system.

OpenSUSE uses RPM

Ubuntu uses DEB

And besides when you choose a Linux distro you need to stick to that distro's repo, otherwise you will end up with a broken system.

---

### Post by kelinu on 2008-11-15
aah damn, i really hoped I could do this one. STill thanks for the reply.  I wanna install Frets on Fire but dont wanna go thruogh the painstaking process of compiling etc.

---

### Post by 67GTA on 2008-11-15
Open Yast and go to Software Repositories. In the bottom left corner is an "ADD" button. This is for adding repos in Opensuse. There are a number of community repos that once added will put Opensuse just shy of the number of packages for Debian/Opensuse. Frets on Fire is in the Buildservice-Games repo. Add it and any other categories you might be interested in and then refresh your repos. You can also turn off auto refresh for each repo when the Yast package manager opens(very annoying) by unchecking the "Automatically Refresh" box for each repo. The quickst and easiest way to refresh the repos is the command line. Opensuse uses zypper which is the backend for Yast package management just like apt is for Ubuntu/Synaptic. 

Update: sudo zypper up 
Refresh repos: sudo zypper ref

There is more info on zypper usage here: [http://en.opensuse.org/Zypper/Usage](http://en.opensuse.org/Zypper/Usage)

Another option is to use the "One Click Install". Just choose your version and search for packages. If you find what you need, then click the install button and it will open Yast and install for you. [http://packages.opensuse-community.org/](http://packages.opensuse-community.org/)

---

