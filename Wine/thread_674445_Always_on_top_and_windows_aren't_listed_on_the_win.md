---
title: "Always on top and windows aren't listed on the window list!"
date: 2008-01-21
forum: Wine
---

### Post by atomkarinca on 2008-01-21
I don't know with which version this started but all my wine programs work "always on top". I can't do anything about it. What's more, the software isn't listed on the window list on the panel and when I minimize a window it's not really minimized but moved down and a weird rectangle shows up.

Is this how it's gonna be? Or did my version of wine come from a different planet?

---

### Post by hikaricore on 2008-01-22
If you check "Allow the window manager to control the windows" under winecfg / Graphics.
You should not have this problem.

If you still do something is up /w either WINE or Metacity/Kwin.
If you're using Berly/Compiz I suggest disabling it and testing that way.

---

### Post by atomkarinca on 2008-01-22
Thanks a lot, that was driving me crazy.

---

