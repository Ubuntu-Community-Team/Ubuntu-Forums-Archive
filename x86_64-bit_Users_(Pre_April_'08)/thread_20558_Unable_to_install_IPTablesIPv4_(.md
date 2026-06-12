---
title: "Unable to install IPTables::IPv4 :("
date: 2005-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by membreya on 2005-03-17
Trying to install IPTables::IPv4 and I'm getting the following output

> packer.c: In function `ipt_do_pack':
packer.c:261: warning: passing arg 3 of `Perl_sv_2pv_flags' from incompatible pointer type
packer.c:319: warning: passing arg 3 of `Perl_sv_2pv_flags' from incompatible pointer type
packer.c:380: warning: passing arg 3 of `Perl_sv_2pv_flags' from incompatible pointer type
packer.c:512: warning: long long unsigned int format, u_int64_t arg (arg 3)
packer.c:523: warning: long long unsigned int format, u_int64_t arg (arg 3)
cc -c  -Iinclude -I/usr/src/linux/include -Wall -DMODULE_PATH=\"/usr/local/lib/IPTables-IPv4\" -DPER
L_USES_64BIT_INT -O2   -DVERSION=\"0.98\" -DXS_VERSION=\"0.98\" -fPIC "-I/usr/lib/perl/5.8/CORE"   u
npacker.c
unpacker.c: In function `ipt_do_unpack':
unpacker.c:264: warning: long long unsigned int format, u_int64_t arg (arg 3)
unpacker.c:267: warning: long long unsigned int format, u_int64_t arg (arg 3)
cc -c  -Iinclude -I/usr/src/linux/include -Wall -DMODULE_PATH=\"/usr/local/lib/IPTables-IPv4\" -DPER
L_USES_64BIT_INT -O2   -DVERSION=\"0.98\" -DXS_VERSION=\"0.98\" -fPIC "-I/usr/lib/perl/5.8/CORE"   m
askgen.c
make -C libiptc/ all
make[1]: Entering directory `/tmp/.webmin/IPTables-IPv4-0.98/libiptc'
gcc -o libip4tc.o -c libip4tc.c -I../include -I/usr/src/linux/include -DIPTABLES_VERSION=\"1.2.8\" -
O2 -Wall
In file included from libip4tc.c:116:
libiptc.c: In function `entry2index':
libiptc.c:136: warning: int format, different type arg (arg 3)
libip4tc.c: In function `dump_entry':
libip4tc.c:148: warning: long long unsigned int format, u_int64_t arg (arg 2)
libip4tc.c:148: warning: long long unsigned int format, u_int64_t arg (arg 3)
gcc -o libip6tc.o -c libip6tc.c -I../include -I/usr/src/linux/include -DIPTABLES_VERSION=\"1.2.8\" -
O2 -Wall
In file included from libip6tc.c:111:
libiptc.c: In function `entry2index':
libiptc.c:136: warning: int format, different type arg (arg 3)
libip6tc.c: In function `dump_entry':
libip6tc.c:179: warning: long long unsigned int format, u_int64_t arg (arg 2)
libip6tc.c:179: warning: long long unsigned int format, u_int64_t arg (arg 3)
ar r libiptc.a libip4tc.o libip6tc.o
ar: creating libiptc.a
make[1]: Leaving directory `/tmp/.webmin/IPTables-IPv4-0.98/libiptc'
Running Mkbootstrap for IPTables::IPv4 ()
chmod 644 IPv4.bs
rm -f blib/arch/auto/IPTables/IPv4/IPv4.so
LD_RUN_PATH="" cc  -shared -L/usr/local/lib IPv4.o loader.o packer.o unpacker.o maskgen.o libiptc/li
biptc.a  -o blib/arch/auto/IPTables/IPv4/IPv4.so      
/usr/bin/ld: libiptc/libiptc.a(libip4tc.o): relocation R_X86_64_32 can not be used when making a sha
red object; recompile with -fPIC
libiptc/libiptc.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [blib/arch/auto/IPTables/IPv4/IPv4.so] Error 1

---

### Post by wmcbrine on 2005-03-17
Did you try what it says ("recompile with -fPIC")?

---

### Post by membreya on 2005-03-18
sorry for the newbieish response, but the only way I know how to install it is with "cpan -i LWP IPTables::IPv4", how would I add the -fPIC option ?

---

### Post by wmcbrine on 2005-03-18
Hmm, that's a good question. You're installing from cpan, yet it's compiling C code... uh... perhaps an environment variable could be set? I dunno, sorry.

---

### Post by djgrandmarquis on 2006-03-25
It looks like you're on an AMD64, like I am. Regardless, I had the same error and solved it by inserting the -fPIC as suggested. The tricky part was finding where to put the flag, and it was needed in two Makefiles:

IPTables-IPv4-0.98/libiptc/Makefile
IPTables-IPv4-0.98/modules/Makefile

Unfortunately there isn't any way to make these modifications through cpan, but I'll walk you through the manual installation (it's fairly easy, and I don't know much about perl):

From the linblock manual... just modified for IPTables::IPv4. This will take about 10 minutes, tops.

Remember, all this must be done as root.

```
sudo mkdir /usr/local/IPTables

cd /usr/local/IPTables
```

Download the module package from CPAN.  You can obtain its URL by loading search.cpan.org in your browser and searching on the module name.  Click on the distribution name (e.g. IPTables-IPv4-0.98.tar.gz) and there will be a "download" link for the .tar.gz package.  Then execute the following sequence of commands.  You would substitute the URL and name of the package you are installing, and if you downloaded the .tar.gz file with your browser you can skip the wget step.
```

sudo wget http://search.cpan.org/CPAN/authors/id/D/DP/DPATES/IPTables-IPv4-0.98.tar.gz

sudo tar zxvf IPTables-IPv4-0.98

sudo cd IPTables-IPv4-0.98/

```
use your favorite text editor:
```
sudo kwrite modules/Makefile

```
Now find the CFLAGS line and add the -fPIC flag to it:

```
CFLAGS := -I$(KERNEL_INC) -I$(NF_INC) -I$(PERL_INC) -I.. -Wall -O2 -Wundef -fPIC

```

Save it, close it.
Repeat the process for the other Makefile:

```
sudo kwrite libiptc/Makefile
```

Again add the -fPIC flag:

```
CFLAGS := -I../include -I/usr/src/linux/include -DIPTABLES_VERSION=\"1.2.8\" -O2 -Wall -fPIC
```

Save it, close it.
Now everything should be all set. So compile it.

```
sudo perl Makefile.PL

sudo make install
```

Now you can test that it installed correctly. If the following command doesn't give you an error, then it's working properly. 

```
perl -MIPTables::IPv4 -e 1
```

---

