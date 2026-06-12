---
title: "apt-get broken after kde4 install"
date: 2008-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by bwp_88 on 2008-01-31
Hi all,

Just installed Kubuntu 7.10 64-bit on my computer yesterday. I installed kde4 as per [http://www.kubuntu.org/announcements/kde-4.0.php](http://www.kubuntu.org/announcements/kde-4.0.php), but now I'm back to using kde3. The kde4 packages are still on my computer. This morning, Adept offered some updates to various kde related programs, but when trying to upgrade kdm the install failed.

Running sudo apt-get -f install gives the following output:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/699kB of archives.
After unpacking 0B of additional disk space will be used.
debconf: Perl may be unconfigured (FileHandle.pm did not return a true value at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 98955 files and directories currently installed.)
Preparing to replace kdm 4:3.5.8-0ubuntu2.1 (using .../kdm_4%3a3.5.8-0ubuntu2.1_amd64.deb) ...
FileHandle.pm did not return a true value at /usr/share/perl5/Debconf/Template.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: warning - old pre-removal script returned error exit status 9
dpkg - trying script from the new package instead ...
FileHandle.pm did not return a true value at /usr/share/perl5/Debconf/Template.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing /var/cache/apt/archives/kdm_4%3a3.5.8-0ubuntu2.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 9
FileHandle.pm did not return a true value at /usr/share/perl5/Debconf/Template.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/kdm_4%3a3.5.8-0ubuntu2.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Looks like a Perl error is preventing apt-get from finishing the kdm install.

```
$ perl -Ww -e 'use FileHandle;'
FileHandle.pm did not return a true value at -e line 1.
BEGIN failed--compilation aborted at -e line 1.
```

When I try to reinstall perl with "sudo aptitude reinstall perl perl-core perl-modules" I get the same error as above because aptitude tries to "finish" installing kdm first.

I also tried forcing kdm to be removed so I could fix Perl:
```

$ sudo dpkg --force-all -r kdm
dpkg: kdm: dependency problems, but removing anyway as you request:
 kubuntu-desktop depends on kdm.
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 98954 files and directories currently installed.)
Removing kdm ...
FileHandle.pm did not return a true value at /usr/share/perl5/Debconf/Template.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
   .... and so on as above

```

Any ideas?

Thanks in advance.

---

### Post by bwp_88 on 2008-02-01
Posting this for the benefit of others who may stumble across the same problem.

I solved it by setting aptitude to keep the same version of kdm and all related dependencies, then re-installing perl:

```
$ sudo dpkg --force-all -r perl-base
$ sudo apt-get install perl-base
```

---

### Post by jerricboy on 2008-04-29
woohoo! thanks! this solved the same problem i had with proftpd

---

