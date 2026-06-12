---
title: "Is there a tutorial on 32 bit software on 64 bit Ubuntu?"
date: 2009-02-05
forum: x86 64-bit Users
---

### Post by GARoss on 2009-02-05
I've had Ubuntu 8.10 for a couple of days now from Win XP Home & experiencing the trials & tribulations. It took 8 hours yesterday to solve a no sound issue! 
I'm hoping there's a tutorial on using 32 bit software on 64 bit machine. It's a RAW editing program, Bibble Labs 4.10, I purchased for XP that is available in 32 bit Linux. After downloading, the installer said it was incompatible on 64 bit version of Ubuntu.
I've heard it is possible to run 32 on a 64 but really get confused with what ***ia32-libs, A 32-bit chroot & KVM or VirtualBox*** are; do I need one or all?
All suggestions are appreciated.
George

---

### Post by MetalFanLiam on 2009-02-05
You can use the command "linux32 ./<filename goes here>" and it should run 32bit applications on a 64bit machine. Also download getlibs, as this will install the necessary 32bit libraries for the 32bit app. Be sure to change the filename in the command to the installer or the executable.

Say if i wanted to install/run something clled test.bin, on my desktop i would do the following:

cd /path/to/Desktop
sudo chmod 777 test.bin
linux32 ./test.bin

---

### Post by GARoss on 2009-02-05
> **MetalFanLiam said:**
> You can use the command "linux32 ./<filename goes here>" and it should run 32bit applications on a 64bit machine. Also download getlibs, as this will install the necessary 32bit libraries for the 32bit app. Be sure to change the filename in the command to the installer or the executable.

I installed getlibs, then downloaded Bibble software again. It failed to install because it's i386. 
Are you suggesting to install from the Command? The download is in the tmp folder; bibblepro-4.10.1-1.i386.rpm

---

### Post by MetalFanLiam on 2009-02-05
Id suggest using a .deb to install from, instead of a RPM. Id also suggest to find an executable file inted of a packge file, and then you can easily use the linux32 command to install it.

---

### Post by GARoss on 2009-02-05
I downloaded & used the installer for **getlibs**. Is there anything else need to activate it?

I tried extracting bibblepro-4.10.1-1.i386.rpm & failed. Renamed to bibblepro-4.10.1-1.i386.deb & tried again & failed; ***ar: /tmp/bibblepro-4.10.1-1.i386.deb: File format not recognized***. So, how do I find an executable if I'm not able to extract the download?

From Bibble's website I don't see a .deb option, just .rpm. Download options are Archive Manager, Firefox-3.0.5 or other. 
Any suggestions?
George

---

### Post by Yellow Pasque on 2009-02-05
If the only thing available to you is an .rpm, try using a program called alien to convert it to a .deb (alien is available in Synaptic). Then you can install it using dpkg --force-architecture

---

### Post by GARoss on 2009-02-05
> **Temüjin said:**
> If the only thing available to you is an .rpm, try using a program called alien to convert it to a .deb (alien is available in Synaptic). Then you can install it using dpkg --force-architecture
Thanks; installing Alien now. Do I use the Terminal to install it using dpkg --force-architecture? As I said, this is all new to be so please be patient. Thanks.
George

---

### Post by Yellow Pasque on 2009-02-05
First, make a backup copy of the .rpm if you haven't already.

I've never used alien with a 32-bit .rpm on a 64-bit system, but I believe it would work something like this:
<Navigate to the directory where the .rpm is>
```
sudo apt-get install alien rpm
sudo alien --to-deb <name of .rpm file>
sudo dpkg -i --force-architecture <name of .deb you generated in previous step>
```

If that doesn't work, you could also try using rpm directly on your file:
```
sudo rpm -i --ignorearch <name of .rpm>
```

---

### Post by GARoss on 2009-02-05
I ran Alien & now bibblepro-4.10.1-1.i386.rpm has extracted & will open but still says .rpm.
I tried *sudo rpm -i --ignorearch <name of .rpm>* & got the results below:

