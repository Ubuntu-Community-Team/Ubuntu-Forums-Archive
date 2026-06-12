---
title: "Where the heck is make"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by miked on 2005-10-14
I've used Linux in the past mostly redhat but I have never seen a package that didnt' come with gcc and make?  Can someone let me know how to install it or is it simply have to be refered in my ssh

Cheers Mike

---

### Post by miked on 2005-10-14
Forget it stupid me forgot all about apt-get whoops :confused:

---

### Post by heimo on 2005-10-14
If you're compiling something, you could install [build-essential]("http://packages.ubuntu.com/breezy/devel/build-essential")
```
sudo apt-get install build-essential
```
(includes [make]("http://packages.ubuntu.com/breezy/devel/make") / [gcc]("http://packages.ubuntu.com/breezy/devel/gcc") and other stuff)

---

### Post by webhead on 2005-10-14
[QUOTE=heimo]If you're compiling something, you could install [build-essential]("http://packages.ubuntu.com/breezy/devel/build-essential")
```
sudo apt-get install build-essential
```
(includes [make]("http://packages.ubuntu.com/breezy/devel/make") / [gcc]("http://packages.ubuntu.com/breezy/devel/gcc") and other stuff)[/QUOTE]

I've tried the above, and I get an error, shown below.  Have I done something wrong?

```

sudo apt-get install build-essential
Password:***************
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
```

Any ideas?

Dan

Edit: PS I just saw that this is in the AMD64 forum, but I am on a regular x86 machine.

---

### Post by heimo on 2005-10-14
[quote=webhead]I've tried the above, and I get an error, shown below.  Have I done something wrong?
[/quote]
Could be your /etc/apt/sources.list file, or maybe you didn't run
```
sudo apt-get update
```
first, because I didn't instruct to. :rolleyes: You can try to install the same package using Synaptic Package Manager.

---

### Post by darkbluesea on 2006-10-21
I actualy have the same problem, I've just installed a brand new ubuntu, and sucessfuly upgraded from 5'10 to 6'10, but when I:


dark@onix:~$ sudo apt-get install gcc
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
  gcc: Depends: gcc-4.0 (>= 4.0.3) but it is not going to be installed
E: Broken packages
dark@onix:~$ 

also: 
sudo apt-get update
sudo apt-get -f update
sudo apt-get install build-essential

None of these works. How to overcome this?

---

