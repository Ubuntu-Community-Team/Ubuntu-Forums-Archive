---
title: "Installing java &amp; flash player"
date: 2005-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by xodeus on 2005-03-22
Hi all.
I've just installed ubuntu and it's a really great port. I really do like it. But I've now come to this point that I need java & flash installed. When I download java from java.com I get the java package so Azureus works but there's no javaplugin_oji.so for my browser. How can it be? Really don't understand. 
Now I can't get the flashplayer-mozilla package either. I get some errors when trying to run an apt-get update. 
The sources.lit & errors are attached.
Please help me out.

//XoDeus

---

### Post by sauteur on 2005-03-22
it's better to use deb packages
refer to [http://ubuntuguide.org/](http://ubuntuguide.org/) for instructions


Regards.
Sauteur

---

### Post by xodeus on 2005-03-22
[QUOTE=sauteur]it's better to use deb packages
refer to [http://ubuntuguide.org/](http://ubuntuguide.org/) for instructions


Regards.
Sauteur[/QUOTE]

As I mentioned then I tried to use the ubuntuguide and can't get the flashplayer-mozilla package. And java is now found as deb package, so it has to be installed from java.com, but it does not provide libjavaplugin_oji.so, I miss that.

---

### Post by mthaddon on 2005-03-22
I don't have java installed, but I do have a working flash player:

sudo apt-get install gpl-flash

It's _really_ buggy and I need to kill it sometimes cos it takes up so much memory, but at least I can view some flash. I don't know if there is a native 64-bit flash plugin. From what I can understand the workaround involves installing 32-bit firefox, but I haven't tried it myself.

Good luck.

Tom

---

### Post by derjohan on 2005-03-22
Sun doesn't provide a 64 bit java plugin. try blackdown java 1.4.2 ([http://www.blackdown.org)](http://www.blackdown.org)), they have a 64 bit mozilla plugin which works for me.

The flashplayer from the gpl-flash homepage ([http://gplflash.sourceforge.net/](http://gplflash.sourceforge.net/)) is a bit newer than the one in the ubuntu repository. I haven't had any big problems with it so far.
It's not optimal, but it works.

---

### Post by blinksilver on 2005-03-22
okay, so i have grabed gpl flash, did an autogen

it worked out then i did a make, and nada,

here is a output, any help is good help

soganess@M6805:~/gplflash-0.4.13$ sudo sh autogen.sh
Password:
I am going to run ./configure with no arguments - if you wish
to pass any to it, please specify them on the autogen.sh command line.
/usr/share/aclocal/pkg.m4:5: warning: underquoted definition of PKG_CHECK_MODULES
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for jpeg_destroy_decompress in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for gzsetparams in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for XOpenDisplay in -lX11... yes
checking X11/XKBlib.h usability... yes
checking X11/XKBlib.h presence... yes
checking for X11/XKBlib.h... yes
checking for mad_frame_decode in -lmad... yes
checking mad.h usability... yes
checking mad.h presence... yes
checking for mad.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating lib/Makefile
config.status: creating player/Makefile
config.status: creating plugin/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

Now type 'make' to compile libflash.
soganess@M6805:~/gplflash-0.4.13$ mkaer
bash: mkaer: command not found
soganess@M6805:~/gplflash-0.4.13$ make
make  all-recursive
make[1]: Entering directory `/home/soganess/gplflash-0.4.13'
Making all in lib
make[2]: Entering directory `/home/soganess/gplflash-0.4.13/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/soganess/gplflash-0.4.13/lib'
Making all in player
make[2]: Entering directory `/home/soganess/gplflash-0.4.13/player'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/soganess/gplflash-0.4.13/player'
Making all in plugin
make[2]: Entering directory `/home/soganess/gplflash-0.4.13/plugin'
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2 -Wall   -o libnpflash.la -rpath /usr/local/lib/mozilla/plugins/ -L../lib/.libs  -lflash libnpflash_la-plugin.lo libnpflash_la-npunix.lo
gcc -shared  .libs/libnpflash_la-plugin.o .libs/libnpflash_la-npunix.o  -Wl,--rpath -Wl,/home/soganess/gplflash-0.4.13/lib/.libs/.libs -Wl,--rpath -Wl,/usr/local/lib -L/home/soganess/gplflash-0.4.13/lib/.libs /home/soganess/gplflash-0.4.13/lib/.libs/.libs/libflash.so  -Wl,-soname -Wl,libnpflash.so.0 -o .libs/libnpflash.so.0.0.0
gcc: /home/soganess/gplflash-0.4.13/lib/.libs/.libs/libflash.so: No such file or directory
make[2]: *** [libnpflash.la] Error 1
make[2]: Leaving directory `/home/soganess/gplflash-0.4.13/plugin'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/soganess/gplflash-0.4.13'
make: *** [all] Error 2

---

### Post by wmcbrine on 2005-03-23
[QUOTE=derjohan]The flashplayer from the gpl-flash homepage ([http://gplflash.sourceforge.net/](http://gplflash.sourceforge.net/)) is a bit newer than the one in the ubuntu repository. I haven't had any big problems with it so far.
It's not optimal, but it works.[/QUOTE]
It crashes my Firefox the instant I go to a site with Flash, even with the FlashBlock extension in place. This is with either the deb or compiling the latest source.

So for now, I built a null plugin for Flash, just to get rid of the annoying "missing plugin" message. (Some guy had done it for FreeBSD a while back; I just made a couple minor patches and recompiled. I found it by searching for "null plugin"... I was thinking I'd have to do more, but by luck, there it was, ready-made.)

---

### Post by blinksilver on 2005-03-23
the one the repo does that, but i think if you comple from source yourself you should be gold, i got it to work on a prevous release, but nada now

---

### Post by blinksilver on 2005-03-23
okay did some more work and now i am here
soganess@M6805:~/gplflash-0.4.13$ sudo make
make  all-recursive
make[1]: Entering directory `/home/soganess/gplflash-0.4.13'
Making all in lib
make[2]: Entering directory `/home/soganess/gplflash-0.4.13/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/soganess/gplflash-0.4.13/lib'
Making all in player
make[2]: Entering directory `/home/soganess/gplflash-0.4.13/player'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/soganess/gplflash-0.4.13/player'
Making all in plugin
make[2]: Entering directory `/home/soganess/gplflash-0.4.13/plugin'
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2 -Wall   -o libnpflash.la -rpath /usr/local/lib/mozilla/plugins/ -L../lib/.libs  -lflash libnpflash_la-plugin.lo libnpflash_la-npunix.lo
gcc -shared  .libs/libnpflash_la-plugin.o .libs/libnpflash_la-npunix.o  -Wl,--rpath -Wl,/home/soganess/gplflash-0.4.13/lib/.libs/.libs -Wl,--rpath -Wl,/usr/local/lib -L/home/soganess/gplflash-0.4.13/lib/.libs /home/soganess/gplflash-0.4.13/lib/.libs/.libs/libflash.so  -Wl,-soname -Wl,libnpflash.so.0 -o .libs/libnpflash.so.0.0.0
gcc: /home/soganess/gplflash-0.4.13/lib/.libs/.libs/libflash.so: No such file or directory
make[2]: *** [libnpflash.la] Error 1
make[2]: Leaving directory `/home/soganess/gplflash-0.4.13/plugin'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/so



oh and one more thing, if you really want flash there is something in the rep called swf-player i belive it does some flash,

---

### Post by blinksilver on 2005-03-23
oh and there is a patch for amd64 user s..............

-- npapi.h_ORIG 2004-11-26 07:17:23.361879416 +0000 
+++ npapi.h 2004-11-26 07:28:09.477654888 +0000 
@@ -36,7 +36,7 @@ 
typedef unsigned short uint16; 
#endif 
#ifndef _UINT32 
-#if defined(__alpha) 
+#if defined(__alpha) || defined(__x86_64__) 
typedef unsigned int uint32; 
#else /* __alpha */ 
typedef unsigned long uint32; 
@@ -46,7 +46,7 @@ 
typedef short int16; 
#endif 
#ifndef _INT32 
-#if defined(__alpha) 
+#if defined(__alpha) || defined(__x86_64__) 
typedef int int32; 
#else /* __alpha */ 
typedef long int32; 
 
 
----------------------------------------------------- 
Fix type size for AMD64 
 
--- graphic32.cc_ORIG 2004-11-26 07:34:59.122379424 +0000 
+++ graphic32.cc 2004-11-26 07:35:36.089759528 +0000 
@@ -30,7 +30,11 @@ 
 
#define PRINT 0 
 
+#if defined(__x86_64__) 
+typedef unsigned int TYPE; 
+#else 
typedef unsigned long TYPE; 
+#endif 
 
GraphicDevice32::GraphicDevice32(FlashDisplay *fd) : GraphicDevice(fd) 
{ 
 
 
----------------------------------------------------- 
Fix type size for AMD64 
 
 
--- swf.h_ORIG 2004-11-26 07:28:38.748205088 +0000 
+++ swf.h 2004-11-26 07:33:37.975715592 +0000 
@@ -18,6 +18,17 @@ 
extern int debug; 
 
// Global Types 
+#if defined(__x86_64__) 
+typedef unsigned int U32, *P_U32, **PP_U32; 
+typedef signed int S32, *P_S32, **PP_S32; 
+typedef unsigned short U16, *P_U16, **PP_U16; 
+typedef signed short S16, *P_S16, **PP_S16; 
+typedef unsigned char U8, *P_U8, **PP_U8; 
+typedef signed char S8, *P_S8, **PP_S8; 
+typedef signed long SFIXED, *P_SFIXED; 
+typedef signed long SCOORD, *P_SCOORD; 
+typedef unsigned long BOOL; 
+#else 
typedef unsigned long U32, *P_U32, **PP_U32; 
typedef signed long S32, *P_S32, **PP_S32; 
typedef unsigned short U16, *P_U16, **PP_U16; 
@@ -27,6 +38,7 @@ 
typedef signed long SFIXED, *P_SFIXED; 
typedef signed long SCOORD, *P_SCOORD; 
typedef unsigned long BOOL; 
+#endif 
 
#define ZOOM(v,f) ((v)/(f)) 
 
 
 
----------------------------------------------------- 
FIX NULL, when font is not defined: eg: [http://www.emme.com](http://www.emme.com) 
 
 
 
--- text.cc_ORIG 2004-11-26 07:45:05.905134424 +0000 
+++ text.cc 2004-11-27 13:31:47.560005720 +0000 
@@ -91,6 +91,10 @@ 
} 
} 
 
+ // Fix code when Font is null, set a default font 
+ if (font == NULL) { 
+ font = new SwfFont(0); 
+ } 
if (tr->nbGlyphs) { 
for(n=0; n < tr->nbGlyphs; n++) { 
tr->glyphs[n].code = font->getGlyphCode(tr->glyphs[n].index); 
@@ -166,7 +170,9 @@ 
fmat.a = fontHeight/1000.0; 
fmat.d = fontHeight/1000.0; 
 
- assert(font != 0); 
+ //Fix case where font is not defined : eg [http://www.emme.com](http://www.emme.com) 
+ if (font != NULL) { // TODO: 
+ 
for (g = 0; g < tr->nbGlyphs; g++) 
{ 
Shape *shape; 
@@ -198,7 +204,7 @@ 
printf("\n"); 
#endif 
} 
- 
+} 
if (gd->showMore) { 
tmat = (*gd->adjust) * (*matrix); 
 
 
----------------------------------------------------- 
 
Fix random crashes occuring on AMD64/SMP with Firefox 1.0 (64 bits). Still not 100% fixed. Help needed here to understand multithreading issues. 
The code seems to be not thread safe, and is responsible for free() exception and wrong pointers. 
For now, semaphore has been added to limit random crashes. Some allocated memory cannot be released, because it sometimes crashes (don't know why). 
 
 
 
--- plugin.c_ORIG 2004-11-26 08:44:31.722047856 +0000 
+++ plugin.c 2004-11-27 12:41:33.544205768 +0000 
@@ -26,6 +26,7 @@ 
#include <X11/IntrinsicP.h> 
#include <X11/Core.h> 
#include <X11/CoreP.h> 
+#include <pthread.h> 
 
#define PRINT 0 
#define FLASH_XEVENT_MASK (ExposureMask|ButtonReleaseMask|ButtonPressMask|PointerMotionMask|KeyPressMask|KeyReleaseMask) 
@@ -70,6 +71,7 @@ 
static long FlashGraphicInitX11(PluginInstance* This); 
static void FlashCopyX11(PluginInstance* This); 
 
+static pthread_mutex_t synchro; 
 
#ifdef C6R5 
// Ugly but it makes it work if it is compiled on 
@@ -175,19 +177,18 @@ 
NPP_Destroy(NPP instance, NPSavedData** save) 
{ 
PluginInstance* This; 
- 
if (instance == NULL) 
return NPERR_INVALID_INSTANCE_ERROR; 
 
This = (PluginInstance*) instance->pdata; 
 
if (This != NULL) { 
- LoadCtxt *l,*prev; 
- 
+ pthread_mutex_lock(&synchro); 
if (This->timer) { 
XtRemoveTimeOut(This->timer); 
This->timer = 0; 
} 
+ 
if (This->fh) { 
XShmDetach(This->dpy, &This->segInfo); 
XSync(This->dpy,False); 
@@ -198,26 +199,10 @@ 
This->fh = 0; 
} 
 
-/* If this line is included mozilla crashes 50%-75% of the time when leaving a page 
- with flash-animation, probably because mozilla already has removed the handler. 
- Somebody with actual knowledge about this should try to make a real fix. 
- 
- 
- XtRemoveRawEventHandler(This->widget, FLASH_XEVENT_MASK, 
- True, (XtEventHandler) flashEvent, (XtPointer)This); 
-*/ 
- 
- prev = 0; 
- for(l = This->loading; l; prev = l, l = l->next) { 
- free(l->data); 
- free(l->url); 
- free(prev); 
- } 
- free(prev); 
- 
- NPN_MemFree(instance->pdata); 
- instance->pdata = NULL; 
- } 
+ NPN_MemFree(instance->pdata); 
+ instance->pdata = NULL; 
+ pthread_mutex_unlock(&synchro); 
+ }  
 
return NPERR_NO_ERROR; 
} 
@@ -272,6 +257,7 @@ 
static void 
flashWakeUp(XtPointer client_data, XtIntervalId *id) 
{ 
+ pthread_mutex_lock(&synchro); 
PluginInstance* This; 
long cmd; 
long wakeUp; 
@@ -295,6 +281,7 @@ 
This->timer = 0; 
} 
} 
+ pthread_mutex_unlock(&synchro); 
} 
 
NPError  
@@ -381,7 +368,6 @@ 
LoadCtxt *l; 
 
This = (PluginInstance*) instance->pdata; 
- 
for(l = This->loading; l != 0; l = l->next) { 
if (l->url && strstr(stream->url, l->url)) { 
break; 
@@ -395,7 +381,6 @@ 
} else { 
l->data = (char *) realloc(l->data, l->size+len); 
} 
- 
memcpy(&l->data[offset], buffer, len); 
l->size += len; 
status = FlashParse(This->fh, l->level, l->data, l->size); 
@@ -446,7 +431,8 @@ 
if (This == 0) return; 
 
l = (LoadCtxt *)malloc(sizeof(LoadCtxt)); 
- l->next = This->loading; 
+ //????? Cause memory area to be deallocated multiple times. needed?: l->next = This->loading; 
+ l->next = 0; 
This->loading = l; 
l->level = level; 
l->data = 0; 
@@ -495,20 +481,24 @@ 
 
if (This == 0) return NPERR_INVALID_INSTANCE_ERROR; 
 
- if (This->fh == 0) { 
- return NPERR_INVALID_INSTANCE_ERROR; 
- } 
- 
+ //if (This->fh == 0) { 
+ // return NPERR_INVALID_INSTANCE_ERROR; 
+ //} 
+ if ((NPP)This->loading == (NPP)instance ) return NPERR_NO_ERROR; // Nothing to deallocate 
for(l = This->loading; l; l = l->next) { 
if (l->url && strstr(stream->url, l->url)) { 
- free(l->data); 
+ // Troubles here! Sometimes seems to be already freed (firefox). 
+ // Someone knows what's happening here? 
+ //free(l->data); // Leak! 
l->data = 0; 
- free(l->url); 
+ //free(l->url); // Leak! 
l->url = 0; 
break; 
} 
} 
 
+ // Forbidden: cannot use any X11 commands since context may be invalid 
+#if 0 
if (!This->gInitDone && This->dpy) { 
FlashGraphicInitX11(This); 
XtAddEventHandler(This->widget, FLASH_XEVENT_MASK, 
@@ -517,6 +507,7 @@ 
 
flashWakeUp((XtPointer)This, 0); 
} 
+#endif 
 
return NPERR_NO_ERROR; 
}

---

### Post by blinksilver on 2005-03-23
and i got it to work 4.12, but i got it work, still crashes firefox on some pages, but getting there, still not that much better then swf-player, because they only recently started dev on the original free code, with i think is the base for both

---

### Post by wmcbrine on 2005-03-23
[QUOTE=blinksilver]the one the repo does that, but i think if you comple from source yourself you should be gold[/QUOTE]
As I said, no:
[quote=wmcbrine]It crashes my Firefox ... This is with either the deb **or compiling the latest source.**[/quote]
Of course, that was before I saw the patch you just posted (which I haven't tried). Where does that originate?

---

### Post by blinksilver on 2005-03-23
it is in the forum for gpl flash, and yes it does work, i patched 4.12, no luck with 4.13 and it works

---

### Post by blinksilver on 2005-03-23
it is in the forum for gpl flash, and yes it does work, i patched 4.12, no luck with 4.13 and it works

---

### Post by killerfish on 2005-03-24
Can you provide instructions on how to apply patch and compile so Flash works?  I'll give them a try tonight/tomorrow and then perhaps we can wiki'fy it...

---

### Post by Alfonso VI on 2005-03-24
[QUOTE=killerfish]Can you provide instructions on how to apply patch and compile so Flash works?  I'll give them a try tonight/tomorrow and then perhaps we can wiki'fy it...[/QUOTE]
 I'd like some instructions made plain for semi-literates like myself...

Also I've just noted that this is a patch for v0.4.12 NOT v0.4.13 (going by the post dates)

---

### Post by zarathustra on 2005-04-03
Sorry if I'm being a bit slow but to clarify: there is a 64bit version of Sun's Java but not a 64bit Firefox plugin?

---

### Post by joshuapurcell on 2005-04-16
That is correct, at least from what Sun has released. There is no official 64-bit Java plug-in, but Blackdown Java supposedly has a working 64-bit plugin you can use.

EDIT: It does work, just installed it last night.

---

