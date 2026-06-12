---
title: "Fullscreen programs (wine) do not hide unity items"
date: 2013-05-06
forum: Wine
---

### Post by sona1111 on 2013-05-06
Hello, I have seen this problem posted around here about two years ago but none of the solutions have worked for me so far. I am using a thinkpad t60 with three different fullscreen wine programs. for each of them, If I disallow the window manager to control the windows in the wine settings, it will display correctly but the keyboard will not function correctly. If I enable the window manager to control the windows then the keyboard will work correctly, but then the unite launcher and top panel will display over the programs. Was their ever a workaround for these problems? I have tried the "legacy fullscreen support" in compiz with no luck.  

thanks.

---

### Post by Jail on 2013-05-06
I have the same problem and I am clueless. sona1111 have you managet to solve it? If so please write what was the solution.

---

### Post by sona1111 on 2013-05-06
I have only posted this less then a day ago, but I have been trying everything. I am through the entire first google page so far. Including a bunch of weird compiz settings. I Think I will try playonlinux next.

---

### Post by sona1111 on 2013-05-13
Still no luck getting the unity bars to go away. Does anyone know how to fix it? or possibly how to capture the keyboard without using the window manager?

---

### Post by QIII on 2013-05-13
[I]Moved to [B]Wine


[/B][/I]Let's see if you get better action here.

Cheers!

---

### Post by sona1111 on 2013-05-13
thank you, though some people have also reported problems with non-wine applications. (the problems I have are only with wine at this time)

---

### Post by sona1111 on 2013-05-17
bump

---

### Post by sona1111 on 2013-05-19
Ok guys, It took a little help from the people at wine forums, but I seem to have solved it, for myself at least. 

All that you need to do is check all the boxes in wine config graphics tab (auto capture, alllow, allow, and emulate desktop) and set the resolution of the desktop in the boxes to exactly what you have set in ubuntu display settings. One pixel off and it becomes a window, but exactly the same it goes full screen! Then all that you have to do is open your program and set the resolution there to be the same as the other two resolution settings, and you should be good to go! (if you cant find the exact resolution you need, check the programs app directory for some .ini file they like to hide the resolutions in.)

Thanks for everyone's help!

---

