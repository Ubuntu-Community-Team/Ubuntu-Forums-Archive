---
title: "compilig 32-bit software -- complains about incompatible libraries"
date: 2006-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by enigma_0Z on 2006-11-19
--ERM-- I meant to say libraries in the subject... --ERM--

Hi, I'm trying to compile some software as 32-bit binaries instead of 64-bit, but I can't quite figure out how.

'CFLAGS="-m32" configure' fails with 

```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

And the relavant lines from config.log:

```
configure:1982: $? = 1
configure:2005: checking for C compiler default output file name
configure:2008: gcc -m32   conftest.c  >&5
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
configure:2011: $? = 1
configure: failed program was:

```

Looks like GCC is trying to compile the 32-bit binary with the 64-bit libs!! ](*,) 

How can I make it see the 32-bit libs instead? Do I have to deal with a chroot to build in? How can I make one?

---

### Post by RAOF on 2006-11-19
You can install the **ia32-libs**, **libc6-dev-i386**, etc packages to get the 32bit libs on your 64bit install.

Alternatively, setting up a development chroot is pretty easy, and not such a bad idea.  **pbuilder** makes this quite easy.  Install the **pbuilder** package, then run 
```
sudo pbuilder create --distribution edgy --debootstrapopts arch --debootstrapopts i386

```
You can then login to your chroot with **sudo pbuilder login**.  This won't save any changes you make in the chroot (you need to pass --save-after-login to do that), though, since it's designed for building debian packages.

---

### Post by enigma_0Z on 2006-11-20
> **RAOF said:**
> You can install the **ia32-libs**, **libc6-dev-i386**, etc packages to get the 32bit libs on your 64bit install.

Alternatively, setting up a development chroot is pretty easy, and not such a bad idea.  **pbuilder** makes this quite easy.  Install the **pbuilder** package, then run 
```
sudo pbuilder create --distribution edgy --debootstrapopts arch --debootstrapopts i386

```
You can then login to your chroot with **sudo pbuilder login**.  This won't save any changes you make in the chroot (you need to pass --save-after-login to do that), though, since it's designed for building debian packages.

The problem is that I want to compile it so I can use it. Once I've got the program compiled, will it look in the proper place for libs?

I dunno if it would help explain myself, but I'm trying to compile cegeda CVS, and I know there's problems with wine on x86-64 systems.

--edit--
Still trying to aviod chroot...

compiling now tells me...

```

/usr/bin/ld: warning: i386 architecture of input file `casemap.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `compose.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `cptable.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `mbtowc.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `string.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `utf8.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `wctomb.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `wctype.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_037.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_042.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_424.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_437.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_500.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_737.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_775.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_850.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_852.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_855.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_856.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_857.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_860.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_861.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_862.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_863.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_864.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_865.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_866.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_869.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_874.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_875.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_878.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_932.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_936.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_949.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_950.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_1006.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_1026.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_1250.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_1251.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_1252.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_1253.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_1254.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_1255.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_1256.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_1257.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_1258.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_10000.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_10006.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_10007.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_10029.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_10079.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_10081.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_20866.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28591.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28592.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28593.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28594.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28595.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28596.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28597.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28598.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28599.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28600.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28603.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28604.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `c_28605.o' is incompatible with i386:x86-64 output
...
gcc -m32 -march=i386 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -Wa,--execstack -D__i386__ -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -o winebuild  import.o main.o parser.o relay.o res16.o res32.o spec16.o spec32.o utils.o        -L../../unicode -lwine_unicode -L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32
/usr/bin/ld: skipping incompatible ../../unicode/libwine_unicode.so when searching for -lwine_unicode
/usr/bin/ld: cannot find -lwine_unicode
collect2: ld returned 1 exit status
make[2]: *** [winebuild] Error 1
make[2]: Leaving directory `/home/enigma/src/build/cegeda/winex/tools/winebuild'
make[1]: *** [winebuild] Error 2
make[1]: Leaving directory `/home/enigma/src/build/cegeda/winex/tools'
make: *** [tools] Error 2

```

Looks like now one of the intermdediate libs isn't working... hrm.

---

### Post by RAOF on 2006-11-20
I believe you want to pass the **-m32** option through to ld as well.  Also, you don't need the **-march=i386** option.  **-m32** will build a 32bit binary for you.

---

### Post by enigma_0Z on 2006-11-20
> **RAOF said:**
> I believe you want to pass the **-m32** option through to ld as well.  Also, you don't need the **-march=i386** option.  **-m32** will build a 32bit binary for you.

gcc is running ld automatically, and -m32 is getting passed along. I'm going to just work in a chroot for now. (I've built one using pbuilder).

---

