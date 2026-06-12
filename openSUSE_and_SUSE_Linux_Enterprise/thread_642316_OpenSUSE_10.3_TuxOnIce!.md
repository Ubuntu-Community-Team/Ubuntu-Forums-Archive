---
title: "OpenSUSE 10.3 TuxOnIce!"
date: 2007-12-16
forum: openSUSE and SUSE Linux Enterprise
---

### Post by khurrum1990 on 2007-12-16
Hi does anyone know if its possible for opensuse 10.3 to use TuxOnIce which (K)Ubuntu uses other than s2ram and s2disk cause they don't work well on my system. S2disk just goes to standby and resets machine. Is there a how to, I posted this on the Suse forums, but no one even bothers to reply there.

---

### Post by K.Mandla on 2007-12-18
Shifted just slightly into the OpenSuse subforum. :)

---

### Post by Incense on 2007-12-24
I guess no one replies here either. Never used tuxonice, but if you can find a deb, I'm sure you can alien it into an RPM and have a go at it from there. Otherwise, I have no clue. 

BTW, have you tried this page yet? 

[http://http://en.opensuse.org/Pm-utils]("http://http://en.opensuse.org/Pm-utils")

Suspend on my notebook works only if I modify 

/usr/lib/pm-utils/defaults

add

S2RAM_OPTS="-f -a 3"

then save it as 

/etc/pm/config.d/config

Don't know if that helps at all. Hope it does.

---

### Post by khurrum1990 on 2007-12-24
> **Incense said:**
> I guess no one replies here either. Never used tuxonice, but if you can find a deb, I'm sure you can alien it into an RPM and have a go at it from there. Otherwise, I have no clue. 

BTW, have you tried this page yet? 

[http://http://en.opensuse.org/Pm-utils]("http://http://en.opensuse.org/Pm-utils")

Suspend on my notebook works only if I modify 

/usr/lib/pm-utils/defaults

add

S2RAM_OPTS="-f -a 3"

then save it as 

/etc/pm/config.d/config

Don't know if that helps at all. Hope it does.
thanks for ur reply, I think Ubuntu/Kubuntu use tuxonice and they work perfectly on this system, s2ram and s2disk, don't work at all.

---

