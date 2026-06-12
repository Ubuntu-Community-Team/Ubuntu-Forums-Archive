---
title: "Cant get mesa to compile"
date: 2006-06-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by danimal87 on 2006-06-05
I'm running 6.06 on an amd64 with and nvidia 6800gs

i'm following this guide [http://www.ubuntuforums.org/showthread.php?t=131659](http://www.ubuntuforums.org/showthread.php?t=131659)
and when I do ```
make linux-dri-x86-64
```

and I get this
could someone tell me what it means and how I should proceed?
thanks
```
(cd configs && rm -f current && ln -s linux-dri-x86-64 current)
make default
make[1]: Entering directory `/root/build/xserver/xorg/Mesa'
make[2]: Entering directory `/root/build/xserver/xorg/Mesa/src'
Making sources for linux-dri-x86-64
make[3]: Entering directory `/root/build/xserver/xorg/Mesa/src/glx/x11'
make[3]: Nothing to be done for `default'.
make[3]: Leaving directory `/root/build/xserver/xorg/Mesa/src/glx/x11'
make[3]: Entering directory `/root/build/xserver/xorg/Mesa/src/mesa'
make[4]: Entering directory `/root/build/xserver/xorg/Mesa/src/mesa'
make[5]: Entering directory `/root/build/xserver/xorg/Mesa/src/mesa/x86'
make[5]: Nothing to be done for `default'.
make[5]: Leaving directory `/root/build/xserver/xorg/Mesa/src/mesa/x86'
make[5]: Entering directory `/root/build/xserver/xorg/Mesa/src/mesa/x86-64'
make[5]: Nothing to be done for `default'.
make[5]: Leaving directory `/root/build/xserver/xorg/Mesa/src/mesa/x86-64'
cd drivers/dri ; make
make[5]: Entering directory `/root/build/xserver/xorg/Mesa/src/mesa/drivers/dri'
echo mach64 mga r128 r200 tdfx unichrome savage r300
mach64 mga r128 r200 tdfx unichrome savage r300
mach64
make[6]: Entering directory `/root/build/xserver/xorg/Mesa/src/mesa/drivers/dri/mach64'
make[6]: Nothing to be done for `default'.
make[6]: Leaving directory `/root/build/xserver/xorg/Mesa/src/mesa/drivers/dri/mach64'
mga
make[6]: Entering directory `/root/build/xserver/xorg/Mesa/src/mesa/drivers/dri/mga'
make[6]: Nothing to be done for `default'.
make[6]: Leaving directory `/root/build/xserver/xorg/Mesa/src/mesa/drivers/dri/mga'
r128
make[6]: Entering directory `/root/build/xserver/xorg/Mesa/src/mesa/drivers/dri/r128'
make[6]: Nothing to be done for `default'.
make[6]: Leaving directory `/root/build/xserver/xorg/Mesa/src/mesa/drivers/dri/r128'
r200
make[6]: Entering directory `/root/build/xserver/xorg/Mesa/src/mesa/drivers/dri/r200'
gcc -c -I. -I../../../../../src/mesa/drivers/dri/common -Iserver -I../../../../../include -I../../../../../include/GL/internal -I../../../../../src/mesa -I../../../../../src/mesa/main -I../../../../../src/mesa/glapi -I../../../../../src/mesa/math -I../../../../../src/mesa/transform -I../../../../../src/mesa/shader -I../../../../../src/mesa/swrast -I../../../../../src/mesa/swrast_setup -I../../../../../src/egl/main -I../../../../../src/egl/drivers/dri `pkg-config --cflags libdrm`  -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC -m64 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DHAVE_ALIAS -DUSE_X86_64_ASM -DRADEON_COMMON=1 -DRADEON_COMMON_FOR_R200 r200_context.c -o r200_context.o
make[6]: Leaving directory `/root/build/xserver/xorg/Mesa/src/mesa/drivers/dri/r200'
make[5]: Leaving directory `/root/build/xserver/xorg/Mesa/src/mesa/drivers/dri'
make[4]: Leaving directory `/root/build/xserver/xorg/Mesa/src/mesa'
make[3]: Leaving directory `/root/build/xserver/xorg/Mesa/src/mesa'
make[2]: Leaving directory `/root/build/xserver/xorg/Mesa/src'
make[1]: Leaving directory `/root/build/xserver/xorg/Mesa'

```

---

### Post by RAOF on 2006-06-06
That's successfully compiled.  What more do you want?

But a better way of getting XGL/Compiz would be to add the repositories from [compiz.net](compiz.net) - they're frequently updated from CVS, and packaged so you only need to **apt-get install compiz xserver-xgl**.  Then fiddle with config files, of course :(

---

