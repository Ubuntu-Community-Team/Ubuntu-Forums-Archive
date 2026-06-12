---
title: "Can't install Wine on Ubuntu LTS 16.04"
date: 2017-06-14
forum: Wine
---

### Post by auran2 on 2017-06-14
Hi, I'm Auran. I've been an Ubuntu user for about a year and 2 months by now, and I'm having trouble installling Wine on my system.
Here's the Terminal output when I type "sudo apt-get install wine"

auran@Auran-Ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 or
                 wine1.8 but it is not installable or
                 wine2.0 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


What can I do to solve this?

---

### Post by kc1di on 2017-06-14
You can try these commands:
```
sudo dpkg --configure -a
```
```
sudo apt-get autoclean
```
```
sudo apt-get clean
```

see if that helps.

---

### Post by auran2 on 2017-06-15
> **kc1di said:**
> You can try these commands:
```
sudo dpkg --configure -a
```
```
sudo apt-get autoclean
```
```
sudo apt-get clean
```

see if that helps.

Hi kc1di, I tried doing all of those commands on my terminal, followed by another failed attempt, here's the terminal output:

```
auran@Gabriel-Ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 or
                 wine1.8 but it is not installable or
                 wine2.0 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Any other solutions?

---

### Post by kc1di on 2017-06-15
Ok let try it this way 
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get purge wine*
sudo apt-get install -f
```

If that does not work install playonlinux and you can choose which wine version it uses.

---

### Post by deadflowr on 2017-06-15
Also, it helps if you post the output from the commands asked, so that others may lend some insight about what may or may not be going on.

---

### Post by sccman on 2017-06-15
Have you tried the WineHQ page for installing Wine on Ubuntu?

Try the link below:

[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

---

