---
title: "A simple hope for Gutsy"
date: 2007-10-15
forum: Za Team - South Africa
---

### Post by flarkit on 2007-10-15
After installing Feisty over the past 2 weeks, I have just this 1 hope:

That I'll be able to upgrade my Feisty installation smoothly to Gutsy. I'd hate to have to reinstall from scratch, and the downloads associated with that. Is it even possible to archive the downloaded installation files on my PC?

My 3D works, my multimedia works, my Compiz Fusion works, my Anjuta works, so I'd really prefer not to reinstall it all again.
:)

---

### Post by davidshere on 2007-10-15
I've been running a Beta version of Gutsy on a test machine of mine that I upgraded from Feisty, which I upgraded from Edgy. They've simplified the upgrade process greatly over the last few releases.  I don't anticipate any problem bringing my two production machines up to 7.1.

---

### Post by flarkit on 2007-10-16
(very, very odd... my previous attempt at this has vanished...)

**FWIW:**


When Ubuntu's Gutsy Gibbon (7.10) is released on Thrusday there will be a mad rush to download updates and ISOs from Ubuntu's servers. This article will explain various ways to upgrade to the latest and greatest by avoiding to download rush.

**Upgrading to Ubuntu 7.10 now, before the rush**
To upgrade to Ubuntu 7.10 now, before the rush, by following these instructions:

    1. Open a terminal window *(Applications -> Accessories -> Terminal*)
    2. Run the following command:

    *update-manager -d* (**after Oct 18th, remove the -d option**) 

[IMG]http://www.thelinuxstore.ca/static/ubuntu_7_10_upgrade/Screenshot-Update%20Manager.jpg[/IMG]

     3. Follow the on-screen instructions

This will upgrade to the release candidate, which is considered complete and stable. On Oct 18th, apply the updates and you will be running 7.10 final release.

Note: *This works only if you are running Ubuntu 7.04. If you are running an older version apply the upgrades in steps (for example, Ubuntu 6.10 -> Ubuntu 7.04 -> Ubuntu 7.10) using the update-manager. Otherwise you may break your Ubuntu installation.*

**Installing Ubuntu 7.10 Release Candidate**
If you are not running Ubuntu download the release candidate ISO image and install it:
[http://releases.ubuntu.com/7.10/ubuntu-7.10-rc-desktop-i386.iso](http://releases.ubuntu.com/7.10/ubuntu-7.10-rc-desktop-i386.iso)
or [http://releases.ubuntu.com/7.10/ubuntu-7.10-rc-desktop-amd64.iso](http://releases.ubuntu.com/7.10/ubuntu-7.10-rc-desktop-amd64.iso)

After installing Ubuntu using the release candidate ISO, apply updates on Oct 18th and you will be running 7.10 final release.
Downloading Ubuntu 7.10 Final Release
If you want to wait until the final release is available:
Try downloading from an Ubuntu mirror
Download the torrent, watch LinuxTracker.org
Slow connection? Slow download?
Order a free Ubuntu 7.10 disc from Ubuntu's ShipIt program (up to 8 weeks for delivery)
Order Ubuntu 7.10 discs from TheLinuxStore.ca (1-5 days for delivery).

[http://www.thelinuxstore.ca/static/ubuntu_7_10_upgrade.html](http://www.thelinuxstore.ca/static/ubuntu_7_10_upgrade.html)

---

### Post by flarkit on 2007-10-17
Tsk. Tsk!

Spent hours doing backups, including that lovely program APTonCD. Then tried doing the update to 7.10. This simply fails with the following:

> sudo update-manager -c -d
warning: could not initiate dbus
extracting '/tmp/tmpzqaugo/gutsy.tar.gz'
authenticate '/tmp/tmpzqaugo/gutsy.tar.gz' against '/tmp/tmpzqaugo/gutsy.tar.gz.gpg'
exception from gpg: GnuPG exited non-zero, with code 65536
Debug information:

gpg: WARNING: unsafe permissions on homedir `/tmp/tmpzqaugo'

gpg: Signature made Fri 05 Oct 2007 22:32:21 SAST using DSA key ID 437D05B5
gpg: /tmp/tmpzqaugo/trustdb.gpg: trustdb created
gpg: BAD signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

Has anyone managed to update to the RC?
:confused:

---

