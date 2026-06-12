---
title: "problem in compiling kernel 2.6.29"
date: 2009-03-30
forum: x86 64-bit Users
---

### Post by sunflowers on 2009-03-30
[COLOR="RoyalBlue"]Hi.I have a problem with comiling kernel 2.6.29 on Ubuntu 8.10 x86_64.
after i finished configureing my kernel and exit from menuconfig,i began to comile with these 2 command:
[/COLOR]
```
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```

[COLOR="RoyalBlue"]but i recived some errors as i inserted them here at the end of prompt:[/COLOR]

```
hossein@polaris-desktop:~$ su
Password:                    
root@polaris-desktop:/home/hossein# cd ~/src/linux-2.6.29/
root@polaris-desktop:~/src/linux-2.6.29# make menuconfig
scripts/kconfig/mconf arch/x86/Kconfig                  
#                                                       
# configuration written to .config                      
#                                                       


*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

root@polaris-desktop:~/src/linux-2.6.29# make-kpkg clean
exec debian/rules  DEBIAN_REVISION=5:10.Custom  clean   

====== making target CLN-common [new prereqs: testdir]======

====== making target CLN-common [new prereqs: ]======
/usr/bin/make -f ./debian/rules real_stamp_clean     
make[1]: Entering directory `/root/src/linux-2.6.29' 
====== making target real_stamp_clean [new prereqs: ]======
running clean                                              
test ! -f scripts/package/builddeb.kpkg-dist ||                     \
          mv -f scripts/package/builddeb.kpkg-dist scripts/package/builddeb
test ! -f scripts/package/Makefile.kpkg-dist ||                     \      
          mv -f scripts/package/Makefile.kpkg-dist scripts/package/Makefile
test ! -f .config  || cp -pf .config config.precious                       
test ! -f Makefile || \                                                    
            /usr/bin/make    ARCH=x86_64 distclean                         
make[2]: Entering directory `/root/src/linux-2.6.29'                       
  CLEAN   /root/src/linux-2.6.29                                           
  CLEAN   .tmp_versions                                                    
  CLEAN   scripts/basic                                                    
  CLEAN   scripts/kconfig                                                  
  CLEAN   /root/src/linux-2.6.29/debian/                                   
  CLEAN   include/config                                                   
  CLEAN   .config .config.old include/asm include/linux/autoconf.h include/linux/version.h include/linux/utsrelease.h include/linux/bounds.h
make[2]: Leaving directory `/root/src/linux-2.6.29'                                                                                         
test ! -f config.precious || mv -f config.precious .config                                                                                  
test ! -f stamp-patch || /usr/bin/make -f ./debian/rules unpatch_now                                                                                                             
test -f stamp-building || test -f debian/official || rm -rf debian                                                                                                               
# work around idiocy in recent kernel versions                                                                                                                                   
test ! -e scripts/package/builddeb.dist || \                                                                                                                                     
            mv -f scripts/package/builddeb.dist scripts/package/builddeb                                                                                                         
test ! -e scripts/package/Makefile.dist || \                                                                                                                                     
            mv -f scripts/package/Makefile.dist scripts/package/Makefile                                                                                                         
