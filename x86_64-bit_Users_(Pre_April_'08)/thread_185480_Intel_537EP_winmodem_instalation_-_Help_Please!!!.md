---
title: "Intel 537EP winmodem instalation - Help Please!!!"
date: 2006-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by andremun on 2006-05-31
Greetings,
I'm new to Linux in general.  I have an AMD64 computer with Ubuntu 5.10 installed. I tried to install my modem, and I only get error messages.  Here are the results:

This packages were installed:

$ sudo apt-get install linux-headers-2.6.12-9-amd64-generic
$ sudo dpkg -i gcc-3.4-base_3.4.4-6ubuntu8.1_amd64.deb
$ sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8.1_amd64.deb
$ sudo dpkg -i gcc-3.4_3.4.4-6ubuntu8.1_amd64.deb


Test 1 


mandres@el-bicho:~/intel-537EP_secure-2.60.80.1$ make clean
cd coredrv; make clean
make[1]: Entering directory `/home/mandres/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.ko *.o .*.o.cmd *.mod.c *~ core .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/home/mandres/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.o *.ko

mandres@el-bicho:~/intel-537EP_secure-2.60.80.1$ make 537
   Module precompile check
   Current running kernel is: 2.6.12-9-amd64-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No existe el fichero o el directorio
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No existe el fichero o el directorio
   version.h matches running kernel
/bin/sh: /sbin/lspci: No existe el fichero o el directorio
Modem type not determined.
$ export MODEM_TYPE=<type>
with type=537 or 537EP or 537SP or 537EA or 537AA
mandres@el-bicho:~/intel-537EP_secure-2.60.80.1$


Prueba 2

mandres@el-bicho:~/intel-537EP_secure-2.60.80.0$ make clean
cd coredrv; make clean
make[1]: Entering directory `/home/mandres/intel-537EP_secure-2.60.80.0/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/mandres/intel-537EP_secure-2.60.80.0/coredrv'
rm -f *.o *.ko

mandres@el-bicho:~/intel-537EP_secure-2.60.80.0$ make 537
   Module precompile check
   Current running kernel is: 2.6.12-9-amd64-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No existe el fichero o el directorio
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No existe el fichero o el directorio
   version.h matches running kernel
2.6.12-9-amd64-generic
make[1]: Entering directory `/home/mandres/intel-537EP_secure-2.60.80.0/coredrv'
make -C /lib/modules/2.6.12-9-amd64-generic/build SUBDIRS=/home/mandres/intel-537EP_secure-2.60.80.0/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-amd64-generic'
  CC [M]  /home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.o
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:70: aviso: el tipo de dato por defecto es `int' en la declaraciÃ³n de `EXPORT_SYMBOL_NOVERS'
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:70: aviso: nombres de parÃ¡metros (sin tipos) en la declaraciÃ³n de la funciÃ³n
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:70: aviso: la definiciÃ³n de datos no tiene tipo o clase de almacenamiento
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c: In function `power_callback':
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:295: error: `PM_SAVE_STATE' no se declarÃ³ aquÃ* (primer uso en esta funciÃ³n)
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:295: error: (Cada identificador no declarado solamente se reporta una vez
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:295: error: para cada funcion en la que aparece.)
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c: In function `open':
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:394: aviso: `pm_register' es obsoleto (declarado en include/linux/pm.h:106)
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c: In function `close':
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:416: aviso: `pm_unregister' es obsoleto (declarado en include/linux/pm.h:111)
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c: At top level:
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:754: aviso: inicializaciÃ³n de tipo de puntero incompatible
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:755: aviso: inicializaciÃ³n de tipo de puntero incompatible
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c: In function `kScheduleDPC':
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:861: aviso: declaraciÃ³n implÃ*cita de la funciÃ³n `pm_access'
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c: In function `dspdrv_CommRamISR':
/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.c:877: aviso: la declaraciÃ³n de la funciÃ³n no es un prototipo
make[3]: *** [/home/mandres/intel-537EP_secure-2.60.80.0/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/mandres/intel-537EP_secure-2.60.80.0/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-amd64-generic'
make[1]: *** [537core_26] Error 2
make[1]: Leaving directory `/home/mandres/intel-537EP_secure-2.60.80.0/coredrv'
2.6.12-9-amd64-generic
Failed to build driver
mandres@el-bicho:~/intel-537EP_secure-2.60.80.0$


It appears to be that there are errors in the code in both drivers 2.60.80.1 and 2.60.80.0.  What am I doing wrong?? or do these drivers won't compile for this version?

---

### Post by chuckman78 on 2006-07-09
Hi andremun:

This might work:

[http://www.ubuntuforums.org/showthread.php?t=210405&highlight=537ep]("http://www.ubuntuforums.org/showthread.php?t=210405&highlight=537ep")

Regards,

Carlos.

---

