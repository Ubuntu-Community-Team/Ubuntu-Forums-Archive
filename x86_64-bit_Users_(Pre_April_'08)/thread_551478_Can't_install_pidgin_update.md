---
title: "Can't install pidgin update"
date: 2007-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by revchris on 2007-09-15
This is what I get after trying to install the 3 udpates (Gaim, Pidgin, Pidgin-data):

W: Failed to fetch [http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/libpurple0_2.2.0-0ubuntu1~upure64_amd64.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/libpurple0_2.2.0-0ubuntu1~upure64_amd64.deb)
  302 Found


W: Failed to fetch [http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/gaim_2.2.0-0ubuntu1~upure64_all.deb](http://janvitus.interfree.it/ubuntu/pool/feisty-upure64/main-amd64/gaim_2.2.0-0ubuntu1~upure64_all.deb)
  302 Found

---

### Post by dasunst3r on 2007-09-15
Try manually downloading the packages and putting them in a folder.  Then, open a terminal, navigate to the folder, and issue the command *sudo dpkg -i *.deb*.  Or, you can open them with GDebi and things will work too, although you'll experience a minute or two of dependency hell (hint: Install libpurple first).

---

### Post by revchris on 2007-09-15
that worked, Thanks!!!

---

