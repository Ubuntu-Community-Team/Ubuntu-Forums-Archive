---
title: "mac mouse +ctrl click"
date: 2006-05-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by freemanen on 2006-05-14
Who do I get a mac mouse to use ctrl click like a second button in ubuntu?

---

### Post by calum on 2006-05-14
[QUOTE=freemanen]Who do I get a mac mouse to use ctrl click like a second button in ubuntu?[/QUOTE]
Don't think you can have Ctrl+Click, but you can set up any keyboard shortcut  you like... default is F12 for right click, F11 for middle click.

You need to edit the MouseButton2 and MouseButton3 entries in /etc/sysctl.conf if you want to change those.  Run 'sudo showkey' and press the shortcut you want to figure out what codes you need to put in /etc/sysctl.conf.

(Or, just buy a cheap 2 or 3 button mouse and use that instead...)

---

### Post by Ptero-4 on 2006-05-15
use mouseemu. It can allow you to use ctrl+click in the same behavior as in MacOS. But mouseemu is a bit buggy so use with caution.

---

