---
title: "Compiling wine under hardy"
date: 2008-04-14
forum: Wine
---

### Post by kolbycrouch on 2008-04-14
well this weekend i got rid of mandriva and went back to good old ubuntu, this time installing hardy because its close to release anyways.

im trying to compile wine 0.9.59 under hardy i386, and after using make i get this after about 10-20 mins, 

```
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./winex11.drv.spec    bitblt.o bitmap.o brush.o clipboard.o clipping.o codepage.o desktop.o dib.o dib_convert.o dib_dst_swap.o dib_src_swap.o event.o graphics.o init.o keyboard.o mouse.o opengl.o palette.o pen.o scroll.o settings.o text.o window.o winpos.o wintab.o x11ddraw.o x11drv_main.o xdnd.o xfont.o xim.o xinerama.o xrandr.o xrender.o xvidmode.o     version.res  -o winex11.drv.so  -luser32 -lgdi32 -ladvapi32 -lkernel32 -lntdll  -lSM -lICE -lXext -lX11  ../../libs/port/libwine_port.a  
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/kolby/Downloads/wine-0.9.59/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/kolby/Downloads/wine-0.9.59/dlls'
make: *** [dlls] Error 2


```
 
i dont want to install binary because i need even the smallest speed boost i can get.

thx in advance

---

### Post by ForksHolder on 2008-05-25
Same Problem. Any Help?

---

### Post by YokoZar on 2008-05-25
apt-get build-dep wine

---

