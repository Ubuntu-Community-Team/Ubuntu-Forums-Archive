---
title: "Help... Update no avaliable"
date: 2008-05-08
forum: x86 64-bit Users
---

### Post by Bookmaster on 2008-05-08
Hi all. I did something with my Ubntu and now cannot install any update.

Here is what I'm getting.

What can I do to solve my problem please?

---

### Post by joselin on 2008-05-08
Post here your /etc/apt/sources.list or try to check it. The problem is there.

Regards

---

### Post by Bookmaster on 2008-05-08
What is wrong please?

---

### Post by kuja on 2008-05-08
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted 

deb http://rs.archive.ubuntu.com/ubuntu/ gutsy main restricted 
deb-src http://rs.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

deb http://rs.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://rs.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

deb http://rs.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse 
deb-src http://rs.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse 

deb http://archive.canonical.com/ubuntu gutsy partner 
deb-src http://archive.canonical.com/ubuntu gutsy partner 

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

#Not sure that you need these two, especially the former, seeing as gutsy proposed is basically
#experimental packages 

#deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
#deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse 

#leaving this one uncommented beause I'm not 100% why it's there, though I can't really
#recommend trying to install debian debs in ubuntu because of dependency issues
deb http://ftp.debian.org etch main
```

---

### Post by joselin on 2008-05-08
Sorry, but i'm at work and can't read odt files. Could you please post it in plain text?

---

### Post by Bookmaster on 2008-05-08
Here is sourcelist as text file.

---

### Post by Yellow Pasque on 2008-05-08
I fixed it. Download the attached file to your desktop and open a terminal.
```
sudo mv ~/Desktop/Fixed.txt /etc/apt/sources.list
```

---

### Post by Bookmaster on 2008-05-09
> **Temüjin said:**
> I fixed it. Download the attached file to your desktop and open a terminal.
```
sudo mv ~/Desktop/Fixed.txt /etc/apt/sources.list
```

Still cannot update my Ubuntu :(

Here is what I'm getting.

---

### Post by Yellow Pasque on 2008-05-09
```
cd /etc/apt
ls
ls apt.conf.d
```

---

### Post by Bookmaster on 2008-05-09
I'm still getting same msg without any possibility of update

---

### Post by Bookmaster on 2008-05-14
Solved

---

### Post by Clancy_s on 2008-05-14
Would you care to share the solution, in case someone else gets the same problem?

---

