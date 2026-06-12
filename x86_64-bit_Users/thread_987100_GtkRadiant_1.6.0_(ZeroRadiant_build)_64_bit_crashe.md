---
title: "GtkRadiant 1.6.0 (ZeroRadiant build) 64 bit crashes"
date: 2008-11-19
forum: x86 64-bit Users
---

### Post by Allochtoon on 2008-11-19
I used these instructions, 

[https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/trunk/COMPILING](https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/trunk/COMPILING)

From the instructions "run 'python ./GtkRadiant/install.py'" didn't work - but what I did was run radiant.bin directly from the ./install dir.

It will then run quite normally however:

Every option in the edit > preferences menu i click leads to a crash:

```

marco@lenovo:~/GtkRadiant/GtkRadiant/install$ ./radiant.bin
I/O warning : failed to load external entity "/home/marco/GtkRadiant/GtkRadiant/install/global.xlink"
I/O warning : failed to load external entity "/home/marco/GtkRadiant/GtkRadiant/install/installs/UrTPack/game/game.xlink"
Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

Segmentation fault
marco@lenovo:~/GtkRadiant/GtkRadiant/install$

```

Also, running q3map2 results in a crash:
```
marco@lenovo:~/GtkRadiant/GtkRadiant/install$ ./q3map2 
2.5.17                                                 
threads: 4                                             
Q3Map         - v1.0r (c) 1999 Id Software Inc.        
Q3Map (ydnar) - v2.5.17                                
GtkRadiant    - v1.6.0 Nov 18 2008 21:46:27            
Last one turns the lights off                          
*** buffer overflow detected ***: ./q3map2 terminated  
======= Backtrace: =========                           
/lib/libc.so.6(__fortify_fail+0x37)[0x7ffce2a4c887]    
/lib/libc.so.6[0x7ffce2a4a750]                         
/lib/libc.so.6[0x7ffce2a4ae0b]                         
./q3map2[0x4305d4]                                     
./q3map2[0x4307f0]                                     
./q3map2[0x426b5f]                                     
/lib/libc.so.6(__libc_start_main+0xe6)[0x7ffce296b466] 
./q3map2[0x403c39]                                     
======= Memory map: ========                           
00400000-004a5000 r-xp 00000000 08:05 320180                             /home/marco/GtkRadiant/GtkRadiant/install/q3map2
006a4000-006a5000 r--p 000a4000 08:05 320180                             /home/marco/GtkRadiant/GtkRadiant/install/q3map2
006a5000-006b8000 rw-p 000a5000 08:05 320180                             /home/marco/GtkRadiant/GtkRadiant/install/q3map2
006b8000-06104000 rw-p 006b8000 00:00 0                                                                                  
06418000-06439000 rw-p 06418000 00:00 0                                  [heap]                                          
7ffce2308000-7ffce2330000 r-xp 00000000 08:05 114799                     /lib/libpcre.so.3.12.1                          
7ffce2330000-7ffce252f000 ---p 00028000 08:05 114799                     /lib/libpcre.so.3.12.1                          
7ffce252f000-7ffce2530000 r--p 00027000 08:05 114799                     /lib/libpcre.so.3.12.1                          
7ffce2530000-7ffce2531000 rw-p 00028000 08:05 114799                     /lib/libpcre.so.3.12.1                          
7ffce2531000-7ffce2548000 r-xp 00000000 08:05 1436274                    /usr/lib/libz.so.1.2.3.3                        
7ffce2548000-7ffce2747000 ---p 00017000 08:05 1436274                    /usr/lib/libz.so.1.2.3.3                        
7ffce2747000-7ffce2749000 rw-p 00016000 08:05 1436274                    /usr/lib/libz.so.1.2.3.3                        
7ffce2749000-7ffce274b000 r-xp 00000000 08:05 114741                     /lib/libdl-2.8.90.so                            
7ffce274b000-7ffce294b000 ---p 00002000 08:05 114741                     /lib/libdl-2.8.90.so                            
7ffce294b000-7ffce294c000 r--p 00002000 08:05 114741                     /lib/libdl-2.8.90.so                            
7ffce294c000-7ffce294d000 rw-p 00003000 08:05 114741                     /lib/libdl-2.8.90.so                            
7ffce294d000-7ffce2ab6000 r-xp 00000000 08:05 114726                     /lib/libc-2.8.90.so                             
7ffce2ab6000-7ffce2cb5000 ---p 00169000 08:05 114726                     /lib/libc-2.8.90.so                             
7ffce2cb5000-7ffce2cb9000 r--p 00168000 08:05 114726                     /lib/libc-2.8.90.so                             
7ffce2cb9000-7ffce2cba000 rw-p 0016c000 08:05 114726                     /lib/libc-2.8.90.so                             
7ffce2cba000-7ffce2cbf000 rw-p 7ffce2cba000 00:00 0                                                                      
7ffce2cbf000-7ffce2cd5000 r-xp 00000000 08:05 114749                     /lib/libgcc_s.so.1                              
7ffce2cd5000-7ffce2ed5000 ---p 00016000 08:05 114749                     /lib/libgcc_s.so.1                              
7ffce2ed5000-7ffce2ed6000 r--p 00016000 08:05 114749                     /lib/libgcc_s.so.1                              
7ffce2ed6000-7ffce2ed7000 rw-p 00017000 08:05 114749                     /lib/libgcc_s.so.1                              
7ffce2ed7000-7ffce2f5b000 r-xp 00000000 08:05 114760                     /lib/libm-2.8.90.so                             
7ffce2f5b000-7ffce315a000 ---p 00084000 08:05 114760                     /lib/libm-2.8.90.so                             
7ffce315a000-7ffce315b000 r--p 00083000 08:05 114760                     /lib/libm-2.8.90.so                             
7ffce315b000-7ffce315c000 rw-p 00084000 08:05 114760                     /lib/libm-2.8.90.so                             
7ffce315c000-7ffce324d000 r-xp 00000000 08:05 1436162                    /usr/lib/libstdc++.so.6.0.10                    
7ffce324d000-7ffce344d000 ---p 000f1000 08:05 1436162                    /usr/lib/libstdc++.so.6.0.10                    
7ffce344d000-7ffce3454000 r--p 000f1000 08:05 1436162                    /usr/lib/libstdc++.so.6.0.10                    
7ffce3454000-7ffce3456000 rw-p 000f8000 08:05 1436162                    /usr/lib/libstdc++.so.6.0.10                    
7ffce3456000-7ffce3469000 rw-p 7ffce3456000 00:00 0
7ffce3469000-7ffce3495000 r-xp 00000000 08:05 1089880                    /usr/lib/libmhash.so.2.0.1
7ffce3495000-7ffce3695000 ---p 0002c000 08:05 1089880                    /usr/lib/libmhash.so.2.0.1
7ffce3695000-7ffce3696000 rw-p 0002c000 08:05 1089880                    /usr/lib/libmhash.so.2.0.1
7ffce3696000-7ffce36b8000 r-xp 00000000 08:05 1435541                    /usr/lib/libjpeg.so.62.0.0
7ffce36b8000-7ffce38b8000 ---p 00022000 08:05 1435541                    /usr/lib/libjpeg.so.62.0.0
7ffce38b8000-7ffce38b9000 rw-p 00022000 08:05 1435541                    /usr/lib/libjpeg.so.62.0.0
7ffce38b9000-7ffce38de000 r-xp 00000000 08:05 1436047                    /usr/lib/libpng12.so.0.27.0
7ffce38de000-7ffce3ade000 ---p 00025000 08:05 1436047                    /usr/lib/libpng12.so.0.27.0
7ffce3ade000-7ffce3ae0000 rw-p 00025000 08:05 1436047                    /usr/lib/libpng12.so.0.27.0
7ffce3ae0000-7ffce3af7000 r-xp 00000000 08:05 114803                     /lib/libpthread-2.8.90.so
7ffce3af7000-7ffce3cf6000 ---p 00017000 08:05 114803                     /lib/libpthread-2.8.90.so
7ffce3cf6000-7ffce3cf7000 r--p 00016000 08:05 114803                     /lib/libpthread-2.8.90.so
7ffce3cf7000-7ffce3cf8000 rw-p 00017000 08:05 114803                     /lib/libpthread-2.8.90.so
7ffce3cf8000-7ffce3cfc000 rw-p 7ffce3cf8000 00:00 0
7ffce3cfc000-7ffce3dbf000 r-xp 00000000 08:05 1434723                    /usr/lib/libglib-2.0.so.0.1800.2
7ffce3dbf000-7ffce3fbe000 ---p 000c3000 08:05 1434723                    /usr/lib/libglib-2.0.so.0.1800.2
7ffce3fbe000-7ffce3fbf000 r--p 000c2000 08:05 1434723                    /usr/lib/libglib-2.0.so.0.1800.2
7ffce3fbf000-7ffce3fc0000 rw-p 000c3000 08:05 1434723                    /usr/lib/libglib-2.0.so.0.1800.2
7ffce3fc0000-7ffce3fc1000 rw-p 7ffce3fc0000 00:00 0
7ffce3fc1000-7ffce4114000 r-xp 00000000 08:05 1436268                    /usr/liAborted
marco@lenovo:~/GtkRadiant/GtkRadiant/install$

```

