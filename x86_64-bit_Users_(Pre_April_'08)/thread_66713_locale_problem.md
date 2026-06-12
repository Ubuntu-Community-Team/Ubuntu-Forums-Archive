---
title: "locale problem"
date: 2005-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by hack_benjamin on 2005-09-18
Whenever i install any program I get this error:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en",
        LC_ALL = (unset),
        LANG = "en_US:en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

anyone help?

---

### Post by Corbelius on 2005-09-18
The liblocale-gettext-perl package is installed?

---

### Post by hack_benjamin on 2005-09-18
yep, and claims to be the newest.

This is my * /etc/environment *

```
LANGUAGE="en_GB:en"

LANG=en_GB.UTF-8

```

---

### Post by Corbelius on 2005-09-18
[QUOTE=hack_benjamin]yep, and claims to be the newest.

This is my * /etc/environment *

```
LANGUAGE="en_GB:en"

LANG=en_GB.UTF-8

```[/QUOTE]

Install localeconf and: dpkg-reconfigure localeconf

---

### Post by hack_benjamin on 2005-09-20
still doing the same thing after installing localeconf and reconfiguring it, and using source /etc/profile

any idea?

---

### Post by Kemotaha on 2005-09-20
I actually got this message all the way through my breezy upgrade on my 32-bit laptop.  I don't know where it is from but doesn't seem to have a negative impact;  at least I haven't seen one.

---

### Post by MBMESSAOUD on 2005-09-21
Hello
I got the same problem

when I tried to install localeconf_0.9.4_all.deb
I get these errors
Selecting previously deselected package localeconf.
(Reading database ... 85131 files and directories currently installed.)
Unpacking localeconf (from localeconf_0.9.4_all.deb) ...
Setting up localeconf (0.9.4) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_TN:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_CTYPE to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_MESSAGES to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_ALL to default locale: No such file or directory

and localeconf_0.9.4_all.deb is not installed

how to How to set LC_CTYPE, LC_MESSAGES, LC_ALL ?

---

### Post by mlomker on 2005-09-21
[This is](http://www.ubuntuforums.org/showthread.php?t=67209) a similar thread, take a look at that and see if it helps.

---

### Post by MBMESSAOUD on 2005-09-21
I have installed new package locales_2.3.5-1ubuntu11_all.deb
 and thers is no problem about locales

Thank you all \\:D/

---

### Post by MblKiTA on 2005-10-31
I"ve got the same problem with the locales:
[PHP]
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
[/PHP]

when I"ve tried to install locales_2.3.5-1ubuntu12_all.deb I"ve recieved the following:
[PHP]
root@nikita:/home/mblkita/downloads # dpkg -i locales_2.3.5-1ubuntu12_all.deb
dpkg: status database area is locked by another process
root@nikita:/home/mblkita/downloads # dpkg -i locales_2.3.5-1ubuntu12_all.deb
Selecting previously deselected package locales.
(Reading database ... 58410 files and directories currently installed.)
Unpacking locales (from locales_2.3.5-1ubuntu12_all.deb) ...
dpkg: dependency problems prevent configuration of locales:
 locales depends on glibc-2.3.5-0ubuntu1; however:
  Package glibc-2.3.5-0ubuntu1 is not installed.
dpkg: error processing locales (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 locales
[/PHP]

I see that I need glibc-2.3.5-0ubuntu1 but where can I get it?

---

### Post by charlieg on 2005-11-23
This fixed things for me:
```
$ apt-get install -f
```

I did it in the middle of the upgrade and it made those locale error messages disappear.

---

### Post by kawinter on 2005-11-24
I tried running apt-get install -f and the message I got was:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

So I ran dpkg --configure -a and my computer crashed and rebooted.  Any ideas?

---

