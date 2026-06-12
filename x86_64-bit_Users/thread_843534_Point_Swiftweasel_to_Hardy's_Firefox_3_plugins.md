---
title: "Point Swiftweasel to Hardy's Firefox 3 plugins?"
date: 2008-06-28
forum: x86 64-bit Users
---

### Post by wilberfan on 2008-06-28
The "standard" Hardy Firefox 3 works fine on my 64-bit Ubuntu install.     I'm rather fond of Swiftweasel, and have just installed the 3.0 32-bit version built for the AMD64 platform, but it doesn't know where to find all of the nifty plugins the "standard" Firefox is using.

Can anyone help me point Swiftweasel to those working plugins?

Thanks!

---

### Post by Zorael on 2008-06-28
Firefox reads a whole bunch of plugin directories. One common for all Mozilla browsers is at **/usr/lib/mozilla/plugins**, so one solution would be to find where your current plugins are stored (**/usr/lib/firefox/plugins**?) and copy them to there.

---

### Post by doorknob60 on 2008-06-28
Instead of copying, just symlink the whole plugins folder :-D That's what I do it works fine.

---

### Post by kahlil88 on 2008-08-03
> **doorknob60 said:**
> Instead of copying, just symlink the whole plugins folder :-D That's what I do it works fine.

I tried this, but Swiftweasel only finds the plugins in **/usr/lib/mozilla/plugins**. There are several in **/usr/lib/xulrunner-addons/plugins** that Firefox finds, but not Swiftweasel.

---

