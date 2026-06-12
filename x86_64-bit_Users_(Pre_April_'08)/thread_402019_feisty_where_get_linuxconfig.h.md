---
title: "feisty: where get linux/config.h ?"
date: 2007-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by t0mas on 2007-04-05
Hello,
I have to install cisco-vpn on my feisty desktop (because my father need it). When I try to run the installation I get:
```

make -C /lib/modules/2.6.20-13-generic/build SUBDIRS=/root/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-13-generic'
  CC [M]  /root/vpnclient/linuxcniapi.o
**/root/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory**
In file included from /root/vpnclient/Cniapi.h:15,
                 from /root/vpnclient/linuxcniapi.c:27:
/root/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
/root/vpnclient/linuxcniapi.c: In function &#8216;CniInjectReceive&#8217;:
/root/vpnclient/linuxcniapi.c:292: error: &#8216;struct sk_buff&#8217; has no member named &#8216;stamp&#8217;
/root/vpnclient/linuxcniapi.c: In function &#8216;CniInjectSend&#8217;:
/root/vpnclient/linuxcniapi.c:432: error: &#8216;struct sk_buff&#8217; has no member named &#8216;stamp&#8217;
make[2]: *** [/root/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/root/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-13-generic'
make: *** [default] Error 2

```

Can you please tell me, where can get linux/config.h ? I installed linux-sources and also linux-headers.

Thank you :-)

---

### Post by kuja on 2007-04-05
Hmm, good question :s 
In Edgy it was in linux-headers,  but it doesn't seem to be present in feisty's linux-headers-2.6.20-13 package.

---

### Post by t0mas on 2007-04-05
so is it a bug?

---

### Post by jarlethorsen on 2007-04-05
I get a similar error trying to compile nvidia drivers from nvidia.com using this kernel, hopefully somebody will come up with a solution very soon!

---

### Post by t0mas on 2007-04-22
solution: 
[http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/]("http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/")

It is a patch for cisco VPN

---

### Post by gmc on 2007-04-22
Hi Folks,

This isn't really a solution to the problem, but a tip that you'll find very useful. If you install "apt-file" (sudo apt-get install apt-file), you can use apt-file to search the repositories for a package(s) that contains specific files. Thus:

```

gord@darwin:~$ sudo apt-file update ; # **Updates the data files so they can be searched...**
Password:
gord@darwin:~$ apt-file search kernel.h | more ; # **show me every package that has kernel.h in it**
dfsbuild: usr/lib/dfsbuild/dfs.html/dfsboot-kernel.html
dfsbuild: usr/lib/dfsbuild/dfs.html/dfsboot-kernel.html.txt
doc-debian: usr/share/doc/debian/FAQ/ch-kernel.html
doc-debian-es: usr/share/doc/debian/es/FAQ/ch-kernel.html
doc-linux-html: usr/share/doc/FAQ/Linux-FAQ/kernel.html
.
. 
.
xen-headers-2.6.19-4-generic-amd64: usr/src/xen-headers-2.6.19-4-generic-amd64/i
nclude/config/debug/kernel.h
xen-headers-2.6.19-4-generic-amd64: usr/src/xen-headers-2.6.19-4-generic-amd64/i
nclude/config/lock/kernel.h
xen-headers-2.6.19-4-generic-amd64: usr/src/xen-headers-2.6.19-4-generic-amd64/i
nclude/linux/kernel.h

```Hope this helps...

Gord

---

### Post by ariel on 2007-04-22
> **t0mas said:**
> solution: 
[http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/](http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/)

It is a patch for cisco VPN

Awesome! Thanks for posting

---

### Post by dante.regis on 2007-04-25
> **t0mas said:**
> solution: 
[http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/]("http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/")

It is a patch for cisco VPN

worked for me too. aparently, there's a new structure on the linux headers, and that's why cisco vpn client cannot find the config.h file.

---

