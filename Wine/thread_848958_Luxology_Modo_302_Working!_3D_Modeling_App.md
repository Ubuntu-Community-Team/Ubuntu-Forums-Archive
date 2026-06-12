---
title: "Luxology Modo 302 Working! 3D Modeling App"
date: 2008-07-04
forum: Wine
---

### Post by grimdeath on 2008-07-04
I was looking over the Wine AppDB tonight and noticed the last test for Modo was version 301 on Gutsy so I thought id give it a try running Wine 1.1.0 and Hardy 32bit. I am happy to report very positive results!

Modo is a great application for 3D modeling, sculpting, painting, rendering, and animation. If other people can submit some positive reviews of it we may have another alternative to Maya/Blender. Luxology has stated they have a working beta client for Linux but that was months ago and no word has been heard since. Hopefully this will help a few other 3D/Linux users out there.

**Instructions:**
[LIST=1]
[*]I downloaded the evaluation copy AND license from here after creating an account:
[http://www.luxology.com/trymodo/]("http://www.luxology.com/trymodo/")
[*]Installed like a normal windows app using Wine.
[*]I had issues getting the license .exe file to work properly so I extracted the loose license file to my desktop and pointed Modo to it when I first started it, it accepted it and loaded into the application normally.
[*]Use like normal!
[/LIST]

**My Experience:**
Everything I tested works, I haven't use the app in a couple months so I do not remember all the shortcuts and techniques but quick tests are very promising. There are some slight graphical glitches with black behind the icons instead of transparency, slight flickering ever now and then, and File menus have a 1-2 second delay after clicked but for the most part is seems completely usable for everyday use. Professionals should probably test on their own machine before completely dropping windows/mac versions.

I have created this thread so other people can test this out and report their results, I recommend you post if it works as well as your system specs and any positive/negative experiences during the process.

I provided some screenshots below of some of the tutorial models that come preinstalled in the Modo directory.

---

### Post by grimdeath on 2008-07-05
[Wine AppDB Entry Accepted]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12874&iTestingId=28092")

Im disappointed no one has tried this out yet :P hopefully there are a few other linux/modo users out there ;)

---

### Post by kahein on 2008-08-05
Hi 

Thanks for your post.
I'm a modo 302 user, it's an great app.
I'm trying to launch it with wine but it don't work.
The install it ok but when i clik on the .exe a blank window open with the modo302 titel bar  and one sec after close itself.
Maybe a make something wrong.

Could you give me some help

Thanks

---

### Post by okf on 2008-08-09
Well it seems to work but when I switch from model to Quadmodel view, an error box appears saying that drawing error. At this point, every viewport for "left", "top", "right" view appear in yellow.

Also, when I have a 3dmodel active in the model view and I switch to other view, the 3dmodel disappears!.

Some other text box and labels fails with transparency and they appear with yellow background.

Other problems detected are mouse selection when you want to change viewport setting, like shading view or when you want to chose another camera. At this time, mouse doesn't highlights the options in the pop up menu and not allow to be selected.

The render time and OpengGL hardware render work well, but due the impossibility to work in normal way, under modeling, painting and animating condition, I moved to C4d (Cinema4d) under Wine, which is more stable and work without any problem.

I have also installed Maya 8.5 64bits Linux version in my Ubuntu 8.04 amd 64 and  it works perfect and fast!

The only thing that I miss from Modo is the ability to make displacement maps and photorealistic-IBL render super fast!

I tried to install Modo 302 under Wine, Cedega 6 and even Crosover. The only one where I was able to install it was wine 1.0.0 and 1.1.1/2.

I hope that Modo 302 will work in future Wine releases.

---

### Post by grimdeath on 2008-09-01
try reseting the viewports back to default (even if they already are) that cleared up a weird issue where everything was red for me.

ive cheated and put it back on my windows boot so I am afraid I cannot provide much support beyond that :P

---

### Post by Gorlist on 2009-12-31
Need to disable VBO (vertex buffering) for quad modeling - but its slow.. 9.10.

[http://ubuntuforums.org/showthread.php?t=1133018](http://ubuntuforums.org/showthread.php?t=1133018)

and

[http://ubuntuforums.org/showthread.php?t=1133018](http://ubuntuforums.org/showthread.php?t=1133018)

---

