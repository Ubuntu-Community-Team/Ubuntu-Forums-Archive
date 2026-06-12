---
title: "Wine won't install"
date: 2008-06-28
forum: Wine
---

### Post by chroncile on 2008-06-28
I was using Ubuntu 7.04, but then I upgraded to 7.10 and now wine won't work so I removed it and tried installing it, but it shows an error:

```

wine:
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed

```

Please help, I want to install wine so badly :(

---

### Post by Victormd on 2008-06-28
have you tried uninstalling and re-installing wine?
```
sudo apt-get remove wine
```
then
```
sudo apt-get install wine
```

---

### Post by chroncile on 2008-06-28
Yeah, and I tried deleting the folder from my home folder, but it still didn't work. :(

---

### Post by Victormd on 2008-06-28
Why did you upgrade to gutsy? Didn't you want to try hardy?

The error you're getting is because it's trying to use libraries related to 7.04 that have been upgraded in 7.10.

Ok then, uninstall wine
```
sudo apt-get autoremove wine
```
then do a bit of cleaning:
```
sudo apt-get autoremove
```
```
sudo apt-get clean
```
Remove all wine related folders:
```
sudo rm -r ~/.wine
```
```
sudo rm -r ~/.local/share/applications/wine
```
and download the latest version of wine from [here]("http://wine.budgetdedicated.com/archive/index.html").
If you're using the 32 bit version, download the "Wine 1.0 i386" deb file. Once you've downloaded it, double click to install. It will tell you that there is an older version in the repositories and ask if you want to install anyway, click ok to continue...

---

### Post by chroncile on 2008-06-28
I didn't have a choice, I was running 7.04 and I did want to upgrade to hardy, but there was no option for it before, but there is now, I think I'm going to upgrade to hardy, but not now. I'll do it at night when I'm sleeping. :D

---

### Post by chroncile on 2008-06-28
Oh wait, that worked, thank you very much. You are a very kind and generous person :)

---

### Post by Victormd on 2008-06-28
it worked? Great, glad I could help!!! :)

A note on the hardy update... don't do it via update manager... well, that seems a bit harsh but yeah, don't... or don't say I didn't warn you... :)
It's best to do a fresh install of Hardy. There have been a lot of complaints from people who updated via update manager and hardware not working... but after a fresh install, everything worked fine.

---

### Post by chroncile on 2008-06-28
But I don't want to do that :(
I have installed so many applications, well not that many, but it's hard to install them and I don't want to do it again! :popcorn:

---

### Post by Victormd on 2008-06-28
Hehehehe... if gutsy is working for you, then keep it, when I had it, I loved it. I upgraded simply because I wanted to see what hardy was all about, and I must say, it's very nice and everything works very well for me... :)

I definetly would not recommend updating via update manager...

---

