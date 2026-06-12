---
title: "How can I install i386 deb files on amd64 ubuntu server edition ?"
date: 2009-08-24
forum: x86 64-bit Users
---

### Post by doeki on 2009-08-24
I have an amd64 ubuntu 9.04 server.

Although I want to use it as a print server, I couldn't find any driver of my printer, Canon lbp 3200.

There're deb files only for i386 on the official site !!! :(

[http://software.canon-europe.com/software/0031118.asp]("http://software.canon-europe.com/software/0031118.asp")

Please, Help me !!

---

### Post by Sam Lars on 2009-08-25
Use the dpkg to install it...
```
dpkg --force-architecture -i package.deb
```

---

### Post by stanca on 2009-08-29
Or:
```
sudo dpkg -i --force-all package_name.deb
```

---