rm -f modules/modversions.h modules/ksyms.ver debian/files conf.vars scripts/cramfs/cramfsck scripts/cramfs/mkcramfs applied_patches debian/buildinfo stamp-build stamp-configure stamp-image stamp-headers stamp-src stamp-diff stamp-doc stamp-manual stamp-patch stamp-buildpackage stamp-debian stamp-arch-conf stamp-indep-conf stamp-configure-arch stamp-configure-indep stamp-configure stamp-arch-build stamp-indep-build stamp-build-arch stamp-build-indep stamp-build stamp-arch-inst stamp-indep-inst stamp-install stamp-install-arch stamp-install-indep stamp-arch-bin stamp-indep-bin stamp-binary stamp-binary-arch stamp-binary-indep debian/stamp-kernel-conf debian/stamp-prepare stamp-patch debian/stamp-conf stamp-debian debian/stamp-build-kernel stamp-buildpackage stamp-kernel-source stamp-kernel-manual stamp-kernel-doc stamp-kernel-headers stamp-kernel-image                      
rm -rf  /root/src/linux-2.6.29/debian/tmp_man                                                                                                                                    
make[1]: Leaving directory `/root/src/linux-2.6.29'                                                                                                                              
====== making target CLN-indep [new prereqs: CLN-common]======                                                                                                                   

====== making target CLEAN/linux-source-2.6.29-custom [new prereqs: CLN-indep]======

====== making target CLEAN/linux-doc-2.6.29-custom [new prereqs: CLN-indep]======

====== making target CLEAN/linux-manual-2.6.29-custom [new prereqs: CLN-indep]======

====== making target clean-indep [new prereqs: linux-source-2.6.29-custom linux-doc-2.6.29-custom linux-manual-2.6.29-custom]======
====== making target CLN-arch [new prereqs: CLN-common]======                                                                      

====== making target CLEAN/linux-headers-2.6.29-custom [new prereqs: CLN-arch]======

====== making target CLEAN/linux-image-2.6.29-custom [new prereqs: CLN-arch]======

====== making target CLEAN/linux-uml-2.6.29-custom [new prereqs: CLN-arch]======

====== making target CLEAN/linux-xen0-2.6.29-custom [new prereqs: CLN-arch]======

====== making target CLEAN/linux-xenu-2.6.29-custom [new prereqs: CLN-arch]======

====== making target clean-arch [new prereqs: linux-headers-2.6.29-custom linux-image-2.6.29-custom linux-uml-2.6.29-custom linux-xen0-2.6.29-custom linux-xenu-2.6.29-custom]======                                                                                                                                                                              
====== making target stamp-clean [new prereqs: clean-indep clean-arch]======                                                                                                     

rm -f  modules/modversions.h modules/ksyms.ver debian/files conf.vars scripts/cramfs/cramfsck scripts/cramfs/mkcramfs applied_patches debian/buildinfo stamp-build stamp-configure stamp-image stamp-headers stamp-src stamp-diff stamp-doc stamp-manual stamp-patch stamp-buildpackage stamp-debian stamp-arch-conf stamp-indep-conf stamp-configure-arch stamp-configure-indep stamp-configure stamp-arch-build stamp-indep-build stamp-build-arch stamp-build-indep stamp-build stamp-arch-inst stamp-indep-inst stamp-install stamp-install-arch stamp-install-indep stamp-arch-bin stamp-indep-bin stamp-binary stamp-binary-arch stamp-binary-indep debian/stamp-kernel-conf debian/stamp-prepare stamp-patch debian/stamp-conf stamp-debian debian/stamp-build-kernel stamp-buildpackage stamp-kernel-source stamp-kernel-manual stamp-kernel-doc stamp-kernel-headers stamp-kernel-image                     
rm -rf  /root/src/linux-2.6.29/debian/tmp_man                                                                                                                                    
rm -f core TAGS                                                     \                                                                                                            
               `find . ! -regex '.*/\.git/.*' ! -regex '.*/\{arch\}/.*'      \                                                                                                   
                       ! -regex '.*/CVS/.*'   ! -regex '.*/\.arch-ids/.*'    \                                                                                                   
                       ! -regex '.*/\.svn/.*'                                \                                                                                                   
                   \( -name '*.orig' -o -name '*.rej' -o -name '*~'       -o \                                                                                                   
                      -name '*.bak'  -o -name '#*#'   -o -name '.*.orig'  -o \                                                                                                   
                      -name '.*.rej' -o -name '.SUMS' -o -size 0 \)          \                                                                                                   
                -print`                                                                                                                                                          
====== making target clean [new prereqs: stamp-clean]======                                                                                                                      
root@polaris-desktop:~/src/linux-2.6.29# fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers                                                     
exec make -f /usr/share/kernel-package/ruleset/minimal.mk debian APPEND_TO_VERSION=-custom  INITRD=YES                                                                           
====== making target minimal_debian [new prereqs: ]======                                                                                                                        
This is kernel package version .                                                                                                                                                 
test -d debian || mkdir debian                                                                                                                                                   
test ! -e stamp-building || rm -f stamp-building                                                                                                                                 
test -f debian/control || sed         -e 's/=V/2.6.29-custom/g'        \                                                                                                         
                -e 's/=D/2.6.29-custom-10.00.Custom/g'         -e 's/=A/amd64/g'  \                                                                                              
                -e 's/=SA//g'   -e 's/=L/ /g' \                                                                                                                                  
                -e 's/=I//g'                                    \                                                                                                                
                -e 's/=CV/2.6/g'                       \                                                                                                                         
                -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                        \                                             
                -e 's/=ST/linux/g'      -e 's/=B/x86_64/g'    \                                                                                                                  
                         /usr/share/kernel-package/Control > debian/control                                                                                                      
test -f debian/changelog ||  sed -e 's/=V/2.6.29-custom/g'             \                                                                                                         
            -e 's/=D/2.6.29-custom-10.00.Custom/g'        -e 's/=A/amd64/g'       \                                                                                              
            -e 's/=ST/linux/g'     -e 's/=B/x86_64/g'         \                                                                                                                  
            -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                             \                                            
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

====== making target CONFIG-common [new prereqs: testdir]======

====== making target debian/stamp-conf [new prereqs: ]======
# work around idiocy in recent kernel versions              
test ! -e scripts/package/builddeb || \                     
            mv -f scripts/package/builddeb scripts/package/builddeb.kpkg-dist
test ! -e scripts/package/Makefile || \                                      
            (mv -f scripts/package/Makefile scripts/package/Makefile.kpkg-dist && \
               (echo "# Dummy file "; echo "help:") >  scripts/package/Makefile)   
test -d debian || mkdir ./debian                                                   
test ! -e stamp-building || rm -f stamp-building                                   
test ! -f ./debian || test -f stamp-debian || test -f debian/official || \         
               (rm -rf ./debian && mkdir ./debian)                                 
test -f stamp-debian  ||                                           \               
          ( test -f debian/official && test -f debian/control) ||          \       
           sed -e 's/=V/2.6.29-custom/g'         -e 's/=D/2.6.29-custom-10.00.Custom/g'        \
               -e 's/=A/amd64/g'   -e 's/=SA//g'  \                                             
                -e 's/=L/lilo (>= 19.1) | grub, /g' -e 's/=I/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'     \
                -e 's/=CV/2.6/g'                      \                                                                                     
                -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g'                       \         
                -e 's/=ST/linux/g'      -e 's/=B/x86_64/g'   \                                                                              
                         /usr/share/kernel-package/Control> debian/control                                                                  
test -f stamp-debian  ||    test -f debian/official ||                \                                                                     
           sed -e 's/=V/2.6.29-custom/g' -e 's/=D/2.6.29-custom-10.00.Custom/g'                   \                                         
            -e 's/=A/amd64/g' -e 's/=M/Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>/g' \                 
            -e 's/=ST/linux/g'     -e 's/=B/x86_64/g'           \                                                                           
                /usr/share/kernel-package/changelog > debian/changelog                                                                      
test  -f debian/rules || install -p -m 755 /usr/share/kernel-package/rules debian/rules                                                     
test  -f stamp-debian || test -f debian/official ||                     \                                                                   
           for file in ChangeLog  Control  Control.bin86 config templates.in rules; do                                      \               
               cp -f  /usr/share/kernel-package/$file ./debian/;                               \                                            
           done                                                                                                                             
test  -f stamp-debian || test -f debian/official ||                     \                                                                   
           for dir  in Config docs examples ruleset scripts pkg po;  do                                      \                              
             cp -af /usr/share/kernel-package/$dir  ./debian/;                                 \                                            
           done                                                                                                                             
echo done >  stamp-debian                                                                                                                   
echo done >  debian/stamp-conf                                                                                                              
====== making target CONFIG-common [new prereqs: stamp-conf]======                                                                          
This is kernel package version 11.001-0.1.                                                                                                  
====== making target stamp-arch-conf [new prereqs: CONFIG-common]======                                                                     

====== making target CONFIG-arch [new prereqs: stamp-arch-conf]======
====== making target conf.vars [new prereqs: Makefile .config]====== 

====== making target CONFIG-arch [new prereqs: .config conf.vars]======
This is kernel package version 11.001-0.1.                             
====== making target CONFIG/linux-headers-2.6.29-custom [new prereqs: CONFIG-arch]======

====== making target CONFIG/linux-image-2.6.29-custom [new prereqs: CONFIG-arch]======

====== making target CONFIG/linux-uml-2.6.29-custom [new prereqs: CONFIG-arch]======

====== making target CONFIG/linux-xen0-2.6.29-custom [new prereqs: CONFIG-arch]======

====== making target CONFIG/linux-xenu-2.6.29-custom [new prereqs: CONFIG-arch]======

====== making target stamp-configure-arch [new prereqs: linux-headers-2.6.29-custom linux-image-2.6.29-custom linux-uml-2.6.29-custom linux-xen0-2.6.29-custom linux-xenu-2.6.29-custom]======
====== making target configure-arch [new prereqs: stamp-configure-arch]======
====== making target stamp-indep-conf [new prereqs: CONFIG-common]======

====== making target CONFIG-indep [new prereqs: stamp-indep-conf]======
====== making target debian/stamp-kernel-conf [new prereqs: .config Makefile]======
/usr/bin/make EXTRAVERSION=-custom   ARCH=x86_64 \
                oldconfig
make[1]: Entering directory `/root/src/linux-2.6.29'
scripts/kconfig/conf -o arch/x86/Kconfig
#
# configuration written to .config
#
make[1]: Leaving directory `/root/src/linux-2.6.29'
/usr/bin/make EXTRAVERSION=-custom   ARCH=x86_64 prepare
make[1]: Entering directory `/root/src/linux-2.6.29'
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/root/src/linux-2.6.29'
make[1]: Entering directory `/root/src/linux-2.6.29'
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
  CC      kernel/bounds.s
  GEN     include/linux/bounds.h
  CC      arch/x86/kernel/asm-offsets.s
In file included from /root/src/linux-2.6.29/arch/x86/include/asm/page.h:42,
                 from /root/src/linux-2.6.29/arch/x86/include/asm/pda.h:8,
                 from /root/src/linux-2.6.29/arch/x86/include/asm/current.h:19,
                 from /root/src/linux-2.6.29/arch/x86/include/asm/processor.h:15,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from include/linux/crypto.h:21,
                 from arch/x86/kernel/asm-offsets_64.c:7,
                 from arch/x86/kernel/asm-offsets.c:4:
/root/src/linux-2.6.29/arch/x86/include/asm/page_64.h:46:2: error: #error "CONFIG_PHYSICAL_START must be a multiple of 2MB"
make[2]: *** [arch/x86/kernel/asm-offsets.s] Error 1
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/root/src/linux-2.6.29'
make: *** [debian/stamp-kernel-conf] Error 2
root@polaris-desktop:~/src/linux-2.6.29#
```

