---
title: "Perl warning: Setting locale failed"
date: 2006-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by jthompson on 2006-12-15
Ok I've read a thousand posts on this issue.  I am having this issue with 64 bit Edgy.

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en",
        LC_ALL = (unset),
        LANG = "en_US.ISO-8859-15"
    are supported and installed on your system.
```

This is driving me nuts.  I recently grabbed the update to the kernel from the update thingy.  I have tried all of the following and nothing works.
```

/etc/default/locale
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
```

```
/etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.ISO-8859-15"
LANGUAGE="en_US:en"
```

I have tried:
```

sudo locale-gen
sudo dpkg-reconfigure locales
```

I tried the package localeconf


Someone mentioned installing a later packge of locales (like version 2.5).  How do you do this?  The latest one I see in edgy is 2.3 something.

---

### Post by Kikoolol on 2006-12-15
Hi !

I had the same kind of issue during my upgrade to edgy ... it's really annoying ! You can fix it by setting correctly the locales in the /var/lib/locales/supported.d directory. You should find some files like "en" and/or "local", then just put the extra locales you want in one of it. To finish, run "dpkg-reconfigure locales" !

Hope this helps !

Kkl

---

### Post by jthompson on 2006-12-18
Ok these are what those two files look like:

```
en

en_US.ISO-8859-15 ISO-8859-15
en_HK.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_IN UTF-8
en_ZW.UTF-8 UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_SG.UTF-8 UTF-8
en_BW.UTF-8 UTF-8
en_ZA.UTF-8 UTF-8
en_CA.UTF-8 UTF-8
en_IE.UTF-8 UTF-8
```

```
local

en_US.UTF-8 UTF-8
en_US.ISO-8859-15 ISO-8859-15
```

I ran dpkg-reconfigure locales and I still get the same error.  It always seems to happen on things written in perl.

---

### Post by Kikoolol on 2006-12-18
Mine is (local) :

```
fr_FR ISO-8859-1
fr_FR.UTF-8 UTF-8
fr_FR@euro ISO-8859-15
```

Maybe you should try the same with "en" instead of "fr" ? The syntax seems to be different for UTF-8 and ISO entries.

Kkl

---

### Post by jthompson on 2006-12-18
I still get the error even after trying your suggestions.  Maybe its just this one perl script.  Its a setup script for the 2X terminal server.  [www.2x.com](www.2x.com).

---

### Post by Kikoolol on 2006-12-18
In my case, the problem happened when using apt (doing the dist-upgrade from dapper to edgy). For a lot of packages, it was displayed again & again on the terminal when "unpacking ..." & "setting ..." them. If you often upgrade your distro using apt and without seeing this kind of message, then yes I guess this particular script you are talking about may be in cause ...

Good luck !

Kkl

---

### Post by alvenegas on 2007-01-25
Hello, 

I get the same errors and by following the various suggestions 
posted here and in other threads, I still have the same problem.
I post here because I believe it is a problem of a32 vs. 64 bit.
When I use perl or other utilities (for example I get Gtk Warning
locale problems as well when invoking firefox32) I get same 
sort of locale problems that fall back to 'C'.  

My problem is that although for 64 bit utilities it does not complain, 
for 32 it does, perhaps it has something to do with it.  Any help will
be greatly appreciated,

> 
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").


When I do 'locale -a' I get :
> 
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX



I do not have any other locale (ISO8859) and I do not know why.  Every time
I run dpkg-reconfigure locales I get:
> 
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.



When I invoke firefox32: I get the following error:
> 
(firefox-bin:21674): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.


Any suggestions other than doing:
sudo apt-get install localeconf
dpkg-reconfigure locales

Any suggestion keeping in mind that it may be a 32 to 64bit consequence?

Thanks in andvance

---

### Post by incubus on 2007-01-25
What about:

```

$ sudo apt-get install --reinstall language-pack-en

```

Of course, replace "en" with your language abbreviation.

incubus

---

### Post by Random20220612 on 2007-01-27
marcelo@marcelo:~$
marcelo@marcelo:~$ sudo apt-get install --reinstall language-pack-es
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsmokeqt1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/180kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "es_ES",
        LC_ALL = "es_ES",
        LC_LANG = "es_ES",
        LANG = "es_ES"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 147473 files and directories currently installed.)
Preparing to replace language-pack-es 1:6.10+20061130 (using .../language-pack-es_1%3a6.10+20061130_all.deb) ...
Unpacking replacement language-pack-es ...
Setting up language-pack-es (6.10+20061130) ...
marcelo@marcelo:~$

---

### Post by Random20220612 on 2007-02-01
This problem was finally solved adding the following lines in the terminal:

cd /usr/lib/locale

sudo ln -s es_ES.utf8 es_ES :D

---

### Post by incubus on 2007-02-01
That was a great job, marcelo.

I hope the other people will get to see your finding.

incubus

PS: perhaps you could point that out on launchpad and let developers know.

---

### Post by uantuzri on 2007-02-03
> **marceloramone said:**
> This problem was finally solved adding the following lines in the terminal:

cd /usr/lib/locale

sudo ln -s es_ES.utf8 es_ES :D

I've been messing with all this for days and the solution was so easy... 

The problem has nothing to do with the 32 vs 64 bits. I'm running a 32-bit box and I had the same problem and the same solution.

Great job, Marcelo!

---

### Post by StarQuake on 2007-02-21
I'm having the problem with en_GB.utf8 but that command doesn't fix it for me. The directory /usr/lib/locale/en_GB also already exists.
This is what i get when running perl:
```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```

---

### Post by urs_buddy7 on 2007-02-22
I also faced same problems...

But it finally got solved using thsi command.

sudo aptitude install locales

-cheers

---

### Post by namit on 2007-03-15
Seams to have worked for me also thanks

---

### Post by ringmaster on 2007-03-20
Worked for me, too. Great job! Is this a bug? I have been waiting too long for this solution!!

Thanks again.

---

### Post by subssn594 on 2007-08-12
This worked for me, too, but using en_US.

---

### Post by TechZilla on 2007-09-23
just switched from debian unstable.... so I deleted "Language-pack-en" thinking it was bloat

...all better after instlling it again

---

### Post by duden on 2007-10-20
An alternative solution to making a symbolic link, is simply to specify the "correct" locale in your environment. If you have the right locale installed, you can see the precise name from the output of dpkg-reconfigure locales. Then you'd add the following to your .bashrc or .zshrc file:

export LC_ALL=es_ES-UTF8
export LANG=es_ES-UTF8

This is probably a better solution than messing around with symbolic links in the filesystem :)

---

### Post by mcdonaldsguy on 2008-01-14
Alternatively, change the environment variable in /etc/environment to make it available system-wide.

For example, my LANG was "en_US" in /etc/environment, but /usr/lib/locale/en_US did not exist. /usr/lib/locale/en_US.utf8 did, so changing LANG to "en_US.UTF8" fixed the problem.

Fwiw, this is a common problem when installing a system via debootstrap.

---

### Post by xithilinx on 2008-07-22
> **duden said:**
> An alternative solution to making a symbolic link, is simply to specify the "correct" locale in your environment. If you have the right locale installed, you can see the precise name from the output of dpkg-reconfigure locales. Then you'd add the following to your .bashrc or .zshrc file:

export LC_ALL=es_ES-UTF8
export LANG=es_ES-UTF8

This is probably a better solution than messing around with symbolic links in the filesystem :)

You are the only person on the internet that I've found that has a fix to this problem.

let me just by say " I FRIGGEN LOVE YOU ". I just wasted about and hour and a half messing with this, and finally I can live in peace again!! :)

---

