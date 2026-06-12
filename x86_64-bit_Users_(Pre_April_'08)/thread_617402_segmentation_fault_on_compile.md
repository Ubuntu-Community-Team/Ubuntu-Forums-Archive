---
title: "segmentation fault on compile"
date: 2007-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mark Grice on 2007-11-19
When I go to compile some programs, I am getting a segmentation fault on my 64-bit Ubuntu (gutsy 7.10). I am running on an AMD 64. I have had no problems running any program. I have done a memtest and it comes back fine.

I have also compiled many programs with no problems.

However, some will not compile.

I am trying to MAKE Window Maker. I run their ./configure so I can run wmaker with GNOME.

But when it gets part way through, I get this error:

 ```
 
/local/include     -g -O2 -c convert.c
 gcc -DHAVE_CONFIG_H -I. -I. -I../src -I/usr/local/include -g -O2 -c convert.c  -fPIC -DPIC -o .libs/convert.o
convert.c: In function 'RConvertImage':
convert.c:915: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[2]: *** [convert.lo] Error 1
make[2]: Leaving directory `/home/mark/GNUstep/Library/WindowMaker/Source/WindowMaker-0.92.0/wrlib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mark/GNUstep/Library/WindowMaker/Source/WindowMaker-0.92.0/wrlib'
make: *** [all-recursive] Error 1


```

Any ideas?

---

### Post by dralokyn on 2007-11-19
did you submit a bug report as per the instructions in your error message? this may be a known issue, with a known fix, or maybe it's a new issue, and the maintainers of the software will like to know about it.

---

### Post by Mark Grice on 2007-11-19
> **dralokyn said:**
> did you submit a bug report as per the instructions in your error message? this may be a known issue, with a known fix, or maybe it's a new issue, and the maintainers of the software will like to know about it.

I was hoping for more input before I filed a report (such as, has anyone else seen this...) but apparently not.

I shutdown the system and came back in.. this time I get through the configure.c file... but I error here (and this looks like a showstopper):

```

 gcc -DHAVE_CONFIG_H -I. -I. -I../src -I/usr/local/include -g -O2 -c convert.c  -fPIC -DPIC -o .libs/convert.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../src -I/usr/local/include -g -O2 -c convert.c -o convert.o >/dev/null 2>&1
`echo /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../src  -I/usr/local/include     -g -O2 | sed -e s/-fomit-frame-pointer//` -O0 -c x86_specific.c
 gcc -DHAVE_CONFIG_H -I. -I. -I../src -I/usr/local/include -g -O2 -O0 -c x86_specific.c  -fPIC -DPIC -o .libs/x86_specific.o
/tmp/ccf34EcI.s: Assembler messages:
/tmp/ccf34EcI.s:40: Error: `pusha' is not supported in 64-bit mode
/tmp/ccf34EcI.s:41: Error: suffix or operands invalid for `pushf'
/tmp/ccf34EcI.s:42: Error: suffix or operands invalid for `pop'
/tmp/ccf34EcI.s:45: Error: suffix or operands invalid for `push'
/tmp/ccf34EcI.s:46: Error: suffix or operands invalid for `popf'
/tmp/ccf34EcI.s:47: Error: suffix or operands invalid for `pushf'
/tmp/ccf34EcI.s:48: Error: suffix or operands invalid for `pop'
/tmp/ccf34EcI.s:57: Error: `popa' is not supported in 64-bit mode
/tmp/ccf34EcI.s:62: Error: `popa' is not supported in 64-bit mode
/tmp/ccf34EcI.s:105: Error: `pusha' is not supported in 64-bit mode
/tmp/ccf34EcI.s:219: Error: `popa' is not supported in 64-bit mode
/tmp/ccf34EcI.s:256: Error: `pusha' is not supported in 64-bit mode
/tmp/ccf34EcI.s:304: Error: `popa' is not supported in 64-bit mode
/tmp/ccf34EcI.s:329: Error: `pusha' is not supported in 64-bit mode
/tmp/ccf34EcI.s:472: Error: `popa' is not supported in 64-bit mode
make[2]: *** [x86_specific.lo] Error 1
make[2]: Leaving directory `/home/mark/GNUstep/Library/WindowMaker/Source/WindowMaker-0.92.0/wrlib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mark/GNUstep/Library/WindowMaker/Source/WindowMaker-0.92.0/wrlib'
make: *** [all-recursive] Error 1


```

I guess, when all is said and done. I should move back to 32-Bit. How disappointing...

---

