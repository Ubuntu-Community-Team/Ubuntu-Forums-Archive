---
title: "Epson R265 Driver problems"
date: 2007-08-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by xidahs on 2007-08-11
Hi guys this is my first post so here goes. I bought an epson r265 yesterday with the understanding that there was a driver available at [http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html) I proceeded to do the usual alien filename.rpm which failed as I'm using 64 bit ubuntu and the rpm is i386 I then proceeded to try build the driver using the tar.gz file using ./configure make make install
however the configure seems to work fine but make runs into problems and fails if anyone had any ideas or a .ppd file for this printer under this architecture that would be superb. If not looks like buying the turboprint driver which I am reluctant to do but at this point seems like the only option
Sorry for the long post but I really am at my wits end
P.S the terminal output is as follows
glenn1@desktop:~/Desktop/pipslite-1.0.0$ make
make  all-recursive
make[1]: Entering directory `/home/glenn1/Desktop/pipslite-1.0.0'
Making all in libltdl
make[2]: Entering directory `/home/glenn1/Desktop/pipslite-1.0.0/libltdl'
/bin/sh ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c ltdl.c
mkdir .libs
gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c  -fPIC -DPIC -o .libs/ltdl.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c -o ltdl.o >/dev/null 2>&1
mv -f .libs/ltdl.lo ltdl.lo
/bin/sh ./libtool --mode=link gcc  -g -O2  -o libltdlc.la   ltdl.lo -ldl 
rm -fr .libs/libltdlc.la .libs/libltdlc.* .libs/libltdlc.*
ar cru .libs/libltdlc.al ltdl.lo
ranlib .libs/libltdlc.al
creating libltdlc.la
(cd .libs && rm -f libltdlc.la && ln -s ../libltdlc.la libltdlc.la)
make[2]: Leaving directory `/home/glenn1/Desktop/pipslite-1.0.0/libltdl'
Making all in src
make[2]: Entering directory `/home/glenn1/Desktop/pipslite-1.0.0/src'
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib   -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL="\"LITE\"" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c str.c
mkdir .libs
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL=\"LITE\" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c str.c  -fPIC -DPIC -o .libs/str.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL=\"LITE\" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c str.c -o str.o >/dev/null 2>&1
mv -f .libs/str.lo str.lo
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib   -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL="\"LITE\"" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c err.c
rm -f .libs/err.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL=\"LITE\" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c err.c  -fPIC -DPIC -o .libs/err.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL=\"LITE\" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c err.c -o err.o >/dev/null 2>&1
mv -f .libs/err.lo err.lo
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib   -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL="\"LITE\"" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c csv.c
rm -f .libs/csv.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL=\"LITE\" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c csv.c  -fPIC -DPIC -o .libs/csv.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL=\"LITE\" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c csv.c -o csv.o >/dev/null 2>&1
mv -f .libs/csv.lo csv.lo
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib   -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL="\"LITE\"" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c mem.c
rm -f .libs/mem.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL=\"LITE\" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c mem.c  -fPIC -DPIC -o .libs/mem.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL=\"LITE\" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c mem.c -o mem.o >/dev/null 2>&1
mv -f .libs/mem.lo mem.lo
/bin/sh ../libtool --mode=link gcc -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL="\"LITE\"" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall  -o libcutils.la   str.lo err.lo csv.lo mem.lo  -lpthread -ldl 
rm -fr .libs/libcutils.la .libs/libcutils.* .libs/libcutils.*
ar cru .libs/libcutils.al str.lo err.lo csv.lo mem.lo
ranlib .libs/libcutils.al
creating libcutils.la
(cd .libs && rm -f libcutils.la && ln -s ../libcutils.la libcutils.la)
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib   -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL="\"LITE\"" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c ekpcom.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib   -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL="\"LITE\"" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c gLoad.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib   -DGS_PATH=\"gs\" -DLOCALEDIR=\"/usr/share/locale\" -DPRINTER_MODEL="\"LITE\"" -DLITE -DLIBPATH=\"/usr/lib/liblite.so\" -DRSC_PATH=\"/etc/pipsrc\" -DSPOOL_NAME=\"lite\" -DLOCALE_PATH=\"/usr/share/locale\" -DDATA_PATH=\"/usr/local/EPAva/LITE\" -DPRTOPT_PATH=\"/usr/local/EPAva/printer/prtOpt.csv\" -DPAPER_PATH=\"/usr/local/EPAva/printer/paper_list.csv\" -D_LPR_DIRECT -fsigned-char -DCUPS_FILTER_PATH=\"/usr/lib/cups/filter\" -g -O2 -Wall -c getstat.c
getstat.c:34:18: error: ltdl.h: No such file or directory
getstat.c: In function &#8216;str_extract&#8217;:
getstat.c:88: warning: cast from pointer to integer of different size
getstat.c:88: warning: cast from pointer to integer of different size
getstat.c: In function &#8216;get_printer_peculiar&#8217;:
getstat.c:141: error: &#8216;lt_dlhandle&#8217; undeclared (first use in this function)
getstat.c:141: error: (Each undeclared identifier is reported only once
getstat.c:141: error: for each function it appears in.)
getstat.c:141: error: expected &#8216;;&#8217; before &#8216;lib_h&#8217;
getstat.c:147: warning: implicit declaration of function &#8216;lt_dlinit&#8217;
getstat.c:150: warning: implicit declaration of function &#8216;lt_dlerror&#8217;
getstat.c:150: warning: passing argument 2 of &#8216;fprintf&#8217; makes pointer from integer without a cast
getstat.c:153: error: &#8216;lib_h&#8217; undeclared (first use in this function)
getstat.c:153: warning: implicit declaration of function &#8216;lt_dlopenext&#8217;
getstat.c:155: warning: passing argument 2 of &#8216;fprintf&#8217; makes pointer from integer without a cast
getstat.c:159: warning: implicit declaration of function &#8216;lt_dlsym&#8217;
getstat.c:159: warning: cast to pointer from integer of different size
make[2]: *** [getstat.o] Error 1
make[2]: Leaving directory `/home/glenn1/Desktop/pipslite-1.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/glenn1/Desktop/pipslite-1.0.0'
make: *** [all-recursive-am] Error 2
glenn1@desktop:~/Desktop/pipslite-1.0.0$

---

### Post by nowhere.elysium on 2007-08-11
[http://ubuntuforums.org/showthread.php?t=410142](http://ubuntuforums.org/showthread.php?t=410142)
[http://ubuntuforums.org/showthread.php?t=332891](http://ubuntuforums.org/showthread.php?t=332891)
These may be of some use. Have you got the ia32libs installed? That'll allow you to emulate i386 architecture wel enough to get away wit the drivers provided.

---

