---
title: "Locale problems in chroot"
date: 2006-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by hardhu on 2006-04-12
Hello everybody,
I have setup a dapper 32bit chroot environment (to run the newer version of tunderbird and firefox that are not yet available for amd64 breezy)  using the tutorial in the wiki, but I have some problems with locale settings:
----
(mychroot)root@eagle:/home/rick# dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_IT:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_US.ISO-8859-1... up-to-date
Generation complete.
----
Can anybody help me to solve this issue? TIA

---

### Post by mattb1982 on 2006-05-23
try this:

sudo apt-get install localeconf

---

### Post by chronobox on 2006-06-09
Try this too:

sudo localedef -i en_US -c -f UTF-8 en_US.UTF-8

---

### Post by hardhu on 2006-06-19
[QUOTE=chronobox]Try this too:

sudo localedef -i en_US -c -f UTF-8 en_US.UTF-8[/QUOTE]


I have tried both solutions, but none seemed to work. I have then successfully removed the problem by re-creating the chroot environment and manually generating locales with 'sudo locale-gen en_US' and 'sudo locale-gen en_US.UTF-8'.
I still don't understand why there is this strange line:

LANGUAGE="en_IT:en"

in my /etc/environment outside the chroot, maybe because in the installation process I have set English as my language  and Italy as my location, but this is giving me no problems.

---

### Post by swamytk on 2006-08-18
Interesting, I am facing this problem with fresh installation of Fedora Core 5 also. Thanks for solution, let me try at FC5.

---

