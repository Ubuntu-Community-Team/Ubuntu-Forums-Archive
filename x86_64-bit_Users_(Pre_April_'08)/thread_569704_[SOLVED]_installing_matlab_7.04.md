---
title: "[SOLVED] installing matlab 7.04"
date: 2007-10-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by miguelan on 2007-10-07
I've  been fighting quite a lot trying to install Matlab 7.04 on my laptop (x86_64 arquitecture).  I've read several threads and done my best finding information through Google. However, I cannot get matlab running.

Basically, the installation proceeds quite fine, i.e. no errors at all, I copy both license files, I replace $HOSTNAME by that of my computer, etc. When running matlab for the first time I get the following error:
"*** glibc detected *** /usr/local/matlab/bin/glnxa64/MATLAB: malloc(): memory corruption: 0x0000000000598320 ***",
which I  solved by adding the following two lines to the .matlab7rc.sh file:
LD_ASSUME_KERNEL=2.4.1
export LD_ASSUME_KERNEL

But after doing all these operations I still get the following error:
"expr: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/uname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

    Sorry! We could not determine the machine architecture for your
           host."

Does anybody out there know how to solve this issue? Is there anybody that successfully installed matlab on a x86_64 machine and who might explain me step by step how to do it?

Thanks in advance,


Miguel

---

### Post by sawjew on 2007-10-08
I had MATLAB R14 SP3 student version installed on my Feisty 64 bit system and it was working fine.  I have now upgraded to Gutsy and haven't got around to installing it yet.  One issue I had is the buffer size  problem as mentioned in the first post here [http://ubuntuforums.org/showthread.php?t=212474&highlight=matlab+install]("http://ubuntuforums.org/showthread.php?t=212474&highlight=matlab+install").  I installed gawk as suggested here and that resolved that issue.

The next problem I had is that the student version only comes in 32 bit not 64 bit but this was resolved by running matlab using the command ```
linux32 matlab
``` rather than simply ```
matlab
```. 

This starts matlab in 32 bit mode and it runs fine.  If you are running the 32 bit version you will need the 32 bit libraries installed and you may also need a 32 bit java runtime.  

Hope you can get it working.  If you can't try Scilab ```
sudo apt-get install scilab
``` or Octave ```
sudo apt-get install octave
```.  You can also get a graphical interface for Octave from here [https://forja.rediris.es/frs/?group_id=60]("https://forja.rediris.es/frs/?group_id=60") but you will have to compile it from source.  

Good luck :)

---

### Post by miguelan on 2007-10-13
Thanks a lot for the info and the fast reply. At the end I did manage to install the 64 bit version.

---

