---
title: "how do u patch wine"
date: 2007-11-21
forum: Wine
---

### Post by finito on 2007-11-21
I have the following Website [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+COD4")
and it asks you to get the patch when I click that i get the followin:

```
diff -Naur wine.old/dlls/wined3d/directx.c wine/dlls/wined3d/directx.c
--- wine.old/dlls/wined3d/directx.c	2007-06-27 16:12:55.000000000 +0200
+++ wine/dlls/wined3d/directx.c	2007-07-03 23:33:08.000000000 +0200
@@ -674,7 +674,7 @@
         }
         if (gl_info->supported[ARB_MULTITEXTURE]) {
             glGetIntegerv(GL_MAX_TEXTURE_UNITS_ARB, &gl_max);
-            gl_info->max_textures = min(MAX_TEXTURES, gl_max);
+            gl_info->max_textures = 8;
             TRACE_(d3d_caps)("Max textures: %d\n", gl_info->max_textures);
 
             if (gl_info->supported[NV_REGISTER_COMBINERS]) {
@@ -1872,7 +1872,11 @@
                                       WINED3DPMISCCAPS_CLIPTLVERTS           |
                                       WINED3DPMISCCAPS_CLIPPLANESCALEDPOINTS |
                                       WINED3DPMISCCAPS_MASKZ                 |
-                                      WINED3DPMISCCAPS_BLENDOP;
+				      WINED3DPMISCCAPS_TSSARGTEMP            |
+				      WINED3DPMISCCAPS_FOGANDSPECULARALPHA   |
+				      WINED3DPMISCCAPS_SEPARATEALPHABLEND    |
+				      WINED3DPMISCCAPS_BLENDOP		 |
+				      WINED3DPMISCCAPS_FOGVERTEXCLAMPED;
                                     /* TODO:
                                         WINED3DPMISCCAPS_NULLREFERENCE
                                         WINED3DPMISCCAPS_INDEPENDENTWRITEMASKS
@@ -2185,7 +2189,7 @@
     *pCaps->MaxVertexBlendMatrixIndex   = 0;
 
     *pCaps->MaxAnisotropy   = GL_LIMITS(anisotropy);
-    *pCaps->MaxPointSize    = GL_LIMITS(pointsize);
+    *pCaps->MaxPointSize    = 64.0f;
 
 
     *pCaps->VertexProcessingCaps = WINED3DVTXPCAPS_DIRECTIONALLIGHTS |
@@ -2247,7 +2251,10 @@
        ------------------------------------------------ */
     if (This->dxVersion > 8) {
         /* d3d9.dll sets D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES here because StretchRects is implemented in d3d9 */
-        *pCaps->DevCaps2                          = WINED3DDEVCAPS2_STREAMOFFSET;
+        *pCaps->DevCaps2                          = WINED3DDEVCAPS2_STREAMOFFSET	|
+						    WINED3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES |
+						    WINED3DDEVCAPS2_PRESAMPLEDDMAPNPATCH |
+						    WINED3DDEVCAPS2_VERTEXELEMENTSCANSHARESTREAMOFFSET;
         /* TODO: VS3.0 needs at least D3DDEVCAPS2_VERTEXELEMENTSCANSHARESTREAMOFFSET */
         *pCaps->MaxNpatchTessellationLevel        = 0;
         *pCaps->MasterAdapterOrdinal              = 0;

```

How do I use that.
Should I copy and paste that somewhere.

Then it says do the following:
```
# cd
# patch -p1 < diff-file
# ./configure
# make depend && make
# su -c "make install"
```

if I do "patch -p1 < diff-file" I get "diff-file doesn't exist"
then "./configure" same thing



Please help

---

### Post by jacksaff on 2007-11-22
You need to be compiling wine yourself to be using that patch.
Get the latest wine source code from cvs or git, and open a terminal in the directory to which you downloaded it. 
Then the patch... ./configure make and so on should work.
Or maybe not.

---

### Post by sirdilznik on 2007-11-22
As jacksaff wrote, you would need to compile the program yourself in order to use the patch (versus installing finished binary like you generally do through Synaptic or apt-get).  If you were to compile it yourself you would need to download the source package, extract it somewhere, then create a blank file inside the directory you extracted.  Call it whatever you want (I'll call it "foo" for the sake of example).  Then copy and paste the contents of the file you displayed into it and save.  (Alternatively you could use wget to download the file to the directory).  From the source code directoy apply the patch with ```
patch -p1 < foo
```
Then compile as usual (probably ./configure;make;make install).

---

### Post by finito on 2007-11-24
I get the following error when I do ./configure

```
finito@finito-desktop:~/Desktop/wine-0.9.49$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
finito@finito-desktop:~/Desktop/wine-0.9.49$ make depend && make
make: *** No rule to make target `depend'.  Stop.
finito@finito-desktop:~/Desktop/wine-0.9.49$ make e
make: *** No rule to make target `e'.  Stop.
finito@finito-desktop:~/Desktop/wine-0.9.49$ make 
make: *** No targets specified and no makefile found.  Stop.
finito@finito-desktop:~/Desktop/wine-0.9.49$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

Let me understand I only need ti do one of these or all

# ./configure
# make depend && make
# su -c "make install"

---

### Post by sirdilznik on 2007-11-24
> **finito said:**
> 

Let me understand I only need ti do one of these or all

# ./configure
# make depend && make
# su -c "make install"
All of those, in that order.

---

### Post by finito on 2007-11-24
yes but how do i solve the error

---

### Post by finito on 2007-11-25
Ok I figuered it out it has somthing to do with my machine being 64-bit, any way this helped..
[http://wiki.winehq.org/WineOn64bit#head-c47d9e53f952c5b6260467e0dc158321229216de]("http://wiki.winehq.org/WineOn64bit#head-c47d9e53f952c5b6260467e0dc158321229216de")

---

### Post by finito on 2007-11-25
OK, I finally got it done.

I got to this part

# su -c "make install"
and it asked for a password and wouldn;t accept the usuall password so I did # sudo make install

It seems to have completed without errors, but I still get the same error.

Do I have to do something to use the new wine or I overwrote the old wine?

Please Advise

---

### Post by sirdilznik on 2007-11-26
> **finito said:**
> OK, I finally got it done.

I got to this part

# su -c "make install"
and it asked for a password and wouldn;t accept the usuall password so I did # sudo make install

It seems to have completed without errors, but I still get the same error.

Do I have to do something to use the new wine or I overwrote the old wine?

Please Advise
Have you copied over the .dll files from a Windowes install (or the net if you can find them) and done the other parts of the instructions as well?

---

### Post by finito on 2007-11-26
I am sorry I wasn't Clear,
The problem is that I get the same error from COD4, not wine,

R6002
 -Floating point not supported...

---

