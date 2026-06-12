---
title: "Installing Steam, what do I need to do?"
date: 2011-10-12
forum: Wine
---

### Post by Lucradia on 2011-10-12
I've read the installation proceedure for steam (official) for wine / ubuntu, and I want to know what is recommended to do besides disabling all effects, (or by using XFCE in the first place) For example, should I just go ahead and disable the overlay renderer? What about those blob files, should I just delete them?

Also, Wine will be installed on a non-NTFS disk (all ext/swap), so don't worry about that. And, will the following games run?

* Terraria (Known, .NET v4 May Not Install: [http://bugs.winehq.org/show_bug.cgi?id=25535](http://bugs.winehq.org/show_bug.cgi?id=25535), Mono cannot be used, as it lacks WPF)
* Portal
* Portal 2

---

### Post by ergo-proxy on 2011-10-13
I'm not aware of any extra recommendations, 
"winetricks corefonts allfonts tahoma gecko gecko-dbg" is enough for me.

---

### Post by directhex on 2011-10-13
> **ergo-proxy said:**
> I'm not aware of any extra recommendations, 
"winetricks corefonts allfonts tahoma gecko gecko-dbg" is enough for me.

Why Gecko? Steam embeds Chrome. It hasn't used the IE ActiveX control (which wine's gecko support emulated) for years

---

### Post by Lucradia on 2011-10-13
> **directhex said:**
> Why Gecko? Steam embeds Chrome. It hasn't used the IE ActiveX control (which wine's gecko support emulated) for years

So skip gecko and install what?

**Edit:** If I run into problems with mono, I cannot install the package known as "xact" unless that's via winetricks, as Ubuntu packages has no xact package. There is, however, an xinput package.

**Edit Edit:** According to the "How To Get Steam Working" section on this page ( [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444) ) it says you have to have gecko and its dbg.

---

### Post by ergo-proxy on 2011-10-14
> **directhex said:**
> Why Gecko? Steam embeds Chrome. It hasn't used the IE ActiveX control (which wine's gecko support emulated) for years
 
True :) I think even the current version of winetricks won't allow for installation.

---

### Post by Lucradia on 2011-10-14
> **ergo-proxy said:**
> True :) I think even the current version of winetricks won't allow for installation.

Wine 1.3 package auto-pulls gecko for wine from wine repos unless you flag --no-install-recommends. But then you need to install ia32-libs-multiarch manually, and a plethora of other things that are recommends and suggested packages. (umefonts, msfonts, etc. the actual required stuff is actually recommends / suggested)

Anyway, I took off xubuntu, because it was going way, WAY too slow in comparison to Windows, for some strange reason. I don't know why, it just was.

---

