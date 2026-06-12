---
title: "Realtime Kernel Installation = No GUI"
date: 2009-01-04
forum: openSUSE and SUSE Linux Enterprise
---

### Post by homerj742 on 2009-01-04
I've been trying to update my Opensuse 11.0 to be a DAW via these instructions: [http://en.opensuse.org/JackLab/3_Steps_to_JAD_for_Beginners_2](http://en.opensuse.org/JackLab/3_Steps_to_JAD_for_Beginners_2)

However, upon installing the realtime kernel, I cannot get a GUI, I just get the command line. Any help would be greatly appreciated. Thank you!

---

### Post by Growbag on 2009-01-05
What message do you get when typing:

***startx***

once logged in?

Oh, you might have to re-initialise your graphics subsystem by running:

[B][I]su
sax2[/I][/B]

And selecting the correct graphics card and monitor.  I've never had to use it so I'm just guessing here!

Whenever you change the kernel you usually have to change the video driver, especially if you are using a 3d one like Nvidia.

---

