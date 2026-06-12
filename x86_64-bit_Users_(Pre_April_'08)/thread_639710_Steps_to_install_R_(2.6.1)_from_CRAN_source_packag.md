---
title: "Steps to install R (2.6.1) from CRAN source packages on AMD64"
date: 2007-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by mdmbkr on 2007-12-13
Hi,

I've encountered this scenario multiple times and I thought it may be helpful to some users to share step by step instructions.  The basic issue is that the CRAN repository of R packages for Ubuntu does not include amd64 builds.  Therefore R needs to be installed using source packages.  I realize this may seem trivial to some users but for others it may help!

Note: I don't know how this will behave if any R packages are already installed.

0a) add the CRAN SOURCE repository to /etc/apt/sources.list.  Example:

```

deb-src http://cran.r-project.org/bin/linux/ubuntu feisty/

```

0b) Use GPG to tell apt about CRAN's keys, to avoid the following error: "The following signatures couldn't be verified because the public key is not available".  For more details see here: [http://cran.r-project.org/bin/linux/ubuntu/README](http://cran.r-project.org/bin/linux/ubuntu/README)

```

gpg --keyserver subkeys.pgp.net --recv-key E2A11821
gpg -a --export E2A11821 | sudo apt-key add -

```

0c) ```
apt-get update
```

1) Install (most of) the packages that will be required to compile the R source packages:

```
sudo apt-get build-dep r-base
```

2) I also had to install these to get the various r-cran-whatever packages to build properly:

```
sudo apt-get install dpatch cdbs libpaper-utils
```

3) Make a directory (i.e., ~/r-installation) and cd into it.

4) Download and compile the r-base package:

```

sudo apt-get -b source r-base

```

5) Install some of the resulting .deb files:

```

for pkg in r-base-core r-base-dev r-base-html r-base-latex r-doc-html r-doc-info r-doc-pdf r-mathlib ; do sudo dpkg -i $pkg*.deb ; done

```

6) Download, compile, and install these packages individually using the following loop (the order is important):

```

for pkg in r-cran-boot r-cran-cluster r-cran-foreign r-cran-vr r-cran-kernsmooth r-cran-lattice r-cran-mgcv r-cran-nlme r-cran-rcompgen r-cran-survival r-cran-rpart r-cran-codetools ; do apt-get -b source $pkg && sudo dpkg -i $pkg*.deb ; done

```

7) Now you can install the remaining .deb packages created in step 4:

```

for pkg in r-recommended r-base ; do sudo dpkg -i $pkg*.deb ; done

```

This entire process takes about 15 minutes for me.

Please say something if there's anything I've overlooked!

Additions thanks to 8rino and monkeyking.

---

### Post by monkeyking on 2008-01-03
Hi,
I need to sudo in step 4.
but nice guide.

---

### Post by incubus on 2008-01-29
mdmbkr,

Fantastic tutorial, thanks for caring to post your notes.  I was following it, but then halfway I noticed that now CRAN does have x86_64 packages.  I do remember that a little while back they didn't.

[http://cran.r-project.org/bin/linux/ubuntu/](http://cran.r-project.org/bin/linux/ubuntu/)

But still, your post is a great tutorial for building in general.

incubus

---

### Post by monkeyking on 2008-06-02
still works on ubuntu8.4 and R2.7.0

thanks again.

---

