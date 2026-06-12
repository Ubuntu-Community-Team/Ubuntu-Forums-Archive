---
title: "Synaps"
date: 2006-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by dimis on 2006-10-08
This is just a report that I have installed [SYNAPS]("http://www-sop.inria.fr/galaad/software/synaps/") under Dapper Drake (6.06 - 64bit) successfully.
Regarding my pc:
```
$ uname -a
Linux crag-hack 2.6.15-26-amd64-generic #1 SMP PREEMPT Fri Sep 8 19:55:50 UTC 2006 x86_64 GNU/Linux
$
```
As you probably know, Synaps has really weird code and requires old compilers so that it runs without problems.
[LIST=1]
[*]For this reason, open Synaptic and install:
[LIST]
[*] gcc-3.3, cpp-3.3, g++-3.3, g77-3.4 (I prefer this instead of g77 - well ... just to be sure ...)
[*] I installed doc files as well, so that they are handy for me as a reference.
[*] Note: I also uninstalled g++-4.0 (+ build-essential, g++, libstdc++6-4.0-dev) as well as gcc-4.0 (+ gcc, g77) from my system.
[/LIST]

[*]Check out which version of gcc and g++ is default, i.e.:
[This step assumes you had installed build-essential package]
```
cd /usr/bin
ls -l gcc
ls -l g++
```
If you don't have symbolic links, or the links show a gcc(g++) greater than 3.3 make 3.3 default by:
```
sudo rm gcc && sudo ln -s gcc-3.3 gcc
sudo rm g++ && sudo ln -s g++-3.3 g++
```
Finally I make a link g77 -> g77-3.4. I don't place the command here so that I can ensure you read this line and give the appropriate command for your configuration, i.e. you might want to have both g77 and g77-3.4 installed on your system, or g77 only, as it seems that synaps is working with both of the above versions.
* I also made the following link but I don't know if it is necessary: gccbug -> gccbug-3.3

[*] Open a terminal and install necessary packages (external dependencies) for Synaps:
[LIST]
[*]**64-bit** Users:
```
sudo apt-get install atlas3-headers atlas3-base atlas3-base-dev refblas3 lapack3 refblas3-dev lapack3-dev lapack3-doc libgmpxx3 libgmp3-dev libgmp3-doc libmpfr1 libmpfr-dev
```
[*]**32-bit** Users:
```
sudo apt-get install atlas3-headers atlas3-sse2 atlas3-sse2-dev refblas3 lapack3 refblas3-dev lapack3-dev lapack3-doc libgmpxx3 libgmp3-dev libgmp3-doc libmpfr1 libmpfr-dev
```
[/LIST]

[*] Configure / Install Synaps:
You can get SYNAPS (tar.gz) [here]("http://gforge.inria.fr/frs/download.php/335/synaps-2.4.0.tar.gz").
Unpack it in your Desktop and execute the following (I want it installed under /opt. If you want to install it somewhere else just change "/opt" with your desired path):
```
sudo mv ~/Desktop/synaps-2.4.0 /opt
cd /opt
sudo chown -R root:root synaps-2.4.0
cd synaps-2.4.0
sudo ./configure CC=gcc-3.3 CXX=g++-3.3 CPP=cpp-3.3 F77=g77-3.4
sudo make
sudo make install
sudo make clean
```

[*] Now edit /etc/environment and add synaps-bin to your path (in my case /opt/synaps-2.4.0/bin) for convenience in command line.

[*] **s++** is now ready, however one gets the following warning:
```
/usr/bin/ld: warning: libstdc++.so.6, needed by /usr/lib/libgmpxx.so, may conflict with libstdc++.so.5
```
For instance: 
```
cp /opt/synaps-2.4.0/linalg/test/L03matstrdbl.cc /tmp
cd /tmp
s++ L03matstrdbl.cc
./L03matstrdbl.ex
```
And the resulting executable is working ok (and not only this!) :D
[/LIST]


**Future Work / Ideas for help are most welcome.**
As you can imagine I tried to resolve the problem for the above warning. This is what I did :
I installed all external dependecies of SYNAPS with Synaptic apart from GMP and mpfr (meaning on step 3 above I didn't install libgmpxx3 libgmp3-dev libgmp3-doc libmpfr1 libmpfr-dev). However, I couldn't UNinstall libgmp3c2 because it has a dependency with Ubuntu-desktop, and, well ... I am not that brave to remove this package! :) Anyway, I downloaded latest release of [GMP]("http://www.swox.com/gmp/"), extracted it and placed it under /usr/local/gmp-4.2.1
I also created a soft link gmp->gmp-4.2.1 under /usr/local/.
Now, in order to install GMP, package m4 is needed, so I opened Synaptic and installed packages m4 and m4-doc. Finally, I did the following (used 3.3 versions, so that I can comply with Synaps) so that I can install latest GMP:
```
cd /usr/local/gmp
sudo ./configure CC=gcc-3.3 CXX=g++-3.3 CPP=cpp-3.3 ABI=64 CPU=amd64 --enable-cxx
sudo make all
sudo make install
sudo make check
``` In order to finalize the installation, I tuned up the system as follows:
```
cd /usr/local/gmp/tune
sudo make tuneup
sudo ./tuneup
``` However, my CPU=amd64 directive was not used :confused: and instead everything was compiled with -mcpu=athlon directive. Apart from that everything else seemed to work perfectly, as the installation passed all tests by 'make check'. Also 'tuneup' didn't give me any trouble.

Getting along, I downloaded and installed [MPFR]("http://www.mpfr.org/mpfr-current/") version 2.2.0 under /usr/local/mpfr-2.2.0 directory with the following:
```
cd /usr/local/mpfr-2.2.0
sudo ./configure CC=gcc-3.3 CXX=g++-3.3 CPP=cpp-3.3 F77=g77-3.4 --with-PACKAGE=yes --with-gmp-include=/usr/local/gmp --with-gmp-lib=/usr/local/gmp/.libs
sudo make
sudo make install
sudo make clean
``` And now proceeded to step 4 above and all installations seemed to work without a problem. Even when compiling a random test program from synaps with the use of s++ no errors were produced. However, the executable could not run due to an unresolved external dependency. I think it was libgmp.so.3 ... I am sorry didn't note it down so that I can remember. Most likely I'll edit this post again to finish this report.

I hope the above can help at least someone!
Regards,
dimis

---

