---
title: "Gutsy server useless due to segfaulting php5-cgi"
date: 2007-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by motin on 2007-12-16
On a freshly installed Gutsy server 64-bit machine, the latest version of php5-cgi is constantly segfaulting causing internal server 500 error messages!

We have five sites here currently:
 1. A drupal-based site
 2. A very simple single php-script based site
 3. A more complex custom developed php-based site
 4. A CakePHP-alfa based site
 5. A CakePHP-prebeta based site

Number 1,2 and 4 works fine, but 3 and 5 causes segfaults everytime!

Live report: Logs generated after a visit on site number 3:

/var/log/syslog:
```
Dec 14 10:35:31 Ubuntu-710-gutsy-64-minimal kernel: [632734.251124] php5-cgi[11686]: segfault at 00007fff5a9b1ff0 rip 00002b8951e62e38 rsp 00007fff5a9b1fb0 error 6

```
/var/log/apache2/error.log (with LogLevel debug):
```
[Fri Dec 14 10:35:30 2007] [warn] FastCGI: (dynamic) server "/var/www/fcgi/domain3.com/php5-fcgi-starter" (uid 2006, gid 2006) restarted (pid 11685)
[Fri Dec 14 10:35:33 2007] [warn] FastCGI: (dynamic) server "/var/www/fcgi/domain3.com/php5-fcgi-starter" (pid 11685) termination signaled
[Fri Dec 14 10:35:33 2007] [warn] FastCGI: (dynamic) server "/var/www/fcgi/domain3.com/php5-fcgi-starter" (pid 11685) terminated by calling exit with status '0'

```
Live report: Logs generated after a visit on site number 5:
/var/log/syslog:
```
Dec 14 10:37:28 Ubuntu-710-gutsy-64-minimal kernel: [632850.783120] php5-cgi[11572]: segfault at 00007fff0c83a5e8 rip 0000000000604c8d rsp 00007fff0c83a5c0 error 6

```
/var/log/apache2/error.log (with LogLevel debug):
```
[Fri Dec 14 10:37:28 2007] [warn] FastCGI: (dynamic) server "/var/www/fcgi/domain5.com/php5-fcgi-starter" (uid 2009, gid 2009) restarted (pid 11854)
[Fri Dec 14 10:37:34 2007] [warn] FastCGI: (dynamic) server "/var/www/fcgi/domain5.com/php5-fcgi-starter" (uid 2009, gid 2009) restarted (pid 11858)
[Fri Dec 14 10:37:40 2007] [warn] FastCGI: (dynamic) server "/var/www/fcgi/domain5.com/php5-fcgi-starter" (uid 2009, gid 2009) restarted (pid 11862)
[Fri Dec 14 10:37:45 2007] [warn] FastCGI: (dynamic) server "/var/www/fcgi/domain5.com/php5-fcgi-starter" (pid 11572) terminated due to uncaught signal '11' (H\x89l$\xe0L\x89l$\xf0H\x89\xfdL\x89t$\xf8H\x89\\$\xd8I\x89\xcdL\x89d$\xe8H\x83\xecHL\x8bgHH\x89T$\x10L\x89OPM\x89\xc6H\x8bD$PH\x89wpH\x89GXI\x83<$), a core file may have been generated

```
Note: This _may_ be related to [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/173817](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/173817) , but as you see above, the error messages differ.
As this is the 1ubuntu6.2 version, I do not think it is related to [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/173043](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/173043) .

I reported this as a bug here: [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/176324](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/176324) , but I'd be happiest if there is any workaround solution not to have to wait 3 months for a fix that may or may not be released for Gutsy...

Any help appreciated!

---