I would like to know how i set up the q3map2 from within Radiant :)

Any help much appreciated!

---

### Post by orbitaldecay on 2008-12-03
I too have encountered this problem.  Have you discovered a solution?

---

### Post by Allochtoon on 2008-12-05
problems with linux radiant still persist

[http://forums.urbanterror.net/index.php/topic,9766.0.html](http://forums.urbanterror.net/index.php/topic,9766.0.html)

follow those instructions, get bspc.exe from the win32 radiant, use the q3map2toolz with wine.

in-radiant compiling is deemed unstable.

---

### Post by obsrv on 2008-12-19
WOW you managed to compile it, it fails for me. How did you compile it? what are dependecies? in the last post I was doing as it said (in the last post :D) in that link I mean.

---

### Post by obsrv on 2008-12-19
This is what I get:

```
plugins/image/bmp.cpp:268: warning: 'pixbytes' may be used uninitialized in this function
plugins/image/bmp.cpp: In function 'void LoadBMP(char*, bitmap_t*)':
plugins/image/bmp.cpp:173: warning: 'pixbytes' is used uninitialized in this function
g++ -o build/release/shobjs/plugins/image/image.os -c -pipe -Wall -fmessage-length=0 -fvisibility=hidden -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -pipe -Wall -fmessage-length=0 -fvisibility=hidden -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -fpermissive -fvisibility-inlines-hidden -O3 -Winline -ffast-math -fno-unsafe-math-optimizations -fno-strict-aliasing -fPIC -DQ_NO_STLPORT -Ibuild/release/shobjs/include -Iinclude -Ibuild/release/shobjs/libs -Ilibs plugins/image/image.cpp
g++ -o build/release/shobjs/plugins/image/jpeg.os -c -pipe -Wall -fmessage-length=0 -fvisibility=hidden -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -pipe -Wall -fmessage-length=0 -fvisibility=hidden -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -fpermissive -fvisibility-inlines-hidden -O3 -Winline -ffast-math -fno-unsafe-math-optimizations -fno-strict-aliasing -fPIC -DQ_NO_STLPORT -Ibuild/release/shobjs/include -Iinclude -Ibuild/release/shobjs/libs -Ilibs plugins/image/jpeg.cpp
plugins/image/jpeg.cpp:44:21: error: jpeglib.h: No such file or directory
plugins/image/jpeg.cpp:45:20: error: jerror.h: No such file or directory
plugins/image/jpeg.cpp:53: error: field 'pub' has incomplete type
plugins/image/jpeg.cpp:56: warning: ISO C++ forbids declaration of 'JOCTET' with no type
plugins/image/jpeg.cpp:56: error: expected ';' before '*' token
plugins/image/jpeg.cpp:58: warning: ISO C++ forbids declaration of 'JOCTET' with no type
plugins/image/jpeg.cpp:58: error: expected ';' before '*' token
plugins/image/jpeg.cpp:59: error: 'boolean' does not name a type
plugins/image/jpeg.cpp:72: error: variable or field 'my_init_source' declared void
plugins/image/jpeg.cpp:72: error: 'j_decompress_ptr' was not declared in this scope
plugins/image/jpeg.cpp:117: error: 'boolean' does not name a type
plugins/image/jpeg.cpp:161: error: variable or field 'my_skip_input_data' declared void
plugins/image/jpeg.cpp:161: error: 'j_decompress_ptr' was not declared in this scope
plugins/image/jpeg.cpp:161: error: expected primary-expression before 'long'
scons: *** [build/release/shobjs/plugins/image/jpeg.os] Error 1
scons: building terminated because of errors.
root@pirate:~/GtkRadiant# 
```

---

### Post by orbitaldecay on 2009-01-01
obsrv: I have assembled a GtkRadiant compiling guide for Ubuntu which can be found at [http://forums.urbanterror.net/index.php/topic,13504.msg179189.html#msg179189](http://forums.urbanterror.net/index.php/topic,13504.msg179189.html#msg179189).  Let me know if you need more help.

---

### Post by Allochtoon on 2009-01-31
Latest svn build the preferences menu works. Maybe someone can make a nice script which fetches & configures all the stuff?


**installing radiant & q3map2 ** from:[http://forums.urbanterror.net/index.php/topic,13504.msg179189.html](http://forums.urbanterror.net/index.php/topic,13504.msg179189.html)

```
sudo apt-get install subversion scons g++ libgtkglext1-dev libxml2-dev libmhash-dev libgtk2.0-dev libpng12-dev libjpeg-dev
```
```
cd /home/$user
```
```
svn checkout https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/trunk/ ./GtkRadiant
```
```
cd GtkRadiant/install/installs
```
```
svn checkout https://zerowing.idsoftware.com/svn/radiant.gamepacks/UrTPack/trunk/ ./UrTPack
```
```
cd ../../
```
```
sudo scons BUILD="release"
```

**making symlinks to gtkradiant && q3map2**

```

cd /usr/local/bin && sudo ln -sf /home/$user/GtkRadiant/install/q3map2 ./
cd /usr/local/bin && sudo ln -sf /home/$user/GtkRadiant/install/radiant.bin ./

```

**making gtkradiant believe u compile for quake3**
```

cd /home/$user/.q3a/q3ut4/ && ln -sf /usr/games/urbanterror quake3

```

Then you can use TAB 'bsp' from gtkradiant to compile and test your map.
see [http://en.wikibooks.org/wiki/GtkRadiant](http://en.wikibooks.org/wiki/GtkRadiant) on how to build maps.

---

### Post by weaponx69 on 2009-10-12
Hey,
  Thanks for the tutorial.  All the compiling works but the last line does not work.  It says no such file or directory.  It should work because all I did was copy and paste all you lines into my terminal.  I didn't change any locations.  Also, to install I researched and found out that I should use;

python install [target] [source]

but that doesn't work either.  It says that it can't find;

 '__main__.py' in 'install'

Do you know anything about that?  I want to use this for a class in Level Design to finish my final project for Level design class at DeVry.  Quickness would be appreciated.

---

