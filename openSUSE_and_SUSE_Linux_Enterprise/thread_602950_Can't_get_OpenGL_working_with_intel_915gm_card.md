---
title: "Can't get OpenGL working with intel 915gm card"
date: 2007-11-04
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Forks Holder on 2007-11-04
Hello there guys,
I'm using openSUSE 10.3, and i was planning to run World Of Warcraft with wine.

By [This Thread]("http://www.linuxforums.org/forum/wine/62932-howto-installing-world-warcraft-wine.html"), i've downloaded wine (source) and WOW installation, andeverything went fine.

I've installed the game, and configured my Wine, but then i saw that i don't have OpenGL for some reason.

Now, When i use "glxgears", i see this gears and it's working great, but when i'm for example entering to Supertux, in optiong it says "OpenGL not supported". Also, in cedega i did the System test, and it says everything's fine exept the 3D thing.

when i've entered to YaST ->Hardware -> Graphic card and monitor, *Than cheking the "Activate 3D Acceleration"*, it does no change.


PLEASE HELP ME, I WANT WOW! :'(

Thanks,
~Forks Holder

---

### Post by carlinuxlearner on 2007-11-04
What kind of graphics card do you have? (open up a terminal and type "lspci | grep VGA" post out put here).

C@RL

::EDIT 
Sorry for my stupid question. Try installing 915resolution with synaptic.

---

### Post by Forks Holder on 2007-11-06
> Holder-linux:/home/holder # lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

that's my graphics card i guess.

And yes, the 915resolution is already installed.

Any ideas?

---

### Post by Forks Holder on 2007-11-08
Bump?

---

