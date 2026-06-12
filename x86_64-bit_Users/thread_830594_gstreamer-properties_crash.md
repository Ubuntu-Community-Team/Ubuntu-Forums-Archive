---
title: "gstreamer-properties crash"
date: 2008-06-16
forum: x86 64-bit Users
---

### Post by mo.reina on 2008-06-16
everytime i run gstreamer-properties and i hit the test button, it crashes.  here is the output

```
mo@mo-laptop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
Segmentation fault
mo@mo-laptop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
Segmentation fault

```

---

### Post by mo.reina on 2008-06-18
bump

---

### Post by willdeans on 2009-08-28
Please improve Linux webcam support.  People can truthfully point to poor webcam support as a reason to prefer Windows. 

#gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
Segmentation fault

#dmesg
[297746.226958] gstreamer-prope[26845]: segfault at 50 rip 7ff837695306 rsp 7fff42dc2610 error 4
[297769.838651] gstreamer-prope[26864]: segfault at ffffffffffffffff rip 7f2a7011b813 rsp 7fff7cd5a220 error 4
[297779.303310] gstreamer-prope[26887]: segfault at 50 rip 7f46b9b31306 rsp 7fffc525faa0 error 4
[298094.762400] gstreamer-prope[27195]: segfault at 50 rip 7f7f3ea44306 rsp 7fff4a170990 error 4
[298259.390914] gstreamer-prope[27381]: segfault at 0 rip 7f6b6ce4e3e4 rsp 7fff7806ce20 error 4
[298277.377215] gstreamer-prope[27408]: segfault at 50 rip 7f690b810306 rsp 7fff16f3cdd0 error 4
[298302.279638] gstreamer-prope[27447]: segfault at ffffffffffffffff rip 7f63bdf76813 rsp 7fffcabb5080 error 4

---

### Post by Yellow Pasque on 2009-08-28
See if this helps: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/115080](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/115080)
If not, search for similar bugs on Launchpad. Report the bug or it has 0 chance of being fixed.

---

