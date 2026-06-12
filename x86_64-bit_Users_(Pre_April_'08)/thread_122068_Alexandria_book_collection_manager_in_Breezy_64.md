---
title: "Alexandria book collection manager in Breezy 64"
date: 2006-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by v79 on 2006-01-26
Hi all,

Not sure where best to report this, so I'll put it here and maybe someone can point me in the right direction.

I couldn't run Alexandria in 64-bit Breezy, and finally tracked it down to a packaging issue with libgettext-ruby1.8

libgettext-ruby1.8 requires I file called /usr/lib/ruby/1.8/gettext/_locale.so, but this file doesn't exist. It has been put in /usr/lib/ruby/1.8/amd64-lunux/gettext/_locale.so . I fixed it with a symlink.

Alexandria still doesn't run for me ( uninitialized constant Pango::ELLIPSIZE_END is the error message).

But I'm working on that one.

Liam

---

### Post by slavik on 2006-01-26
I would submit a copy of the post to the developers or the package maintainer.

---

### Post by jon_gunnar on 2006-01-27
[QUOTE=v79]Hi all,

Not sure where best to report this, so I'll put it here and maybe someone can point me in the right direction.

I couldn't run Alexandria in 64-bit Breezy, and finally tracked it down to a packaging issue with libgettext-ruby1.8

libgettext-ruby1.8 requires I file called /usr/lib/ruby/1.8/gettext/_locale.so, but this file doesn't exist. It has been put in /usr/lib/ruby/1.8/amd64-lunux/gettext/_locale.so . I fixed it with a symlink.
Liam[/QUOTE]

Interesting.Installed with apt-get and got the same error.I copied the file to /usr/lib/ruby/1.8/gettext/_locale.so and then the program starts okay.Cant import data from tellico saves,but havent looked into why yet. Should be able to do it.

---

