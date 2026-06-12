---
title: "Installation hangs at folder selection"
date: 2008-01-29
forum: Wine
---

### Post by briansrapier on 2008-01-29
I am in the process of port the last of the apps I use in windows over to Ubuntu. The last remaining item is M$ Office Communicator (2005). I have looked at Pidgin-sipe, but it does not yet support TLS, so I'm back to Communicator.

I am trying to run the installation using:

```

$ wine msiexec /i COMMUNICATOR.MSI

```

All seems well until I get to the installation folder selection. The default is C:\Program Files\Microsoft Office Communicator\. Trying to click 'Next' does nothing. Even if I try to select a different directory, nothing. No errors either.

I am running Wine 0.9.54 on a Pentium dual-core 3.8 with 4 GB RAM. I should note that I successfully installed MS Office 2K3 without a hitch with the exception that Outlook will not work (this is noted in the appdb).

Any ideas on why this isn't working and the best approach to debugging it (from a 'newbie to wine' standpoint).

---

### Post by briansrapier on 2008-01-31
Bump, please.

---

### Post by adam1115 on 2008-02-24
It doesn't work.

Try Windows Messenger (the old version of LCS), it seems to work.

---

