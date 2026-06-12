---
title: "Xgrafix on 7.04 64bit"
date: 2007-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by thobor on 2007-04-23
Im  running Ubuntu Feisty 7.04 64bit
I have been trying to install xgrafix on my system but I'm having problems with the tk.h and tcl.h files. According to the xgrafix README, Im supposed to gedit the Imakefile and add the paths to  tk.h and tcl.h.

using:
locate tk.h tcl.h
gives:
/usr/include/tcl8.4/tk-private/generic/tk.h
/usr/include/tcl8.4/tk.h

/usr/include/tcl8.4/tcl-private/generic/tcl.h
/usr/include/tcl8.4/tcl.h


This is what that part of my Imake-file looks like (but tried using both paths in the Imake-file):

XCOMM Location where tcl.h can be found
TCL_H = /usr/include/tcl8.4

XCOMM Location where tk.h can be found
TK_H = /usr/include/tcl8.4


Creating the Makefile seems to go smoothly
sudo xmkmf
mv -f Makefile Makefile.bak
imake -DUseInstalled -I/usr/lib/X11/config

but when trying to run "sudo make all" I get this error message:

gcc -O   -c -o xgcrosshair.o xgcrosshair.c
In file included from xgcrosshair.c:1:
xgrafixint.h:24:17: error: tcl.h: No such file or directory
xgrafixint.h:25:16: error: tk.h: No such file or directory
In file included from xgcrosshair.c:1:
xgrafixint.h:96: error: expected specifier-qualifier-list before ‘Tk_Window’
xgrafixint.h:166: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
xgrafixint.h:168: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mainWindow’
xgrafixint.h:278: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_ANSI_ARGS_’
xgrafixint.h:280: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_ANSI_ARGS_’
xgrafixint.h:286: warning: parameter names (without types) in function declaration
xgrafixint.h:287: warning: parameter names (without types) in function declaration
xgcrosshair.c:6: error: expected ‘)’ before ‘cl’
xgcrosshair.c:46: error: expected ‘)’ before ‘cl’
make: *** [xgcrosshair.o] Error 1

Seems unable to find the tcl.h and tk.h files for some reason.
any help would be appreciated

---

### Post by Rob_Frohne on 2007-08-28
Hi,

I was having a similar problem and installed the dev packages for both tcl 8.3 and 8.4 and the tk 8.4 dev packages and it went away.

Best wishes,

Rob

---

