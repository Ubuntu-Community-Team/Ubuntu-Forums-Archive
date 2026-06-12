---
title: "wine hell 20.04"
date: 2021-03-17
forum: Wine
---

### Post by cmcanulty on 2021-03-17
I got a new laptop and have spent all day following various tutorials to install wine and every one gives errors and dependency problems. I have tried command line, synaptic, software app . Never was an issue before 20.04. I also followed the instructions here with same broken pkgs and dependency issues. Yet synaptic finds no broken pkgs.
[https://wiki.winehq.org/Ubuntu]("https://wiki.winehq.org/Ubuntu")
Also every time I try a new tutorial it removes chrome, skype and google earth!

---

### Post by CelticWarrior on 2021-03-17
I wonder what the problem or difficulty is with
```
sudo apt install wine
```

---

### Post by cmcanulty on 2021-03-17
I did that and then more errors

```
cmcanulty@DarcyTech:~$ wine
it looks like wine32 is missing, you should install it.
as root, please execute "apt-get install wine32"
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
cmcanulty@DarcyTech:~$ sudo apt-get install wine32
[sudo] password for cmcanulty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine32 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libwine
E: Package 'wine32' has no installation candidate
cmcanulty@DarcyTech:~$ ~$ sudo apt install libwine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libwine is already the newest version (5.0-3ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cmcanulty@DarcyTech:~$ wine
it looks like wine32 is missing, you should install it.
as root, please execute "apt-get install wine32"
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
cmcanulty@DarcyTech:~$ 

```

lots of google entries for these issues in 20.04 with wine but nothing works. This is an amd processor I wonder if that could cause an issue

---

### Post by HermanAB on 2021-03-18
Wine is a 32 bit program.  Ubuntu doesn’t do 32 bit by default anymore.  In my experience a virtual machine with Win7 works way better than Wine.

---

### Post by cmcanulty on 2021-03-18
I have 32 bit architecture installed. Are you actually saying wine won't work in 20.04? I have it installed o several 20.04 computers. I  am asking about a particular computer where it fails. Thank you.

---

### Post by CelticWarrior on 2021-03-18
Try purging the WineHQ PPA that you added probably for no good reason (as 99% of the users following the instructions you referenced) and then install it from the official Ubuntu repository (older version but always installs and works correctly). If you need a newer version then, instead of using the WineHQ PPA, install PlayOnLinux so you can manage different container with different Wine versions if it must be.

---

### Post by slickymaster on 2021-03-18
*Thread moved to **Wine**.*

---

