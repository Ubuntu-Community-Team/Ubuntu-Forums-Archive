---
title: "Going to try openSuse"
date: 2007-08-31
forum: openSUSE and SUSE Linux Enterprise
---

### Post by mips on 2007-08-31
I have 800MB available for downloads which I have to use by the end of the day or i loose it, so i decided to download opensuse 10.3 B2 i386 to try out.

Will let you know what i think of it after i have burned the cd.

---

### Post by reckless2k2 on 2007-08-31
after the mess with 10.1 and package management, i really have just made a pass on anything suse going forward. i liked the product quite a bit but doing most things in suse were always such a hassle like samba and such. i'd rather just reach out to pclinuxos if i'm going to bother with a rpm based desktop distro.

---

### Post by bluenova on 2007-08-31
Suse is great in all espects until you get to the package manager. What is it with RPM based systems that make them so slow?

---

### Post by mips on 2007-08-31
Oh well, I'm 21% into the download so I might as well carry on.

I have not heard good stories about its package management but I suppose I will just have to find this out for myself.

Suppose this is where apt shines, makes one wonder why other distros go down the route the do. I also like ports & portage.

---

### Post by RedDwarf on 2007-08-31
> **mips said:**
> Suppose this is where apt shines
Not so much: [http://svn.labix.org/smart/trunk/README](http://svn.labix.org/smart/trunk/README)
```
------------
Case Studies
------------

In this section will be described real cases showing `Smart` behavior
in comparison with other tools, or handling unusual situations.

Notice that Smart was not tuned to work in any of these cases, and
the reason it works is because handling unusual situations was the
initial project goal.


Case 1 - APT
------------

This case happened in a real world environment where a weakness in
the algorithm used by `APT` (which is the same used in `APT-RPM`)
turned a simple operation into a problem of obscure results.
Smart Package Manager was used in the same environment to show
its results.

The problem starts when an installation of `xscreensaver` is tried::

  [root@damien:/root] apt-get install xscreensaver
  Reading Package Lists... Done
  Building Dependency Tree... Done
  Some packages could not be installed. This may mean that you have
  requested an impossible situation or if you are using the unstable
  distribution that some required packages have not yet been created
  or been moved out of Incoming.
  
  Since you only requested a single operation it is extremely likely that
  the package is simply not installable and a bug report against
  that package should be filed.
  The following information may help to resolve the situation:
  
  The following packages have unmet dependencies:
    xscreensaver: Depends: libglade-2.0.so.0
                  Depends: libxml2.so.2
  E: Broken packages

[B]The error shown makes the user believe that `libglade-2.0.so.0` and
`libxml2.so.2` are not available. That's not the case[/B]::

 [root@damien:/root] apt-get install libxml2
 Reading Package Lists... Done
 Building Dependency Tree... Done
 Some packages could not be installed. This may mean that you have
 requested an impossible situation or if you are using the unstable
 distribution that some required packages have not yet been created
 or been moved out of Incoming.
 
 Since you only requested a single operation it is extremely likely that
 the package is simply not installable and a bug report against
 that package should be filed.
 The following information may help to resolve the situation:
 
 The following packages have unmet dependencies:
   libxml2: Depends: glibc-iconv but it is not going to be installed
 E: Broken packages

**Another misguiding error message.** Let's go further::

 [root@damien:/root] apt-get install glibc-iconv
 Reading Package Lists... Done
 Building Dependency Tree... Done
 Some packages could not be installed. This may mean that you have
 requested an impossible situation or if you are using the unstable
 distribution that some required packages have not yet been created
 or been moved out of Incoming.
 
 Since you only requested a single operation it is extremely likely that
 the package is simply not installable and a bug report against
 that package should be filed.
 The following information may help to resolve the situation:
 
 The following packages have unmet dependencies:
   glibc-iconv: Depends: glibc-gconvdata (= 2.3.3) but 1:2.3.2-586_1cl is to be installed
 E: Broken packages

[B]Version `2.3.3` is needed, but `1:2.3.2-586_1cl` is to be installed. This
message is mostly correct. The only problem is, "1:2.3.2-586_1cl" is
already installed[/B]::

 [root@damien:/root] apt-cache policy glibc-gconvdata
 glibc-gconvdata:
   Installed: 1:2.3.2-586_1cl
   Candidate: 1:2.3.2-586_1cl
   Version Table:
  *** 1:2.3.2-586_1cl 0
         100 RPM Database
      0:2.3.3-69473cl 0
         500 file: conectiva/all pkglist

The problem was found. A package from another repository (586_1cl shows
it's not native, in that specific case) has a higher epoch than the one
available in the usual repository. [B]This clearly shows that the APT
algorithm marks a single version as candidate, and when this is not the
wanted version for some operation, the whole operation is compromised.[/B]

When testing `Smart Package Manager` in the same environment, the
expected result is obtained::

 [root@damien:/root] smart install xscreensaver
 Updating cache...              ######################################## [100%]
 
 Computing transaction...
 
 Downgrading packages (1):
   glibc-gconvdata-0:2.3.3-69473cl.i386
 
 Installing packages (4):
   glibc-iconv-0:2.3.3-69473cl.i386
   libglade2-2.4.0-68154cl.i386
   libxml2-2:2.6.13-67598cl.i386
   xscreensaver-4.15-69825cl.i386

 Confirm changes (Y/n)?

Smart correctly selected `glibc-gconvdata` for downgrading as the only
possibility of performing the user requested operation.

Case 2 - APT & YUM
------------------

This is another real case, and is being reproduced in a controlled
environment for tests with YUM, APT-RPM, and Smart.

The issue is, a package named `A` requires package `BCD` explicitly, and
RPM detects implicit dependencies between `A` and `libB`, `libC`, and `libD`.
Package `BCD` provides `libB`, `libC`, and `libD`, but additionally there
is a package `B` providing `libB`, a package `C` providing `libC`, and
a package `D` providing `libD`.

In other words, there's a package `A` which requires four different symbols,
and one of these symbols is provided by a single package `BCD`, which happens
to provide all symbols needed by `A`. There are also packages `B`, `C`, and `D`,
that provide some of the symbols required by `A`, but can't satisfy all
dependencies without `BCD`.

The expected behavior for an operation asking to install `A` is obviously
selecting `BCD` to satisfy `A`'s dependencies, on the other hand, `YUM` and
**APT fail to deliver that as a guaranteed operation**, as is shown
below.

First, let's see how YUM deals with the problem::

  [root@burma ~]% yum install A
  Setting up Install Process
  Setting up Repo:  localpub
  repomd.xml                100% |=========================|  951 B    00:00
  Reading repository metadata in from local files
  localpub  : ################################################## 5/5
  Resolving Dependencies
  --> Populating transaction set with selected packages. Please wait.
  ---> Downloading header for A to pack into transaction set.
  A-1.0-1cl.i386.rpm        100% |=========================| 1.0 kB    00:00
  ---> Package A.i386 0:1.0-1cl set to be installed
  --> Running transaction check
  --> Processing Dependency: libD for package: A
  --> Processing Dependency: libC for package: A
  --> Processing Dependency: libB for package: A
  --> Processing Dependency: BCD for package: A
  --> Restarting Dependency Resolution with new changes.
  --> Populating transaction set with selected packages. Please wait.
  ---> Downloading header for D to pack into transaction set.
  D-1.0-1cl.i386.rpm        100% |=========================| 1.0 kB    00:00
  ---> Package D.i386 0:1.0-1cl set to be installed
  ---> Downloading header for C to pack into transaction set.
  C-1.0-1cl.i386.rpm        100% |=========================| 1.0 kB    00:00
  ---> Package C.i386 0:1.0-1cl set to be installed
  ---> Downloading header for B to pack into transaction set.
  B-1.0-1cl.i386.rpm        100% |=========================| 1.0 kB    00:00
  ---> Package B.i386 0:1.0-1cl set to be installed
  ---> Downloading header for BCD to pack into transaction set.
  BCD-1.0-1cl.i386.rpm      100% |=========================| 1.0 kB    00:00
  ---> Package BCD.i386 0:1.0-1cl set to be installed
  --> Running transaction check
  
  Dependencies Resolved
  Transaction Listing:
    Install: A.i386 0:1.0-1cl
  
  Performing the following to resolve dependencies:
    Install: B.i386 0:1.0-1cl
    Install: BCD.i386 0:1.0-1cl
    Install: C.i386 0:1.0-1cl
    Install: D.i386 0:1.0-1cl
  Is this ok [y/N]:


YUM selected **all** packages for installation, even though `BCD`
alone would satisfy `A`'s dependencies.

Let's see how APT deals with that::

  [root@burma ~]% apt-get install A
  Reading Package Lists... Done
  Building Dependency Tree... Done
  The following extra packages will be installed:
    B BCD
  The following NEW packages will be installed:
    A B BCD
  0 upgraded, 3 newly installed, 0 removed and 0 not upgraded.
  Need to get 0B/4055B of archives.
  After unpacking 0B of additional disk space will be used.
  Do you want to continue? [Y/n] n

[B]As a coincidence, APT did a better job, and selected only `B` and
`BCD` to satisfy `A`'s dependency, which is still not right.[/B]

Now, let's see how Smart would solve the problem::

  [root@burma ~]% smart install A
  Updating cache...               ######################################## [100%]
  
  Computing transaction...
  
  Installing packages (2):
    A-1.0-1cl@i386     BCD-1.0-1cl@i386
  
  2.7kb of package files are needed.
  
  Confirm changes (Y/n)?

Smart correctly selected only `BCD`, since it's necessary anyway, and
solves all dependencies.


Case 3 - APT & YUM
------------------

That's another interesting case which was tested with APT-RPM and YUM.

In this case, there's a package `A` version 1.0 installed in the
system, and there are two versions available for upgrading: 1.5 and 2.0.
Version 1.5 may be installed without problems, but version 2.0 has a
dependency on `B`, which is not available anywhere.

In this case, the best possibility is upgrading to 1.5, since upgrading
to 2.0 is not an option.

Let's see how APT reacts to this situation::

  [root@burma ~]% apt-get upgrade A
  Reading Package Lists... Done
  Building Dependency Tree... Done
  The following packages have been kept back
    A
  0 upgraded, 0 newly installed, 0 removed and 1 not upgraded.

[B]APT seems to refuse to upgrade `A`, even though version 1.5 might be
installed without problems.[/B]

What happens when forcing APT to install `A`::

  [root@burma ~]% apt-get install A
  Reading Package Lists... Done
  Building Dependency Tree... Done
  Some packages could not be installed. This may mean that you have
  requested an impossible situation or if you are using the unstable
  distribution that some required packages have not yet been created
  or been moved out of Incoming.
  
  Since you only requested a single operation it is extremely likely that
  the package is simply not installable and a bug report against
  that package should be filed.
  The following information may help to resolve the situation:
  
  The following packages have unmet dependencies:
    A: Depends: B but it is not installable
  E: Broken packages

[B]It really refuses to install the newest version, and doesn't consider
the possibility of using version 1.5.[/B]

Now, let's see how YUM would handle it.

:Update: This test case was showing the wrong results for YUM, since it
         was using a cached version of the package header that didn't
         present the missing dependency. I apologise for showing invalid
         results.

::

  [root@burma ~]% yum update
  Setting up Update Process
  Setting up Repo:  localpub
  repomd.xml                100% |=========================|  951 B    00:00
  Reading repository metadata in from local files
  primary.xml.gz            100% |=========================|  809 B    00:00
  MD Read   : ################################################## 3/3
  localpub  : ################################################## 3/3
  Resolving Dependencies
  --> Populating transaction set with selected packages. Please wait.
  ---> Downloading header for A to pack into transaction set.
  A-2.0-1cl.i386.rpm        100% |=========================| 1.3 kB    00:00
  ---> Package A.i386 0:2.0-1cl set to be updated
  --> Running transaction check
  --> Processing Dependency: B for package: A
  --> Finished Dependency Resolution
  Error: missing dep: B for pkg A

Just like APT, YUM selected version 2.0 and didn't consider the
availability of an intermediate version.

Now, let's see how Smart would behave in the same situation::

  [root@burma ~]% smart upgrade
  Loading cache...
  Updating cache...               ######################################## [100%]
  
  Computing transaction...
  
  Upgrading packages (1):
    A-1.5-1cl@i386
  
  1.3kb of package files are needed.
  
  Confirm changes (Y/n)?

Smart correctly selects the intermediate version 1.5, which is the
only viable possibility given the current options.


Case 4 - APT
------------

This case presents the following situation: there's a package `A`,
installed in the system, which depends on `libfoo`, currently
being provided by `B` 1.0. What happens if `B` is upgraded to
version 2.0, but `libfoo` is moved to be provided by package `C`?

The expected behavior would be to upgrade `B` to version 2.0,
and install `C` to satisfy `A`'s dependency.

That's not what happens with APT::

  [root@burma ~]% apt-get dist-upgrade
  Reading Package Lists... Done
  Building Dependency Tree... Done
  Calculating Upgrade... Done
  The following packages will be upgraded
    B
[B]  The following packages will be REMOVED:
    A[/B]
  1 upgraded, 0 newly installed, 1 removed and 0 not upgraded.
  Need to get 0B/1321B of archives.
  After unpacking 0B of additional disk space will be used.
  Do you want to continue? [Y/n]

Let's see Smart in the same situation::

  [root@burma ~]% smart upgrade
  Loading cache...
  Updating cache...               ######################################## [100%]
  
  Computing transaction...
  
  Upgrading packages (1):
    B-2.0-1cl@i386
  
  Installing packages (1):
    C-2.0-1cl@i386
  
  2.6kB of package files are needed.
  
  Confirm changes (Y/n)?

[B]Smart correctly selected package `C` for installation as a viable
possibility of leaving `A` installed in the system while upgrading
`B`.[/B]
```

---

### Post by reckless2k2 on 2007-08-31
suse 10.0 was soooooo good. suse 10.1 really killed all my suse love off. you really don't have the old school "rpm hell" that you use to get anymore but since 10.1 the new package management backend is not so hot. when i started to get involved more with networking and servers suse really was troublesome. some people swear by it. i just prefer PCLOS if i'm going to play with a rpm based distro. maybe the next version might pull me back but i doubt it. PCLOS just does a lot of everything better.

---

### Post by Incense on 2007-09-01
I've been a long time (open)SUSE user, and I love it. The desktop feels great, speed really is not a problem, and everything does what I need. Yast does take a while to start up when you want to install software, but you can use the SMART package manager. 10.3 does not feel quite ready yet, but it does look like an exciting release. I'm really glad they did away with zenworks in this release. It was the bane of 10.1, and 10.2.

---

