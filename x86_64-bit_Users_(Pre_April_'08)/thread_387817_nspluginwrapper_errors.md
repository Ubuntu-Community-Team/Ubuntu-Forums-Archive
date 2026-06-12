---
title: "nspluginwrapper errors"
date: 2007-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by toecutter on 2007-03-18
Hi all, 

I'm new to Ubuntu - installed 6.10 last week and have just a little use on it - I'm slowly getting to terms with it and planning on getting DVD backup, my multi-button mouse, etc. working. 

One of the unforeseen things I struggled with early on was getting Flash to work in Firefox on the 64-bit version. I tried the various install methods from these threads:

[http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)
[http://ubuntuforums.org/showpost.php?p=2072904&postcount=30](http://ubuntuforums.org/showpost.php?p=2072904&postcount=30)
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)

I do now have Flash working on Firefox 32-bit, but when I try to install things I regularly get errors about 'nspluginwrapper' and the install doesn't go through. This happens when trying to get things working through terminal or Automatix, etc.

I didn't really understand that I'd have to go through a few hoops to get 64-bit version working just the way I want it, but that's okay - I knew I'd have to get through a few hoops to get other things working, so I don't mind the extra bit of hassle. I just want to be able to install stuff properly, and this nspluginwrapper thing seems to be a hurdle at the moment. 

I can't even get rid of 'orphaned' files (as outlined here: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)) because of this nspluginwrapper thing.

Does anyone have any ideas I can try to resolve this? Cheers! :)

---

### Post by jackrobinson on 2007-03-18
> **toecutter said:**
> Hi all, 

I'm new to Ubuntu - installed 6.10 last week and have just a little use on it - I'm slowly getting to terms with it and planning on getting DVD backup, my multi-button mouse, etc. working. 

One of the unforeseen things I struggled with early on was getting Flash to work in Firefox on the 64-bit version. I tried the various install methods from these threads:

[http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)
[http://ubuntuforums.org/showpost.php?p=2072904&postcount=30](http://ubuntuforums.org/showpost.php?p=2072904&postcount=30)
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)

I do now have Flash working on Firefox 32-bit, but when I try to install things I regularly get errors about 'nspluginwrapper' and the install doesn't go through. This happens when trying to get things working through terminal or Automatix, etc.

I didn't really understand that I'd have to go through a few hoops to get 64-bit version working just the way I want it, but that's okay - I knew I'd have to get through a few hoops to get other things working, so I don't mind the extra bit of hassle. I just want to be able to install stuff properly, and this nspluginwrapper thing seems to be a hurdle at the moment. 

I can't even get rid of 'orphaned' files (as outlined here: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)) because of this nspluginwrapper thing.

Does anyone have any ideas I can try to resolve this? Cheers! :)
paste the result of the following:
```
sudo apt-get -f install
```

---

### Post by toecutter on 2007-03-19
Thanks - here's what I get (a typical ending to attempted installs):

> [FONT="Courier New"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libktnef1 libkcal2b libkdepim1a libkmime2 libkleopatra1 libgpgme11
  libkpimidentities1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up nspluginwrapper (0.9.91.3-2) ...
Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Segmentation fault (core dumped)
dpkg: error processing nspluginwrapper (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 nspluginwrapper[/FONT]

I've gotten similar end messages to installing:

DVD Ripper
GNOME Baker
GAIM 2.0beta3.1
MPlayer
Multimedia Codecs
NIDSWrapperGdesklets
Azureus

and many others (these are just error reports from Automatix)

---

### Post by jackrobinson on 2007-03-19
> **toecutter said:**
> Thanks - here's what I get (a typical ending to attempted installs):



I've gotten similar end messages to installing:

DVD Ripper
GNOME Baker
GAIM 2.0beta3.1
MPlayer
Multimedia Codecs
NIDSWrapperGdesklets
Azureus

and many others (these are just error reports from Automatix)
ok do this:
```
sudo rm -f /var/lib/dpkg/info/nspluginwrapper.postrm
sudo rm -f /var/lib/dpkg/info/nspluginwrapper.prerm
sudo apt-get remove nspluginwrapper
```
All errors should go after this.

---

### Post by toecutter on 2007-03-19
Excellent, I'll try that as soon as I get home! (wishing I had remote desktop set up now :))

Last question - will this solution affect the Flash player in my 32-bit Firefox (which is why I installed the nspluginwrapper)?

Many many thanks for the help! :D

---

