---
title: "Trouble getting martian to compile"
date: 2007-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Master Planeswalker on 2007-05-03
Hello,

I'm trying to install the martian software, to get my Agere DSP winmodem to work. I'm using an AMD-64 processor and 7.04 Ubuntu for 64-bit PC.

Details of the modem are (at least for now) irrelevant, since my problem is with compilation of the martian files.

I have installed build-essential succesfully, and I am executing the instructions carefully, but continuously getting the same error:

(my system is in spanish language)

```
modules/2.6.20-15-generic/build M="/home/alberto/martian/kmodule" clean
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.20-15-generic'
  CLEAN   /home/alberto/martian/kmodule/.tmp_versions
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: se sale del directorio `/home/alberto/martian/kmodule'
make -C modem/ clean
make[1]: se ingresa al directorio `/home/alberto/martian/modem'
-e     RM       OBJS
-e     RM       BINS
-e     RM       TOOLS
make[1]: se sale del directorio `/home/alberto/martian/modem'
alberto@hagane-no:~/martian$ 
alberto@hagane-no:~/martian$ make all
make -C kmodule/ modules
make[1]: se ingresa al directorio `/home/alberto/martian/kmodule'
make -C /lib/modules/2.6.20-15-generic/build M="/home/alberto/martian/kmodule"  modules
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/alberto/martian/kmodule/martian.o
/home/alberto/martian/kmodule/martian.c: En la función ‘martian_isr’:
/home/alberto/martian/kmodule/martian.c:160: aviso: no se utiliza el valor calculado
/home/alberto/martian/kmodule/martian.c: En la función ‘martian_add’:
/home/alberto/martian/kmodule/martian.c:662: aviso: se pasa el argumento 2 de ‘request_irq’ desde un tipo de puntero incompatible
  CC [M]  /home/alberto/martian/kmodule/marsio.o
  CC [M]  /home/alberto/martian/kmodule/mfifo.o
  LD [M]  /home/alberto/martian/kmodule/martian_dev.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/alberto/martian/kmodule/martian_dev.mod.o
  LD [M]  /home/alberto/martian/kmodule/martian_dev.ko
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: se sale del directorio `/home/alberto/martian/kmodule'
make -C modem/ all
make[1]: se ingresa al directorio `/home/alberto/martian/modem'
-e     CC       main.o
main.c: En la función ‘monitor_state’:
main.c:730: aviso: el formato ‘%d’ espera el tipo ‘int’, pero el argumento 4 es del tipo ‘long int’
main.c:731: aviso: el formato ‘%d’ espera el tipo ‘int’, pero el argumento 4 es del tipo ‘long int’
main.c:732: aviso: el formato ‘%d’ espera el tipo ‘int’, pero el argumento 4 es del tipo ‘long int’
main.c:733: aviso: el formato ‘%d’ espera el tipo ‘int’, pero el argumento 4 es del tipo ‘long int’
main.c:734: aviso: el formato ‘%d’ espera el tipo ‘int’, pero el argumento 4 es del tipo ‘long int’
-e     CC       dumpers.o
-e     CC       log.o
-e     CC       session.o
-e     CC       mport.o
mport.c: En la función ‘mport_init’:
mport.c:409: aviso: conversión a puntero desde un entero de tamaño diferente
-e     CC       pty.o
-e     CC       sysdep.o
-e     CC       isr.o
isr.c: En la función ‘serve_interrupts’:
isr.c:64: aviso: conversión de puntero a entero de tamaño diferente
isr.c: En la función ‘launch_isr_thread’:
isr.c:195: aviso: conversión a puntero desde un entero de tamaño diferente
-e     CC       smp.o
-e     CC       core_if.o
core_if.c: En la función ‘Get_PCI_BASE_ADDRESS_IO_MASK’:
core_if.c:183: aviso: entero grande truncado implícitamente al tipo unsigned
-e     CC       coresubst.o
-e     CC       link.o
link.c: En la función ‘link_to_driver’:
link.c:98: aviso: conversión de puntero a entero de tamaño diferente
link.c:102: aviso: conversión de puntero a entero de tamaño diferente
link.c:110: aviso: conversión de puntero a entero de tamaño diferente
-e     CC       tweakrelocsdynamic.o
tweakrelocsdynamic.c: En la función ‘tweak_areloc’:
tweakrelocsdynamic.c:178: aviso: conversión a puntero desde un entero de tamaño diferente
tweakrelocsdynamic.c:182: aviso: conversión a puntero desde un entero de tamaño diferente
tweakrelocsdynamic.c:223: aviso: conversión a puntero desde un entero de tamaño diferente
tweakrelocsdynamic.c: En la función ‘relocate_symbol’:
tweakrelocsdynamic.c:303: aviso: conversión de puntero a entero de tamaño diferente
tweakrelocsdynamic.c: En la función ‘locate_map_using_proc’:
tweakrelocsdynamic.c:331: aviso: conversión a puntero desde un entero de tamaño diferente
-e     CC       coreadd.o
-e     CC       elf386tweakrelocs
-e     LD       marscore.o
ld: Relocatable linking with relocations from format elf32-i386 (ltmdmobj.o) to format elf64-x86-64 (marscore.o) is not supported
make[1]: *** [marscore.o] Error 1
make[1]: se sale del directorio `/home/alberto/martian/modem'
make: *** [all] Error 2
alberto@hagane-no:~/martian$

```

looks like there might be a problem with the architechture, but the martian homepage says it's compatible with x86-64, and it beats me how to solve it.

Any input would be appreciated.
Thanks.

---

### Post by Coucouf on 2007-05-03
Hello !

Here's what you will be needing to compile your extraterrestrial module correctly :
- first make sure you have the packages **libc6-i386** and **libc6-dev-i386** installed via aptitude or synaptic
- then open the file [FONT="Courier New"]martian/modem/Makefile[/FONT] with your favorite text editor and replace on line 9 ```
HOST := $(shell uname -i)
``` by ```
HOST := $(shell uname -m)
```

With this it compiled correctly for me.

I can't tell you whether installing/running the driver works as I don't have such a modem myself. :)

---

### Post by Master Planeswalker on 2007-05-03
Thanks, I'll be trying that right away, and I'll post the results later!

EDIT: Thanks a lot, it installed OK this way. Tweaking the modem config files took a bit, but now it's working allright!

---

### Post by danierusama on 2008-03-05
I had the same problem and this post solved it in no time! :lolflag:

same distro, same archtype... ima still a linux newb, after this! i gotta say it is easy to use after a bit of fun with it, just get the needed packages fo' yo' shite and u got it half-done! :KS

big kudos to this guy who posted the solution !!!

---

