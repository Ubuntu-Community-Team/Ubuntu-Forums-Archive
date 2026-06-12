---
title: "Can't Upgrade to Gutsy"
date: 2007-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by theWrkncacnter on 2007-10-24
I've tried with the update manager, and with the alternate cd, but both times, the upgrader stalls on "Checking Package Manager"

I haven't heard anybody else complain about this, which leads me to believe that there's something wrong with some setting somewhere.

Any ideas?

---

### Post by ndihmo on 2007-10-24
Go to: Main Menu > System > Administration > Software Sources > Download From 

Select the Main Server and try again. 

If it wont help, go to a Terminal and type

```
sudo aptitude update
```

then 

```
sudo aptitude safe-upgrade
```

if you have any problem at the "sudo aptitude update" post you error here.

ndimo.

---

### Post by theWrkncacnter on 2007-10-24
well sudo aptitude update worked, but sudo aptitude safe-upgrade did not

$ sudo aptitude safe-upgrade
Unknown command "safe-upgrade"
aptitude 0.4.4

---

### Post by ndihmo on 2007-10-24
try $man aptitude and look what kind of an upgrade do you want to do.
I use Gutsy on a intel centrino notebook and I usually do $sudo aptitude full-upgrade

there are safe-upgrade and full-upgrade.

---

### Post by theWrkncacnter on 2007-10-24
aptitude doesn't have those options for me

---

