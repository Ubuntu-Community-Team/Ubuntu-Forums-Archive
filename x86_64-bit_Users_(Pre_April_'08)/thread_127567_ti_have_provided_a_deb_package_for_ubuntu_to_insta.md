---
title: "ti have provided a deb package for ubuntu to install firefox 1.5.0.1 on amd64 machine"
date: 2006-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by hasek on 2006-02-09
hello friends,

i have created a deb ubuntu package for latest version of firefox for amd64 architecture

you can download it at

[http://s1m0ne.free.fr/firefox_1.5.0.1-1_amd64.deb](http://s1m0ne.free.fr/firefox_1.5.0.1-1_amd64.deb)

to install it do

sudo dpkg -i firefox_1.5.0.1-1_amd64.deb

it also update synaptic

---

### Post by davidcrickett on 2006-02-09
... but it says the package has the wrong architecture for AMD64. :confused:

---

### Post by Stormbringer on 2006-02-09
The architecture of the package is fine ... the problem is another one:

sudo dpkg -i firefox_1.5.0.1-1_amd64.deb results in the following error-message:

```

dpkg: regarding firefox_1.5.0.1-1_amd64.deb containing firefox:
 mozilla-firefox-locale-en-gb conflicts with firefox (>> 1.0.999)

```

hasek, any thoughts on how to install your package without breaking anything?

---

### Post by hasek on 2006-02-10
[QUOTE=Stormbringer]The architecture of the package is fine ... the problem is another one:

sudo dpkg -i firefox_1.5.0.1-1_amd64.deb results in the following error-message:

```

dpkg: regarding firefox_1.5.0.1-1_amd64.deb containing firefox:
 mozilla-firefox-locale-en-gb conflicts with firefox (>> 1.0.999)

```

hasek, any thoughts on how to install your package without breaking anything?[/QUOTE]
don't worry Stormbringer, you will not break anything this conflict is normal as you havent completely uninstall all previous firefox versions

just do "apt-get remove mozilla-firefox-locale-en-gb"

and then "again dpkg -i firefox_1.5.0.1-1_amd64.deb"

firefox 1.5.0.1 is uncompatible with 1.0, just remove the damned package "mozilla-firefox-locale-en-gb"

it will work

---

### Post by hasek on 2006-02-10
[QUOTE=davidcrickett]... but it says the package has the wrong architecture for AMD64. :confused:[/QUOTE]

what kind of architecture have you ?

please do "uname -a" and give me the result

---

### Post by Stormbringer on 2006-02-10
> **hasek]don't worry Stormbringer, you will not break anything this conflict is normal as you havent completely uninstall all previous firefox versions

just do "apt-get remove mozilla-firefox-locale-en-gb"

and then "again dpkg -i firefox_1.5.0.1-1_amd64.deb"

it will work[/QUOTE]

Hi, hasek!

First off, thanks for taking your time to provide a AMD64 deb.

Got it installed - I removed "mozilla-firefox-locale-en-gb" along with "language-support-en" - but now I seem to have another problem (sorry for being such a pain):

Firefox starts up, shows a "Checking for compatiblity updates" window for a second and finally displays the "Welcome" page.

- At the bottom of the window I have a BIG grey bar, displaying a red "^", right under the statusbar that doesn't seem to go away. I saved my old profile and tried to start with a new one - but the problem persists.

- Firefox doesn't take any input from the keyboard. If I try to type in some URL it doesn't work said:**
> 
firefox 1.5.0.1 is uncompatible with 1.0


That what bugs me the most --- the annoyingly deep integration of Firefox into Ubuntu is as disturbing as the browser-integration of another famous operating system (you know, the one carrying a flag in its logo). Sorry for the rant - but I felt to express this.

---

### Post by hasek on 2006-02-10
have you uninstall properly all firefox packages ?

"apt-get remove mozilla-firefox" to remove previous ubuntu version 1.0.7

you can use synaptic as well by doing a search firefox and uninstall any package concerning firefox

if issues are still there

the issue is strange, my friend of mine installed it with no issues at all, may be some strange incompatibility, with your gnome libraries

first of all remove it just do apt-get remove firefox, it will remove properly my deb package.

try to reinstall it by being root if still not working uninstall the package


loggin as root

We will check if with a compiled version it does the same.

download the firefox source at [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.1/source/firefox-1.5.0.1-source.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.1/source/firefox-1.5.0.1-source.tar.bz2)

unpack this by doing tar xvjf firefox-1.5.0.1-source.tar.bz2 in /root/
go in the mozilla unpacked directory

go in this mozilla directory

do a "ac_cv_visibility_pragma=no ./configure --enable-application=browser"

if no errors

then do ./make

if no compile errors

you can do 

make install, 

and firefox 1.5.0.1 is installed.

i can help you if you got compile errors

if the bugs are still here, i really don't have a clue

---

### Post by Andrew Shimmin on 2006-02-10
I've got the same trouble Stormbringer does, with this.  I checked the FF forums and the grey bar below the status bar is usually an extension conflict.  I disabled each (then, finally, every) of my extensions, and reloaded. No good.  It ignores all boundries, running text from anywhere over onto whatever is next to it.  I'll try uninstalling and re-installing. Then, if that doesn't work, compiling my own, I guess. Is Deer Park really better than 1.0.7?

---

### Post by davidcrickett on 2006-02-10
Linux KONGARTHUR 2.6.12-10-amd64-generic #1 Mon Jan 16 17:16:24 UTC 2006 x86_64 GNU/Linux

---

### Post by hasek on 2006-02-13
be sure than in synaptic there is no more package related to firefox 1.07. move your  .mozilla/ in your home user directory. 

delete any /usr/local/lib/firefox or mozilla libraries

reinstall my package. If still not working follow my procedure for recompiling it yourself

---

### Post by Stormbringer on 2006-02-13
Hi, hasek!

Thanks for the advice ... after going through some trouble I finally managed to compile FF 1.5.0.1 myself.

Sorry to say, but it didn't solve the problems I mentioned above - the huge gray bar on the bottom is still there, and FF keeps on misbehaving. Cannot be related to some extension conflict (see Andrew Shimmin's post) since I started with an absolutely new and clean profile.

I'm giving up on this this matter ... will wait for Dapper to get FF 1.5 amd64.

Note to Ubuntu devs: How about revamping your update policy a little and provide Firefox / Thunderbird Updates to Breezy (x86 / x86_64) users?

---

