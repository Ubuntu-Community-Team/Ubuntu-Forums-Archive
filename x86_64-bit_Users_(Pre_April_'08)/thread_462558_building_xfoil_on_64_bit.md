---
title: "building xfoil on 64 bit"
date: 2007-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pdavid on 2007-06-02
Hi

I'm trying to build xfoil [http://web.mit.edu/drela/Public/web/xfoil/]("http://web.mit.edu/drela/Public/web/xfoil/")

on Ubuntu Feisty Fawn amd64. I've had some experience building stuff, but I don't really know what I'm doing. Xfoil doesn't have a configure script, and relies on editing of makefiles.

The issue I'm having is that the first few bits work (it requires you to make "osgen", "osmap.o" and "LibPlt.a"), but when I do "make xfoil", I get standardish output, then the error 

david@ubuntu64:~/CFD/Xfoil/bin$ make xfoil
<snip>
g77 -c -g -O0 -C  ../osrc/osmap.f
gcc -c -m32  ../osrc/getosfile.c
g77 -o xfoil xfoil.o xpanel.o xoper.o xtcam.o xgdes.o xqdes.o xmdes.o xsolve.o xbl.o xblsys.o xpol.o xplots.o pntops.o xgeom.o xutils.o modify.o blplot.o polplt.o aread.o naca.o spline.o plutil.o iopol.o gui.o sort.o dplot.o profil.o userio.o frplot.o ntcalc.o osmap.o getosfile.o ../plotlib/libPlt.a  -L/usr/X11R6/lib -lX11 -i_dynamic
/usr/bin/ld: warning: i386 architecture of input file `getosfile.o' is incompatible with i386:x86-64 output
osmap.o: In function `osmap_':
/home/david/CFD/Xfoil/bin/../osrc/osmap.f:138: undefined reference to `getosfile_'
collect2: ld returned 1 exit status
make: *** [xfoil] Error 1

I've come across this before, and just added "-m32" to CFLAGS and LDFLAGS (for no good reason, other than I came across it in a google search, and thought I may as well give it a try, and it worked) but this doesn't seem to work here (nor does adding it to FFLAGS as well, as the program is written in Fortran 77). It seems to be some kind of 64-bit issue. Also, if I leave LDFLAGS blank, it doesn't give the incompatible input/output file error, but leaves the undefined reference to getosfile one.

So firstly, can anyone help me, or tell me what other information they might need to do so?

And secondly, is there some general set of instructions for building things on 64-bit systems?

Apologies if there's a similar thread already, but I did look and couldn't find one.

---

### Post by Pdavid on 2007-06-02
Just fixed it by using the 'f77' instead of the 'g77' compiler option in the makefile. Don't know what difference that should make,  but it works.

---

