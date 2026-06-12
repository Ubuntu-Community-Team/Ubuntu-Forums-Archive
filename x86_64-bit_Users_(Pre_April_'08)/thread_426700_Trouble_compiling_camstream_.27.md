---
title: "Trouble compiling camstream .27"
date: 2007-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by firecat53 on 2007-04-28
Hi. I'm trying to compile camstream 0.27 and am  not having much luck. Version .26 in the repos is know not to work with my webcam (as is camorama). I'm just looking for a simple tool to take and save some pix with the webcam. Feisty AMD-64. HP pavilion dv6000

I've got all the requisite dev files (libqt3-headers, libjpeg-dev, libpng-dev), automake, build-essential.

QTDIR=/usr/share/qt3
export QTDIR

./configure works just fine.

make gives the following:
```

 make  all-recursive
make[1]: Entering directory `/home/firecat53/camstream-0.27'
Making all in ccvt
make[2]: Entering directory `/home/firecat53/camstream-0.27/ccvt'
if gcc -DPACKAGE_NAME=\"ccvt\" -DPACKAGE_TARNAME=\"ccvt\" -DPACKAGE_VERSION=\"0.5\" -DPACKAGE_STRING=\"ccvt\ 0.5\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ccvt\" -DVERSION=\"0.5\" -DSTDC_HEADERS=1 -DHAVE_MMX= -DLITTLE_ENDIAN=1 -D_REENTRANT= -DQT_THREAD_SUPPORT= -I. -I.     -g -O2 -MT ccvt_misc.o -MD -MP -MF ".deps/ccvt_misc.Tpo" -c -o ccvt_misc.o ccvt_misc.c; \
        then mv -f ".deps/ccvt_misc.Tpo" ".deps/ccvt_misc.Po"; else rm -f ".deps/ccvt_misc.Tpo"; exit 1; fi
gcc  -g -O2 -c ccvt_mmx.S
ccvt_mmx.S: Assembler messages:
ccvt_mmx.S:306: Error: suffix or operands invalid for `push'
ccvt_mmx.S:306: Error: suffix or operands invalid for `push'
ccvt_mmx.S:306: Error: suffix or operands invalid for `push'
ccvt_mmx.S:308: Error: suffix or operands invalid for `push'
ccvt_mmx.S:203: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:312: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:312: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:312: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:315: Error: suffix or operands invalid for `push'
ccvt_mmx.S:315: Error: suffix or operands invalid for `push'
ccvt_mmx.S:315: Error: suffix or operands invalid for `push'
ccvt_mmx.S:317: Error: suffix or operands invalid for `push'
ccvt_mmx.S:203: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:319: Error: suffix or operands invalid for `push'
ccvt_mmx.S:319: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:321: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:321: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:321: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:324: Error: suffix or operands invalid for `push'
ccvt_mmx.S:324: Error: suffix or operands invalid for `push'
ccvt_mmx.S:324: Error: suffix or operands invalid for `push'
ccvt_mmx.S:326: Error: suffix or operands invalid for `push'
ccvt_mmx.S:203: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:330: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:330: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:330: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:333: Error: suffix or operands invalid for `push'
ccvt_mmx.S:333: Error: suffix or operands invalid for `push'
ccvt_mmx.S:333: Error: suffix or operands invalid for `push'
ccvt_mmx.S:335: Error: suffix or operands invalid for `push'
ccvt_mmx.S:203: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:337: Error: suffix or operands invalid for `push'
ccvt_mmx.S:337: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:339: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:339: Error: suffix or operands invalid for `pop'
ccvt_mmx.S:339: Error: suffix or operands invalid for `pop'
make[2]: *** [ccvt_mmx.o] Error 1
make[2]: Leaving directory `/home/firecat53/camstream-0.27/ccvt'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/firecat53/camstream-0.27'
make: *** [all] Error 2

```


Any thoughts?  Or alternatives?  My webcam works with Ekiga, but that really doesn't have much other than a low-res screen capture. Not sure what tools are available w/ Kopete.

Thanks! Scott

---

