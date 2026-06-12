---
title: "Problems Building Xnee v3.03"
date: 2009-05-20
forum: x86 64-bit Users
---

### Post by monikersupreme on 2009-05-20
I am attempting to build the latest release of xnee (v3.03) on an AMD64 X2 4600+ processor running Ubuntu v8.10.

I was previously able to successfully install xnee v3.02 by executing the following commands as per the installation instructions & readme's:

[I]./configure --enable-gnome-applet --prefix=/usr
make
sudo make install[/I]

... and I was also able to uninstall v3.02 using:

*sudo make uninstall*

I uninstalled v3.02 in order to update to v3.03 however when I attempt to install this latest version using the same sequence of commands (as I used for the previous version) I get the following configuration:
 
[I]Configuration of Xnee finished
 ==============================
    PACKAGE              xnee
    VERSION              3.03
 
   Xnee Developer flags
   -------------------------------------
    VERBOSE_FLAG         -DUSE_VERBOSE
    GCOV_FLAG           
    GPROF_FLAG          
    BUF_VERBOSE_FLAG     -DNO_BUF_VERBOSE
    PEDANTIC_FLAGS      
    LIBDL               
    LIBSEMA              -lpthread
    X11_LIBS             -lX11 -lXtst
    PANEL_SERVER_DIR     ${exec_prefix}/lib/bonobo/servers
    PANEL_APPLET_DIR     ${exec_prefix}/lib/gnome-panel
    PIXMAP_DIR           pixmap
    CONVERT             
 

   Building the following components
   -------------------------------------
   
        cli
        gnee
        pnee
   Excluding the following components
   -------------------------------------
   
        doc (docs are already included in dist file)

   Static or dynamic linking for programs (true)
   -------------------------------------
        static
 
   Settings ok?[/I]


...and when I attempt a "make" I run into compilation problems.
[I]
make  all-recursive
make[1]: Entering directory `/home/monikersupreme/Desktop/INBOX/xnee-3.03'
Making all in libxnee
make[2]: Entering directory `/home/monikersupreme/Desktop/INBOX/xnee-3.03/libxnee'
Making all in src
make[3]: Entering directory `/home/monikersupreme/Desktop/INBOX/xnee-3.03/libxnee/src'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..    -I../include   -g -DUSE_VERBOSE   -DNO_BUF_VERBOSE  -DHAVE_XOSD  -g -O2 -MT feedback.lo -MD -MP -MF .deps/feedback.Tpo -c -o feedback.lo feedback.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../include -g -DUSE_VERBOSE -DNO_BUF_VERBOSE -DHAVE_XOSD -g -O2 -MT feedback.lo -MD -MP -MF .deps/feedback.Tpo -c feedback.c  -fPIC -DPIC -o .libs/feedback.o
feedback.c: In function ‘feedback’:
feedback.c:273: error: invalid initializer
make[3]: *** [feedback.lo] Error 1
make[3]: Leaving directory `/home/monikersupreme/Desktop/INBOX/xnee-3.03/libxnee/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/monikersupreme/Desktop/INBOX/xnee-3.03/libxnee'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/monikersupreme/Desktop/INBOX/xnee-3.03'
make: *** [all] Error 2[/I]

...and thus cannot successfully execute a "sudo make install".

(BTW ignore the hardware specs on my signature... this question if for my workstation which is running the hardware stated above)

Any help would be much appreciated...

---

### Post by monikersupreme on 2009-05-26
Got a response from the developers... thought I'd post it here since there haven't been any response from the community regarding this question to date:

[I]hi

Change the line libxnee/src/feedback.c line 273 to:


  va_list ap;


It's done (now) in CVS. A nightly dist (with some other fixes) will be available in a couple of hours here:

  [http://itupw056.itu.chalmers.se/xnee/nightly-dists/](http://itupw056.itu.chalmers.se/xnee/nightly-dists/)


/h[/I]

Still have yet to try this out myself but hopefully it will prove useful.

---

