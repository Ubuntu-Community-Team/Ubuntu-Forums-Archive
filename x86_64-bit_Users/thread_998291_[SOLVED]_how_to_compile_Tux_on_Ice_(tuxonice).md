---
title: "[SOLVED] how to compile Tux on Ice (tuxonice)"
date: 2008-11-30
forum: x86 64-bit Users
---

### Post by blackpaw on 2008-11-30
Trying to compile support for TuxOnIce (suspend2) support into Intrepid's Kernel and somehow I go in circles.. can someone help me?


I follow [this]("http://www.blogs.uni-osnabrueck.de/rotapken/2008/11/13/enhance-intrepid-ibex-with-tuxonice/") guideline and the ubuntu helpfile [here]("https://help.ubuntu.com/community/Suspend2Kernel")


Running make-kpkg for the first time results in:
```

exec debian/rules  APPEND_TO_VERSION=-tuxonice  INITRD=YES  ROOT_CMD=fakeroot  kernel-image kernel-headers 
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
The changelog says we are creating 2.6.27-7-tuxonice.
However, I thought the version is ..-tuxonice
exit 3
make: *** [debian/stamp-conf] Error 3
bazi@bazi-desktop:/usr/src/linux-source-2.6.27$ 

```

I tried with image 2.6.27-7 and -10, both result in this error. 

Now, checking "Makefile" I see "EXTRAVERSION" indicated with a dot (also .7) the instructions turn it into a dash.

> Edit the Makefile and find the line that starts with “EXTRAVERSION =”. Change the value of this option to you’re extraversion. The following command should do this for you:

$ sudo sed -i -r -e "s/^(EXTRAVERSION\s*=\s*).*/\1-$(uname -r | cut -d- -f2)/" Makefile

So I turn it into a dot again (.10) and I get this:
```

Makefile:528: /usr/src/linux-source-2.6.27/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-source-2.6.27/arch/xen/Makefile'.  Stop.
make: *** [conf.vars] Error 2
bazi@bazi-desktop:/usr/src/linux-source-2.6.27$ 

```

Notice the "xen" in the path? Why is it there? 

Looking at line 528 I find:
include $(srctree)/arch/$(SRCARCH)/Makefile
However, my $ARCH should be 'x86_64'
SRCARCH should then be 'x86' (it is being changed earlier)

Could this be because of AMD64?

I tried one more thing: adding '--ARCH=x86_64' to the make-kpkg call and I arrive at:
```

====== making stamp-configure because of  ======
The changelog says we are creating ..-tuxonice
However, I thought the version is 2.6.27.7-tuxonice
exit 4
make: *** [sanity_check] Error 4

```

So I am back at square 1.

Any coders here willing to help? 

I would try with the x86 (i386) architecture, however, I need a lot of RAM for emulation/virtualization purposes so I can not go with stock kernels.

Cheers,


Andreas

---

### Post by Cybso on 2008-12-04
Hi Andreas,

I tried to contact you, but due to an error in my contact form I did not receive your mail address.

I have an amd64 avaible now, and Intrepid is installing at the moment. So I may be able to check wether I can reproduce your error or not this evening.

Nevertheless it would be useful to get a copy of your .config and Makefile.

---

### Post by Cybso on 2008-12-05
Andreas,

this problems seems to be identical with [https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/281699](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/281699). I was able to reproduce it, too. I've updated my article.

Thanks for the hint!

---

### Post by blackpaw on 2008-12-06
Thanks for having a look :)

Just realized what you meant with the contact form... your website! ;)

I will try tonight with 
> --arch=am64 --subarch=x86_64
or for that case: amd64.. whichever is correct :)

---

### Post by Cybso on 2008-12-06
It's "amd64" :-). If you don't want to repeat all steps it should be sufficient to just remove everything from linux-source-2.7.27/include/config and linux-source-2.7.27/debian.

Oh, and just one thing: It seems that the XEN-options have been enabled within the current kernel's config (I always wonder if /boot/config-* is **really** the one the kernel is compiled with). Disable them, or you'll get an 'linux-xenu'-package instead of 'linux-image'.

---

### Post by blackpaw on 2009-01-03
That did the trick!

