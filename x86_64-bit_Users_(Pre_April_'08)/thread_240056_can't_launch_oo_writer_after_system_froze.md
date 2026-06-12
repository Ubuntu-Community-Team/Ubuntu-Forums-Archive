---
title: "can't launch oo writer after system froze"
date: 2006-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by braj on 2006-08-20
A couple of days ago my computer froze while I was working on some odt files and the only way to start it going was to switch electricity off and on. Now I can't launch oo writer - when I click on it it just shows for a couple of seconds that it's starting to load and then nothing happens. Does anyone know what to do? (sorry if this is a trivial problem but don't know that much about Linux yet :( ...)

---

### Post by braj on 2006-08-27
I tried to run it through terminal, using the command I found after right-click on Writer symbol in Properties and this is what it says:

johny@ubuntugold:~$ ooffice -writer%U
Gtk-Message: Failed to load module "gail": libgail.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge": libspi.so.0: cannot open shared object file: No such file or directory


Fatal exception: Signal 11
Stack:
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c51f]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c83f]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c8dd]
[0xffffe500]
/lib32/libc.so.6(vsscanf+0x6d)[0x564f907d]
/lib32/libc.so.6(sscanf+0x2b)[0x564f3e7b]
/usr/lib/openoffice/program/libvclplug_gtk680li.so(_Z13InitAtkBridgev+0x35)[0x59308fdd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so(create_SalInstance+0x19d)[0x59307341]
/usr/lib/openoffice/program/libvcl680li.so[0x55791369]
/usr/lib/openoffice/program/libvcl680li.so[0x5579146a]
/usr/lib/openoffice/program/libvcl680li.so(_Z7InitVCLRKN3com3sun4star3uno9ReferenceINS1_4lang20XMultiServiceFactoryEEE+0xb7)[0x555f4ad3]
/usr/lib/openoffice/program/libvcl680li.so[0x555f4c31]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x29)[0x555f4cf9]
/usr/lib/openoffice/program/soffice.bin(sal_main+0x47)[0x80646db]
/lib32/libc.so.6(__libc_start_main+0xd2)[0x564b6ea2]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window11RequestHelpERK9HelpEvent+0x31)[0x8064615]
/usr/lib/openoffice/program/soffice: line 233:  6263 Zrušené               "$sd_prog/$sd_binary" "$@"

** (process:6250): WARNING **: Unknown error forking main binary / abnormal early exit ...

---

### Post by braj on 2006-09-02
So it seems that there remains nothing but to reinstal the whole system. I just wonder whether this is something I will have to do everytime my oowriter refuses to load... :(

---

### Post by Kilz on 2006-09-02
> **braj said:**
> So it seems that there remains nothing but to reinstal the whole system. I just wonder whether this is something I will have to do everytime my oowriter refuses to load... :(

Have you tried to reinstall OO?

---

