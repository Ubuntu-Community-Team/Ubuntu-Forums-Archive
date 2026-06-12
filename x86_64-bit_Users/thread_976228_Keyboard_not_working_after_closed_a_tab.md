---
title: "Keyboard not working after closed a tab"
date: 2008-11-09
forum: x86 64-bit Users
---

### Post by wangrui on 2008-11-09
Hi everyone,

Does anyone who installed ubuntu 8.10 AMD64 has this problem?

After I installed ubuntu 8.10, keyboard behave weird. For example, if I open a terminal, press Ctrl+Shift+T to open a new tab, then press Ctrl+D to close the new tab, then the keyboard will stop working in the old tab. Only key combinations with Alt key can still work. If I don't press Alt, no key will work. But if I switch to another window and then switch back, the keyboard will start working again.

This problem only happens in the 64bit version. I installed 32bit on another machine which don't have this problem.

Because this problem, I can't use eclipse any more. Because there are pop up windows in eclipse all the time. Whenever there is a popup window, the keyboard will stop working until I switch to another window and switch back.

---

### Post by howefield on 2008-11-09
Can't emulate that issue, works fine here with 64 bit.

You probably already tried a different keyboard ?

---

### Post by wangrui on 2008-11-09
Using another keyboard didn't solve the problem. It's more like a software problem. Because if I connect to this machine using VNC, It still has the same problem.

I guess it's my own problem then. Thanks for the feedback.

---

### Post by wangrui on 2009-01-30
The problem was solved by running
```
im-switch -s scim-bridge
```

---

