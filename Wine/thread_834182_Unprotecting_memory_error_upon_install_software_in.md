---
title: "Unprotecting memory error upon install software in Wine"
date: 2008-06-19
forum: Wine
---

### Post by IronArjen on 2008-06-19
I am trying to install "Genedoc" which is kind of a text-editor in Wine. On dapper this used to work but on Hardy I cannot get it running. I get the following error message:

Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.


Anybody any idea? I run a Phenom

---

### Post by xeth_delta on 2008-06-19
> **IronArjen said:**
> I am trying to install "Genedoc" which is kind of a text-editor in Wine. On dapper this used to work but on Hardy I cannot get it running. I get the following error message:

Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.


Anybody any idea? I run a Phenom

My guess would be that the problem has its origin in the fact that the wine version in dapper was a different one. You could try finding out what version it was, download the source code, compile it and install it somewhere in your home directory, so that you don't taint the current version. Then you can run genedoc alone on the older version of wine.

Please let us know should you need any assistance with this.

---

### Post by IronArjen on 2008-06-19
I could not dig out which version I used but do know that genedoc works in 0.9.31. I downloaded it from sourceforge and followed instructions. I first uninstalled the Wine I had installed since the only software I plan to use is genedoc. Then I first tried it the hard way:

./configure
make depend
make
make install

but this went wrong in the configuration. 

configure: error: C compiler cannot create executables
See `config.log' for more details.

the log does NOT show more details (as far as I can see that is):

configure:2486: error: C compiler cannot create executables
See `config.log' for more details.

Obviously I tried the short way but with no more success.
So indeed if you can give me another clue/guidance that will be really appreciated.

---

### Post by xeth_delta on 2008-06-20
> **IronArjen said:**
> I could not dig out which version I used but do know that genedoc works in 0.9.31. I downloaded it from sourceforge and followed instructions. I first uninstalled the Wine I had installed since the only software I plan to use is genedoc. Then I first tried it the hard way:

./configure
make depend
make
make install

but this went wrong in the configuration. 

configure: error: C compiler cannot create executables
See `config.log' for more details.

the log does NOT show more details (as far as I can see that is):

configure:2486: error: C compiler cannot create executables
See `config.log' for more details.

Obviously I tried the short way but with no more success.
So indeed if you can give me another clue/guidance that will be really appreciated.

No problem. You need to install the build-essential package:
```
sudo apt-get install build-essential
```
Then, to compile and install this older version of wine in a different path, so that it does not over-writes the standard one, you can, for instance, install it in your home directory:

```
cd ~
mkdir compiled_progs
```
Go back to the directory containing the wine source code, the one you downloaded:
```
make clean
./configure --prefix=/home/user_name/compiled_progs/
make
make install
```
Where user_name is your user name.

The way you would execute it, since it is not in the bash $PATH environment variable, would be to call it by specifying the path towards it.

You could, by the other hand, just create a link to it:
```
sudo ln -s /home/user_name/compiled_progs/bin/wine /usr/bin/wine-old
```

And now you should be able to run GeneDoc with:
```
wine-old GeneDoc.exe
```
or the real name the GeneDoc executable has.

---

### Post by IronArjen on 2008-06-20
I am afraid that is not it. Although I had uninstalled the current wine version and had installed build-essential (hence it should have worked) I followed the exact procedure you posted.

arjen@Comparative_Genomics:~$ make clean
make: *** No rule to make target `clean'. Stop.

Then trying to cofigure:

arjen@Comparative_Genomics:~/Desktop/Software_downloads/wine-0.9.31$ ./configure --prefix=/home/arjen/compiled_progs/
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


Any idea is appreciated!

---

### Post by xeth_delta on 2008-06-20
> **IronArjen said:**
> I am afraid that is not it. Although I had uninstalled the current wine version and had installed build-essential (hence it should have worked) I followed the exact procedure you posted.

arjen@Comparative_Genomics:~$ make clean
make: *** No rule to make target `clean'. Stop.

Then trying to cofigure:

arjen@Comparative_Genomics:~/Desktop/Software_downloads/wine-0.9.31$ ./configure --prefix=/home/arjen/compiled_progs/
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


Any idea is appreciated!

