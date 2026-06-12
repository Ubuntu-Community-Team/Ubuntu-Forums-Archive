---
title: "/etc/apt/sources.list"
date: 2005-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pitbull11188 on 2005-05-30
Coud someone please copy and paste the contents of this file for me. You can navigate to it by entering "sudo gedit /etc/apt/sources.list" into the shell. Thanks.

---

### Post by RaverDK on 2005-05-30
[QUOTE=Pitbull11188]Coud someone please copy and paste the contents of this file for me. You can navigate to it by entering "sudo gedit /etc/apt/sources.list" into the shell. Thanks.[/QUOTE]
 raver@boxie:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 4
model name      : AMD Athlon(tm) processor
stepping        : 4
cpu MHz         : 1395.318
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr pni syscall mmxext 3dnowext 3dnow
bogomips        : 2760.70

raver@boxie:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Just to make sure for you im NOT running on a 64Bit CPU, soo if not working - DONT kill me :)

Hope you get it working... 

Ovre and out!

---

### Post by Pitbull11188 on 2005-05-30
It didn't work. Now following your request I won't kill you just dismember you...Just kidding. Thanks for the attempt though it is appreciated.

---

### Post by N'Jal on 2005-05-30
I have almost had this problem myself until i realised that i had a back up somewhere, it's gone now, so for the rest of us would it be a good idea to have a vanilla 'sources.list file for download on the website?

---

### Post by ::DoGG:: on 2005-05-30
Here You go:

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb-src http://pl.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pl.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://pl.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted
# deb-src http://pl.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe


```

---

### Post by Pitbull11188 on 2005-05-30
Is there a possibility of the servers being down because no matter how many different setups I try Sudo apt-get update still doesn't work?

---

### Post by GeirG on 2005-05-30
We might be able to help you better if you cut 'n paste the error messages you get.

Regards,

---

### Post by christooss on 2005-05-30
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz)  403 Forbidden

Only backports doesn't work

Use thos one

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted

---

### Post by Pitbull11188 on 2005-05-30
Ok this is a copy of my sources.list file:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted
# deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
-----------------------------------------------------------------------------------------------------------------------------------
and this is a list of the error message that I get: 

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Connection failed
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
  Connection failed
Err [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) hoary Release.gpg
  Connection failed
26% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting



Thanks.

---

### Post by rider343 on 2005-05-30
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Marillat
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by Pitbull11188 on 2005-05-31
Ok, I have tryed several people's configurations for the sources.list file and nothing works. Is it possible the servers are down?, because if not I'm going to have to reformat and I'd rather not.

---

### Post by GeirG on 2005-06-01
Hmmm... not sure about this one,

Have you tried apt-setup?

Regards,

---

### Post by nortoncillo on 2005-06-02
here's mine sources.list

##deb cdrom:[Ubuntu 4.10 _hoary Warthog_ - Preview amd64 Binary-1 (20041020)]/ unstable main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main universe restricted multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse


# deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java

# deb [http://ftp.cl.debian.org/debian/](http://ftp.cl.debian.org/debian/) sarge main non-free contrib
# deb [http://www.kalyxo.org/debian/](http://www.kalyxo.org/debian/) experimental main




you can notice that i have some debian and java sources, but those you can ignore

ps: sometimes some of the sources dont answer to the update or upgrade apt, but in my case, thats kind of normal...

here's the output for apt-get update

$ sudo apt-get update
Password:
Des:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Des:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Des:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16,9kB]
Des:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Des:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release [16,8kB]
Des:6 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages [25,1kB]
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Des:7 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages [16,8kB]
Des:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages [5424B]
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/universe Packages
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/multiverse Packages
Des:9 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources [6339B]
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Sources
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/universe Sources
Des:10 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources [3668B]
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/multiverse Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Sources
Descargados 91,4kB en 7s (12,9kB/s)
Leyendo lista de paquetes... Hecho                   <yes im using ubuntu in spanish>

---

### Post by dbernar1 on 2005-06-02
Try to see if you are set up to use a proxy, in synpatic.

---

### Post by XDevHald on 2005-06-02
First off, I do NOT recommend using Marillat due to unstable packages and other security issues, if this has been resolved then feel free to use it, but I don't advise it.

Second, the sources.list I have here listed below works perfectly and running well on apt-get.

 > deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 


---

### Post by JeffcS on 2005-06-11
I used the source
> b cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted  

But get the folowing error, get the same with other plug-ins.

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla

Please help!!

---

### Post by nogitsune on 2005-06-21
```
 
Fetched 50.0kB in 14s (3370B/s)
 Failed to fetch   [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz)   MD5Sum mismatch
 Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz)   MD5Sum mismatch
 Reading package lists... Done
 W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com)  hoary-security/main Packages  (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages)  - stat (2 No such file or directory)
 W: You may want to run apt-get update to correct these problems
 E: Some index files failed to download, they have been ignored, or old ones used  instead.

```


this is my problem, i #-rd the security package for now, whats in there?

thanks yáll

---

### Post by nogitsune on 2005-06-21
```
 
Fetched 50.0kB in 14s (3370B/s)
 Failed to fetch   [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz)   MD5Sum mismatch
 Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz)   MD5Sum mismatch
 Reading package lists... Done
 W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com)  hoary-security/main Packages  (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages)  - stat (2 No such file or directory)
 W: You may want to run apt-get update to correct these problems
 E: Some index files failed to download, they have been ignored, or old ones used  instead.

```


this is my problem, i #-rd the security package for now, whats in there?

thanks yáll

---

### Post by Optimal Aurora on 2005-06-21
why do that just go to [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories) and get that...

Hay are you running the 32bit version...

---

