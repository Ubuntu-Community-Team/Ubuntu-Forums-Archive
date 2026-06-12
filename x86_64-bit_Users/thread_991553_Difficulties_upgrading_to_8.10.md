---
title: "Difficulties upgrading to 8.10"
date: 2008-11-23
forum: x86 64-bit Users
---

### Post by tibbar_eht on 2008-11-23
I have been having issues trying to upgrade to 8.10.  If I use the update manager or text line I still get to the same error.  it is as follows
```
W:Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/dists/gutsy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/dists/gutsy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

I have inserted the 7.10 CD and still get the same error.  Is there anyone out there that might have an idea how I can upgrade without having to reload from scratch?

Thanks in advance.

---

### Post by John Jason Jordan on 2008-11-23
> **tibbar_eht said:**
> I have been having issues trying to upgrade to 8.10.  If I use the update manager or text line I still get to the same error.  it is as follows
```
W:Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/dists/gutsy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/dists/gutsy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

I have inserted the 7.10 CD and still get the same error.  Is there anyone out there that might have an idea how I can upgrade without having to reload from scratch?

Did you mean upgrade to 8.10, or to 7.10? 

What version do you have right now? (Post the results of "uname -a" from the command line.)

You can add CD-ROMS with a GUI by going to System > Administration > Software Sources.

You can do the apt-get dist-upgrade over the net if you have a stable internet connection. But it takes a long time, so don't do it from a coffee shop or someplace where you might be interrupted.

---

### Post by tibbar_eht on 2008-11-23
The results of the uname is as follows:

```
Linux Usagi7 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux

```

I am trying to upgrade to 8.10.   I have the apt-get iso and followed the upgrade direction on the Ubuntu site. 

Thanks again.

---

### Post by John Jason Jordan on 2008-11-23
> **tibbar_eht said:**
> The results of the uname is as follows:

```
Linux Usagi7 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux

```

I am trying to upgrade to 8.10.   I have the apt-get iso and followed the upgrade direction on the Ubuntu site.

I have never done an upgrade from an iso - I have always done apt-get dist-upgrade from the command line with an internet connection. 

Evidently apt-get is looking for the Gutsy CD. I would suggest going into System > Administration > Software Sources and removing the 7.10 (Gutsy) CD from the list of sources.

---

### Post by tibbar_eht on 2008-11-24
Thank you I was not aware of the software sources area.  That did the trick.

Cheers

---

