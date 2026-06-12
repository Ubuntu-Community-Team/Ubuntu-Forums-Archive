---
title: "xwinwrap - 64"
date: 2007-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Squish on 2007-07-22
Sorry, I have looked all over, but I cant seem to figure out where to download a 64bit version of xwinwrap...?

I am using feisty, and am looking forward to doing the screensaver background trick. Through use of beryl, I have been convincing allot of people to start using ubuntu. Its funny what a little bit of eye candy will do... ha ha

is there a way to install the 32bit, I got the deb package of that downloaded, but I dont know the trick to installing it.

thanks!

---

### Post by Sqwishy on 2007-07-22
Here i just got it :) Download the two needed files from here
[http://webcvs.freedesktop.org/xapps/xwinwrap/](http://webcvs.freedesktop.org/xapps/xwinwrap/)
Then navagate to the directory they're at (ex. "cd ~/Desktop")
Then type make to compile the binary
Then type ./xwinwrap and if it says ' xwinwrap: Error: couldn't create command line ' then xwinwrap has been compiled goodly
Then do something like ' sudo mv xwinwrap /usr/local/bin/xwinwrap ' and you should be able to use it! 

Check out  [http://swik.net/xwinwrap](http://swik.net/xwinwrap)  for more info!

---

### Post by jorgeneo560 on 2007-08-04
i can't compile, i tried to intall this way..

cracker@cracker-desktop:~$ sudo cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
cvs checkout: CVS password file /home/cracker/.cvspass does not exist - creating a new file
cvs checkout: Updating xwinwrap
U xwinwrap/Makefile
U xwinwrap/xwinwrap.c
cracker@cracker-desktop:~$ cd xwinwrap
cracker@cracker-desktop:~/xwinwrap$ make
cc -g -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls   -c -o xwinwrap.o xwinwrap.c
En el fichero incluído de xwinwrap.c:26:
/usr/include/X11/Xlib.h:52:23: error: sys/types.h: No existe el fichero ó directorio
xwinwrap.c:32:36: error: X11/extensions/Xrender.h: No existe el fichero ó directorio
xwinwrap.c:34:20: error: stdlib.h: No existe el fichero ó directorio
xwinwrap.c:35:20: error: string.h: No existe el fichero ó directorio
xwinwrap.c:36:20: error: signal.h: No existe el fichero ó directorio
xwinwrap.c:37:19: error: stdio.h: No existe el fichero ó directorio
xwinwrap.c:38:20: error: unistd.h: No existe el fichero ó directorio
xwinwrap.c:39:22: error: sys/wait.h: No existe el fichero ó directorio
xwinwrap.c:40:22: error: sys/stat.h: No existe el fichero ó directorio
xwinwrap.c:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pid’
xwinwrap.c: En la función ‘addArguments’:
xwinwrap.c:62: aviso: declaración implícita de la función ‘realloc’
xwinwrap.c:62: aviso: la asignación crea un puntero desde un entero sin una conversión
xwinwrap.c: En la función ‘findArgbVisual’:
xwinwrap.c:96: error: ‘XRenderPictFormat’ no se declaró aquí (primer uso en esta función)
xwinwrap.c:96: error: (Cada identificador no declarado solamente se reporta una vez
xwinwrap.c:96: error: ara cada funcion en la que aparece.)
xwinwrap.c:96: error: ‘format’ no se declaró aquí (primer uso en esta función)
xwinwrap.c:115: aviso: declaración implícita de la función ‘XRenderFindVisualFormat’
xwinwrap.c:116: error: ‘PictTypeDirect’ no se declaró aquí (primer uso en esta función)
xwinwrap.c: En la función ‘sigHandler’:
xwinwrap.c:131: aviso: declaración implícita de la función ‘kill’
xwinwrap.c:131: error: ‘pid’ no se declaró aquí (primer uso en esta función)
xwinwrap.c: En la función ‘usage’:
xwinwrap.c:137: aviso: declaración implícita de la función ‘fprintf’
xwinwrap.c:137: aviso: declaración implícita incompatible de la función interna ‘fprintf’
xwinwrap.c:137: error: ‘stderr’ no se declaró aquí (primer uso en esta función)
xwinwrap.c: En la función ‘main’:
xwinwrap.c:170: aviso: declaración implícita incompatible de la función interna ‘fprintf’
xwinwrap.c:170: error: ‘stderr’ no se declaró aquí (primer uso en esta función)
xwinwrap.c:179: aviso: declaración implícita de la función ‘strcmp’
xwinwrap.c:224: aviso: declaración implícita de la función ‘atof’
xwinwrap.c:248: aviso: declaración implícita incompatible de la función interna ‘fprintf’
xwinwrap.c:280: aviso: declaración implícita incompatible de la función interna ‘fprintf’
xwinwrap.c:325: aviso: declaración implícita de la función ‘sprintf’
xwinwrap.c:325: aviso: declaración implícita incompatible de la función interna ‘sprintf’
xwinwrap.c:327: error: ‘pid’ no se declaró aquí (primer uso en esta función)
xwinwrap.c:327: aviso: declaración implícita de la función ‘fork’
xwinwrap.c:331: aviso: declaración implícita de la función ‘perror’
xwinwrap.c:334: aviso: declaración implícita de la función ‘execvp’
xwinwrap.c:336: aviso: declaración implícita de la función ‘exit’
xwinwrap.c:336: aviso: declaración implícita incompatible de la función interna ‘exit’
xwinwrap.c:342: aviso: declaración implícita de la función ‘signal’
xwinwrap.c:342: error: ‘SIGTERM’ no se declaró aquí (primer uso en esta función)
xwinwrap.c:343: error: ‘SIGINT’ no se declaró aquí (primer uso en esta función)
xwinwrap.c:347: aviso: declaración implícita de la función ‘waitpid’
xwinwrap.c:349: aviso: declaración implícita de la función ‘WIFEXITED’
xwinwrap.c:350: aviso: declaración implícita incompatible de la función interna ‘fprintf’
xwinwrap.c:351: aviso: declaración implícita de la función ‘WEXITSTATUS’
make: *** [xwinwrap.o] Error 1
cracker@cracker-desktop:~/xwinwrap$

---

### Post by riffer7 on 2007-11-18
I got the same error message!!! Any suggestions? Please help us out!

---

