---
title: "AmazonMP3 for AMD64 Linux Mint Gloria"
date: 2009-11-11
forum: x86 64-bit Users
---

### Post by bucc5062 on 2009-11-11
I have spent a few hours on this issue.  I have about 10 tabs open in Firefox and looked at countless posting regarding this basic issue, getting amazonmp3 to work on an amd 64 Linux box.  I had it working when I was running kubuntu 9.04, but the upgrade killed my system so I wiped and installed Mint Linux (Gloria) which is ubuntu 9.1 based.

I get to installing amazonmp3 and I get the same problem with 64 bit mismatches.

Yes, I did a force install
Yes, I installed getlibs
Yes, I copy and pasted many commandline statements to get this program to work.

I actually got the problem down to (what seems to be) one error:
```

me@MyBox ~/Documents $ sudo getlibs /usr/bin/amazonmp3
No match for libpangomm-1.4.so.1
No match for libpangomm-1.4.so.1
No match for libpangomm-1.4.so.1
No packages to install
me@MyBox ~/Documents $ 

```
Yes, I checked *every* repository in synaptic and did an update/reload.  When I get to the specific library in question I even tried this:
```

me@MyBox ~/Documents $ sudo getlibs -p libpangomm-1.4.so.1
The following i386 packages will be installed: libpangomm-1.4.so.1
Continue [Y/n]? y
W: Unable to locate package libpangomm-1.4.so.1
E: No packages found
libpangomm-1.4.so.1 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
me@MyBox ~/Documents $ 

```
Short of pasting an image of my install app list I have installed libpangomm-1.4-1 

