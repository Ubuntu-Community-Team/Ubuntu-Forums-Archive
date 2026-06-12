---
title: "[SOLVED] &amp;quot;$HOME/.wine&amp;quot;  to  &amp;quot;.wine&amp;quot;"
date: 2008-10-26
forum: Wine
---

### Post by kvk on 2008-10-26
My bad- I posted this following a SOLVED thread because of issue similarities, but I'll post it as its own thread as the other is marked solved.

I've got 1.01 running on Ibex with:

1. No browsing of c:/
2. No MS equation editor extension in Word
3. Attempting to add MathType to Word usually freezes, requiring Force Quit, and when it does function, Word will no longer Save.

One of the Ubuntu programmers advised changing "$HOME/.wine" into simply ".wine", but my question is: where? It might be that all my issues are derived from that same problem, but I'm not sure where the fix is initiated.

When attempting to install MathType:


```
arctos@arctos:~/Desktop$ wine MTW6.0c.exe
fixme:ole:CoInitializeSecurity (0x413ea8,-1,(nil),(nil),1,3,(nil),72,(nil)) - stub!
err:ole:CoGetClassObject class {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} not registered
err:ole:CoGetClassObject no class object {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} could be created for context 0x1
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f884): stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f86c): stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f86c): stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f86c): stub

fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
etc.

fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
etc.


```

---

### Post by YokoZar on 2008-10-27
> **kvk said:**
> My bad- I posted this following a SOLVED thread because of issue similarities, but I'll post it as its own thread as the other is marked solved.

I've got 1.01 running on Ibex with:

1. No browsing of c:/
2. No MS equation editor extension in Word
3. Attempting to add MathType to Word usually freezes, requiring Force Quit, and when it does function, Word will no longer Save.

One of the Ubuntu programmers advised changing "$HOME/.wine" into simply ".wine", but my question is: where? It might be that all my issues are derived from that same problem, but I'm not sure where the fix is initiated.Regarding the browsing C:\ drive thing: You don't need to do anything other than let update manager do it's thing - I patched the package and it got rebuilt today.

As for your other two issues I'm afraid they're just (separate) outstanding bugs in Wine.

> When attempting to install MathType:
```
arctos@arctos:~/Desktop$ wine MTW6.0c.exe
fixme:ole:CoInitializeSecurity (0x413ea8,-1,(nil),(nil),1,3,(nil),72,(nil)) - stub!
err:ole:CoGetClassObject class {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} not registered
err:ole:CoGetClassObject no class object {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} could be created for context 0x1
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f884): stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f86c): stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f86c): stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f86c): stub

fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
etc.

fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
etc.


```Your program failing to install has nothing to do with the error in the .desktop file that made the "brose C:\ drive" button not work.

---

### Post by kvk on 2008-10-27
Most excellent! Thanks for the information, and for all your work on Ubuntu!!

I'll see if anyone over on the Wine end of things knows anything about this one.

Thanks again!!

---

