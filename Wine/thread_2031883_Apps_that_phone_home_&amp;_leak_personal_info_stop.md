---
title: "Apps that phone home &amp; leak personal info: stop them in wine with AppArmor"
date: 2012-07-22
forum: Wine
---

### Post by foresto on 2012-07-22
I don't like software to "phone home", partly out of principle, but mainly because there have been so many examples of programs collecting and exposing personal information without the user's permission.

Back when I was using Windows, the solution was to install a personal firewall.  When I switched to Linux, I found that it didn't really have an equivalent.  (While the Linux built-in firewall is good at keeping intruders out, it offers no easy way for a user to limit network access on a per-application basis.)  Perhaps this is because most Linux software is open source, making its network behavior easy to discover, and personal firewalls unnecessary.  Of course, Windows software (running with wine) can still sneak around on the network without my knowledge.

My solution:  AppArmor profiles for wine and its helper programs.  I put these together over the weekend with guidance from [this wiki page]("http://wiki.apparmor.net/index.php/AppArmorWine").  I'm posting here in case anyone else finds my work useful.

The profiles are defined in two files; one for the profile-specific stuff and one to hold all the common parts.  (Putting everything in one file would have required a lot of duplicate text, since AppArmor doesn't seem to have a macro syntax.)  Here they are:

File 1: [COLOR="DarkGreen"]/etc/apparmor.d/usr.bin.wine[/COLOR]
```

# Last Modified: Fri Jul 20 22:13:58 2012
#include <tunables/global>

/usr/bin/wine {

  #include <local/winecommon>

  /usr/bin/wine mr,
  /usr/bin/wine-preloader px,

}


/usr/bin/wineserver {

  #include <local/winecommon>

  capability sys_ptrace, # for wine crash dumps

  owner /proc/*/mem r,
  /usr/bin/wineserver mr,

}


/usr/bin/wine-preloader {

  #include <abstractions/nvidia>
  #include <local/winecommon>

  owner /proc/*/fd/ r,
  owner /proc/*/status r,
  owner /proc/*/task/ r,
  /usr/bin/update-mime-database rPix,
  /usr/bin/update-mime-database-real rPix,
  /usr/bin/update-desktop-database Pix,
  /usr/bin/wine mrpx,
  /usr/bin/wine-preloader mrix,
  /usr/bin/wineserver px,

}

```

File 2: [COLOR="DarkGreen"]/etc/apparmor.d/local/winecommon[/COLOR]
```

# vim:syntax=apparmor

# This file contains permissions common to wine, wine-preloader, wineserver.

#include <abstractions/audio>
#include <abstractions/base>
#include <abstractions/cups-client>
#include <abstractions/fonts>
#include <abstractions/freedesktop.org>
#include <abstractions/p11-kit>
#include <abstractions/ssl_certs>
#include <abstractions/user-tmp>
#include <abstractions/xdg-desktop>
#include <abstractions/X>

/ r,
/etc/cups/ppd/* r,
/etc/default/nss r,
/etc/fstab r,
/etc/host.conf r,
/etc/hosts r,
/etc/mtab r,
/etc/nsswitch.conf r,
/etc/passwd r,
/home/ rw,
/home/** mrwk,
/proc/scsi/scsi r,
owner /tmp/** mrwkl,
/usr/lib{,32,64}/** mr,
/usr/share/wine/** r,
/{,var/}run/resolvconf/resolv.conf r,
/var/lib/dbus/machine-id r,

```

With those files installed and AppArmor restarted, the games and utilities I run under Wine have access to the things they need, but not to the network.  I can see AppArmor doing its job by watching the output of this command:

tail -f /var/log/kern.log

I do have one Windows app that legitimately needs network access and a few other things, so I made a special profile just for it.  So long as I run its .exe file directly instead of passing it as an argument to /usr/bin/wine, this special profile overrides the ones above.  It looks something like this:

[COLOR="DarkGreen"]/etc/apparmor.d/home.me.bin.windows-email-reader.exe[/COLOR]
```

#include <tunables/global>

/home/me/bin/windows-email-reader.exe {

  #include <abstractions/consoles>
  #include <abstractions/dbus-session>
  #include <abstractions/nameservice>
  #include <local/winecommon>

  /usr/bin/wine-preloader rix,
  /usr/bin/wineserver rix,
  /usr/bin/wine mr,
  /usr/bin/xdg-open Pux,

}

```

All these files were made on Ubuntu Precise with AppArmor 2.7.102.  Other releases or distributions might have different AppArmor features or different helper files in /etc/apparmor.d/abstractions/.

Your mileage may vary.  Anything that goes wrong due to you using (or misusing) this information is entirely your own fault.  With all that said, I hope this helps someone!

---

### Post by foresto on 2012-07-22
For anyone interested, I came across the [Arkose](https://launchpad.net/arkose) application sandboxing tool today, which is now part of the Ubuntu Universe repository.  I haven't used it, but it looks very interesting.  [Here](http://www.stgraber.org/category/arkose/) are some blog posts from the developer.

---

