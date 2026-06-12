---
title: "wrong ELF class: ELFCLASS64"
date: 2013-03-29
forum: Wine
---

### Post by JohnPta on 2013-03-29
I try to install WINE in Ubuntu 12.04 LTS 
The WINE version is 1.5.26

First I got the error message:"/usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory"

So I created the directory with its sub directory and copied the file "gnome-keyring-pkcs11.so" into that directory.
Than I ran winecfg again.

Now I got the error message: "wrong ELF class: ELFCLASS64"

Now, I feel, am getting deeper and deeper onto trouble.
Can somebody explain to me how to get WINE to work without messing up Ubuntu? ?

---

### Post by thatguruguy on 2013-03-29
> **JohnPta said:**
> I try to install WINE in Ubuntu 12.04 LTS 
The WINE version is 1.5.26

First I got the error message:"/usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory"

So I created the directory with its sub directory and copied the file "gnome-keyring-pkcs11.so" into that directory.
Than I ran winecfg again.

Now I got the error message: "wrong ELF class: ELFCLASS64"

Now, I feel, am getting deeper and deeper onto trouble.
Can somebody explain to me how to get WINE to work without messing up Ubuntu? ?
Try this. Open a terminal and type:
```
sudo apt-get install ia32-libs
```

---

### Post by JohnPta on 2013-03-30
I did install that: "sudo apt-get install ia32-libs"

Than I ran again "WINECFG" and this is what I got.

p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: wrong ELF class: ELFCLASS64

Than I tried to stop the process by "Ctrl C"

err:ntdll:RtlpWaitForCriticalSection section 0x7ba43340 "console.c: CONSOLE_CritSect" wait timed out in thread 0029, blocked by 0025, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bcc5a20 "loader.c: loader_section" wait timed out in thread 0025, blocked by 0009, retrying (60 sec)
wine: Critical section 7ba43340 wait failed at address 0x7bc36cb5 (thread 0027), starting debugger...
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc36cb5
root@jan-desktop:~# 


Next Step ??????

---

### Post by JohnPta on 2013-03-30
I tried to install a Window package anyway. That did not work so I rebooted the computer and ran "WINECFG" again.
First I got this:  wrong ELF class: ELFCLASS64

Than I closed the Grey "WINE" window. Than I got this: root@jan-desktop:~# fixme:msvcrt:__clean_type_info_names_internal (0x3560a4) stub
fixme:msvcrt:__clean_type_info_names_internal (0x1011a354) stub

Does this point to a faulty memory chip???

---

