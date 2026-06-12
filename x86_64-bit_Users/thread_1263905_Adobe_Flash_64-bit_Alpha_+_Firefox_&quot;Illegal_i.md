---
title: "Adobe Flash 64-bit Alpha + Firefox &quot;Illegal instruction&quot; crash"
date: 2009-09-11
forum: x86 64-bit Users
---

### Post by Anusiya on 2009-09-11
If you have installed the latest 64-bit flashplugin from Adobe's website and Firefox crashes with "Illegal instruction", this might be the FIX you are looking for! Thanks to the Gentoo forums for pointing this out!

It seems that certain processors (like Xeon older versions) lack an instruction set "lahf_lm" which Flash requires. Run:

```
$ cat /proc/cpuinfo | grep lahf_lm
```

If you do not receive an output, you do not have LAHF instruction set and hence Flash exits with an "Illegal instruction".

Thanks to Maks Verver from Gentoo list, download the file attachment flashplugin-lahf-fix.tar.gz, extract it and run:
```
$ gcc -fPIC -shared -nostdlib -lc -oflashplugin-lahf-fix.so flashplugin-lahf-fix.c
```
 
Copy the flashplugin-lahf-fix.so file to where you have the libflashplayer.so file (eg. /usr/lib/mozilla/plugins)

That's it! The fix is kind of inelegant, but works flawlessly till Intel comes out with a fix for including LAHF/SAHF in a bios update.

Thanks,
Anusiya

---

### Post by davisch on 2009-09-11
I had to put the fix in $HOME/.mozilla/plugins to get it to work but that may be unique for me.  

Thank you so much for posting this and thank you to the Gentoo folks for coming up with it.

---

### Post by EL CHAVO on 2009-09-20
That didn't work for me, still get an Illegal instruction crash when I visit latimes.com.  Oh well, I guess I'll just buy the paper! ;)

---

### Post by afeasfaerw23231233 on 2009-10-08
It works! Thanks.

---

### Post by gunnar123 on 2009-10-12
> **Anusiya said:**
> 
```
$ cat /proc/cpuinfo | grep lahf_lm
```

If you do not receive an output, you do not have LAHF instruction set and hence Flash exits with an "Illegal instruction".

I read in a post although "lahf_lm" may appear as part of the cpuinfo entry for "flags" a processor might still not support LAHF.  Some early AMD processors did not report LAHF as supported although support existed internally. So a workaround was recommended for driver vendors by AMD where they could explicitly write to a register so that the CPU would then indicate LAHF support. But it seems in some cases third party drivers ended up enforcing this flag also for CPU's that lacked actual support:
[http://patchwork.kernel.org/patch/40128/](http://patchwork.kernel.org/patch/40128/)
which lead to less capable CPU's being exposed to LAHF instructions, thus crash situations.

A way to do a concrete test on your machine could be to compile small program such as:
#include <stdio.h>
int main() {
 printf("Hello\n");
 asm("lahf");
}

If the lahf instruction results in "Illegal instruction" when run, then your CPU is not up to it.
I run a recent notebook with Athlon X2 64 and it seems to work there.
Apparently LAHF got introduced back in 2005 or so (AMD silicon revision E), so not likely to show up in recent products.
AMD elaborate exhaustively on the details here:
[http://support.amd.com/us/Processor_TechDocs/25759.pdf](http://support.amd.com/us/Processor_TechDocs/25759.pdf) (100 pages)
see also: [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by e.m.fields on 2009-10-18
SOLVED

THANKS! You people who take the time to post solutions to these forums ROCK.  That's what makes this community so good, hats off.

---

### Post by bobbearr on 2009-11-11
I followed all the instructions ... worked only once the restart FIREFOX but at next reboot only a black screen for example video youtube....but firefox doesn't crash ... it work with chrome..

And now?

---

### Post by nixed242 on 2009-11-12
> **davisch said:**
> I had to put the fix in $HOME/.mozilla/plugins to get it to work but that may be unique for me.  

Thank you so much for posting this and thank you to the Gentoo folks for coming up with it.


I had to put it in the same directory, but it worked!!! Thanks for posting.

---

### Post by ralferoo on 2009-11-17
This fix works great thanks! :)

---

