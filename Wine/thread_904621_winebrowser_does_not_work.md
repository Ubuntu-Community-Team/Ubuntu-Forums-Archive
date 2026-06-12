---
title: "winebrowser does not work"
date: 2008-08-29
forum: Wine
---

### Post by tak1150 on 2008-08-29
winebrowser used to work and I used to able to use Windows program (eg SciFinder) that would launch Firefox through Wine. But it does not work after Wine hit the 1.0 version milestone.

BTW, SciFinder behaves correctly under crossover, but it is much slower. For some reason it's X5 faster in Wine! So I'd like to use it with Wine if possible. Thanks.

Here's the output
> err:winebrowser:wmain Usage: winebrowser URL

---

### Post by tak1150 on 2008-08-29
I actually just fixed this issue.
First off, I was not using winebrows/er correctly.
Once I typed
> winebrowser [http://www.google.com](http://www.google.com)
it worked.
Then I went into .wine/system.reg and replaced all occurrences of
> winebrowser.exe
with
> winebrowser.exe %1
then it worked!

---

### Post by windwalker78 on 2010-06-19
Thank you :):guitar:

---

### Post by Sef on 2010-06-19
Locked. Necromancing.

---

