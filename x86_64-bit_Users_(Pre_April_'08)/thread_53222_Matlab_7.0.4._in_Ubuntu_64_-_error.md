---
title: "Matlab 7.0.4. in Ubuntu 64 - error"
date: 2005-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by emrys on 2005-07-30
Hi,

I have installed Matlab 7.0.4. in my ubuntu 64-bit laptop but I can't run it.

I always have this error:

"/usr/local/matlab704/bin/util/oscheck.sh: line 150: /lib64/libc.so.6: Permission denied
*** glibc detected *** malloc(): memory corruption: 0x0000000000597dc0 ***
Aborted"

Any clues?

Thanks!

---

### Post by snoochems on 2005-08-01
I'm a uni student that uses matlab a lot. 
I am currently contemplating using a Linux distro, so i'm very interested in if you can get Matlab to work on Ubuntu.

---

### Post by DancingSun on 2005-08-01
I don't use MatLab, but it sounds like you might be running a 32-bit program that is accessing a 64-bit library, which resulted in memory mis-allocation.

If Matlab has a 64-bit version, make sure you are running that.  But before you do that, try running Matlab with "sudo" in front of it in the command line.  This might fix your permission denied message.

---

### Post by emrys on 2005-08-01
[QUOTE=DancingSun]I don't use MatLab, but it sounds like you might be running a 32-bit program that is accessing a 64-bit library, which resulted in memory mis-allocation.

If Matlab has a 64-bit version, make sure you are running that.  But before you do that, try running Matlab with "sudo" in front of it in the command line.  This might fix your permission denied message.[/QUOTE]

Well, I have installed the 64-bit version of Matlab and I already tried to run it as a root user. Same problem thought. The "permision denied" message still there.

More ideas?

It can be related with some libraries?? I run Breezy and because of the inestability this days, I don't have all the libraries updated...

¿?

---

### Post by DancingSun on 2005-08-01
[QUOTE=emrys]Well, I have installed the 64-bit version of Matlab and I already tried to run it as a root user. Same problem thought. The "permision denied" message still there.

More ideas?

It can be related with some libraries?? I run Breezy and because of the inestability this days, I don't have all the libraries updated...

¿?[/QUOTE]
Hmm...it could be...but your libc.so.6 resides in /lib64, that lookslike it should be 64-bit.  One option you can try is re-installing libc.so.6, and see if the same thing still happens.

You know, interestingly, I don't have libc.so.6 in my /lib64 directory, it's in my /lib32 directory instead!  You might want to investigate this a bit...

---

### Post by emrys on 2005-08-01
[QUOTE=DancingSun]Hmm...it could be...but your libc.so.6 resides in /lib64, that lookslike it should be 64-bit.  One option you can try is re-installing libc.so.6, and see if the same thing still happens.

You know, interestingly, I don't have libc.so.6 in my /lib64 directory, it's in my /lib32 directory instead!  You might want to investigate this a bit...[/QUOTE]
Good Idea. I have discovered that changing the permissions of lib.so.6 (in fact is just a link to libc-2.3.5.so), giving "Execute" permissions, the first error dissapears.

Now we have: 

"xyz@ubuntu:~$ sudo matlab
*** glibc detected *** malloc(): memory corruption: 0x0000000000597dc0 ***
Aborted"

I tried reinstalling libc6 but, no changes.

 ](*,)

---

### Post by DancingSun on 2005-08-01
Ok, I have libc-2.3.2.so and it is located in:
[list=a]
[*]/lib
[*]/lib32
[*]/lib32/tls
[/list] 

I checked the libc6 package in Synaptic and it doesn't install anything in /lib64!

BTW, I'm a newcomer to Linux in and Ubuntu, so I probably can't do any super cool manuevers to get you out of this one, but just helping wherever I can.

---

### Post by emrys on 2005-08-01
[QUOTE=DancingSun]Ok, I have libc-2.3.2.so and it is located in:
[list=a]
[*]/lib
[*]/lib32
[*]/lib32/tls
[/list] 

I checked the libc6 package in Synaptic and it doesn't install anything in /lib64!

BTW, I'm a newcomer to Linux in and Ubuntu, so I probably can't do any super cool manuevers to get you out of this one, but just helping wherever I can.[/QUOTE]
Thanks a lot DancingSun for the help!

I think that 2.3.2. is the 32-bit version. The 64-bit is 2.3.5.
For Breezy, the lib64 folder just links to the lib folder. The 2.3.2. is in lib32 and 2.3.5. in lib.

Anyway, I just don't know what to do with this. The mem alloc error is still there... ¿?¿?

---

### Post by DancingSun on 2005-08-01
What if you try running using the 32-bit version of libc?

You might want to verify that the memory sticks are error free as well.

---

### Post by emrys on 2005-08-01
[QUOTE=DancingSun]What if you try running using the 32-bit version of libc?

You might want to verify that the memory sticks are error free as well.[/QUOTE]

If I change the path to run lib32 version, the error is:

