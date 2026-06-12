---
title: "libc header files"
date: 2007-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by OldAlgis on 2007-06-30
In the past I used SUSE, but on a new amd 64 PC the only distro that works reliably is ubuntu/kubuntu 7.04.  So I have installed kubuntu 7.04 as my main distro on this computer.  My PC has a NVIDIA chipset motherboard (Gigabyte GA-M61P-S3). It all works fine, but at this stage I can not get better resolution than 1024x768.  

To remedy this I want to install a new NVIDIA driver, which I have downloaded.  When I issue the command:

sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run

after a few introductory questions, the server responds with the following message:

"You do not appear to have libc header files installed in your system.  Please install distribution's libc development package".

As I am not familiar as yet with details of "apt", I can not determine what package I should install.  I am stumped!  

I have looked at other questions, which are mainly concerned with version 6 ubuntu.  It does not help as no equivalent packages seem to exist for version 7.

I would appreciate if somebody could tell me:
1. What packages I should install
2. Where can I find information about it, so I do not have to ask in future.

I will be most grateful for any and all suggestions.

---

### Post by Stephen Howard on 2007-06-30
I don't run 64bit, so its a bit of a guess, but I think the likely package is:  [FONT="Fixedsys"]libc6-dev-amd64[/FONT]

Do the following from a command line:

```
[FONT="Fixedsys"]sudo apt-get install build-essential[/FONT]
```

The above command installs a bunch of software you'll need for compiling drivers etc.  It should install the libc6-dev-amd64 package, but if you still get the error message, then do the following to install the libc6 libraries:

```
[FONT="Fixedsys"]sudo apt-get install libc6-dev-amd64[/FONT]
```

---

### Post by Stephen Howard on 2007-06-30
> Where can I find information about it, so I do not have to ask in future.

The man[ual] command is always useful:

```
man apt-get
```

---

### Post by Mongoose on 2007-06-30
There are also GUI tools like synaptic which have context and package search.  I suggest looking into that as well.  I've used Debian for years, but sometimes I perfer to use synaptic if I'm searching for something and I don't know its package name.  Sure beats greping apt-cache output.  That said if something breaks you'll want to know apt and dpkg utils at least.  

You should look at the synaptic repository settings and make sure you have universe, etc enabled for the most packages.  ^^

---

### Post by OldAlgis on 2007-06-30
> **Stephen Howard said:**
> I don't run 64bit, so its a bit of a guess, but I think the likely package is:  [FONT="Fixedsys"]libc6-dev-amd64[/FONT]

Do the following from a command line:

```
[FONT="Fixedsys"]sudo apt-get install build-essential[/FONT]
```

Thank you for the above command, which did the trick and enabled the installation of the NVIDIA drivers.

That the NVIDIA drivers turned out not to be very useful, is another story... Anyway, I was able to get a 1280 x 1024 screen  - and that was the object of this exercise.

Thanks to all who replied - all replies were useful, but the main "thank you" goes to Stephen Howard - his information gave all that I needed!

Thank you all,

Al.

---

### Post by Chucky5150 on 2007-07-01
Awesome!

The very first post that I read is just what I was looking for. Oh and it fixed my problem!


Search FTW :popcorn:

---

### Post by adolfo158 on 2007-07-10
[SIZE="3"][SIZE="4"]
Hi, I have the same problem with the same driver as above y tried the option given but I received answer of "not found":

adolfo@gaia2:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

adolfo@gaia2:~$ sudo apt-get install libc6-dev-amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libc6-dev-amd64
adolfo@gaia2:~$ 


any help would be much appreciated,

Adolfo[/SIZE][/SIZE]

---

### Post by jespdj on 2007-07-11
That is strange, Adolfo, because those packages should be available in the default Ubuntu package repository. Try this to update the list of packages that apt-get knows:
```
sudo apt-get update
```
And then try again.

---

### Post by NeillHog on 2007-07-21
Wow! Thanks
Exactly the answer I needed.
And now my Kubuntu doesn't lock up any more even with the nv1dia driver :-)

Now I just need to get the second monitor working.

---

### Post by sparks0548 on 2007-07-25
I hope I'm not too late, but I had similar problems and the NVIDIA drivers rocked when you added the following steps after installing the driver from the SH file:

The latest NVIDIA driver seems to default to 16 bit depth but beryl requires 24 bit so to change this do the following

sudo gedit /etc/X11/xorg.conf

find the "screen" section and change the value of the default depth from 16 to 24 so it now looks like this:
[size="3"]
Section "Screen"
Defaultdepth 24

sudo nvidia-xconfig --add-argb-glx-visuals


I snagged this from:  [http://ubuntuforums.org/showthread.php?t=458164](http://ubuntuforums.org/showthread.php?t=458164)

---

### Post by circuz_phreak on 2007-08-05
Tried the solution mentioned, when i do apt get it asks me to insert my linux cd due to media change, however it doesnt read my cd.  I cant even mount the volume because it doesnt read anything.  How can this be if I just installed of it, i burnt the iso off the website.

---

### Post by idiefouru on 2007-10-31
It helped to me install the new drivers for my 140m nvidia card.

thansk a lot 
venu

---

