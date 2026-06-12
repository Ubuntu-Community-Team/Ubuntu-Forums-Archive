---
title: "Error: Dependency is not satisfiable: amule-common (= 2.1.0-1ubuntu1)"
date: 2009-08-21
forum: x86 64-bit Users
---

### Post by sprilutsky on 2009-08-21
Installing amule client

Running UE 2.3 on Intel Pentium 4 Duo core

Was trying to install amule_2.1.0-1ubuntu1_amd64.deb client

1.first got an error that need to install libcrypto++5.2c2a_5.2.1c2a-2_amd64.deb
    Installed it - no problem

2. Installing amule_2.1.0-1ubuntu1_amd64.deb client - still getting the error:
    Error: Dependency is not satisfiable: amule-common (= 2.1.0-1ubuntu1)

If someone already ran into that, can you provide the work around or feedback how to go around this problem

---

### Post by jwaffolter on 2009-08-22
in a terminal
sudo apt-get install amule-common

---

### Post by Yellow Pasque on 2009-08-23
That's an old version of amule. Just install amule from Synaptic, or download appropriate packages here: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=amule](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=amule)

---

