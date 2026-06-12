---
title: "Really low fps in Counter Strike Source"
date: 2008-09-17
forum: Wine
---

### Post by swankyfb on 2008-09-17
Hello, in general i am having a really bad frame rate and i am estimating it is at maybe 5 fps. might anyone have a solution for my problem?

thanks for looking.

---

### Post by hikaricore on 2008-09-17
More info would be helpful for anyone who could offer assistance.

Video hardware (this one is quite important), CPU, RAM, ect.

If you're using an integrated chipset such as Intel you may be at an impasse.
This type of hardware extensively uses Direct3D in a ***dows environment to make
up for its lacking abilities on its own.  Such hardware usually has limited OpenGL support
and quite limited or badly written drivers under Linux.  OpenGL support is key under WINE
as WINE basically converts directx commands into OpenGL for video output.

If you do have capable hardware you'll need to let us know how you installed the drivers and such.

---

### Post by Trap3d on 2008-11-02
had the same trouble, upgraded drivers now it works like a charm, lot of ppl miss that on ubuntu cause on xp standart drivers make laggy even page scrolling down but here its fine so yea pretty much just go **System>Administration>Hardware drivers** and choose ur cards latest driver select and push Activate then restart and should work excelently

---

### Post by Dark9204 on 2008-11-02
Remember that you must run it in -dxlevel 81 tag. otherwise you will only get about 20FPS no matter what and the game will lag.

Example:
env WINEPREFIX="/home/erik/.wine" wine "C:\Program Files\Steam\Steam.exe" -applaunch 240 -dxlevel 81

---

### Post by Ameneon on 2008-11-02
Yup, quite remarkable what a difference that makes. 82 seems to work nice too, although I don't know how much a difference there would be between the two in terms of performance and looks.

---

### Post by tillerz on 2009-11-05
Hi there, I have a very similar problem, my computer is running at like 20 FPS max.. I've followed guides on google on lowering it with the use of commands but not had much joy..
 
System spec:
 
Dell Optiplex 170L
Intel (R)
Celeron(R) CPU 3.06GHz
512MB of RAM
 
Not sure about updating drivers either really, could really use someone who can guide me through if possible, 
 
Thanks :)

---

### Post by gradinaruvasile on 2009-11-05
> **swankyfb said:**
> Hello, in general i am having a really bad frame rate and i am estimating it is at maybe 5 fps. might anyone have a solution for my problem?

thanks for looking.

Open a terminal, type:

```
lspci
```

then press enter. Post the output of that command (copy-paste) in your forum message (useful if its between the CODE (#) tags).
The command lists your hardware on your computer.

---

