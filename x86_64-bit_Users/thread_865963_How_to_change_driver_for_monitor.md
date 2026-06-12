---
title: "How to change driver for monitor?"
date: 2008-07-21
forum: x86 64-bit Users
---

### Post by gretarsson on 2008-07-21
I am having problem about my monitor withch is Samsung LCD tv with pc (1376x768) input,  I have ubuntu 8.04Hardy with nvidia 7600 GS G.card but if I use nvidia driver for my card then I can not go higher than 640x400 but if I use default driver (vesa) I can go up to 800x600 but in my tv manual they say use vesa driver to go up to 1376x768 but how do I change my vesa driver in terminal so I can go up to 1376x768? I have no problem about install nivida driver but in my nvidia settings I can only use 640x400 or 400x320.
Thanks

---

### Post by Master Chief on 2008-07-21
Did you install nvidia-settings i.e. do you have the following menu item:

System -> Administration -> NVIDIA X Server Settings

If not you; can install it with the Synaptic Package Manager (search for "nvidia-settings").

If you did, or after the installation open it and go to "X Server Display Configuration". Does that list your monitor/the correct monitor?

You can also check the native/best resolutions under:

GPU 0 - (GeForce 7600 GS) -> DFP-0 (Samsung aAaAaAaA)

---

### Post by DJ_Peng on 2008-07-21
I ended up using a Windows drivers .inf file (I think it was an *.inf file) for my monitor when I got my new Envision LCD monitor. That worked well enough that even SecondLife knows my system supports 1280x1024 resolution, something it refused to do with my old LCD monitor.

---

### Post by gretarsson on 2008-07-21
> **Master Chief said:**
> Did you install nvidia-settings i.e. do you have the following menu item:

System -> Administration -> NVIDIA X Server Settings

If not you; can install it with the Synaptic Package Manager (search for "nvidia-settings").

If you did, or after the installation open it and go to "X Server Display Configuration". Does that list your monitor/the correct monitor?

You can also check the native/best resolutions under:

GPU 0 - (GeForce 7600 GS) -> DFP-0 (Samsung aAaAaAaA)

I have nvidia driver for my Ubuntu 8.04 amd64 and nvidia X server setting but if I connect my pc with Acer monitor I got up to 1900x1000 but this pc are for my son and he is using Samsung LCD with pc inplug(1372x768) and if I connect that pc to his LCD with nvidia driver I can not go higher than 640x400, so what I need to know how can I changes this or how to I change to vesa driver, I know my default driver is vesa but he only give my 800x600 and in Samsung manual they talk about vesa driver which support 1376x768.
Thanks

---

### Post by Blakefreak on 2008-07-21
alt F2
gksudo displayconfig-gtk

Then pick your monitor and driver.

Restart

Happy

---

### Post by gretarsson on 2008-07-22
> **Blakefreak said:**
> alt F2
gksudo displayconfig-gtk

Then pick your monitor and driver.

Restart

Happy

Thank you that works for me now I can display my screen up to 1280x768 I just use LCD panel display in 60Hz and nvidia 7series
gretarsson :)

---

### Post by gretarsson on 2008-07-22
> **Blakefreak said:**
> alt F2
gksudo displayconfig-gtk

Then pick your monitor and driver.

Restart

Happy

Thank you that works for me now I can display my screen up to 1280x768 I just use LCD panel display in 60Hz and nvidia 7series
gretarsson :)

---

