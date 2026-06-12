---
title: "VTK package - libvtkTcl doesn't exist"
date: 2005-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by oeolartep on 2005-04-28
The libvtkTCL shared library doesn't exist in libvtk  package.

I'm trying to compile VTK with the "vtkpatented=ON" and "wrap TCL=ON" cmake options but get the following error :

Building shared library /../../VTK/bin/libvtkzlib.so...
/usr/bin/ld: gzio.o: relocation R_X86_64_32S can not be used when
making a shared object; recompile with -fPIC

I 've tested with -fPIC, but it didn't work.
I really need the libvtkTcl library. 

help me.

---

### Post by DJ_Max on 2005-04-28
[QUOTE=oeolartep]The libvtkTCL shared library doesn't exist in libvtk  package.

I'm trying to compile VTK with the "vtkpatented=ON" and "wrap TCL=ON" cmake options but get the following error :

Building shared library /../../VTK/bin/libvtkzlib.so...
/usr/bin/ld: gzio.o: relocation R_X86_64_32S can not be used when
making a shared object; recompile with -fPIC

I 've tested with -fPIC, but it didn't work.
I really need the libvtkTcl library. 

help me.[/QUOTE]
 There's a package called vtk-tcl, try:
```

sudo apt-get install vtk-tcl

```

---

### Post by oeolartep on 2007-04-02
thanks,  it works

---

