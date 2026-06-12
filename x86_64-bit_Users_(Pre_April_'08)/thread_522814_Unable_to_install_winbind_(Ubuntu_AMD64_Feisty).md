---
title: "Unable to install winbind (Ubuntu AMD64 Feisty)"
date: 2007-08-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by bandoba on 2007-08-11
I just installed Ubuntu Fesity 64-bit (AMD64) on server running AMD64 4000+ processor. I now want to install winbind package. While installing that using apt-get I get following error...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  winbind: Depends: samba-common (= 3.0.24-2ubuntu1) but 3.0.24-2ubuntu1.2 is to be installed
E: Broken packages

```

I tried to uninstall existing samba-common using Synpatic Package Manager but it tells me that samba-common depends on smbclient and ubuntu-desktop. Since I don't want to uninstall ubuntu-desktop I was wondering if there is any way to get over that error?

TIA.

---

### Post by Kilz on 2007-08-11
> **bandoba said:**
> I just installed Ubuntu Fesity 64-bit (AMD64) on server running AMD64 4000+ processor. I now want to install winbind package. While installing that using apt-get I get following error...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  winbind: Depends: samba-common (= 3.0.24-2ubuntu1) but 3.0.24-2ubuntu1.2 is to be installed
E: Broken packages

```

I tried to uninstall existing samba-common using Synpatic Package Manager but it tells me that samba-common depends on smbclient and ubuntu-desktop. Since I don't want to uninstall ubuntu-desktop I was wondering if there is any way to get over that error?

TIA.

Did you follow the instructions and file a bug report on launchpad?

---

### Post by bandoba on 2007-08-12
Thanks for you reply Kliz. After posting the error, I checked my sources.list file and found that some of the repositories were disabled. I then enabled all repositories universe and multiverse specifically and uninstalled samba first. Then I reinstalled samba and winbind and everything worked fine.

---

### Post by Anubis on 2007-11-18
After todays update, Gutsy updated samba and winbind, but could not finish update because apt cannot start winbind.

---

