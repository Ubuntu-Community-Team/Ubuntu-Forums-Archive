---
title: "[SOLVED] CTRL shortcuts don't work"
date: 2008-10-07
forum: x86 64-bit Users
---

### Post by solidboss on 2008-10-07
I upgraded to intrepid beta yesterday, but this problem was present previous to that. Shortcut keys involving CTRL no longer work; they used to about two weeks ago but no longer.

I've tried remapping the keys using xkbdmap and xmodmap, everything looks right. Then when I try to ctrl-c or ctrl-a it doesn't work, regardless of what application(firefox, openoffice, gedit) I'm using.

There is an exception, shortcuts set in System>Preferences>Keyboard Shortcuts. Those shortcuts work with CTRL(although CTRL-ALT-DEL doesn't respond quickly).

I'm running Ubuntu Intrepid Ibex Beta AMD64 on an Athlon X2 computer with 4GB ram and 4GB swap.

Solid

---

### Post by solidboss on 2008-10-08
This is what happens when I put xmodmap into terminal:

```
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
```

---

### Post by solidboss on 2008-10-08
Well after searching through everything that could possibly have affected my keyboard I found a single keybinding in CompizConfig Settings Manager that was bound to ctrl, the key combination was "ctrl". There wasn't even an action set to it, which is way nothing happened when I pressed control.

I assume I did it by accident and didn't notice.

Solid

---

### Post by egregory on 2008-10-29
hello mate, tell me little bit about this ctr problem as i have the same problem and its driving me bananas!! so what happened and how exaclty did you fix it in Compiz.....
thanks

Ed

---

### Post by egregory on 2008-10-29
never mind i just had a moment of enlightment and managed to fix it myself! i changed something preveously in Compiz which completely pooped up my CTR key!

---

