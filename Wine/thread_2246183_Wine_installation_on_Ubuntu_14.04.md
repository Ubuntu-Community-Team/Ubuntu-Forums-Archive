---
title: "Wine installation on Ubuntu 14.04"
date: 2014-09-29
forum: Wine
---

### Post by minerbog on 2014-09-29
Hi,

About a month ago I upgraded from 12.04 LTS to 14.04 LTS and all is good. Except...

Yesterday I tried to launch one of my wine apps and it just wouldn't work. Hmmm? I thought. On much digging I discovered that wine was no longer installed so I tried to install it in the normal manner. Here's where the problems start!

Wine just will not install. It says 1.7 depends on 1.6. Then 1.6 depends on 1.5 etc etc. It also says there is broken dependencies which I just cannot fix in the normal ways IE. ```
apt-get install -f

aptitude install wine
```

All I get is this 
```
sudo apt-get purge wine

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'wine' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

sudo apt-get -f install wine

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Please help, I'm just lost now!!

Gavin.

---

### Post by kc1di on 2014-09-29
I can't really think of why your getting those messages.  Wine version are normally independent of each other and I've never run into that problem.
That being said I suspect the problem may be something left over from 12.04 that didn't get properly updated or removed.

I would try this.
```
sudo apt-get purge wine
```
```
sudo apt-get autoremove
```
```
sudo apt-get install wine
```

---

### Post by minerbog on 2014-09-30
Dave

---

### Post by minerbog on 2014-09-30
Hi Dave,

Here the responses....
```
sudo apt-get purge wine
[sudo] password for gavin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'wine' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

```
sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


I just don't know where to go from here??

Gavin.

---

### Post by mastablasta on 2014-09-30
interesting. open synaptic and search for wine packages. try to repair them. how did you install wine before? 

Check the software sources list (in software center) see if any PPA or something from 12.04 is still active.  if active then disable and try again.

how about if you install playonlinux which is made to run several wine version next to eachother.
or try a manual wine install.

---

### Post by minerbog on 2014-10-01
To be honest I cannot remember how I install it originally as it was done back on 10 or even lower!! It would probably of been ```
sudo apt-get install wine
``` as I'm not a big fan of Synaptic.

> **mastablasta said:**
> 
Check the software sources list (in software center) see if any PPA or something from 12.04 is still active.  if active then disable and try again.


I have checked all the PPA's and they are all set to use the trusty versions so I assume they're ok.

Gavin.

---

### Post by minerbog on 2014-10-01
Just an update. In Synaptic when I try and fix broken packages I get this...

```

E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```

However, I cannot find any held packages!

---

### Post by minerbog on 2014-10-02
Just to update you all I have fixed the problem.

It turned out to be the library libjson-c2 was still the precise version. I just force it to use the trusty version, updated and wine install with no problem.

Thanks for all your advice guys.

Gavin.

---

### Post by mvdk2 on 2015-06-22
> **minerbog said:**
> Just to update you all I have fixed the problem.

It turned out to be the library libjson-c2 was still the precise version. I just force it to use the trusty version, updated and wine install with no problem.

Thanks for all your advice guys.

Gavin.

Thank you for sharing your success. 
I am in the same position by wrongly installing Wine in the amd64 edition on a PC which is not an AMD 64. 
Now I am unable to install the correct Wine in my 14.04. Same kind of messages as described above. 

Could you inform me what you mean by: **I just force it** **to use the trusty version** - What should I do?

Mart

---

