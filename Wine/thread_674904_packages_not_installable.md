---
title: "packages not installable?"
date: 2008-01-22
forum: Wine
---

### Post by secondstage on 2008-01-22
new to this ok at terminal

tried to get wine installed using the sticky "HowTo: Get The Latest Wine" from Cochise. Everything worked fine until i typed "sudo apt-get install wine" in terminal came back and read quote

john@john-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages
john@john-desktop:~$ 

if those packages are 'not installable' then what do i do?

---

### Post by stoneybroke on 2008-01-22
Best thing to do is use Synaptic Package Manager to install programs in System>administration>synaptic package manager

Just use the search button to search for wine and use that to install it o.k.

---

### Post by secondstage on 2008-01-22
tried and got this

edit: it says 
"wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: libaudio2  but it is not installable"

how do i make them installable?

---

### Post by thomasow on 2008-02-21
> **secondstage said:**
> tried and got this

edit: it says 
"wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: libaudio2  but it is not installable"

how do i make them installable?


Hello.  I to am new to Linux/Ubuntu, and when attempting to install Wine on 7.10 Gutsy, get the same error message as above.  Has anyone resolved this?  Any advice on what we might try?

---

### Post by thomasow on 2008-02-21
In another thread, the following solution was given:  Need to configure SPM to look at resources:

 Originally Posted by taurus  View Post
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark for all the lines except the last one, Source code, and Cdrom in the window below. Close it and press Refresh. Now, see if you can find wine from the Search field and install it from there. Otherwise, shutdown synaptic and install it with apt-get from a terminal again.

---

### Post by youngboipsl on 2008-10-04
thank you! its my first official day on ubuntu, you helped me too!

---

### Post by Dark9204 on 2008-10-04
Its you fist day using ubuntu and you are using 7.10? the newest is 8.04 and 8.10 should be finished at october the 30.

Can somebody answer me, why do people still use ubuntu 7.10, and why do some of then go as low as wine 0.9.20?

---

### Post by david_kt on 2008-10-04
> **secondstage said:**
> 
The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages
john@john-desktop:~$ 

if those packages are 'not installable' then what do i do?

First, try:

```
sudo apt-get update
sudo apt-get upgrade
```

and then try again:

```
sudo apt-get install wine
```

If still have same problem, try:

```
sudo apt-get install binfmt-support libaudio2
```

and post what the outpout of the terminal.

DK

---

