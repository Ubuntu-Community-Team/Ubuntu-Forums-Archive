---
title: "X-Fi Xtreme Gamer - Errors"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by wingle on 2008-11-02
Hello everyone, 

I have just installed 08.10 and am really liking it.  I blitzed my 08.04 installation so have been working in a nice clean O/S.

I have a Creative Xtreme Gamer and am trying to follow the installation guide [here]("http://ubuntuforums.org/showpost.php?p=4823915&postcount=675") to make it work.  I've got as far as compiling my customised kernel but I've run in to some errors and wondered if anyone could help.  I'm a bit of a noob and have never compiled my own kernel before.

The errors produced when running make-kpkg are shown below.  Does this trace information mean anything to anyone?  I'd really like some help with this one.

Thanks,
Ben

```
root@ben-desktop:/usr/src/linux# make-kpkg clean
exec make -f /usr/share/kernel-package/ruleset/minimal.mk clean 
====== making target minimal_clean [new prereqs: ]======
Cleaning.
test ! -f .config || cp -pf .config config.precious
test ! -e stamp-building || rm -f stamp-building
test ! -f Makefile || \
            make    ARCH=xen distclean
make[1]: Entering directory `/usr/src/linux-source-2.6.27'
Makefile:528: /usr/src/linux-source-2.6.27/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-source-2.6.27/arch/xen/Makefile'. Stop.
make[1]: Leaving directory `/usr/src/linux-source-2.6.27'
make: *** [minimal_clean] Error 2
root@ben-desktop:/usr/src/linux# fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
exec make -f /usr/share/kernel-package/ruleset/minimal.mk debian APPEND_TO_VERSION=-custom  INITRD=YES 
====== making target minimal_debian [new prereqs: ]======
This is kernel package version .
test -d debian || mkdir debian
test ! -e stamp-building || rm -f stamp-building
test -f debian/control || sed         -e 's/=V/2.6.27.2-custom/g'        \
                -e 's/=D/2.6.27.2-custom-10.00.Custom/g'         -e 's/=A/amd64/g'  \
	        -e 's/=SA//g'   -e 's/=L/ /g' \
                -e 's/=I//g'                                    \
                -e 's/=CV/2.6/g'                       \
                -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                        \
                -e 's/=ST/linux/g'      -e 's/=B/xen/g'    \
		         /usr/share/kernel-package/Control > debian/control
test -f debian/changelog ||  sed -e 's/=V/2.6.27.2-custom/g'             \
	    -e 's/=D/2.6.27.2-custom-10.00.Custom/g'        -e 's/=A/amd64/g'       \
            -e 's/=ST/linux/g'     -e 's/=B/xen/g'         \
	    -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g' 	                    \
             /usr/share/kernel-package/changelog > debian/changelog
install -p -m 755 /usr/share/kernel-package/rules debian/rules
for file in ChangeLog  Control  Control.bin86 config templates.in rules; do                                      \
            cp -f  /usr/share/kernel-package/$file ./debian/;                               \
        done
for dir  in Config docs examples ruleset scripts pkg po;  do                                      \
          cp -af /usr/share/kernel-package/$dir  ./debian/;                                 \
        done
test -d ./debian/stamps || mkdir debian/stamps 
exec debian/rules  APPEND_TO_VERSION=-custom  INITRD=YES  kernel_image kernel_headers 
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 3: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator

====== making target CONFIG-common [new prereqs: testdir]======

====== making target debian/stamp-conf [new prereqs: ]======
The changelog says we are creating 2.6.27.2-custom.
However, I thought the version is ..-custom
exit 3
make: *** [debian/stamp-conf] Error 3

```

---

### Post by wingle on 2008-11-03
I have found some useful information on [LinuxQuestions]("http://www.linuxquestions.org/questions/debian-26/toruble-with-kernel-compile-lenny-663456/") and will try this out tonight.

Am I going to have to recompile like this each time a new kernel is released?

Ben

---

### Post by wingle on 2008-11-03
Yes, the  LinuxAnswers post was correct, disabling CONFIG_XEN in Processor Type and Features did the trick and cleared the errors.

Is this a bug that I should file a report on, or was it just a stupid mistake from me?

Ben

---

### Post by xasx on 2008-11-03
Hi!

One question: were you able to get your X-Fi working?
I got the modules compiled, but they won't work, telling me:

```

[  739.092382] ctalsa: no symbol version for bytes_to_order
[  739.092392] ctalsa: Unknown symbol bytes_to_order
[  739.092854] ctalsa: no symbol version for get_ossrv
[  739.092856] ctalsa: Unknown symbol get_ossrv
[  739.093566] ctalsa: no symbol version for heap_alloc
[  739.093568] ctalsa: Unknown symbol heap_alloc
[  739.093801] ctalsa: no symbol version for ioctl_dispatch
[  739.093803] ctalsa: Unknown symbol ioctl_dispatch
[  739.093864] ctalsa: no symbol version for heap_free
[  739.093865] ctalsa: Unknown symbol heap_free

```

Perhaps I have configured some modules not to be built. I just don't know which these are and how to find out. Are there any options that must be set additionally to those required in the Howto-post?

Any help would be appreciated.
Thanks
xasx

Edit: I only changed Processor type to Core2 and disabled old ALSA API support which leads into the same result.

---

### Post by xasx on 2008-11-04
Hello,

I found some kind of a solution here:
[http://forums.creative.com/creativelabs/board/message?board.id=soundblaster&message.id=131774#M131774](http://forums.creative.com/creativelabs/board/message?board.id=soundblaster&message.id=131774#M131774)

Unfortunately with no true line-in support...

Better than nothing. Thanks for the work!

---

