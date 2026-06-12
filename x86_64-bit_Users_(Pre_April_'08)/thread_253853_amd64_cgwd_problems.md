---
title: "amd64 cgwd problems"
date: 2006-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sqwishy on 2006-09-09
i installed compiz sucessfuly. but of course thats not enough i need cgwd...! so after reading and struggling through the tutorials and howto's i got the reposotories working from [http://beerorkid.com/compiz/](http://beerorkid.com/compiz/) but now i have run into a different problem.

```
sqwishy@mudskipper:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-core compiz-plugins
The following NEW packages will be installed:
  compiz-core compiz-plugins
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0B/814kB of archives.
After unpacking, 3564kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 97020 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_0.0.13.45-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.45-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/compiz', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking compiz-plugins (from .../compiz-plugins_0.16-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-plugins_0.16-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libwobbly.a', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-core_0.0.13.45-0ubuntu1_amd64.deb
 /var/cache/apt/archives/compiz-plugins_0.16-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
sqwishy@mudskipper:~$
```

thats what i do when i try to fix the 2 broken packages. please help me fix this i've already tryed for over half an hour. ](*,)

---

### Post by xopher on 2006-09-09
Hmm, the packages for amd64 in that repository are not up to date.

You might try the ones I compiled yesterday, which are up2date.. And they work perfectly for me ;)

Repository:
```
deb http://koti.mbnet.fi/xopher/Files/compiz-amd64 ./
```

Im not promising that Ill keep this repo updated, but for now when the official repos arent, use this.

Hope youll get it working.

---

### Post by Sqwishy on 2006-09-09
i get this error 
```
Failed to fetch http://koti.mbnet.fi/xopher/Files/compiz-amd64/./Packages.gz 302 Found

```
my geeklord of a brother (using gentoo) tryed helping me but he doesn't know ubuntu so well and my mom is all %!@#&? and i have no clue how to fix it anyways. 302 means it was redirecting it right? :confused:

EDIT: i manualy downloaded the packages i need to unbreak the broken things, compiz-core and compiz-plugins.
compiz-plugins wont install kuz it needs compiz-core.
compiz-core wont install because things are broken... ](*,)

---

### Post by xopher on 2006-09-11
What's the exact line you got in your sources.list ?

Another user has been experiencing the same problem with my repository, but it works flawlessly for me. And whatever I try I cant reproduce the error. Make sure you dont write .../compiz-amd64 and ./ without the space between.

Ill ask around and see if there's something I can do.

PS. You can install them manually too, by installing them in the correct order or forcing them with dpkg, using --force-depends.

---

### Post by xopher on 2006-09-11
I changed the repo, it should work fine now.

The address:

```
deb http://koti.mbnet.fi/xopher dapper main-amd64
```

Comments appreciated.

edit: Repo not maintained anymore. Ive started uploading packages directly to quinns repos. So you can use the official repositories from now on again. 8)

---

