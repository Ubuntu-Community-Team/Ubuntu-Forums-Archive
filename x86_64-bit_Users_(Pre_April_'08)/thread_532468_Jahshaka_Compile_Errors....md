---
title: "Jahshaka Compile Errors..."
date: 2007-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by theharshone on 2007-08-22
Hi
I use feisty amd64 and I cannot get Jahshaka to work. I get this error:
```
rm -f libopengpulib.so.1.0.0 libopengpulib.so libopengpulib.so.1 libopengpulib.so.1.0
g++ -shared -Wl,-soname,libopengpulib.so.1 -o libopengpulib.so.1.0.0 gpumathlib.o gpumathlib_textures.o glsl_objects.o   -L/usr/share/qt3/lib -L/usr/X11R6/lib -L/usr/X11R6/lib ../../AuxiliaryLibraries/glew/libglew.a -lqt-mt -lGLU -lGL -lXmu -lXext -lX11 -lm -lpthread
/opt/kde/bin/ld: ../../AuxiliaryLibraries/glew/libglew.a(glew.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
../../AuxiliaryLibraries/glew/libglew.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [../lib/libopengpulib.so.1.0.0] Error 1
make[2]: Leaving directory `/tmp/jahshaka-2.0.0/jahshaka/source/OpenLibraries/opengpulib'
make[1]: *** [sub-opengpulib] Error 2
make[1]: Leaving directory `/tmp/jahshaka-2.0.0/jahshaka/source/OpenLibraries'
make: *** [sub-source-OpenLibraries] Error 2

```
Has anyone else got it working, if so, could they plz post a package?

Thanks!:)

---

