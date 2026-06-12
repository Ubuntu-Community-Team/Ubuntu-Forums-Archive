---
title: "pixmap engine on Hardy amd64"
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by sidrit on 2008-05-01
hey guys.
a couple of days ago i upgraded to hardy , transition wich went smooth enough.

the issue is that now that i found the time to do some visual customizations
i found out that there is no gtk-engines-pixmap package for hardy-

out of curiosity i tried the gutsy package which complains that it can't find libglib1.2.

this one can't be installed from synaptics that suggests the installation of
libglib1.2ldbl instead- lib which i have already installed and upgraded-

anyone hit this issue yet?

thanks in advance.
sid

---

### Post by sidrit on 2008-05-05
*bump*
nobody? :confused:

---

### Post by Cappy on 2008-05-05
Change to the directory of the deb in the console and use
```
sudo dpkg -i --force-all gtk-engines-pixmap_0.12-8.1_amd64.deb
```
replacing "gtk-engines-pixmap_0.12-8.1_amd64.deb" with the actual filename.

Here's the link again if you need it:
[http://mirrors.kernel.org/ubuntu/pool/universe/g/gtk-engines/gtk-engines-pixmap_0.12-8.1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gtk-engines/gtk-engines-pixmap_0.12-8.1_amd64.deb)

---

### Post by sidrit on 2008-05-05
Thank you for the reply cappy.
So, i got the deb and forced it to install.

Installed a couple of themes which required that engine, but it still seems to not affect anything-

On top of this i should mention that synaptics perpetually complains of broken dependencies.

When issuing a fix command i get: 


```

sid@dev:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  gtk-engines-pixmap
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 840kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


```


Still a no go for me. :(

---

### Post by Tom Mann on 2008-05-06
Have you tried typing

apt-get install gtk-engines-pixmap

now that it's installed, it should set itself in the db as manually installed, and should stop trying to remove itself.

---

