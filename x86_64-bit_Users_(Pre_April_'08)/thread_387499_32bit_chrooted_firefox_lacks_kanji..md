---
title: "32bit chrooted firefox lacks kanji."
date: 2007-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jingu on 2007-03-18
I made a 32-bit chroot a while ago to install zsnes, and decided I might as well install the 32-bit version of Firefox while I was at it, since youtube links seem to be ubiquitous these days, and I wanted to see what I was missing.
Well, I suppose my 32-bit install lack some fonts, because on sites with kanji (which I visit fairly often) I get the little unicode code point boxes instead of the symbol. Looking around, it seems that Bengali and Thai are also absent, which is merely annoying, since they all work perfectly on all of my 64-bit programs.
I looked around a bit on synaptic (32-bit, of course), and I found something called "xfonts-intl-japanese", but it didn't seem to do anything.

Sorry for being a newb, but I just don't know what I need to install.

---

### Post by kuja on 2007-03-20
I've never played with it, bu t perhaps the "mozilla-firefox-locale-*" packages might have something to do with it?

---

### Post by Jingu on 2007-03-21
I found it!
It's the ttf-opensymbol package, which "includes support for wingdings, bullets, and non-latin characters."
I think that the locale packages are for translating the interface....

---

### Post by Jingu on 2007-03-21
Whoops :oops:
I accidently opened the 64-bit version, after installing the font package. The 32-bit one still lacks the correct characters. I'll try adding a locale package, to see if that works.

---