Hmm, I wonder if you need the kernel headers for this.
```
sudo apt-get install linux-headers-generic
```

In any case, if you have a look at [http://packages.ubuntu.com/search?keywords=wine&searchon=names&suite=dapper&section=all](http://packages.ubuntu.com/search?keywords=wine&searchon=names&suite=dapper&section=all) you will be able to download the wine .deb file for dapper. To install it:

```
sudo dpkg -i package_name
```

[EDIT] Ok, this is the way packages needed to compile wine are installed:
```
sudo apt-get build-dep wine
```
Please notice that the dependencies are installed for the latest version of wine in the repositories, so they might be different versions from the one requested by the older version of wine.

---

### Post by IronArjen on 2008-06-20
I did not quite understand the part on dapper, maybe we are miscommunicating here: I run Hardy Heron.

Maybe we are not since during the make i get the error regarding libXext, so I lack a compatible library here, a dependency. How do I find find out which one. I checked other threads on lxext and people suggest:

apt-get build-dep wine

This I have done.

So two steps forward, the configuration works, the make depend works (I guess this one checks whether the dependencies are there, not whether they are correct?). Two to go?........

---

### Post by xeth_delta on 2008-06-20
> **IronArjen said:**
> I did not quite understand the part on dapper, maybe we are miscommunicating here: I run Hardy Heron.

Maybe we are not since during the make i get the error regarding libXext, so I lack a compatible library here, a dependency. How do I find find out which one. I checked other threads on lxext and people suggest:

apt-get build-dep wine

This I have done.

So two steps forward, the configuration works, the make depend works (I guess this one checks whether the dependencies are there, not whether they are correct?). Two to go?........

Hmm, not sure about the "make depend" thing. I have not used it since I was compiling 2,4 kernel series, years ago.

Now, "make" and "make install". Make the soft-link with "ln -s" and hopefully enjoy! :D

What I meant with the .deb file, is, that you could try installing that old dapper wine version on your Heron machine.

---

### Post by xeth_delta on 2008-06-20
for the missing library:
```
cd /usr/lib
find * | grep libXext
```
post the output

[EDIT] just as an example, in my machine libXext.so is a softlink that points to libXext.so.6.4.0. If libXext.so does not exist, create a soft-link in a similar fashion:

```
ln -s /usr/lib/libXext.so.6.4.0 libXext.so
```

---

### Post by IronArjen on 2008-06-23
find * | grep libXext

libXext.a
libXext.so
libXext.so.6
libXext.so.6.4.0


What I do not 100% understand is how to make the softlink. As I understand it the ln -s command points to the file you indicate. Hence I gave the command in the directory where I do the compilation.  Than again make:

/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [ddraw.dll.so] Error 2
make[2]: Leaving directory `/home/arjen/Desktop/Software_downloads/wine-0.9.31/dlls/ddraw'
make[1]: *** [ddraw] Error 2
make[1]: Leaving directory `/home/arjen/Desktop/Software_downloads/wine-0.9.31/dlls'
make: *** [dlls] Error 2

Either I made the link incorrectly since it still looks in bin/ld or something else is wrong. Then agian I guess I need an older version of the library, put it somewhere where it does not interfere with other processes and make the softlink? Which old library and where to find it?

---

### Post by xeth_delta on 2008-06-23
Wait, that's something I did not notice before:

> /usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext

The problem does not seem to be that there is no "libXext.so", but that the ones the compiler is trying to link against are incompatible with how the program is being compiled.

Something like this can occur when you have different versions of the libraries, for example if you have both the 32 and 64 bit ones.

Are you perchance running Ubuntu under 64 bit?

---

### Post by IronArjen on 2008-07-01
Sorry for the delay. Yes I am.

---

### Post by xeth_delta on 2008-07-02
> **IronArjen said:**
> Sorry for the delay. Yes I am.

Ok, I believe the compiler is picking up the wrong libraries (the ones for 32 bit). I will write again a bit later. There must be an option that can pe passed to the configure script, so that it links with the right libraries.

---

### Post by IronArjen on 2009-09-28
Finally after a year or more I fugured it out and it is really simple. The problem is the install not the software itself. Install the Genedoc in Windooze (keep it in a Directory), copy the directory to .Wine, a doubleclick launches the program.
Rock on............

---

