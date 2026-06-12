---
title: "xorg crash to text screen when closing a firefox tab"
date: 2008-06-26
forum: x86 64-bit Users
---

### Post by cionci on 2008-06-26
I have a strange issue with Hardy. After a long and intense session of Firefox, may occur an xorg crash when closing a Firefox tab.
Requirements to replicate the issue on my system:
- an intense firefox session without closing it
- intense use of tabs
- sites with multiple flash animations
- Compiz enabled
Xorg crashes to text mode and the only way to return to graphics is to hit CTRL+ALT+DEL to restart the system. In text mode remains a strange unmovable mouse pointer.
I've [filled a bug]("https://bugs.launchpad.net/ubuntu/+source/xorg"), but in the meanwhile I want to know if someone has the same issue. 
In the bug description I've written a procedure that lead me to replicate the issue, but not always, only two or three times over many retries.
I don't know if it's related to fglrx driver, I use default version shipped in Hardy.

---

