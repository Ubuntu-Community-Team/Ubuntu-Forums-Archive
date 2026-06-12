---
title: "Here same directions if you have installed Ubuntu and doesn't display graphic screen!"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by sidy on 2006-05-07
:D HELLO EVERY ONE;) 

I'm so happy! It's been nearly a month and specially the last 48 hours working hard "we" found the solution.

\\:D/ MY PC HAS GRAPHIC DISPLAY WORKING:-\" 

After many ways "we" have tryed, the last tryed was.
Ctrl+Alt+F1
-I went to the graphic card (physic), jot down the FX5200LP number.
-Then on root went to:

sudo dpkg-reconfigure xserver-xorg

-In there I've changed the standard graphic 

form "s3" to "nv" for nVidia,

-then enter. The next screen I deleted all information about S3 and put:

nv nVidia FX5200LP

-Then enter. And just the normal log in with graphic screen.

I just want thank all of you for keep trying through many ways.

Thank you;) 

Sidney.

---

