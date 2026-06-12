---
title: "acrobat reader installation problem . (Possibly) unsatisfiable dependency"
date: 2009-05-26
forum: x86 64-bit Users
---

### Post by bappy004 on 2009-05-26
I downloaded the "acroread_8.1.3-0medibuntu0.8.10.2_amd64.deb" package found in the medibuntu repositories. but when i tried to install it, it said "Error: Dependency is not satisfiable: acroread-debian-files (>= 0.0.24medibuntu1.1)".

Next, I tried to install "acroread-debian-files_0.0.29medibuntu2_amd64.deb", it said, "Error: Dependency is not satisfiable: acroread (>= 8.1.3)"

:((

what sort of dependency is that? "Acroread" depending on "acroread-debian-files" and "acroread-debian-files" depending on "Acroread" for installation !!!!

which one to install first?
please help me out of this dillema

---

### Post by oldos2er on 2009-05-26
Do you have Medibuntu enabled in your sources.list? Here's how: [http://help.ubuntu.com/community/Medibuntu](http://help.ubuntu.com/community/Medibuntu)

---

### Post by bappy004 on 2009-05-27
Actually, I have a very slow internet connection in my home(~12KBps). so i downloaded those .deb packages of acroread from the home of one of my friends whose speed is good( the acroread pacakges are about 40MB in size i think). but what to do!!! i think i shall have to download with my slow conn  at last :(

---

### Post by Yellow Pasque on 2009-05-27
Install them at the same time:
```
sudo dpkg -i acroread_8.1.3-0medibuntu0.8.10.2_amd64.deb acroread-debian-files_0.0.29medibuntu2_amd64.deb
```

---

