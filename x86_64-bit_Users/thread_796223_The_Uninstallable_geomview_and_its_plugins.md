---
title: "The Uninstallable: geomview and its plugins"
date: 2008-05-16
forum: x86 64-bit Users
---

### Post by TheOne...more on 2008-05-16
here is the story;

I installed gutsy and every thing went ok "with lots of efforts of course", but when i tried to install geomview from the repo it always gave me this error "/usr/lib/geomview/gvx: Symbol `_XmStrings' has different size in shared object, consider re-linking" and the idea suggested itself, compile the source!

so here what i did, i downloaded the latest and compiled it. it complained two or three times but i solved these and every thing went fine, and even it actually did start "from the source directory"...lol. BUT when i typed "make install" it always refused to start giving me this message "/usr/local/libexec/geomview/gvx: error while loading shared libraries: libgeomview-1.9.2.so: cannot open shared object file: No such file or directory".

I tried to add the /usr/local/lib path of geomview to the environment variable PATH, nothing changed. I thought the fault was the geomview script and tried to add the /usr/local/lib path to GEOMVIEW_LOAD_PATH, nothing changed. and when every thing seemed to fail i tried older versions until 1.9.1, but nothing changed.

not only this, when i tried to ./configure the orrery it complained about libtcl although i have tcl and tk packages installed.

So what is wrong!!?

oh i almost forgot to mention that it worked fine on etch, which added to my wonder.

thanx all

---

