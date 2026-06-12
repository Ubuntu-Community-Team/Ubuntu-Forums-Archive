---
title: "Firefox cannot start after upgrade to 3.5"
date: 2009-09-03
forum: x86 64-bit Users
---

### Post by afeasfaerw23231233 on 2009-09-03
I've followed this guide 
[http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/](http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/)

installed Ubuntuzilla and run this command```

ubuntuzilla.py -a install -p firefox

```
But now firefox cannot start, even I run "firefox" in the terminal. 
```

/opt/firefox/firefox-bin: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory

```

Here's what shown up in the terminal during the installation
```

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.5.2.tar.bz2

Downloading Firefox archive from the Mozilla site

--13:47:50--  ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.2/linux-i686/en-US/firefox-3.5.2.tar.bz2
           => `firefox-3.5.2.tar.bz2'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.2/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.5.2.tar.bz2 ... done.
Length: 9,863,958 (9.4M) (unauthoritative)

100%[====================================>] 9,863,958    428.62K/s    ETA 00:00

13:48:34 (236.60 KB/s) - `firefox-3.5.2.tar.bz2' saved [9863958]


Downloading Firefox signature from the Mozilla site

--13:48:34--  ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.2/linux-i686/en-US/firefox-3.5.2.tar.bz2.asc
           => `firefox-3.5.2.tar.bz2.asc'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.2/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.5.2.tar.bz2.asc ... done.
Length: 194 (unauthoritative)

100%[====================================>] 194           --.--K/s             

13:48:38 (25.55 MB/s) - `firefox-3.5.2.tar.bz2.asc' saved [194]

tru::1:1229880839:0:3:1:5
gpg: error reading key: public key not found
gpg --list-keys --with-colons 0E3606D9
Mozilla GPG key not present on the system. Will attempt to retrieve from keyserver.
Process returned code 2

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: requesting key 812347DD from hkp server subkeys.pgp.net
gpg: key 0E3606D9: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: key 812347DD: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 2
gpg:               imported: 2
Successfully retrieved Mozilla Software Releases Public key from subkeys.pgp.net .


Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Friday, July 31, 2009 AM08:27:29 HKT using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8

Extracting archive

Trying to determine firefox plugin path...

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.5.2 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
no crontab for wong
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.


```
I am using Ubuntu 8.04 x64. Thanks!

Edit: Some additonal information
```
ls /usr/bin/firefox -l
lrwxrwxrwx 1 root root 20 2009-09-03 13:50 /usr/bin/firefox -> /opt/firefox/firefox

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
```

```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://hk.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://hk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://hk.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy universe
deb http://hk.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://hk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://hk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://hk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://hk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

## latex for Ooo 
deb http://www.fyma.ucl.ac.be/ubuntu feisty contrib

## vlc 1.0
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu hardy main 

```

---

### Post by utnubuuser on 2009-09-03
Hi -- don't really know what the issue might be, but this [http://www.psychocats.net/ubuntu/firefox]("http://www.psychocats.net/ubuntu/firefox") is the intruction I followed and it works well.

---

### Post by afeasfaerw23231233 on 2009-09-03
Thanks for the link. But still doesn't work
I've download the i686 version from mozilla's site and run this command from psychocats' tutorial
```
if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```
Same error message when attempting to run firefox 
```
firefox
/opt/firefox/firefox-bin: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory

```
Why I can't find a x64 version from mozilla's site? Only the i686 version available?

---

### Post by nanotube on 2009-09-03
Hi
well, first of all, not a big surprise that you are getting the same problem with both methods, since at the core, they both do the exact same thing.

unfortunately, mozilla doesn't release 64bit builds, and probably won't at least until ff4...

as to your specific problem: it appears to be a dependency bug in the hardy ia32 library. See this for more detail, and a workaround:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/253430](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/253430)

---

### Post by Yellow Pasque on 2009-09-03
Maybe try this PPA: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by afeasfaerw23231233 on 2009-09-03
Now would anyone please tell me how to reinstall firefox 3.0 version?
I've already reinstalled it from synaptic, but still get the same error message ```

 firefox
/opt/firefox/firefox-bin: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory

```

---

### Post by nanotube on 2009-09-04
as per the ubuntuzilla instructions, use the "remove" command to uninstall the mozilla build of 3.5 and go back to the repositories version.

```
ubuntuzilla.py -a remove -p firefox
```

[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by afeasfaerw23231233 on 2009-09-04
Thanks. Revert to 3.0 now.

---