### Post by frosch6669 on 2007-04-25
try to ln -s autoconf.h config.h
in /usr/src/linux-haeders-xxxxx/include/linux
this helped

---

### Post by exidez on 2007-04-30
i tried the above but i just get more errors

Making module
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/exidez/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/exidez/vpnclient/linuxcniapi.o
  CC [M]  /home/exidez/vpnclient/frag.o
  CC [M]  /home/exidez/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /home/exidez/vpnclient/interceptor.o
/home/exidez/vpnclient/interceptor.c: In function &#8216;handle_vpnup&#8217;:
/home/exidez/vpnclient/interceptor.c:310: warning: assignment from incompatible pointer type
/home/exidez/vpnclient/interceptor.c:334: warning: assignment from incompatible pointer type
/home/exidez/vpnclient/interceptor.c:335: warning: assignment from incompatible pointer type
/home/exidez/vpnclient/interceptor.c: In function &#8216;do_cleanup&#8217;:
/home/exidez/vpnclient/interceptor.c:378: warning: assignment from incompatible pointer type
/home/exidez/vpnclient/interceptor.c: In function &#8216;recv_ip_packet_handler&#8217;:
/home/exidez/vpnclient/interceptor.c:553: error: &#8216;CHECKSUM_HW&#8217; undeclared (first use in this function)
/home/exidez/vpnclient/interceptor.c:553: error: (Each undeclared identifier is reported only once
/home/exidez/vpnclient/interceptor.c:553: error: for each function it appears in.)
/home/exidez/vpnclient/interceptor.c:557: error: too many arguments to function &#8216;skb_checksum_help&#8217;
/home/exidez/vpnclient/interceptor.c: In function &#8216;do_cni_send&#8217;:
/home/exidez/vpnclient/interceptor.c:680: error: &#8216;CHECKSUM_HW&#8217; undeclared (first use in this function)
/home/exidez/vpnclient/interceptor.c:683: error: too many arguments to function &#8216;skb_checksum_help&#8217;
make[2]: *** [/home/exidez/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/exidez/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".




this patch also seems to hang on me and nothing seems to happend!
Whats can i do?????????


edit///////////////


Ok i fixed the problem
it looks like to apply the patch i need to type
patch -i <the file name>

i didint have -i before

it has installed great now

---

### Post by ddrichards on 2007-06-07
I've tried everything on this page and still get this error:

```

make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/dan/cisco/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/dan/cisco/vpnclient/linuxcniapi.o
/home/dan/cisco/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/dan/cisco/vpnclient/linuxcniapi.c:292: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/dan/cisco/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/dan/cisco/vpnclient/linuxcniapi.c:432: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/home/dan/cisco/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/dan/cisco/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```

Any other Ideas?

Thanks!!

---

### Post by sampan74 on 2007-08-15
Im having the exact same problem as you have, ddrichards.... So, is there anyone out there that has gotten around this issue?

---

### Post by sampan74 on 2007-08-15
Ok! Problem solved. Here is what I did... 

Download this version of the vpn client:
[http://www.filewatcher.com/_/?q=vpnclient-linux-4.8.00.0490-k9.tar.gz](http://www.filewatcher.com/_/?q=vpnclient-linux-4.8.00.0490-k9.tar.gz)

Apply the patch and follow the updated instructions there:
[http://tuxx-home.at/archives/2007/05/29/T16_34_26/](http://tuxx-home.at/archives/2007/05/29/T16_34_26/)

---

### Post by demiurgicdaemon on 2007-09-07
Wow! Thank you!  The initial patch mentioned worked great for me.  Also, if you just change the numbers in the url when downloading the patch to use for more recent kernels, it works!  I got mine to work for 2.6.22.

---

### Post by helpdeskdan on 2007-09-10
Another thanks - patch worked for me

---

### Post by Jandark on 2008-04-29
tnx doods my problem solved with ln autoconf.h file

---