Here is a list of files in usr/lib (which I know is 64 bit libraries:
```

me@MyBox ~/Documents $ ls /usr/lib/libpang* -l
lrwxrwxrwx 1 root root     24 2009-11-02 10:24 /usr/lib/libpango-1.0.so.0 -> libpango-1.0.so.0.2400.1
-rw-r--r-- 1 root root 298320 2009-04-14 06:19 /usr/lib/libpango-1.0.so.0.2400.1
lrwxrwxrwx 1 root root     29 2009-11-02 10:24 /usr/lib/libpangocairo-1.0.so.0 -> libpangocairo-1.0.so.0.2400.1
-rw-r--r-- 1 root root  48208 2009-04-14 06:19 /usr/lib/libpangocairo-1.0.so.0.2400.1
lrwxrwxrwx 1 root root     27 2009-11-02 10:24 /usr/lib/libpangoft2-1.0.so.0 -> libpangoft2-1.0.so.0.2400.1
-rw-r--r-- 1 root root 188016 2009-04-14 06:19 /usr/lib/libpangoft2-1.0.so.0.2400.1
lrwxrwxrwx 1 root root     24 2009-11-02 10:24 /usr/lib/libpangomm-1.4.so.1 -> libpangomm-1.4.so.1.0.30
-rw-r--r-- 1 root root 189184 2009-03-30 11:19 /usr/lib/libpangomm-1.4.so.1.0.30
lrwxrwxrwx 1 root root     25 2009-11-02 10:24 /usr/lib/libpangox-1.0.so.0 -> libpangox-1.0.so.0.2400.1
-rw-r--r-- 1 root root  52376 2009-04-14 06:19 /usr/lib/libpangox-1.0.so.0.2400.1
lrwxrwxrwx 1 root root     27 2009-11-02 10:24 /usr/lib/libpangoxft-1.0.so.0 -> libpangoxft-1.0.so.0.2400.1
-rw-r--r-- 1 root root  31368 2009-04-14 06:19 /usr/lib/libpangoxft-1.0.so.0.2400.1
me@MyBox ~/Documents $ 

```
Here is the file list for the 32 bit library
```

me@MyBox ~/Documents $ ls /usr/lib32/libpang* -l
lrwxrwxrwx 1 root root     17 2009-11-02 22:17 /usr/lib32/libpango-1.0.so -> libpango-1.0.so.0
lrwxrwxrwx 1 root root     24 2009-11-02 22:17 /usr/lib32/libpango-1.0.so.0 -> libpango-1.0.so.0.2400.1
-rw-r--r-- 1 root root 268288 2009-04-14 06:19 /usr/lib32/libpango-1.0.so.0.2400.1
lrwxrwxrwx 1 root root     22 2009-11-02 22:17 /usr/lib32/libpangocairo-1.0.so -> libpangocairo-1.0.so.0
lrwxrwxrwx 1 root root     29 2009-11-02 22:17 /usr/lib32/libpangocairo-1.0.so.0 -> libpangocairo-1.0.so.0.2400.1
-rw-r--r-- 1 root root  42812 2009-04-14 06:19 /usr/lib32/libpangocairo-1.0.so.0.2400.1
lrwxrwxrwx 1 root root     20 2009-11-02 22:17 /usr/lib32/libpangoft2-1.0.so -> libpangoft2-1.0.so.0
lrwxrwxrwx 1 root root     27 2009-11-02 22:17 /usr/lib32/libpangoft2-1.0.so.0 -> libpangoft2-1.0.so.0.2400.1
-rw-r--r-- 1 root root 161876 2009-04-14 06:19 /usr/lib32/libpangoft2-1.0.so.0.2400.1
lrwxrwxrwx 1 root root     18 2009-11-02 22:17 /usr/lib32/libpangox-1.0.so -> libpangox-1.0.so.0
lrwxrwxrwx 1 root root     25 2009-11-02 22:17 /usr/lib32/libpangox-1.0.so.0 -> libpangox-1.0.so.0.2400.1
-rw-r--r-- 1 root root  46940 2009-04-14 06:19 /usr/lib32/libpangox-1.0.so.0.2400.1
lrwxrwxrwx 1 root root     20 2009-11-02 22:17 /usr/lib32/libpangoxft-1.0.so -> libpangoxft-1.0.so.0
lrwxrwxrwx 1 root root     27 2009-11-02 22:17 /usr/lib32/libpangoxft-1.0.so.0 -> libpangoxft-1.0.so.0.2400.1
-rw-r--r-- 1 root root  26196 2009-04-14 06:19 /usr/lib32/libpangoxft-1.0.so.0.2400.1
me@MyBox ~/Documents $ 

```

What repository would I find libpangomm*?

I am missing **one** thing and it is driving me nuts.  Either there is a script somewhere that sets up amazonmp3 for 64 bit systems and i jsut cannot find it for all my Google searches, or there is a reposity I am missing in synaptic that I need to add, or....what?

I realize it may be a simple getlibs command I missed and I hope someone out there ran into the same issue with Gloria (the OS not the girlfriend) and can help.

As a side note when I did the force (which I read in one posting never to do...why then in other postings are we told to do this?) I got this out put:

```

me@MyBox ~/Documents $ sudo dpkg -i --force-all amazonmp3.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 176152 files and directories currently installed.)
Preparing to replace amazonmp3 1.0.3-1 (using amazonmp3.deb) ...
Unpacking replacement amazonmp3 ...
Setting up amazonmp3 (1.0.3-1) ...

Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

me@MyBox ~/Documents $ 
```

---

### Post by oldos2er on 2009-11-11
This software worked for me: [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by Yellow Pasque on 2009-11-12
[http://packages.debian.org/sid/libpangomm-1.4-1](http://packages.debian.org/sid/libpangomm-1.4-1)

---

### Post by bucc5062 on 2009-11-12
Temujin,

Thanks for the reply.  I checked out the link and it turns out I already have that package installed:

C++ Wrapper for pango (shared libraries)
> 
Pangomm is a C++ wrapper for the pango library. Originally part of
gtkmm, pangomm provides convenient C++ interfaces for handling both
the layout and internationalization of text in graphical applications.

This package contains the shared library.


I tried installing every package I could relate to the install.  I sent a message to cappy showing the original getlibs error hoping he/she may shed light on this one file.  here is a recap of my attempt (again)

```

me@MyBox ~/Documents $ sudo getlibs /usr/bin/amazonmp3
[sudo] password for me: 
No match for libpangomm-1.4.so.1
No match for libpangomm-1.4.so.1
No match for libpangomm-1.4.so.1
No packages to install
me@MyBox ~/Documents $ sudo getlibs -l libpangomm-1.4.so.1
No match for libpangomm-1.4.so.1
No packages to install
me@MyBoxs ~/Documents $ sudo getlibs -p libpangomm-1.4.so.1
The following i386 packages will be installed: libpangomm-1.4.so.1
Continue [Y/n]? y
W: Unable to locate package libpangomm-1.4.so.1
E: No packages found
libpangomm-1.4.so.1 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
me@MyBox ~/Documents $ 

```

This is what baffles me, I have every default repository open for Gloria.  Do I need to add a different one even though the package was installed?

I did an ls for the library in lib and I get this:

```

me@MyBox /usr/lib $ ls
libpangomm-1.4.so.1  libpango
me@MyBox /usr/lib $ 

```

To confirm, I do an ls for lib32 and no libpangmmo:

```

me@MyBox /usr/lib32 $ ls libpan*
libpanel.so.5                  libpangoft2-1.0.so.0
libpanel.so.5.7                libpangoft2-1.0.so.0.2400.1
libpango-1.0.so                libpangox-1.0.so
libpango-1.0.so.0              libpangox-1.0.so.0
libpango-1.0.so.0.2400.1       libpangox-1.0.so.0.2400.1
libpangocairo-1.0.so           libpangoxft-1.0.so
libpangocairo-1.0.so.0         libpangoxft-1.0.so.0
libpangocairo-1.0.so.0.2400.1  libpangoxft-1.0.so.0.2400.1
libpangoft2-1.0.so
me@MyBox /usr/lib32 $ 

```

I feel it is a problem with getlibs, but related to my repository list.  S, I have the libpangmmo package installed, now what?

---

### Post by Yellow Pasque on 2009-11-12
You have to get the i386 .deb: [http://packages.debian.org/sid/i386/libpangomm-1.4-1/download](http://packages.debian.org/sid/i386/libpangomm-1.4-1/download) and then run getlibs on that:
```
sudo getlibs -p libpangomm-1.4-1_2.26.0-1_i386.deb
```

---

### Post by bucc5062 on 2009-11-14
Temujin,

I'm really trying here, but something is not clicking.  I understand (eventually) what you posted, I went to the link and realized I needed to add the repository to my list:

```

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb http://archive.canonical.com/ubuntu/ jaunty partner 

## +++ Medibuntu (stable) +++
deb http://packages.medibuntu.org/ jaunty free non-free 
deb http://ppa.launchpad.net/project-neon/ppa/ubuntu/ jaunty main 
deb-src http://ppa.launchpad.net/project-neon/ppa/ubuntu/ jaunty main 
[COLOR="Red"]deb http://http.us.debian.org/debian/ sid main  [/COLOR]
deb http://ppa.launchpad.net/do-core/ppa/ubuntu/ jaunty main 
deb http://ppa.launchpad.net/do-core/ppa/ubuntu/ jaunty main 

```

yet when I do that and attempt to reload the list I get this wonderful message:

```

W: GPG error: http://http.us.debian.org sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B

```

Okay, I look that up in google.  No many entries but the tend to talk about performing this command:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 9AA38DCD55BE302B

```

then this command:
```
gpg -a --export 55BE302B | sudo apt-key add -
```

Done and Done.

So back to the original command and 

```
 sudo getlibs -p libpangomm-1.4-1_2.26.0-1_i386.deb
The following i386 packages will be installed: libpangomm-1.4-1_2.26.0-1_i386.deb
Continue [Y/n]? y 
W: Unable to locate package libpangomm-1.4-1_2.26.0-1_i386.deb
E: No packages found
libpangomm-1.4-1_2.26.0-1_i386.deb was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

 sudo getlibs -p libpangomm-1.4.so.1
The following i386 packages will be installed: libpangomm-1.4.so.1
Continue [Y/n]? y
W: Unable to locate package libpangomm-1.4.so.1
E: No packages found
libpangomm-1.4.so.1 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install



```

<RANT>
Decades of being a computer programmer, working with mainframes to laptops, and I am brought to my knees pleading, KIS, what am I doing wrong here.  It is one friggin file and I've spent easy eight hours trying, thinking, researching, and asking for help.  I curse amazon, those lazy *** greed mongers that cannot take time to make a 64-bit package, but that does not help get this POS 32-bit program to work.
</RANT>

Okay, do I copy down, manually, some files?  I'll do it.  Do I run some obscure linux command, I'll do it.  I stop short of live sacrifices and I think two years is enough hazing to be able to join the Linux fraternity.  What am I missing?

I did play around with the publickey problem, thought I got it, ran a ap-get update and in the long list I saw this:

[COLOR="Red"]```
Get:3 http://http.us.debian.org sid Release.gpg [835B]                                                     
Ign http://http.us.debian.org sid/main [/COLOR]Translation-en_US                                                   
Hit http://packages.medibuntu.org jaunty Release.gpg                                                       
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                                           
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US                                        
[COLOR="Red"]Get:4 http://http.us.debian.org sid Release [101kB]   [/COLOR]                                                     
Hit http://ppa.launchpad.net jaunty Release.gpg                                                              
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                           
Hit http://ppa.launchpad.net jaunty Release                                                                
[COLOR="Red"]Hit http://http.us.debian.org sid/main Packages  [/COLOR]

```

There must be another path to this solution.  Again, I am running Linux Mint 7 (Gloria) on an AMD64 box.

---

### Post by Yellow Pasque on 2009-11-14
No, don't add debian sid to the sources list. Just download the package and run the command on it.

---

### Post by gcornett on 2009-11-15
I guess I'm just lazy.  I simply installed AmazonMP3 in a 32 bit Ubuntu Virtualbox guest. Worked fine.

---

