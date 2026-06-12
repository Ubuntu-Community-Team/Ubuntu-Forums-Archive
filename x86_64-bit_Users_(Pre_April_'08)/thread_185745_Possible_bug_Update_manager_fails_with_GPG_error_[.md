---
title: "Possible bug: Update manager fails with GPG error [including a possible workaround]"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by mojamoja on 2006-06-01
Standard installation, I didn't mess with stuff yet.

When running the update manager (manually or when clicking the "updates available" icon).

Upon clicking Check to check for new updates I get the following error:

```
W: GPG error: http://security.ubuntu.com breezy-security Release: Unknown error executing gpgv
W: GPG error: http://dk.archive.ubuntu.com breezy Release: Unknown error executing gpgv
W: GPG error: http://dk.archive.ubuntu.com breezy-updates Release: Unknown error executing gpgv
```gpgv: keyblock resource 

I tried running gpgv in a console:
```
`/home/tor/.gnupg/trustedkeys.gpg': general error
```

I did 
```

tor@gyuudon:~$ touch .gnupg/trustedkeys.gpg
tor@gyuudon:~$ gpgv
```

So touching the file solves the problem with gpgv, however I still get the same error from update-manager. I touched the file for root as well.

---

### Post by spawn968 on 2006-06-08
I had a similiar problem after dusting off my computer from when I moved, and it turned out the system clock was set to sometime in 2003.  Gpg wouldn't import keys with that much variation in time.  Wish I could help you more than that, but that's what worked for me.  Try importing a key with "gpg --keyserver subkeys.pgp.net --recv 437D05B5" and see what it says

---

### Post by rcatman on 2006-06-15
I'm having the same problmen. I typed in 'gpg --keyserver subkeys.pgp.net --recv 437D05B5". 

ryan@rubuntu:~$ gpg --keyserver subkeys.pgp.net --recv 437D05B5
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpg: key 437D05B5 was created 60908747 seconds in the future (time warp or clock problem)
gpg: key 437D05B5 was created 60908747 seconds in the future (time warp or clock problem)
gpg: key 437D05B5 was created 60908747 seconds in the future (time warp or clock problem)
gpg: key 437D05B5 was created 60908747 seconds in the future (time warp or clock problem)
gpg: key 437D05B5: no valid user IDs
gpg: this may be caused by a missing self-signature
gpg: Total number processed: 1
gpg:           w/o user IDs: 1
ryan@rubuntu:~$ sudo apt-get updaGet:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Fetched 945B in 2s (423B/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: Unknown error executing gpgvW: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: Unknown error executing gpgvW: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: Unknown error executing gpgvW: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release: Unknown error executing gpgvW: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: Unknown error executing gpgvW: You may want to run apt-get update to correct these problems

Whats going on???? Obviously theres something wrong with my system clock and its interrupting the update. What did this do anyways?

---

### Post by biocrasher on 2006-06-15
I  had the exact same problem today, after a hardware upgrade.
As spawn968 said I also noticed that the clock was set back to 2003 something.
Setting it right fixed everything
(I was aslo getting warnings from konqueror, kdewalet and others about not trusted certificates).

---

