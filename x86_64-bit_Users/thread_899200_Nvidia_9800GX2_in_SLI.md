---
title: "Nvidia 9800GX2 in SLI"
date: 2008-08-24
forum: x86 64-bit Users
---

### Post by IamNehalem on 2008-08-24
Hello people,

I have 2x9800gx2s installed and I'm just wondering how can i see if they are working in SLI or not? I mean i have installed the NVIDIA propriety drivers by administration-hardware drivers. I also installed the nvidia control panel but there is nowhere mentioned anything related to SLI.

Is SLI even available in linux?

Thankx

---

### Post by John.Michael.Kane on 2008-08-24
> **IamNehalem said:**
> Hello people,

I have 2x9800gx2s installed and I'm just wondering how can i see if they are working in SLI or not? I mean i have installed the NVIDIA propriety drivers by administration-hardware drivers. I also installed the nvidia control panel but there is nowhere mentioned anything related to SLI.

Is SLI even available in linux?

Thankx

Running the below command should add sli to you xorg conf file.

```
sudo nvidia-xconfig --sli=auto
```
Next restart with ctrl alt backspace

Or if you already setup your xorg previously. You can try adding the below line to your xorg Section "Device"

```
Option "sli" "Auto"
```

Other options:

Open your terminal and type the the below. (SLIAA is used as an example there are other options available incl AFR, SFR):
 > sudo nvidia-xconfig -sli=SLIAA
 > hit ctrl+alt+F2 to exit gnome. 
 > then sudo /etc/init.d/gdm stop to shutdown the X server
 > sudo /etc/init.d/gdm start

To verify SLI mode click Applications >> System Tools >> NVIDIA X Server Settings then
 > Select OpenGL Settings from the menu on the left.
 > Check Enable Heads-Up-Display
 > Type glxgears


Hope this helps.

---

### Post by zero7404 on 2009-05-01
> **John.Michael.Kane said:**
> Running the below command should add sli to you xorg conf file.

```
sudo nvidia-xconfig --sli=auto
```
Next restart with ctrl alt backspace

Or if you already setup your xorg previously. You can try adding the below line to your xorg Section "Device"

```
Option "sli" "Auto"
```

Other options:

Open your terminal and type the the below. (SLIAA is used as an example there are other options available incl AFR, SFR):
 > sudo nvidia-xconfig -sli=SLIAA
 > hit ctrl+alt+F2 to exit gnome. 
 > then sudo /etc/init.d/gdm stop to shutdown the X server
 > sudo /etc/init.d/gdm start

To verify SLI mode click Applications >> System Tools >> NVIDIA X Server Settings then
 > Select OpenGL Settings from the menu on the left.
 > Check Enable Heads-Up-Display
 > Type glxgears


Hope this helps.

just discovered this thread and tried out these steps, typing glxgears showed the window with moving gears and in the window it says "SLi"....is this confirmation that both GPUs are splitting the render for what's displayed on the screen ?

i'm transitioning from vista to ubuntu, but i want to be sure that both GPUs are getting equal usage all the time....

after a restart, looking in the X Server Display Configuration pane, i see Seiko (DFP-0 on GPU-0) listed for Model. that's telling me that it's using GPU-0 for the display....or not ?

---

### Post by inobe on 2009-05-01
just do

```
sudo lspci | grep VGA
```

if two cards appear' that's sli

---