"Inconsistency detected by ld.so: rtld.c: 1259: dl_main: Assertion `_rtld_local._dl_rtld_map.l_prev->l_next == _rtld_local._dl_rtld_map.l_next' failed!
*** glibc detected *** malloc(): memory corruption: 0x0000000000597dc0 ***
Aborted"

I will try now a memtest to discard problems with memory.

Thanks DS.

---

### Post by snoochems on 2005-08-01
where does one get the 64 bit version of matlab?  Is it built into the 'normal' matlab 7?

---

### Post by emrys on 2005-08-01
If I am not wrong, the normal Matlab for Linux 7.0.4 includes linux 32/64 and MacOS X versions.

---

### Post by DancingSun on 2005-08-01
Also, you might want to try to re-install MatLab...and just in case, re-download the 64-bit version and install it.

---

### Post by emrys on 2005-08-06
I have solved the above problem: 

[http://lists.suse.com/archive/suse-linux-e/2005-Jul/1537.html](http://lists.suse.com/archive/suse-linux-e/2005-Jul/1537.html)

<cite>
Open the .matlab7rc.sh file in your $MATLAB/bin folder (where $MATLAB
is your MATLAB installation directory). Add the following two lines to
the beginning of the .matlab7rc.sh file:

%%%BEGIN_CODE%%%
LD_ASSUME_KERNEL=2.4.1
export LD_ASSUME_KERNEL
%%%END_CODE%%%
</cite> 
*************************************
BUT, the I have another problem:

**********
"expr: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/uname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

    Sorry! We could not determine the machine architecture for your
           host. Please contact:

               MathWorks Technical Support

           for further assistance.

trap: usage: trap [-lp] [arg signal_spec ...]"
***********

Any clues??

---

### Post by DancingSun on 2005-08-06
Does "uname" work in your terminal?
You might want to contact MatLab's tech support as well.  Seems like their 64-bit program doesn't support 64-bit OSes too well  :-?

---

### Post by emrys on 2005-08-06
Yes, uname works in my terminal. The output for uname -a is:
"Linux ubuntu64 2.6.12-6-amd64-k8 #1 Fri Aug 5 20:51:28 BST 2005 x86_64 GNU/Linux"

Well, I don't know, maybe the fact that I am running Breezy, and its not yet a stable distro can explain the problems...

Anyone have Matlab 7.0.4. SP2 working in Hoary 64???
Problems?

---

### Post by n0ah420 on 2005-08-22
Contact [email]support@mathworks.com[/email].  There are ways to resolve the issue you are seeing.

---

### Post by emrys on 2005-09-12
OK, one more step.

The above problem can be resolved (maybe): [http://newsreader.mathworks.com/WebX?14@217.Ak6VaXZIXqw.0@.ef07675](http://newsreader.mathworks.com/WebX?14@217.Ak6VaXZIXqw.0@.ef07675)

But then, a new problem arises:

"/bin/sh: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory"

The file is in /lib 

I don't want to use Windows just for Matlab... any clues??

---

### Post by pmar on 2005-10-18
Hi, it seems like the problem is (re)solved in Matlab SP3. So, no problems running SP3 on Breezy:

$ uname -sr 
2.6.12-9-amd64-k8-smp

however there are some minor compatibility issues between Matlab SP2 and SP3....

Cheers,
Petar

---

### Post by DancingSun on 2005-10-18
Well, it's still nice to see them fixing up the 64-bit compatibility issue!:)

---

### Post by vextorspace on 2005-11-10
[QUOTE=emrys]Hi,

I have installed Matlab 7.0.4. in my ubuntu 64-bit laptop but I can't run it.

I always have this error:

"/usr/local/matlab704/bin/util/oscheck.sh: line 150: /lib64/libc.so.6: Permission denied
*** glibc detected *** malloc(): memory corruption: 0x0000000000597dc0 ***
Aborted"

Any clues?

Thanks![/QUOTE]

This is a fresh error in Breazy.  When I had hoary hedgehog, aside from some errors with the os detection script that insists on executing a library to figure out what version it is (which you fixed by changing the permissions), there were no troubles.  I would also guess that it is library version related.  It is a malloc error after all.  I will have to check the other system to see what libc version it used.

-Doug

---

### Post by n0ah420 on 2005-11-10
>  Open the .matlab7rc.sh file in your $MATLAB/bin folder (where $MATLAB
is your MATLAB installation directory). Add the following two lines to
the beginning of the .matlab7rc.sh file:

LD_ASSUME_KERNEL=2.4.1
export LD_ASSUME_KERNEL
 
This usually fixes the malloc error as well.  That version of MATLAB was built on glibc 2.3.3.

---

### Post by ccool on 2005-12-12
I have the same error, and it was working perfectly before I upgrade my ubuntu to hoary :s

---

### Post by dsdsdds on 2007-04-26
:-/ I ran matlab then I got this.
My OS is Ubuntu 7.04 x86_64, Matlab is R14.

$ matlab
awk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
/bin/pwd: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
expr: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Internal error 2: Could not determine the path of the
                  MATLAB root directory.

                  original command path = /usr/local/bin/matlab
                  current  command path = /usr/local/bin/matlab

                  Please contact:

                      MathWorks Technical Support

                  for further assistance.

What should I do then??

---

