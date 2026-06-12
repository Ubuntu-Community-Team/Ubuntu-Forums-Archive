---
title: "enhanced graphics"
date: 2008-02-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by gimpguy2000 on 2008-02-29
Hi all,

I just built a new PC, now using Ubuntu GG 64 version. I now have the graphic capability to run something and thought I'd enable the enhanced graphics and such and it told me to restart the computer. When I did, my screen came back with quadruple windows and very "videod" look, horizontal lines all across making it impossible to read. I am using onboard Nvidia graphics, 256 mb. 

I was wondering a way to set it back , seeming I can't even read my screen. So I would assume I have to do this from command line, I have no idea how to though. 

Thanks!

Paul

I have an Asrock MB, 64 AMD athlon 4200 2X , 2 gigs ram>ddr2 ,  256 onboard NVIDIA.

---

### Post by gloscherrybomb on 2008-02-29
dpkg-reconfigure xserver-xorg

type this in to the terminal when you use recovery mode (press esc at grub)

Going for all the defaults usually works. Hope this helps.

---

### Post by bford16 on 2008-02-29
If you just want to reconfigure the video part of the x-server, use "dpkg-reconfigure -phigh."  (This command requires sudo.)  This will prompt you to set your video driver (you should try nvidia first), and video resolution (choose the highest rate you know your monitor can handle, plus some lower rates in case the higher ones don't work.)  If you still have problems, you may have to try again, and set your video driver to vesa.

---

### Post by gimpguy2000 on 2008-02-29
Thanks all, much appreciated. It seems the NVIDIA wasn't detected prior as I thought it was. It SHOULD have been but wasn't. It was unrecoverable and kept getting worse until I had no screen at all so I re-installed. This time, Ubuntu detected my NVIDIA on it's own and all is well. 

 Now I just have to figure out the 3-d cube everyone raves about and some other things, lol. 

Thanks again,

Paul

---

