---
title: "how do i knowm a program is closed?"
date: 2008-05-19
forum: Wine
---

### Post by Silpheed2K on 2008-05-19
like for instance i'm going around and testing apps... and some of them dont open in Wine.. or pop up with error messages... how do i know that the program isnt hanging in the background or still using up memory and CPU after i clicked and the thing errored... just curious as to how i can check this.

---

### Post by Dr Small on 2008-05-19
Try looking for a running process:
```
ps aux | grep wine
```

---

