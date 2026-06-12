---
title: "Perl completely broken"
date: 2008-08-14
forum: x86 64-bit Users
---

### Post by obscurans on 2008-08-14
Tried apt-getting a package or two and that failed with some error messages about missing perl things, so:

```
/usr/lib/perl/5.8.8/auto/POSIX$ sudo apt-get install --reinstall perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4055kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can't locate auto/POSIX/autosplit.ix in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl/5.8/AutoLoader.pm line 160.
 at /usr/lib/perl/5.8/POSIX.pm line 7
Can't locate auto/POSIX/load_import.al in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/POSIX.pm line 15
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
```

As you can see reinstalling perl itself doesn't work...

```
$sudo apt-get source --compile perl
```

This fails as well, the same way.

```
E: /var/cache/apt/archives/perl-base_5.8.8-12_amd64.deb: unable to stat `./usr/lib/perl/5.8.8/auto/POSIX/autosplit.ix' (which I was about to install)
```

This is how Synaptic dies when I reinstall perl from it. So I unpacked the tarball myself. But now:

```
/usr/lib/perl/5.8.8/auto/POSIX$ sudo ls -l
chmod: cannot access `atol.al': Permission denied
chmod: cannot access `autosplit.ix': Permission denied
chmod: cannot access `bsearch.al': Permission denied
```

So not only do the files exist, root is banned from them? Every time I attempt anything that accesses these files, Firefox and the other active applications get "Uninterruptible" (read:unresponsive) status and everything generally hangs for a minute before the offending program gives up. Even kill -9 on the process hangs.

On a side note, my hard drive is on the way out (~10 bad sectors). Anyone seen this type of weirdness?

---

