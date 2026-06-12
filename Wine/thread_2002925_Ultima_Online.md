---
title: "Ultima Online"
date: 2012-06-13
forum: Wine
---

### Post by LinXNut on 2012-06-13
Hey guys I was wondering if anyone has gotten Ultima Online to work in wine? Or, if anyone has found a game similar to it? I really do not want to install windows again just to play it...However, I did install Ultima and attempted to run it, but the patching process is taking 5x longer than it should.

Thanks

---

### Post by ajackson on 2012-06-13
Try this in a terminal window first, 12.04 seems to have a few wine related problems solved with that.
```
echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope
```

---