[COLOR="RoyalBlue"][B]what should i do to solve this problem.
Thanks.[/B][/COLOR]

---

### Post by kevmitch on 2009-03-30
First of all, I would recommend against compiling a kernel as root. That's what fakeroot is there for: to create a package with root-owned files without being root. That's also why the /usr/src and /usr/local/src directories have special ownership and permissions. They belong to the group "src" and are writable by anyone in that group. You should add yourself to the src group

```
adduser hossein src
```

And do everything except actually install the kernel package as your regular user. 

That said, I'm not sure if that's what's causing your problem. I just tried downloading 2.6.29 and compiling with your command as my regular user on Jaunty and it seems to work ok. What version of GCC are you using? I think there were a bunch of versions that are known not to work for 2.6.29.

```
gcc -v
```

There's also a possibility that there's something in your config that I don't have. I just copied mine out of the distributed kernel

```
cp /boot/config-2.6.28-11-generic /usr/src/linux-2.6.29/.config
```

And went with the defaults where there were new options. If you attach your /usr/src/linux-2.6.29/.config I could take a look at that.

---

### Post by Yellow Pasque on 2009-03-30
What is output of:
```
cd /root/usr/src/linux-2.6.29/
cat .config | grep CONFIG_PHYSICAL
```

You can manually change the PHYSICAL_START variable when you do menuconfig. It's called "Physical address where the kernel is loaded" under the "Processor Type and Features" submenu. My 2.6.27 kernel has a default of 0x200000

