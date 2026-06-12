---
title: "Broken Packages?"
date: 2008-06-26
forum: x86 64-bit Users
---

### Post by Matt You on 2008-06-26
I want to install the flashplugin-nonfree for firefox. but when i do, i eventually get the error: 

"The following packages have unmet dependancies: flashplugin-nonfree: Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1) but it is not going to be installed.
E: Broken packages"

So I type this: "sudo apt-get install flashplugin-nonfree nspluginwrapper"

But I get that nspluginwrapper depends on ia32-libs.  It leads me on a wild goose chase until i get to this command: "sudo apt-get install flashplugin-nonfree nspluginwrapper ia32-libs lib32asound2 libasound2"

But it errors saying that libasound2 is already the newest version (even though it said lib32asound2 depends on libasound2) and still tells me it can't install because lib32asound2 has the unmet dependancy of libasound2.  And again says "E: Broken Packages"

Thanks for any help in advance!

---

### Post by PeterBBB on 2008-06-26
I had a similar problem. It seems I had a more recent version of libasound2 than the official one. You should have the 'Hardy' version, currently 1.0.15.3.    

If you have something like 1.0.16.2  it won't work.

Use 'force version' in Synaptic Package Manager to install the right version of libasound2


PB.

---

### Post by fudoki on 2008-06-26
> **PeterBBB said:**
> I had a similar problem. It seems I had a more recent version of libasound2 than the official one. You should have the 'Hardy' version, currently 1.0.15.3.    

If you have something like 1.0.16.2  it won't work.

Use 'force version' in Synaptic Package Manager to install the right version of libasound2


PB.

Just an observation:  This is the kind of stuff that makes folks walk away from Linux.  When you do an "upgrade" things should still work without having to take a multi-hour or multi-day time out to stop and do tons of research to fix what worked fine before the "upgrade"/"update".

Do any of the folks making the new releases have any idea what the term "backward compatible" or "configuration integrity" mean?

On my system, the new kernels do not load, and when you load the old, working kernels they are running at 800x600 - completely useless.  Since this is a "production setting", I have had to fall back to Debian machines and Windows.

Will I have a day or two, besides today, to waste finding out why things are broken?  I sure hope not.  Life is just too short.

---

### Post by Sockerdrickan on 2008-06-28
I can't install ia32-libs because libasound2 is not available for download

---

