---
title: "Unable to install Wine on Ubuntu 16.04.1"
date: 2016-12-23
forum: Wine
---

### Post by garvind25 on 2016-12-23
Hi there,

  I wanted to install Wine on my Ubuntu desktop install. I did the following on my terminal: 

```
sudo apt-get install wine
```

I got the following message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libstdc++-5-dev : Depends: libstdc++6 (>= 5.4.0-6ubuntu1~16.04.4) but 5.4.0-6ubuntu1~16.04.1 is to be installed
 libstdc++6 : Depends: gcc-5-base (= 5.4.0-6ubuntu1~16.04.1) but 5.4.0-6ubuntu1~16.04.4 is to be installed
 wine : Depends: wine1.6 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

What should I do pls.  

Thanks,

Arvind Gupta

---

### Post by garvind25 on 2016-12-23
problem solved.... 

 I did 
sudo apt-get install -f

---

### Post by ajgreeny on 2016-12-23
Well done! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by tarpan67 on 2017-02-24
I had the same problem and "sudo apt-get install -f" did not help. I fixed the problem by changing the repo to the main Ubuntu server instead of the local one (Poland)...

---

