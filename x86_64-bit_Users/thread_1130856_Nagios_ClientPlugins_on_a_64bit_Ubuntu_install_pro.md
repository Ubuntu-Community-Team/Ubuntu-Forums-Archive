---
title: "Nagios Client/Plugins on a 64bit Ubuntu install problem"
date: 2009-04-20
forum: x86 64-bit Users
---

### Post by rigged 00 on 2009-04-20
Hi

I am a bit stuck with getting a nagios client (64 bit Ubuntu) to be monitored by my nagios host. I am trying to install the client/plugins on a 64 bit Ubuntu 606 machine but it keeps giving a error. I am following the steps as stated in [http://www.thegeekstuff.com/2008/06/how-to-monitor-remote-linux-host-using-nagios-30/](http://www.thegeekstuff.com/2008/06/how-to-monitor-remote-linux-host-using-nagios-30/)

When I do #./configure  in the Plugins download directory it completes with no error, but when I do  #make it gives the below error:
____________________
make[2]: Entering directory `/root/nagios/nagios-plugins-1.4.11/plugins'
/bin/sh ../libtool --tag=CC --mode=link gcc  -g -O2  -ldl -L. -o check_apt  check_apt.o utils.o ../lib/libnagiosplug.a ../gl/libgnu.a runcmd.o
gcc -g -O2 -o check_apt check_apt.o utils.o runcmd.o  -ldl -L/root/nagios/nagios-plugins-1.4.11/plugins ../lib/libnagiosplug.a ../gl/libgnu.a
/usr/bin/ld: i386 architecture of input file `utils.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `runcmd.o' is incompatible with i386:x86-64 output
collect2: ld returned 1 exit status
make[2]: *** [check_apt] Error 1
make[2]: Leaving directory `/root/nagios/nagios-plugins-1.4.11/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/nagios/nagios-plugins-1.4.11'
make: *** [all] Error 2
___________________

I have tried a few articles to get 32bit compiled on 64bit, but I keep getting the same results. Any one have a suggestion on how to get it working or where will I be able to a 64bit version of the nagios plugins?

---

### Post by rigged 00 on 2009-04-21
My problem was solved by a user on Expert-Exchange.com below is his recomendation that solved my problem.
[http://www.experts-exchange.com/Networking/Network_Management/Network_Analysis/Q_24336887.html](http://www.experts-exchange.com/Networking/Network_Management/Network_Analysis/Q_24336887.html)

Information below taken from [here]("http://www.linux-noob.com/forums/index.php?showtopic=3420&view=findpost&p=12136"):

"Adding -m32 to your CFLAGS and/or LDFLAGS should force building 32-bit applications. This assumes your setup is prepared for 32-bit applications already of course.

$ export CFLAGS='-m32'
$ export LDFLAGS='-m32'
$ ./configure ... etc .. etc .."

---

