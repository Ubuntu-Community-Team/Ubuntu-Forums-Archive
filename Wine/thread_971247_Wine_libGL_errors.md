---
title: "Wine libGL errors"
date: 2008-11-04
forum: Wine
---

### Post by Svv on 2008-11-04
When running WoW with wine I get the following errors...

```
libGL error: drmMap of framebuffer failed (Cannot allocate memory)
libGL error: reverting to (slow) indirect rendering
```

Which is very odd considering when I run glxinfo it tells me I have direct rendering.

```
sv@Meh:~$ glxinfo | grep direct
direct rendering: Yes
```

Any help?

---

