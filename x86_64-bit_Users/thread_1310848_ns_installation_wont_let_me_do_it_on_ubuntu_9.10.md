---
title: "ns installation wont let me do it on ubuntu 9.10"
date: 2009-11-02
forum: x86 64-bit Users
---

### Post by foottuns on 2009-11-02
Helllo there, I don't know if here is the place but I am trying to configure ns on my system, I saw a few tutorials which they were interested and good, but all the time when I try to compile the ns source I get this error and I don't know what should I do to fix it.

Error 

 ```

checking for a BSD-compatible install... /usr/bin/install -c
checking system version (for dynamic loading)... Linux-2.6.31-14-generic
No explicit static compilation flag; setting V_STATIC to ""
checking for dlopen in -ldl... yes
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
rm -f libotcl.so otcl.o so_locations
gcc -c -g -O2 -DNDEBUG -DUSE_SHM -fpic -I. -I/home/bogdan/ns/ns-allinone-2.34/include -I/home/bogdan/ns/ns-allinone-2.34/include -I/home/bogdan/ns/ns-allinone-2.34/include -I/include  otcl.c
ld -shared -o libotcl.so otcl.o
otcl.o: In function `OTclDispatch':
/home/bogdan/ns/ns-allinone-2.34/otcl-1.13/otcl.c:495: undefined reference to `__stack_chk_fail_local'
otcl.o: In function `Otcl_Init':
/home/bogdan/ns/ns-allinone-2.34/otcl-1.13/otcl.c:2284: undefined reference to `__stack_chk_fail_local'
ld: libotcl.so: hidden symbol `__stack_chk_fail_local' isn't defined
ld: final link failed: Nonrepresentable section on output
make: *** [libotcl.so] Error 1
otcl-1.13 make failed! Exiting ...
See http://www.isi.edu/nsnam/ns/ns-problems.html for problems

```

---

### Post by inforfang on 2009-11-02
i have same problem ...

---

### Post by foottuns on 2009-11-02
and did you sort it out in any way? i think is the path for X11, i try to edit the file but no luck...

---

### Post by inforfang on 2009-11-02
i read the [http://www.isi.edu/nsnam/ns/ns-problems.html](http://www.isi.edu/nsnam/ns/ns-problems.html) but no luck to find the problem ...

i think maybe ubuntu 9.10 gcc not compatible with ns version 2.34 ... 
in ns wiki , ns compiled in ubuntu 9.04 dicussed , and i install it in 9.04 but in 9.10 i have problem. 
:(

---

### Post by foottuns on 2009-11-02
ohh bloody hell, i need it so much and i dont want to change my os, there's got to be a way for this.............

---

### Post by foottuns on 2009-11-02
problem sort it out, now is working perfectly , i will soon write a tutorial regarding to this and post it here............

---

### Post by inforfang on 2009-11-03
:) that's great ...
I would like to try your method ...

---

### Post by davide_dvd on 2009-11-04
I've got the same problem, I had ubuntu 8.04 till yesterday and everything worked great, now with 9.10 release i've tried to install NS-2 again but this problem appeared... what can we do??

I've tried with both versions 2.34 and 2.33 (all-in-one) but i have the same problem

---

### Post by Conendrum on 2009-11-05
Hi guys!
I gotta exactly the same pb: i try to install ns2 (v2.34) on the new ubuntu version 9.1, but it doesnt work (same error as foottuns)

Foottuns, u said u solved the pb. Can u give us some hints? I would be very thankful :)

See u!

---

### Post by Equinoxe_4 on 2009-11-05
It seems to be a problem with gcc-4.4.1 and oTCL
 
Check this: [http://www.linuxquestions.org/questions/linux-networking-3/ns-installation-wont-let-me-do-it-on-ubuntu-9.10-766193/](http://www.linuxquestions.org/questions/linux-networking-3/ns-installation-wont-let-me-do-it-on-ubuntu-9.10-766193/)

---

### Post by Conendrum on 2009-11-06
Thanks a lot!! It works perfectly now!!!

---

### Post by yasirimteyaz on 2009-11-06
Check out my latest blog on installing ns2 on Ubuntu 9.10 [http://bit.ly/1DiXzB](http://bit.ly/1DiXzB)
It works perfectly with this method.

---

