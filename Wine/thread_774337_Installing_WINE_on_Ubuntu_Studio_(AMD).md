---
title: "Installing WINE on Ubuntu Studio (AMD)"
date: 2008-04-29
forum: Wine
---

### Post by petrafan007 on 2008-04-29
OK, I am at a complete loss here. I know what needs to be installed on this machine---

wine_0.9.60~winehq0~ubuntu~8.04-1ubuntu1_amd64.deb

when I try to install it, I get the following error:

Failed to install package "blah"

debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs
shellf buffer or without a controlling terminal.)
debconf: falling back to frontend: readline
Selecting previously deselected...etc

then another time i tried to run it...

dpkg:regarding (said filename) containing wine, pre-dependency problem
wine pre-depends on dpkg (>= 1.14.12ubuntu3)
dpkg is installed, but is version 1.14.5ubuntu16.
dpkg: error processing (said filename) (--install):
pre-dependency problem - not installing wine

Does this mean that wine does not work in the latest version of ubuntu studio or something?

Any help would be appreciated. Thanks!!!!

---

### Post by Jimmey on 2008-04-29
You should try using the version that's (probably) in the repositories - Would there be a problem with that?

sudo apt-get install wine

---

### Post by anuban on 2008-04-29
> **petrafan007 said:**
> OK, I am at a complete loss here. I know what needs to be installed on this machine---

wine_0.9.60~winehq0~ubuntu~8.04-1ubuntu1_amd64.deb

when I try to install it, I get the following error:

Failed to install package "blah"

debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs
shellf buffer or without a controlling terminal.)
debconf: falling back to frontend: readline
Selecting previously deselected...etc

then another time i tried to run it...

dpkg:regarding (said filename) containing wine, pre-dependency problem
wine pre-depends on dpkg (>= 1.14.12ubuntu3)
dpkg is installed, but is version 1.14.5ubuntu16.
dpkg: error processing (said filename) (--install):
pre-dependency problem - not installing wine

Does this mean that wine does not work in the latest version of ubuntu studio or something?

Any help would be appreciated. Thanks!!!!


Have you gone through the steps mentioned on Wine site about how to install latest wine on Ubuntu:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
Here is the link, read it carefully and follow the steps.  Just run the commands mentioned, you should be fine.
I got it without any problem on my Ubuntu Hardy installation.:)

---

