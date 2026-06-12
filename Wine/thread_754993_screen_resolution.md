---
title: "screen resolution"
date: 2008-04-14
forum: Wine
---

### Post by Caesum on 2008-04-14
I've been playing diablo2 but after playing my screen resolution is messed up, is there a line I can add to this to restore it?

```

#!/bin/bash
xgamma -gamma 2.0
cd "/d2/Diablo II"
wine "game.exe"
xgamma -gamma 1.0

```

---

