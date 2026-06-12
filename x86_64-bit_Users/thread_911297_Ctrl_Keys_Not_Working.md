---
title: "Ctrl Keys Not Working"
date: 2008-09-05
forum: x86 64-bit Users
---

### Post by wingle on 2008-09-05
A strange issue this one...

I know the hardware is working fine because I have no problem in Windows.  It seems like the event for this key is being intercepted by something.

I've been searching but can't find the answer.  It seems some output from xev might help so here are the results for pressing left ctrl followed by right ctrl.

```
FocusOut event, serial 31, synthetic NO, window 0x3200001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  59  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3200001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  
```

Pressing shift and _then_ pressing ctrl gives the usual, desired behaviour.

Does anyone have any thoughts on how to correct this?  It's trivial but actually really annoying!

Thanks,
wingle

---

### Post by elmoosecapitan on 2008-09-05
Try System~>Preferences~>Keyboard~>Layout and System~>Preferences~>Keyboard Shortcuts.

Check those out; if the layout is some obscure region change it.


cheers

---

