---
title: "WoW Crash - But only when the game is 'visible'"
date: 2007-12-06
forum: Wine
---

### Post by plenderj on 2007-12-06
Here's a bizarre enough one. Desktop machine, P4 3GHz, 2GB of RAM, ATI Radeon X1800. Ubuntu Gutsy Gibbon. Using the latest '50 version of WINE.
I've also tried Cedega too; that just bombs with a memory access exception when trying to fire up the game. It does however pass my system on all of its tests.

Machine is stable/ok. glxgears works just fine. I have direct rendering.

I can fire up WoW, and was having a problem after accepting the TOS whereby it would crash. That problem has since gone away. The problem now is this:

When I log in to the world it will crash. So when the world is going to be displayed it causes the entire machine to crash and I have to cycle the power.
I can't CTRL+ALT+F1, CTRL+ALT+BACKSPACE, and that CTRL+ALT+SysRq thing does nothing either. There are no messages, no warnings, just plain hanging goodness.

Interestingly, if I leave WoW running in the background in windowed mode, and leave it long enough to log in to the world, the machine will keep running. But once I switch to WoW and it has to actually display the world, it then falls over.

I've tried a variety of graphics options. D3D Rendering is disasterously slow.
Under OpenGL the interface is very responsive and works perfectly. It's just the pesky business of logging in that's a problem :D

Any thoughts?

---

### Post by ajmorris on 2007-12-06
You're not running compiz or beryl at all are you?

---

### Post by Ferrat on 2007-12-06
How did you install the game? have you tried Blizzards recovery tool?

---

