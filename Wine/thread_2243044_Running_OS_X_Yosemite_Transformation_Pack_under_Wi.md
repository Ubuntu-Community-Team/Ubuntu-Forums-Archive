---
title: "Running OS X Yosemite Transformation Pack under Wine"
date: 2014-09-05
forum: Wine
---

### Post by joyousjake on 2014-09-05
I recently downloaded the Yosemite Transformation Pack for Windows in order to use some msstyles and themes under Wine. Whenever I try to install it, it never shows up. Why is this?

---

### Post by johso on 2014-11-29
hey joyousjake,
  
I am almost certain that this is because actual Microsoft Windows systems use a different application set for rendering windows. (I mean: the boxes that your applications are inside of and the buttons and options they have).  
  
This means that it looks much the same, but all the buttons and the gray parts you see, and the title bar and such, are all made to look so because of processes running in a full Windows install.

So when you install the theme, you install it for a window system that isn't there.  
Instead, WINE has it's own way of mimicking the look and feel of the windows, which is naturally focused on performance.
(So, it isn't so fancy.)

I hope that clears things up!

---

