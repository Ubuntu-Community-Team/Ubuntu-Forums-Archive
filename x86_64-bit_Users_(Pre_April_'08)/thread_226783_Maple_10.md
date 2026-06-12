---
title: "Maple 10"
date: 2006-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by calvinthomas on 2006-07-31
It seems that getting Maple 9.5 to install in Ubuntu 64bit is not possible, can anyone tell meif the latest version (10) suffers the same problems or does this version work well? I have Maple 9.5 and don't want to fork out for Maple 10 unless I know its going to work, I know that Mathematica works but my department doesn't use this so for me its only a backup option!

Calv

---

### Post by Kilz on 2006-07-31
> **calvinthomas said:**
> It seems that getting Maple 9.5 to install in Ubuntu 64bit is not possible, can anyone tell meif the latest version (10) suffers the same problems or does this version work well? I have Maple 9.5 and don't want to fork out for Maple 10 unless I know its going to work, I know that Mathematica works but my department doesn't use this so for me its only a backup option!

Calv

I did a google search and came up with a few pages you might want to look at.
[http://beta.mapleprimes.com/forum/uninstalling-maple-10](http://beta.mapleprimes.com/forum/uninstalling-maple-10)
[http://www.physics.drexel.edu/liki/index.php/Debian_Sysadmin#Maple_10_install](http://www.physics.drexel.edu/liki/index.php/Debian_Sysadmin#Maple_10_install)
[https://www.cs.uwaterloo.ca/twiki/view/CF/MapleInstallation](https://www.cs.uwaterloo.ca/twiki/view/CF/MapleInstallation)

The last one is instructions for 64bit

---

### Post by calvinthomas on 2006-07-31
Thanks for the links, my concern is with it working in the AMD64 version of Ubuntu, does the third link you provided give a method for how to install it in AMD64 or is I64 different?

Calv

---

### Post by Kilz on 2006-07-31
> **calvinthomas said:**
> Thanks for the links, my concern is with it working in the AMD64 version of Ubuntu, does the third link you provided give a method for how to install it in AMD64 or is I64 different?

Calv

Im not sure, maybe someone else can chime in. But the fact that the maple installer says /tmp/maple10/X86_64/Disk1 leads me to believe that it will work on the amd64. You may want to contact maple directly.

---

### Post by calvinthomas on 2006-07-31
Ok, i've contacted Maple directly, when I recieve a response I'll post it here incase its of any use to anyone else.

Calv

---

### Post by hizaguchi on 2006-08-01
If it doesn't work out, there's always Maxima. :)

---

### Post by calvinthomas on 2006-08-01
True but Maple is more powerful than Maxima and my department uses it so when I do modules that require it, its easier to get support in Maple, i've switched to 32bit Ubuntu and 9.5 now works flawlessly

Calv

---

### Post by bmcage on 2006-08-04
You can install Maple 9.5 on amd64. 
See my reply in thread [http://ubuntuforums.org/showthread.php?p=1337016](http://ubuntuforums.org/showthread.php?p=1337016)

---

### Post by dimis on 2006-08-04
What is your problem with maple 9.5 ?
If I remember correctly, I installed it quite effortlessly.

---

### Post by bmcage on 2006-08-06
Maple 9.5 and 10 work in 32 bit version without problem as mentioned.
In AMD64 some tweaking is needed to the installer to get it to install. At least on Ubuntu 6.06 which I have.

---

### Post by dimis on 2006-09-30
It worked far simpler for me (64bit Dapper):
1) Copied entire disc on drive.
2) Added execution permission on the .sh installer
3) Executed the installer.
4) Maple 9.5 is installed and ready to run. :)

- dimis -

---

### Post by bmcage on 2006-10-02
Dimis, can you for certainty give the result of ```
cat /proc/version
``` and ```
uname -a
```
Just to know what kernel and what chipset you work on.

---

### Post by dimis on 2006-10-02
As requested:
```
$ cat /proc/version
Linux version 2.6.15-26-amd64-generic (buildd@king) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Fri Sep 8 19:55:50 UTC 2006
$ uname -a
Linux crag-hack 2.6.15-26-amd64-generic #1 SMP PREEMPT Fri Sep 8 19:55:50 UTC 2006 x86_64 GNU/Linux
$
```
Are you guys possibly using [SYNAPS]("http://www-sop.inria.fr/galaad/software/synaps/") ? There are issues with this library which lead you on an earlier version of gcc/g++ (I think it is 3.3) as well as some conflicts on libstdc++. Perhaps there are conflicts with these earlier versions for Maple9.5... But this is a wild guess for now. I 'll let you know within this week since I am about to install Synaps at home as well.

---

### Post by dimis on 2006-10-08
I am confused with Maple... I did the tweaking I describe [here]("http://www.ubuntuforums.org/showthread.php?t=273672") in order to run and use as testbeds some SYNAPS implementations. My Maple 9.5 installation, is working ok. But this time I wanted to install the executable on another directory not inside my home directory. So I tried to launch the installation once more with the way I describe above. However, this time, things didn't work out ... :confused: and your tips bmcage lead me to success. I don't know what to say, because prior to my Synaps installation, my installation went without any problem. My best guess is that it has something to do with build-essential package which I had previously installed or m4 which I had previously not installed. As you can read on my thread about SYNAPS, I uninstalled g++-4.0, build-essential, g++, libstdc++6-4.0-dev and meanwhile while playing with GMP I installed m4, m4-doc packages...

Anyway, I don't experience any problem, neither with my old /home/... installation nor with my new one under /opt which I intend to share with other users on this system. I just felt I had to report this. Thanks again for your tip bmcage. :)


Regards,
- dimis -

P.S.: My uname -a hasn't changed.

---

