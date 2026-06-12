---
title: "How do I - Install new versions of software in Gutsy."
date: 2009-02-17
forum: x86 64-bit Users
---

### Post by u-slayer on 2009-02-17
I'm using gutsy 64-bit and want to upgrade VLC to the latest version. I tried adding the backports repository: 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main universe multiverse restricted 
but that didn't give me a new version of vlc. 

I tried clicking on the deb here: [http://packages.ubuntu.com/intrepid/amd64/vlc](http://packages.ubuntu.com/intrepid/amd64/vlc), but It says that it "conflicts with the package vlc-nox"

Isn't there an easy way to upgrade software with installing a whole new Operating System?

---

### Post by jet2230 on 2009-02-17
> **u-slayer said:**
> 
I tried clicking on the deb here: [http://packages.ubuntu.com/intrepid/amd64/vlc](http://packages.ubuntu.com/intrepid/amd64/vlc), but It says that it "conflicts with the package vlc-nox"


have you tried: sudo apt-get --purge vlc-nox

before installing the deb?

---

### Post by u-slayer on 2009-02-17
I tried it and I get:

Error: Dependency is not satisfiable: vlc-nox when I try to install the 0.94 deb.

---

### Post by dcstar on 2009-02-21
> **u-slayer said:**
> I tried it and I get:

Error: Dependency is not satisfiable: vlc-nox when I try to install the 0.94 deb.

You just cannot install some packages from future versions because they can have a multitude of dependencies that you cannot fix.

You can try and compile the new version from source, but it is possible that the new version will also have dependencies that are not available for your platform.

---

### Post by mikewhatever on 2009-02-21
The particular program you want, VLC, had swiched from gtk to qt4, which is probably why it's hard to install. Also note, that Intrepid has 0.9.4 version, which isn't the latest available. I think it's time to consider an upgrade or reinstall, since Gutsy is reaching it's end of life in April this year.

---

### Post by Yellow Pasque on 2009-02-21
If you don't want to do a complete reinstall, you could just upgrade to hardy and use this PPA: 
[https://launchpad.net/~c-korn/+archive/ppa](https://launchpad.net/~c-korn/+archive/ppa)

As noted, Canonical will stop supporting all updates (including critical/security) for Gutsy in april. Hardy is an LTS release, and is supported until 4/2011

---

