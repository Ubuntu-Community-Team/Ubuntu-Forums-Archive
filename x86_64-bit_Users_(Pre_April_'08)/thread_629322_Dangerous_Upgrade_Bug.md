---
title: "Dangerous Upgrade Bug"
date: 2007-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by bpazolli on 2007-12-02
Doing an automatic upgrade from my 64bit gutsy system I got an error message as such
```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
The process spits this message up every time I try to install anything using apt until I type in "sudo apt-get remove cupsys" which removes cupsys and thus the problem. By running "sudo apt-get install cupsys" I recieved the following dump
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  cupsys-bsd cupsys-driver-gutenprint cupsys-driver-gimpprint
  foomatic-filters-ppds xpdf-korean xpdf-japanese xpdf-chinese-traditional
  xpdf-chinese-simplified cups-pdf hplip
The following NEW packages will be installed:
  cupsys
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2033kB of archives.
After unpacking 11.4MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package cupsys.
(Reading database ... 94640 files and directories currently installed.)
Unpacking cupsys (from .../cupsys_1.3.2-1ubuntu7.1_amd64.deb) ...
Setting up cupsys (1.3.2-1ubuntu7.1) ..
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I have done "sudo apt-get clean" to remove the download files in case of a corrupted download, no help and I have gone through manually and tried to confirm each dependency, all of which seem fine, and done "apt-get update" after install as well.

Further note that when typing cupsys into terminal I get a command not found message, I don't know if this normal or not. I am starting to think this is an actual bug. I am this close to reinstalling linux, which is something I thought only had to be done in windows. I would like to know how I can download the pre-update download I have already tried the version here [http://packages.ubuntu.com/gutsy/net/cupsys](http://packages.ubuntu.com/gutsy/net/cupsys) to no luck, i.e. seems to be the same.

---

### Post by Mr_bleu on 2007-12-02
How is this DANGEROUS?

---

### Post by bpazolli on 2007-12-02
I have an upgrade that gets suggested to me in a bubble that makes my system virtually useless, explain to me how that is not dangerous. Now can you actually help me or are you just getting off topic. If its so innocent then tell me how to fix it[]

---

### Post by tgalati4 on 2007-12-02
It's not serious.  Your printing engine (cupsys) is broken.  Updates to the kernel will often break it.  Search the forums for cupsys and you will see lots of tips on how to repair.

You need to get into the details to fix it.  Installing and reinstalling sometimes fixes it, but you will have to go deeper.  Did you have any printers working before?

Try:

>sudo /etc/init.d/cupsys start

Describe the output of (in a Browser):

[http://localhost:631](http://localhost:631)

---

### Post by bpazolli on 2007-12-02
I did the step described above 
```
sudo /etc/init.d/cupsys start
```
And I got
```
 * Starting Common Unix Printing System: cupsd                           [ OK ] 
```
Which would suggest things running fine but I still get at the end of every apt-get command
```

Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bpazolli on 2007-12-02
I had a HP laserjet 1200 working before

---

### Post by bpazolli on 2007-12-03
I am going to have to reinstall the entire operating system if someone doesn't help me

---

### Post by Jouke74 on 2007-12-03
You have to force-reconfigure the packages. Just wait, will post these command later, I cannot do that from work now. You can also autoremove the whole cups, then reinstall.

---

### Post by Jouke74 on 2007-12-04
To fix broken packages:

1. Try to configure all packages that are not configured : 
sudo dpkg --configure -a

2. Try to let apt-get remove all problematic packages: 
sudo aptitude -f remove

3. Rerun this after running the command above: 
sudo dpkg --configure -a

4. To remove left-overs (dependencies) etc: 
sudo apt-get remove
sudo apt-get autoremove

5. Reinstall problematic package, and check if there are no dependencies which cannot be met.

---

### Post by cybergalvez on 2007-12-10
> **Jouke74 said:**
> To fix broken packages:

1. Try to configure all packages that are not configured : 
sudo dpkg --configure -a

2. Try to let apt-get remove all problematic packages: 
sudo aptitude -f remove

3. Rerun this after running the command above: 
sudo dpkg --configure -a

4. To remove left-overs (dependencies) etc: 
sudo apt-get remove
sudo apt-get autoremove

5. Reinstall problematic package, and check if there are no dependencies which cannot be met.

did this work for you?

---

### Post by Jouke74 on 2007-12-11
For me yes :-)

---

