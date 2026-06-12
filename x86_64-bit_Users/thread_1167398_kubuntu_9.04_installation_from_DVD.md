---
title: "kubuntu 9.04 installation from DVD"
date: 2009-05-22
forum: x86 64-bit Users
---

### Post by OldAlgis on 2009-05-22
Hi,

I've just installed kubuntu9.04 from a 4.3 GB kubuntu 9.04 amd_64 DVD on a laptop with an Intel 64 bit Celeron processor. The installation seemed to go without any problems, the systems "works", the (for me unfamiliar) KDE 4 desktop is displayed at 1280x800 and 60 Hz refresh rate.  The laptop is an Acer Aspire 5315 model. 

Usually I am openSUSE user, but on the laptop I switched to ubuntu, now kubuntu, because of the much superior support for laptop cooling fan and screen brightness controls. 

I am surprised that in spite of 4.3 GB installation media, synaptic or some other package installer is NOT installed by default.  Nor is the apt-get install <xyz> functional, though apt is installed.  It would seem that the repositories for apt are not installed.  I would not mind doing the apt configuration by CLI, if I knew how to, but I have been spoiled by the availability of GUI tools on openSUSE - everything can be done by yast.  

I like ubuntu/kubuntu, with preference to the kubuntu.  Do not want to ditch it just because the installation looks dodgy.  Could I get some advice how to configure the repositories for apt using the CLI, please?  Any other suggestions would be most welcome.

Thank you in anticipation - I know how helpful your forums have been in the past.

OldAl.

---

### Post by becho on 2009-05-23
Are you sure you are running Kubuntu. Last i checked they don't have a dvd iso to download. Maybe you purchased a Kubuntu DVD or did you download it?

---

### Post by Yellow Pasque on 2009-05-23
So what happens when you try to use apt-get install?
```
sudo apt-get install <some package>
```

Also, do you have the repositories in your sources?
```
cat /etc/apt/sources.list
```

---

### Post by tabibito on 2009-05-23
You could use KPackageKit if you want to manage your repositories the GUI way. It's accessible from System-->KPackageKit.

---

### Post by OldAlgis on 2009-05-23
> **becho said:**
> Are you sure you are running Kubuntu. Last i checked they don't have a dvd iso to download. Maybe you purchased a Kubuntu DVD or did you download it?

Yes, it is a kubuntu-9.04-dvd-amd64.iso, downloaded from a reputable mirror in Australia (internode), 9.3 GB,

Thanks for your interest, becho.

---

### Post by OldAlgis on 2009-05-23
> **Temüjin said:**
> So what happens when you try to use apt-get install?
```
sudo apt-get install <some package>
```

Also, do you have the repositories in your sources?
```
cat /etc/apt/sources.list
```

1. apg-get install <some package> returns "<some package> not found."

2. sudo ls /etc/sourc*  tells me "no such file".

So apt program is installed, but not configured...

Temüjin, Thank you!  I gather that kubuntu should have installed and configure apt.  It is possible that Celeron 64 bit is not compatible with the amd-64 OS?  That is most likely explanation.

---

### Post by OldAlgis on 2009-05-23
> **tabibito said:**
> You could use KPackageKit if you want to manage your repositories the GUI way. It's accessible from System-->KPackageKit.

Thanks for the suggestion, tabibito.  I think that Synaptic would do the trick, if it was installed.  

This whole installation looks very suspicious to me, Perhaps I should try 32 bit CD - I am in the process of downloading it from internode mirror on another PC.  Should I be able to access Systen --> KPackageKit by anonymous ftp /  http?

Thanks again,

---

### Post by Yellow Pasque on 2009-05-23
Post the output of this command:
> cat /etc/apt/sources.list

---

### Post by OldAlgis on 2009-05-24
> **Temüjin said:**
> Post the output of this command cat /etc/apt/sources.list:
```

ak@amd64:~> cat /etc/apt/sources.list
cat: /etc/apt/sources.list: No such file or directory
ak@amd64:~>

```

The file simply does not exist - ergo the apt is not configured...

Thanks, Temüjin!

---

