---
title: "Can someone explain ZEN?"
date: 2007-08-21
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 67GTA on 2007-08-21
I have been reading up on open suse while my PC is getting a new HD. I was going to dual boot with Ubuntu once I get it back. I have seen several articles on adding repos with 10.2. Some recommend removing Zen when installing, while others make no mention of it. The articles that said to remove Zen said that yast would handle software and updates by itself. If that is the case, then what is Zen and what does it do? I have read that 10.3 was not going to include Zen. 

Also, does suse actually detect hardware better, or does Ubuntu just not show it? Suse had every piece of hardware listed just as detailed as Windows would. When I looked at the hardware info in Ubuntu, there were a lot of specs blank or left out. Is it just the software that is reading the hardware that makes the difference?

---

### Post by Incense on 2007-08-21
Everything you ever wanted to know about ZENworks.

[http://en.opensuse.org/Zmd]("http://en.opensuse.org/Zmd")

I removed it and I use SMART. It makes OpenSuse life much better IMO.

[http://susewiki.org/index.php?title=Smart]("http://susewiki.org/index.php?title=Smart")

I would recommend disabling ZMD, it just doesn't work very well. You can use SMART to update, or the Opensuse Updater.

```
su -c "rczmd stop; rpm -e zmd libzypp-zmd-backend sqlite-zmd rug zen-updater"
```

Hope that helps!

---

### Post by 67GTA on 2007-08-21
Thanks, that is what I was looking for. I missed it on the documentation page. It seems like an extra step that slows the whole process. It sounds like it may have trickled down from Suse to open suse. I will try disabling it when I reinstall. One of the articles said you could deselect it before installation. I have yet to try smart. Does it speed up open suse any?

---

### Post by igknighted on 2007-08-21
> **67GTA said:**
> Thanks, that is what I was looking for. I missed it on the documentation page. It seems like an extra step that slows the whole process. It sounds like it may have trickled down from Suse to open suse. I will try disabling it when I reinstall. One of the articles said you could deselect it before installation. I have yet to try smart. Does it speed up open suse any?

Yes, very noticeably faster.  The GUI for smart is GTK based, so it looks kinda crappy in KDE (like synaptic would... which while we are on the subject is also able to be used if you install apt4rpm).  I typically use zypper (yast on the CLI) when using suse.  It might not be very fast, but it is reliable.

One last note about Zen... its great if you want to manage a bunch of computers in say, an enterprise setting... but as far as the home user is concerned, its crap and has little to no use.  So while it is not necessarily a "bad" piece of software, it was very poorly placed on the home users desktop.

---

### Post by RedDwarf on 2007-08-22
Anyway should be noted that a lot of people complained about ZMD when the real problem was located in libzypp.
Yes, for a home user ZMD is an extra step completly unneeded that adds some work to the process. But even without ZMD any program using libzypp is completly unusable (tens of minutes to start YaST) in a system with 256MB RAM if you use the (big) official repository and the classic ones (packman, guru, last KDE and Firefox...) while Smart has no problems at all. The fact that every time that you want to install something from the DVD with YaST *all* the repositories are updated automatically (there is no way to avoid this) is a problem of libzypp, not ZMD.
The big gain in 10.3 isn't that ZMD will be removed (always a plus), the big improvemente comes from tha fact that the updated libzypp will create a cache of the metadata. The libzypp from openSUSE 10.2 needs to parse the metadata every time that you want to do anything, that is slow.

And yes, in the installation of openSUSE 10.2 you can select "openSUSE Software Management" (without ZMD) or "Enterprise Software Management" (with ZMD), being the Enterprise the default.

> **igknighted said:**
> One last note about Zen... its great if you want to manage a bunch of computers in say, an enterprise setting...
How this works? I haven't any idea about all the Novell propietary stuff. I understand that ZMD is a daemon listening for "something", but what is the program that will send this something?

---

