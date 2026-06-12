---
title: "Lightning/Sunbird 0.7"
date: 2007-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ev.Eli on 2007-10-29
Mozilla has released them, but they have yet to provide 64-bit builds. Has anybody gotten 64-bit Lightning 0.7 off the ground? I couldn't really figure out how to compile it from the Mozilla site, but if somebody pointed in the right direction I'd be willing to give it a try.

EDIT: I managed to compile it, and as far is I can tell, it works!
[http://www.zshare.net/download/45422513cc5f1a/]("http://www.zshare.net/download/45422513cc5f1a/")
This is the mozconfig I used:
```

. $topsrcdir/mail/config/mozconfig
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/tbird-lightning
mk_add_options MOZ_CO_PROJECT=mail,calendar
mk_add_options MOZ_MAKE_FLAGS=-j4
ac_add_options --enable-extensions=default,lightning
ac_add_options --enable-optimize
ac_add_options --disable-debug
ac_add_options --disable-libxul
ac_add_options --disable-tests
ac_add_options --enable-system-cairo
ac_add_options --enable-strip

```

---

### Post by Kilz on 2007-10-29
[Swiftdove]("http://swiftweasel.wiki.sourceforge.net/Swiftdove") is a 64bit optimized build of the Thunderbird 2.0.0.7 source. It comes with Lightning installed by default.

---

### Post by crjackson on 2007-10-29
> **Ev.Eli said:**
> Mozilla has released them, but they have yet to provide 64-bit builds. Has anybody gotten 64-bit Lightning 0.7 off the ground? I couldn't really figure out how to compile it from the Mozilla site, but if somebody pointed in the right direction I'd be willing to give it a try.

Thunder / Lightening are both in the 64-bit Gutsy repo.  I don't about the Sunbird, I'll have to check that out at home...

---

### Post by Ev.Eli on 2007-10-29
Thanks kilz, but I'm talking about the new version of Lightning that was released a few days ago. According to SF, the latest version of Swiftdove is from late September, so it would still be using the old version of Lightning.

@crjackson: The version of Lightning in the repo is 0.5, not 0.7. I'm not sure I like the idea of installing extensions from the repo anyway.

---

### Post by Kilz on 2007-10-29
Swiftdove uses the .7pre lightning. Its just the pre release. You can take a look at the attached screenshot.

---

### Post by Ev.Eli on 2007-10-29
Just want to post and update and tell anybody who cares that I did manage to compile Lightning. There's a link to the xpi in the first post.

---

### Post by mrfreddy on 2007-10-30
That installed OK. Now I just have to stress test it. ;)

Thanks for filling this rather shocking hole.

---

### Post by mcdee on 2007-10-30
I compiled this up as well and it seems to work fine for me (64-bit gutsy).  It's required for the recent GCal provider update so yes it is surprising that it is not available as one of the 'standard' precompiled options.

If there are problems with the link above you can pull it from here instead: [http://blog.devzero.net/2007/10/lightning-07-for-x8664.html](http://blog.devzero.net/2007/10/lightning-07-for-x8664.html) and I'll try to keep it up-to-date as new versions of Lightning are produced.

---

### Post by EelcoW on 2007-11-01
thanks!

---

