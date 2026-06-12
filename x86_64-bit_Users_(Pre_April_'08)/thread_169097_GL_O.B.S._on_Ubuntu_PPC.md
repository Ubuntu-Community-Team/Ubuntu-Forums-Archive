---
title: "GL O.B.S. on Ubuntu PPC?"
date: 2006-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by davygravy on 2006-05-01
Anyone able to get [GL O.B.S.]("http://globs.sourceforge.net/") to build on Ubuntu Dapper PPC?

I tried the directions at this [Ubuntu HowTo]("http://www.ubuntuforums.org/archive/index.php/t-157429.html") but no go...

anybody...?

---

### Post by ssam on 2006-05-02
what error message are you getting

---

### Post by davygravy on 2006-05-02
I was careful to satisfy all **listed **dependencies... seems unlikely that there could be unlisted ones, but...

I followed directions at the HowTo page... and get this...

```

davidpurdy@ubuntublue:~/Desktop/globs-0.1$ scons
scons: Reading SConscript files ...
:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library libSDL... yes
Checking for IMG_GetError() in C library libSDL_image... yes
:: Compiling benchmarks for posix
:: Building binary message catalogs
scons: done reading SConscript files.
scons: Building targets ...
gcc -D_REENTRANT -I/usr/include/SDL -c -o src/benchmarks/GL_blit/gl_blit.o src/benchmarks/GL_blit/gl_blit.c
src/benchmarks/GL_blit/gl_blit.c:31:19: error: GL/gl.h: No such file or directory
In file included from src/benchmarks/GL_blit/gl_blit.c:32:
src/benchmarks/GL_blit/gl_blit.h:6: error: syntax error before 'GLuint'
src/benchmarks/GL_blit/gl_blit.h:6: warning: no semicolon at end of struct or union
src/benchmarks/GL_blit/gl_blit.h:7: warning: data definition has no type or storage class
src/benchmarks/GL_blit/gl_blit.h:8: error: syntax error before 'x'
src/benchmarks/GL_blit/gl_blit.h:8: warning: data definition has no type or storage class
src/benchmarks/GL_blit/gl_blit.h:9: error: syntax error before 'angle'
src/benchmarks/GL_blit/gl_blit.h:9: warning: data definition has no type or storage class
src/benchmarks/GL_blit/gl_blit.h:10: error: syntax error before 'xsize'
src/benchmarks/GL_blit/gl_blit.h:10: warning: data definition has no type or storage class
src/benchmarks/GL_blit/gl_blit.h:11: error: syntax error before '}' token
src/benchmarks/GL_blit/gl_blit.c: In function 'main':
src/benchmarks/GL_blit/gl_blit.c:55: error: 'GLfloat' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:55: error: (Each undeclared identifier is reported only once
src/benchmarks/GL_blit/gl_blit.c:55: error: for each function it appears in.)
src/benchmarks/GL_blit/gl_blit.c:55: error: syntax error before 'angle'
src/benchmarks/GL_blit/gl_blit.c:100: error: 'GL_PROJECTION' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:103: error: 'GL_MODELVIEW' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:106: error: 'GL_DEPTH' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:115: error: 'GL_TEXTURE_2D' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:116: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:148: error: 'GL_COLOR_BUFFER_BIT' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:162: error: 'GL_TRIANGLES' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:179: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:179: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:180: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:184: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:185: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:191: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:192: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:193: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:198: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:199: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:200: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:206: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:206: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:207: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c: In function 'AllocSprite':
src/benchmarks/GL_blit/gl_blit.c:228: error: 'GLuint' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:228: error: syntax error before 'texnum'
src/benchmarks/GL_blit/gl_blit.c:239: error: invalid application of 'sizeof' to incomplete type 'struct Sprite'
src/benchmarks/GL_blit/gl_blit.c:241: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:241: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:242: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:243: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:243: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:251: error: 'GL_MAX_TEXTURE_SIZE' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:258: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:259: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:265: error: 'GLint' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:265: error: syntax error before 'wreal'
src/benchmarks/GL_blit/gl_blit.c:268: error: 'wreal' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:269: error: 'hreal' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:270: error: 'xpad' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:271: error: 'ypad' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:305: error: 'texnum' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:306: error: 'GL_TEXTURE_2D' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:307: error: 'GL_TEXTURE_MAG_FILTER' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:307: error: 'GL_LINEAR' undeclared (first use in this function)src/benchmarks/GL_blit/gl_blit.c:308: error: 'GL_TEXTURE_MIN_FILTER' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:310: error: 'GL_RGBA' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:310: error: 'GL_UNSIGNED_BYTE' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:312: error: 'GL_RGB' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:314: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c: In function 'FreeSprite':
src/benchmarks/GL_blit/gl_blit.c:327: error: 'GLuint' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:327: error: syntax error before 'texnum'
src/benchmarks/GL_blit/gl_blit.c:330: error: 'texnum' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:330: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c: In function 'BlitSprite':
src/benchmarks/GL_blit/gl_blit.c:345: error: 'GLint' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:345: error: syntax error before 'wreal'
src/benchmarks/GL_blit/gl_blit.c:348: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:348: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:349: error: 'wreal' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:349: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:350: error: 'hreal' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:350: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:351: error: 'xpad' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:351: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:352: error: 'ypad' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:352: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:354: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:355: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:358: error: 'GL_SRC_ALPHA' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:358: error: 'GL_ONE_MINUS_SRC_ALPHA' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:359: error: 'GL_BLEND' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:361: error: 'GL_TEXTURE' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:366: error: 'GL_MODELVIEW' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:370: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:370: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:370: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:370: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:371: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:372: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:372: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:374: error: 'GL_TEXTURE_2D' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:374: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:375: error: 'GL_QUADS' undeclared (first use in this function)
src/benchmarks/GL_blit/gl_blit.c:378: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:378: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:379: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:380: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:380: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:381: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:381: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:382: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:382: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:383: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:384: error: dereferencing pointer to incomplete type
src/benchmarks/GL_blit/gl_blit.c:384: error: dereferencing pointer to incomplete type
scons: *** [src/benchmarks/GL_blit/gl_blit.o] Error 1
scons: building terminated because of errors.
davidpurdy@ubuntublue:~/Desktop/globs-0.1$


```

ideas, anyone?

Is this a GL-ATI no-worko-wello-on-PPCo problemo?

davygravy

---

### Post by davygravy on 2006-05-05
bump...anyone...?

---

### Post by davygravy on 2006-05-06
OK, w/ the last latest update (incremental) using the Update Manager, I see that some of xorg  was updated.  Running  the instructions listed at the HOWTO site does now work - GL O.B.S. is now installed and runs.



This was on Dapper Flight 6, PPC.

---

### Post by aimislame15 on 2006-05-06
What exactly does GLOBS do?

---

### Post by davygravy on 2006-05-06
[QUOTE=aimislame15]What exactly does GLOBS do?[/QUOTE]

[GL O.B.S.]("http://globs.sourceforge.net/") is a sort of benchmarking utility.  I wanted to have it installed so I could figure out whether or not my Blue&White w/ Radeon 7000 was set up correctly- video&graphics-wise.  I also installed driconf so I could tweak the settings.

My overall impression of Ubuntu PPC has been very positive, but the graphics performance seems to be the weak point, IMHO.  My hope is to find a way to tweak my settings so that things are more acceptable.

---