I can only point to your [[COLOR="Red"]fine tutorial[/COLOR]]("http://www.blogs.uni-osnabrueck.de/rotapken/2008/11/13/enhance-intrepid-ibex-with-tuxonice/"), cybso. Thanks a lot!

Andreas

---

### Post by linuxvacuum on 2009-01-06
After running```
sudo dpkg -i /usr/src/linux-*$(uname -r | cut -d- -f1,2)-tuxonice*.deb
```


I get```
(Reading database ... 182268 files and directories currently installed.)
Preparing to replace linux-headers-2.6.27-7-tuxonice 2.6.27-7-tuxonice-10.00.Custom (using .../linux-headers-2.6.27-7-tuxonice_2.6.27-7-tuxonice-10.00.Custom_i386.deb) ...
Unpacking replacement linux-headers-2.6.27-7-tuxonice ...
Preparing to replace linux-image-2.6.27-7-tuxonice 2.6.27-7-tuxonice-10.00.Custom (using .../linux-image-2.6.27-7-tuxonice_2.6.27-7-tuxonice-10.00.Custom_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.27-7-tuxonice ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-tuxonice
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Setting up linux-headers-2.6.27-7-tuxonice (2.6.27-7-tuxonice-10.00.Custom) ...

Setting up linux-image-2.6.27-7-tuxonice (2.6.27-7-tuxonice-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.27-7-tuxonice
) points to /boot/initrd.img-2.6.27-7-tuxonice
 (/boot/initrd.img-2.6.27-7-tuxonice) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.27-7-tuxonice.postinst line 583.
vmlinuz(/boot/vmlinuz-2.6.27-7-tuxonice
) points to /boot/vmlinuz-2.6.27-7-tuxonice
 (/boot/vmlinuz-2.6.27-7-tuxonice) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.27-7-tuxonice.postinst line 583.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-tuxonice
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```
This error
```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
[B]run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20

Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.27-7-tuxonice.postinst line 1181.
dpkg: error processing linux-image-2.6.27-7-tuxonice (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.27-7-tuxonice[/B]
```

How can I solve this ?

---

### Post by blackpaw on 2009-01-07
Hi!

This error is caused by the nvidia proprietary driver which was compiled for the ubuntu stock kernel. 
What worked for me was to go to System &#8594; Administration &#8594; Hardware drivers

There you should see the current nvidia driver in use marked with a green lamp. (active)
Disable this driver and reboot. Then, go there again and enable the driver again.
If it goes well, it will download and compile a new driver/module/whatever for you. One more reboot and you should be rolling. :)

Cheers


Andreas

---

### Post by linuxvacuum on 2009-01-07
Thanks blackpaw, but what would be the terminal commands to do that? I do not have the GNOME desktop installed and I have the server version.

---

### Post by blackpaw on 2009-01-08
Sorry, I stopped hacking on the console when I got a child.. no more time for that.. or better: Free time needs to be spent differently now ;)

Maybe someone else can help you or you can check 
here: [https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules)
and here: [http://www.tranquillity.se/2008/11/10/nvidia-problems-in-ubuntu-810/](http://www.tranquillity.se/2008/11/10/nvidia-problems-in-ubuntu-810/)
and here: [http://ubuntuforums.org/showthread.php?t=965180](http://ubuntuforums.org/showthread.php?t=965180)


Andreas

---

### Post by minj on 2009-01-26
I tried to follow your tutorial with hardy but encountered an error during patching:

```
can't find file to patch at input line 1769
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/debian/binary-custom.d/lpia/config.lpia b/debian/binary-custom.d/lpia/config.lpia
|index 8abf7c2..1352ba1 100644
|--- a/debian/binary-custom.d/lpia/config.lpia
|+++ b/debian/binary-custom.d/lpia/config.lpia

```

any ideas?

---

### Post by user17 on 2009-02-20
Installing Tuxonice is neither quick nor easy, and it looks as though future kernel updates may wreck it. As I am setting up a computer for someone who has no computer knowledge at all, the threat of future catastrophe is unacceptable. The computer I am working on suspended and resumed easily under Gutsy after setting post_video=false in some file whose name I can't remember. After Gutsy, no matter what I did, the computer -a Compaq Presario V5206- would suspend, but would only resume to a black screen. It seems kind of absurd that something that worked under Gutsy with minimal tweaking will not work under Hardy or Intrepid.

---

