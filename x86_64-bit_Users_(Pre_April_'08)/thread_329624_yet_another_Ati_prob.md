---
title: "yet another Ati prob"
date: 2007-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by blu3sman on 2007-01-01
ok i've read  hundreds of threads on this Ati prob and have no luck solving it so figured maybe my prob is something different. I'm running Ubuntu Edgy 6.10 and am using an Ati Radeon x1900XTX card.

First up this is what my "fglrxinfo" tells me:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

yes its the common Mesa prob but no matter what instructions i've read/tried to fix this, nothing works.
for starters can someone tell me why my "XFree86-DRI" is missing and how do i "install" it??

---

### Post by blu3sman on 2007-01-04
AT LAST!!!!!....yes you guessed it i finally gotit running!!

Basically i reinstalled Edgy then DID NOT try to install video drivers how i had previously.

found this guide here that i hadnt seen before [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually)

followed it using the Ubuntu way and VIOLA, I GOT 3D GRAPHICS!! :) 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1900 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

---

