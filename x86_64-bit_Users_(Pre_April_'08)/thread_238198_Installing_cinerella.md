---
title: "Installing cinerella?"
date: 2006-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by lukus001 on 2006-08-17
After following a ubuntu forum guide and other installation methods from sites with dead repos to installing via cinelerra's own sources i've still yet to actually install it...

Via cinerella's source I get the error:
> Configured successfully.  Type 'make' to build it.
lukus001@verpix:~/Desktop/cinelerra-2.1$ make
make -f build/Makefile.cinelerra
sh: -c: line 1: syntax error: unexpected end of file
make[1]: Entering directory `/home/lukus001/Desktop/cinelerra-2.1'
gcc -c -O2 -fomit-frame-pointer -falign-loops=2 -falign-jumps=2 -falign-functions=2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I../../freetype-2.1.4/include -I../../ -DHAVE_OSS -DHAVE_FIREWIRE  soundtest.c -o x86_64/soundtest.o
Assembler messages:
FATAL: can't create x86_64/soundtest.o: No such file or directory
make[1]: *** [x86_64/soundtest.o] Error 1
make[1]: Leaving directory `/home/lukus001/Desktop/cinelerra-2.1'
make: *** [all] Error 2
lukus001@verpix:~/Desktop/cinelerra-2.1$


Following the guide [here]("http://www.ubuntuforums.org/showthread.php?t=215252") I get the error:
>  relocation R_X86_64_32 against `first_avcodec' can not be used when ma king a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../lib64/libavcodec.a: could not re ad symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libquicktimehv.la] Error 1
make[3]: Leaving directory `/home/lukus001/hvirtual/quicktime'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/lukus001/hvirtual/quicktime'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lukus001/hvirtual'
make: *** [all] Error 2

Also installing the deb files someone provided on that page (lower down) it installs cinelerra but it needs GLIBC_2.4 which from my search appears to be a edgy only file and have been advised against installing it from the people @ #ubuntu+1 since I would have to pretty much update dapper to edgy.   Before someone says "have you recomplied with -fPIC" the answer is no, because I have no real clue as to what that means and as to what i apply it to.

Any help appresiated.

---

### Post by juicemansam on 2006-08-19
Not to discourage you, but I've tried compiling Cinelerra quite a few times, in both 32 and 64-bit environments. I tell you it wasn't a nice experience. I'd try running Alien on the website provided 64-bit binary package. That at least works most of the time. But if you, like me until I gave up, insist compiling it yourself, I'd try and compile every individual library first, then make sure than parent make files don't delete any objects, which will be a big pain. I'd also try to compile it with the least amount of gcc flags. Good luck!

Edit: strange, they don't seem to have a 64-bit download anymore, just sources. Also, you might want to try the HV recommended fork at [http://cvs.cinelerra.org/](http://cvs.cinelerra.org/).

---

### Post by aouie on 2007-06-28
As has been pointed out in other places, the AMD64 packages for edgy listed at the [Cinelerra CV site]("http://cvs.cinelerra.org/") [site]("http://cvs.cinelerra.org/") works in feisty too.
Sincerely,
Aouie

---

