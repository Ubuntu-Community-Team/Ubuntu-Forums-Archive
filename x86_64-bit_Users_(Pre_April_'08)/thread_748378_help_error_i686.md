---
title: "help error i686"
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by jefenet on 2008-04-07
hi, i am installing dictconv, but i have a problem.

root@jefenet-laptop:/home/jefenet/dictconv-0.2# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized
configure: error: /bin/bash ./config.sub i686-pc-linux- failed


how i can to solve it? 

checking build system type... Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized


thnx

---

### Post by kuja on 2008-04-09
I don't know where it would be, but you'd probably want to change "i686-pc-linux" to "i686"

---

### Post by Yellow Pasque on 2008-04-09
Open the config.sub file. Go to line 1172 and change this section:
```
echo Invalid configuration \`$1\': machine \`$basic_machine\' not recognized 1>&2
exit 1
```
--->
```
basic_machine=i686-pc
```

And change the section beginning at line 1373 from:
```
os=`echo $os | sed 's/[^-]*-//'`
echo Invalid configuration \`$1\': system \`$os\' not recognized 1>&2
exit 1
```
--->
```
os=`echo $os | sed -e 's|linux|linux-gnu|'`
```

---

### Post by jefenet on 2008-04-12
i did that but i have the same problem

i'm new in ubuntu and linux sorry...

help me step to step

root@jefenet-laptop:/home/jefenet# ./configure
bash: ./configure: No existe el fichero ó directorio
root@jefenet-laptop:/home/jefenet# cd dictconv-0.2
root@jefenet-laptop:/home/jefenet/dictconv-0.2# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... Invalid configuration `i686-pc-linux-': machine `i686-pc-linux' not recognized
configure: error: /bin/bash ./config.sub i686-pc-linux- failed

---

### Post by jefenet on 2008-04-12
> **Temüjin said:**
> Open the config.sub file. Go to line 1172 and change this section:
```
echo Invalid configuration \`$1\': machine \`$basic_machine\' not recognized 1>&2
exit 1
```
--->
```
basic_machine=i686-pc
```

echo Invalid configuration \`$1\': machine \`$basic_machine\' not recognized 1>&2
		exit 1
		basic_machine=i686-pc
		;;


And change the section beginning at line 1373 from:
```
os=`echo $os | sed 's/[^-]*-//'`
echo Invalid configuration \`$1\': system \`$os\' not recognized 1>&2
exit 1
```
--->
```
os=`echo $os | sed -e 's|linux|linux-gnu|'`
```



# Get rid of the `-' at the beginning of $os.
		os=`echo $os | sed 's/[^-]*-//'`
		echo Invalid configuration \`$1\': system \`$os\' not recognized 1>&2
		exit 1
		os=`echo $os | sed -e 's|linux|linux-gnu|'`
		;;

**is it ok?? i did that and again i did ./configure but i have the same error**

---