george@george-desktop:~$  sudo rpm -i --ignorearch bibblepro-4.10.1-1.i386.rpm
error: Failed dependencies:
	/bin/sh is needed by bibblepro-4.10.1-1.i386
	libX11.so.6 is needed by bibblepro-4.10.1-1.i386
	libXcursor.so.1 is needed by bibblepro-4.10.1-1.i386
	libXext.so.6 is needed by bibblepro-4.10.1-1.i386
	libXft.so.2 is needed by bibblepro-4.10.1-1.i386
	libXinerama.so.1 is needed by bibblepro-4.10.1-1.i386
	libXrandr.so.2 is needed by bibblepro-4.10.1-1.i386
	libXrender.so.1 is needed by bibblepro-4.10.1-1.i386
	libc.so.6 is needed by bibblepro-4.10.1-1.i386
	libc.so.6(GLIBC_2.0) is needed by bibblepro-4.10.1-1.i386
	libc.so.6(GLIBC_2.1) is needed by bibblepro-4.10.1-1.i386
	libc.so.6(GLIBC_2.1.2) is needed by bibblepro-4.10.1-1.i386
	libc.so.6(GLIBC_2.1.3) is needed by bibblepro-4.10.1-1.i386
	libc.so.6(GLIBC_2.2) is needed by bibblepro-4.10.1-1.i386
	libc.so.6(GLIBC_2.3) is needed by bibblepro-4.10.1-1.i386
	libdl.so.2 is needed by bibblepro-4.10.1-1.i386
	libdl.so.2(GLIBC_2.0) is needed by bibblepro-4.10.1-1.i386
	libdl.so.2(GLIBC_2.1) is needed by bibblepro-4.10.1-1.i386
	libfontconfig.so.1 is needed by bibblepro-4.10.1-1.i386
	libfreetype.so.6 is needed by bibblepro-4.10.1-1.i386
	libgcc_s.so.1 is needed by bibblepro-4.10.1-1.i386
	libgcc_s.so.1(GCC_3.0) is needed by bibblepro-4.10.1-1.i386
	libgcc_s.so.1(GLIBC_2.0) is needed by bibblepro-4.10.1-1.i386
	libm.so.6 is needed by bibblepro-4.10.1-1.i386
	libm.so.6(GLIBC_2.0) is needed by bibblepro-4.10.1-1.i386
	libm.so.6(GLIBC_2.1) is needed by bibblepro-4.10.1-1.i386
	libm.so.6(GLIBC_2.2) is needed by bibblepro-4.10.1-1.i386
	libpthread.so.0 is needed by bibblepro-4.10.1-1.i386
	libpthread.so.0(GLIBC_2.0) is needed by bibblepro-4.10.1-1.i386
	libpthread.so.0(GLIBC_2.1) is needed by bibblepro-4.10.1-1.i386
	libpthread.so.0(GLIBC_2.2) is needed by bibblepro-4.10.1-1.i386
	libpthread.so.0(GLIBC_2.3.2) is needed by bibblepro-4.10.1-1.i386
	libstdc++.so.5 is needed by bibblepro-4.10.1-1.i386
	libstdc++.so.5(CXXABI_1.2) is needed by bibblepro-4.10.1-1.i386
	libstdc++.so.5(GLIBCPP_3.2) is needed by bibblepro-4.10.1-1.i386
	libstdc++.so.5(GLIBCPP_3.2.2) is needed by bibblepro-4.10.1-1.i386
	libstdc++.so.6 is needed by bibblepro-4.10.1-1.i386
	libstdc++.so.6(CXXABI_1.3) is needed by bibblepro-4.10.1-1.i386
	libstdc++.so.6(GLIBCXX_3.4) is needed by bibblepro-4.10.1-1.i386
george@george-desktop:~$ 

Not clear what to do next. Does it need to be converted to a .deb?

Thanks

---

### Post by jespdj on 2009-02-05
You need to install the 32-bit libraries that the 32-bit software needs. 32-bit software cannot use the 64-bit libraries that are on your system.

First, try to install the package ia32-libs, which contains many of the most common 32-bit libraries:
```
sudo apt-get install ia32-libs
```
For other libraries that are needed, you can use getlibs, or try to find and manually install the missing 32-bit libraries.

---

### Post by GARoss on 2009-02-06
Actually, I did a work-a-round by installing Wine, then installed the Windows version. It worked smoothly; even accepted my product key without a glitch.
Thanks to all! Not only is Linux new to me, so is 64 bit, and when something doesn't work it goes over my head fast.

---

