---
title: "2 issues upgrading to 9.10: keepassX &amp; Compiz"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by Rizlaw on 2009-11-01
After performing a successful upgrade from 9.04 to 9.10 I find two issues:

1. My password program "KeepassX 0.4.1" no longer works properly. Entering my master password causes the program to instantly crash. The same version of the program on my 9.10 32 bit box works perfectly with the same database file. I've filed a Launchpad bug on this issue.

Does anyone have similar problems or a solution?

2. Less important, my mouse wheel no longer rotates my cube in Compiz. No settings were changed as this was an in place upgrade from 64 bit 9.04 to 9.10. Interestingly, the wheel works correctly when I place the mouse pointer over the Cairo-Dock "Switcher" applet and then rotate the wheel.

Rotating the desktops also works from the keyboard or, if I depress and hold the mouse wheel and move the mouse left or right to make the cube spin to the desktop I want.

Has anyone noticed this change in Compiz behavior with 9.10/64?

---

### Post by Benchamoneh on 2009-11-11
I can't comment on keepassX but I've upgraded to 9.10 64 and my mousewheel fails to rotate the desktop cube too. I'm looking into it, has anyone else any ideas as to why this is?

---

### Post by Benchamoneh on 2009-11-12
Well I've got the answer to the mousewheel desktop rotation, here's what I did.

First, fire up CCSM. Then in the Desktop section enable Desktop Cube, Rotate Cube and Viewport Switcher. To get the mousewheel working again you need to edit the options for Viewport Switcher on the Desktop Based Viewport Switching tab (it's the top two options; Move Left & Move Right). Set these two to the input for mousewheel up and down - for me this was Button4 and Button5 respectively but YMMV.

After that configure your cube however you'd like it! You're on your own with KeepassX though as I don't use it.

---

### Post by Benchamoneh on 2009-11-12
Just noticed actually that you should probably set the mousewheel buttons for Move Next/Prev instead of left/right otherwise you cant rotate the cube from desktop 4 to 1 or vice versa.

---

