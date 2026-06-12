---
title: "Steam problem!"
date: 2008-03-14
forum: Wine
---

### Post by YotamG on 2008-03-14
I Need help!
I'm kinda new Ubuntu user and my big bro helped me with wine and stuff so I've installed steam BUT, I Can't see texts! this thing makes me mad!! I Can't Play no games and I'm soooo bored so please help me :(

---

### Post by jeffus_il on 2008-03-14
You probably have a font problem with wine, I think this may help you:
> Or-- I have the open-source versions of the MS files installed as the
'corefonts' package-- if you do as well, you can

1) copy the fonts to Wine's font folder;

2) edit the Wine config to point to the directory where the fonts live
(/usr/share/fonts/corefonts), using either the config file (if you have
one), or the Registry-- you should be able to do this with Wine's
regedit, meaning Wine's regedit works for this purpose, but I don't know
where to find the key to change this setting, having not yet looked for
it. So I can't tell you what reg file it's in, or what it is called, or
even if it exists (all of the config settings were moved to the
Registry, but other users have reported being unable to find some of the
settings they are used to, and winecfg does not handle this).

3) If you have Windows installed somewhere, you can copy the fonts and
dump them in Wine's fonts folder.

But the above manner of installing the 'real' MS fonts will also work--
I've done almost all of these at some time or another, but currently
don't think I'm doing anything, as Wine 20050628 is working fine with
fonts without my intervention-- and in fact, it works better than
Cedega, which often has blank text where Wine does not. So if you are
using an older version of Wine than the current, you might consider
upgrading.

Hope this helps,
Holly



I found it here:
[http://www.winehq.org/pipermail/wine-users/2005-July/018430.html](http://www.winehq.org/pipermail/wine-users/2005-July/018430.html)

---

### Post by YotamG on 2008-03-14
I've tried... and sadlly it doesn't work :(

---

### Post by IsawSp4rks on 2008-03-14
Which version of WINE are you using?

---

### Post by YotamG on 2008-03-14
0.9.46... I Think

---

### Post by IsawSp4rks on 2008-03-15
That's an old version.  Have you updated it via Synaptic?  Ever since WINE 9.56 my Steam font problems became a non issue.

---

