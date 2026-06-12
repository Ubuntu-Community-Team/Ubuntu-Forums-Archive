---
title: "Scribus Needs Updating"
date: 2006-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2006-11-16
Hi guys, I noticed scribus has been updated to 1.3.3.5 now but my edgy system still has 1.3.3.4

i think scribus should keep being updated with these releases as these are important bug fixes that scribus users really need straight away, lots of features are still buggy so please keep the updated packages coming with release ubuntu guys...

---

### Post by RAOF on 2006-11-17
> **jonah1980 said:**
> Hi guys, I noticed scribus has been updated to 1.3.3.5 now but my edgy system still has 1.3.3.4

i think scribus should keep being updated with these releases as these are important bug fixes that scribus users really need straight away, lots of features are still buggy so please keep the updated packages coming with release ubuntu guys...

They're unlikely to hit the official repositories, but if you ask really nicely (and I find the time) I'll add them to mine :).

For bonus marks, you could either write or point me to a program that monitors a directory, and then runs a list of programs on any new files matching *.dsc added to the directory :).

---

### Post by paperclip on 2006-11-17
[http://www.scribus.net/index.php?name=Sections&req=viewarticle&artid=4&page=1](http://www.scribus.net/index.php?name=Sections&req=viewarticle&artid=4&page=1)

This link is for the Scribus repositories for Debian based distros.  I'm running Scribus 1.3.3.5 on my dapper install.

Ad this to your sources..

```
# debian.scribus.net - Primary repository
    
deb http://debian.scribus.net/debian dapper main restricted
    
deb-src http://debian.scribus.net/debian dapper main restricted
    
# debian.tagancha.org - Backup repository
    
deb http://debian.tagancha.org/debian dapper main restricted
    
deb-src http://debian.tagancha.org/debian dapper main restricted
```

then run this..

```
sudo aptitude update
sudo aptitude install scribus-ng
```

---

### Post by jonah1980 on 2006-11-17
this won't work for amd64 though, cos they don't have packages for 64bit, but thanks for suggestions.

and roaf, would you be so kind, you're a lovely nice person and that would be awesome if you could supply an edgy up-to-date scribus...

---

### Post by kleeman on 2006-11-17
I did it. The deb is a quality one prepared with 

fakeroot debian/rules binary

and works fine on my system. Get it here:

[http://www.yourfilelink.com/get.php?fid=215444](http://www.yourfilelink.com/get.php?fid=215444)

Install with

sudo dpkg -i scribus-ng_1.3.3.5.dfsg-1_amd64.deb

---

### Post by jonah1980 on 2006-11-17
wow cool thanks

---

### Post by John Jason Jordan on 2006-11-17
> **kleeman said:**
> I did it. The deb is a quality one prepared with 
fakeroot debian/rules binary
and works fine on my system. Get it here:
[http://www.yourfilelink.com/get.php?fid=215444](http://www.yourfilelink.com/get.php?fid=215444)
Install with
sudo dpkg -i scribus-ng_1.3.3.5.dfsg-1_amd64.deb
OK, I downloaded the file. But I have 1.3.3.2 installed from Synaptic (scribus-ng). Before I install 1.3.3.5, do I need to uninstall 1.3.3.2?

---

### Post by kleeman on 2006-11-17
Nope it installs over the top. You'll see the edgy version in the version tab of synaptic.

---

### Post by John Jason Jordan on 2006-11-17
> **kleeman said:**
> Nope it installs over the top. You'll see the edgy version in the version tab of synaptic.
Didn't work. :(

Here are the error messages:

```
(Reading database ... 126253 files and directories currently installed.)
Preparing to replace scribus-ng 1.3.3.2.dfsg-1~dapper1 (using .../scribus-ng_1.3 .3.5.dfsg-1_amd64.deb) ...
Unpacking replacement scribus-ng ...
dpkg: dependency problems prevent configuration of scribus-ng:
 scribus-ng depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 scribus-ng depends on libcupsys2 (>= 1.2.3); however:
  Version of libcupsys2 on system is 1.2.2-0ubuntu0.6.06.
 scribus-ng depends on libfreetype6 (>= 2.2); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu2.2.
 scribus-ng depends on libgcc1 (>= 1:4.1.1-12); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 scribus-ng depends on libgnutls13 (>= 1.4.0-0); however:
  Package libgnutls13 is not installed.
 scribus-ng depends on libgpg-error0 (>= 1.2); however:
  Version of libgpg-error0 on system is 1.1-4.
 scribus-ng depends on libstdc++6 (>= 4.1.1-12); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
 scribus-ng depends on libtasn1-3 (>= 0.3.4); however:
  Package libtasn1-3 is not installed.
 scribus-ng depends on libxml2 (>= 2.6.26); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
dpkg: error processing scribus-ng (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 scribus-ng
```

I'm not a programmer or a Linux guru, so I don't know what any of that means, except that evidently 1.3.3.5 requires a bunch of libraries that 1.3.3.2 did not.

---

### Post by jonah1980 on 2006-11-17
worked great for me, but i did have 1.3.3.4 already installed...

---

### Post by kleeman on 2006-11-17
> **John Jason Jordan said:**
> Didn't work. :(

Here are the error messages:

```
(Reading database ... 126253 files and directories currently installed.)
Preparing to replace scribus-ng 1.3.3.2.dfsg-1~dapper1 (using .../scribus-ng_1.3 .3.5.dfsg-1_amd64.deb) ...
Unpacking replacement scribus-ng ...
dpkg: dependency problems prevent configuration of scribus-ng:
 scribus-ng depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 scribus-ng depends on libcupsys2 (>= 1.2.3); however:
  Version of libcupsys2 on system is 1.2.2-0ubuntu0.6.06.
 scribus-ng depends on libfreetype6 (>= 2.2); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu2.2.
 scribus-ng depends on libgcc1 (>= 1:4.1.1-12); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 scribus-ng depends on libgnutls13 (>= 1.4.0-0); however:
  Package libgnutls13 is not installed.
 scribus-ng depends on libgpg-error0 (>= 1.2); however:
  Version of libgpg-error0 on system is 1.1-4.
 scribus-ng depends on libstdc++6 (>= 4.1.1-12); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
 scribus-ng depends on libtasn1-3 (>= 0.3.4); however:
  Package libtasn1-3 is not installed.
 scribus-ng depends on libxml2 (>= 2.6.26); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
dpkg: error processing scribus-ng (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 scribus-ng
```

I'm not a programmer or a Linux guru, so I don't know what any of that means, except that evidently 1.3.3.5 requires a bunch of libraries that 1.3.3.2 did not.
You look like you are running dapper not edgy. The package will only work on edgy unfortunately because I no longer run dapper.

---

### Post by paperclip on 2006-11-17
For Dapper see my post above.. :)  I didn't realize that I was in the 64-bit x86 forum.. yikes..

Jonah1980: gp2xuser.com is 404

---

### Post by paperclip on 2006-11-17
Ok.. that makes no sense.. 

Sorry.. I'm going to stop now..

---

### Post by RAOF on 2006-11-17
> **jonah1980 said:**
> this won't work for amd64 though, cos they don't have packages for 64bit, but thanks for suggestions.

and roaf, would you be so kind, you're a lovely nice person and that would be awesome if you could supply an edgy up-to-date scribus...

Your wish is my command :).  The Misc section of my Edgy repository will soon contain Feisty's scribus-ng_1.3.3.5.dfsg-1.  Just as soon as it's finished building.  Man, it's pretty big, and C++ always takes a while :).

Edit: I'll also build it for Dapper, although that might not work so well.  It build-depends on some more recent toolchain stuff than you find in Dapper.

---

### Post by jonah1980 on 2007-02-04
hey guys anyone got scribus 1.3.3.7 for amd64 yet? i'm on feisty but no doubt edgy version might work....

---

### Post by John Jason Jordan on 2007-02-05
I had Scribus 1.3.3.4 o my Edgy amd64 computer and I just noticed that Update Manager listed Scribus as upgradable. But when I tried to do it I could not. It said the public key for the Janvitus repository was incorrect. It worked before, something must have changed. So I closed Update Manager and opened Synaptic. Scribus-ng 1.3.3.4 was the latest listing, but it had an upgradable marker on it, so I right-clicked and told Synaptic to upgrade it. Synaptic proceeded to do so without problem. Afterwards I launched Scribus and the Help > About screen said it was 1.3.3.5.

Update Manager is also happy now, but I don't understand why Update Manager could not find it but Synaptic could. Oh well. I would like to fix the Janvitus repository key problem, though.

---

### Post by RAOF on 2007-02-05
> **jonah1980 said:**
> hey guys anyone got scribus 1.3.3.7 for amd64 yet? i'm on feisty but no doubt edgy version might work....

AMD64 builds for both edgy and feisty are now hitting my repositories.  Knock yourselves out.

---

### Post by John Jason Jordan on 2007-02-05
> **RAOF said:**
> AMD64 builds for both edgy and feisty are now hitting my repositories.  Knock yourselves out.
Great! Just installed the upgrade. Except the Help > About screen says it is 1.3.3.6cvs, not 1.3.3.7. Oh well. 
Thanks!

---

### Post by RAOF on 2007-02-05
> **John Jason Jordan said:**
> Great! Just installed the upgrade. Except the Help > About screen says it is 1.3.3.6cvs, not 1.3.3.7. Oh well. 
Thanks!

They're built from official 1.3.3.7 deb-src provided by the Scribus project.  Go file a bug against their packages :).

---

### Post by jonah1980 on 2007-02-06
hey thanks man :)

---

### Post by cmost on 2007-02-06
Umm, perhaps a stupid question:  How does one access your repository RAOF?  I skimmed through the entire thread but didn't see any repo listing.  Thanks.

---

### Post by RAOF on 2007-02-06
Links in my sig, so they're all over the place.

The US mirror is down, though.  I really need to follow that up :).

---

