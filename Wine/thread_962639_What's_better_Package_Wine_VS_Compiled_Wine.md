---
title: "What's better Package Wine VS Compiled Wine?"
date: 2008-10-29
forum: Wine
---

### Post by Sugi on 2008-10-29
I am currently using both, compiled wine and wine from a package (.deb).  I have read before that compiled Wine runs a little bit better then wine from a package, but I have also read on other forums people just use the package to install wine while saying compile wine and wine from a package is the same.  I am aware that compiled wine can be moved freely and won't mess with another version of wine if installed on the same system.

But performance while, which one is better?  Or which one may spit out more errors?

Sugi

---

### Post by ethoxyethaan on 2008-10-29
.deb &#23455;&#38555;&#25991;&#12364;&#12414;&#12392;&#12417;&#12425;&#12428;&#12414;&#12377;

i tried hard with that, Anyhow.
what do you mean with "compiled and .deb" because i think Canonical uses GCC to compile wine, and you use GCC as well i assume, (if you use the Wine makefile that is). 

is there a difference between them? or did canonical change some of the source code.

---

### Post by YokoZar on 2008-10-29
The only reason to compile Wine yourself is if you have some sort of patch for it.  In that case, though, you're probably better off [downloading the source package and rebuilding that](http://yokozar.livejournal.com/14389.html).

> **ethoxyethaan said:**
> .deb &#23455;&#38555;&#25991;&#12364;&#12414;&#12392;&#12417;&#12425;&#12428;&#12414;&#12377;

i tried hard with that, Anyhow.
what do you mean with "compiled and .deb" because i think Canonical uses GCC to compile wine, and you use GCC as well i assume, (if you use the Wine makefile that is). 

is there a difference between them? or did canonical change some of the source code.
Canonical doesn't build the package, I do ;)

The source code is also unchanged from upstream Wine, although there are a few additional user interface elements (eg the link to Applications->Wine->Browse C:\ drive)

---

