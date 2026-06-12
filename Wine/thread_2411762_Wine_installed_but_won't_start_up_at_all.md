---
title: "Wine installed but won't start up at all"
date: 2019-02-03
forum: Wine
---

### Post by neil40 on 2019-02-03
Wine will not run for me. Can anyone help please? Googling around for ages leads me to believe that I am doing everything correctly but of course I cannot be sure so I'd appreciate help in getting it working please.

wine ADE_4.5_Installer.exe

Command 'wine' not found, but can be installed with:

sudo apt install wine-development
sudo apt install wine-stable     

It is installed as this command reveals (I think)

 sudo apt-get install wine-stable

Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine-stable is already the newest version (4.0~bionic).

This are my version details

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

---

### Post by Dennis N on 2019-02-03
Restart computer. Then try **wine --help**

You should see something like this:

```
[dmn@Roxanne ~]$ wine --help
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit

```

Did that work?

---

### Post by neil40 on 2019-02-03
No I am afraid it didn't. This is what I get
wine --help

Command 'wine' not found, but can be installed with:

sudo apt install wine-development
sudo apt install wine-stable

---