---

### Post by sunflowers on 2009-03-30
> **Temüjin said:**
> What is output of:
```
cd /root/usr/src/linux-2.6.29/
cat .config | grep CONFIG_PHYSICAL
```

You can manually change the PHYSICAL_START variable when you do menuconfig. It's called "Physical address where the kernel is loaded" under the "Processor Type and Features" submenu. My 2.6.27 kernel has a default of 0x200000

[COLOR="RoyalBlue"]Thanks dear Temüjin. with your help, i solved that problem.[/COLOR]:P
[COLOR="RoyalBlue"]but, how can i add {solved} to my thread?[/COLOR]

---

### Post by sunflowers on 2009-03-30
> **kevmitch said:**
> First of all, I would recommend against compiling a kernel as root. That's what fakeroot is there for: to create a package with root-owned files without being root. That's also why the /usr/src and /usr/local/src directories have special ownership and permissions. They belong to the group "src" and are writable by anyone in that group. You should add yourself to the src group

```
adduser hossein src
```

And do everything except actually install the kernel package as your regular user. 

That said, I'm not sure if that's what's causing your problem. I just tried downloading 2.6.29 and compiling with your command as my regular user on Jaunty and it seems to work ok. What version of GCC are you using? I think there were a bunch of versions that are known not to work for 2.6.29.

```
gcc -v
```

There's also a possibility that there's something in your config that I don't have. I just copied mine out of the distributed kernel

```
cp /boot/config-2.6.28-11-generic /usr/src/linux-2.6.29/.config
```

And went with the defaults where there were new options. If you attach your /usr/src/linux-2.6.29/.config I could take a look at that.

[COLOR="RoyalBlue"]**thank you for your help. but i solved that problem by changig the value of Physicall_address...  . but i want to attach my 2.6.29 kernel`s config for your information.**[/COLOR]

---

