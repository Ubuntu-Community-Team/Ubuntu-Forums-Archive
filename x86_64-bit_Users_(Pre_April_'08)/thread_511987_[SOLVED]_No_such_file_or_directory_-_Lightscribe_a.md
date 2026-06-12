---
title: "[SOLVED] No such file or directory - Lightscribe and others"
date: 2007-07-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by MMoudry on 2007-07-28
Hi,
I dunno what I am doing wrong but on my fresh installation of 64-bit Ubuntu Feisty Fawn Server. I have installed 4L lightscribe packages from LaCie (once they were converted from rpm to deb). When I try to execute the software I get this :
```
myuser@myhost:/usr/4L$ ls 4L-*
4L-cli  4L-gui
myuser@myhost:/usr/4L$ ./4L-cli
-bash: ./4L-cli: No such file or directory
```

Here is the ls -l of the two files :
```
myuser@myhost:/usr/4L$ ls -l 4L-*
-rwxr-xr-x 1 root root   60540 2006-08-10 15:20 4L-cli
-rwxr-xr-x 1 root root 6320572 2006-08-10 15:20 4L-gui
```

Here is strace of the executable:
myuser@myhost:/usr/4L$ strace ./4L-cli
```
execve("./4L-cli", ["./4L-cli"], [/* 19 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl(3, F_GETFL)                       = 0x8002 (flags O_RDWR|O_LARGEFILE)
fstat(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 1), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aac33849000
lseek(3, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or di"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0x2aac33849000, 4096)            = 0
exit_group(1)                           = ?
Process 15281 detached
```

Same thing happens when I try to download the Folding@Home client SMP 64 bit:
```
myuser@myhost:~/fah$ wget http://folding.stanford.edu/release/FAH_SMP_Linux.tgz
--22:15:24--  http://folding.stanford.edu/release/FAH_SMP_Linux.tgz
           => `FAH_SMP_Linux.tgz'
Resolving folding.stanford.edu... 171.67.22.50
Connecting to folding.stanford.edu|171.67.22.50|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 138,250 (135K) [application/x-tar]

100%[====================================>] 138,250      128.35K/s

22:15:26 (128.02 KB/s) - `FAH_SMP_Linux.tgz' saved [138250/138250]

myuser@myhost:~/fah$ tar xzf FAH_SMP_Linux.tgz
myuser@myhost:~/fah$ ls -l
total 448
-rwxr-xr-x 1 myuser myuser 249556 2007-06-27 02:23 fah5
-rw-r--r-- 1 myuser myuser 138250 2007-06-27 15:53 FAH_SMP_Linux.tgz
-rwxr-xr-x 1 myuser myuser 68492 2006-11-21 20:19 mpiexec
myuser@myhost:~/fah$ ./fah5
-bash: ./fah5: No such file or directory
```

The Strace :
```
myuser@myhost:~/fah$ strace ./fah5
execve("./fah5", ["./fah5"], [/* 19 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl(3, F_GETFL)                       = 0x8002 (flags O_RDWR|O_LARGEFILE)
fstat(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 1), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2b1b7861a000
lseek(3, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or di"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0x2b1b7861a000, 4096)            = 0
exit_group(1)                           = ?
Process 15286 detached
```

I have no idea what is happening, does the executables execute themselves and then try to load a nonexisting library?


MM

---

### Post by MMoudry on 2007-07-31
Come on guys, is this such a noob question that it's not worth responding to?

---

### Post by Anandavala on 2007-07-31
I'm getting very similar errors too - I'm a linux noob too so I don't know any more about it than you.

I just downloaded euphoria from [http://www.rapideuphoria.com](http://www.rapideuphoria.com) 
The installation instructions say to just put its bin directory in your PATH then load the path variable and then run the executables from the command line.

But instead I get:

$ exu mylib.exu
bash: /home/john/euphoria/bin/exu: No such file or directory

But here it is:

$ ls -l /home/john/euphoria/bin/exu
-rwxr-xr-x 1 john john 338084 2007-06-07 11:43 /home/john/euphoria/bin/exu

I've used euphoria in windoze for years and it's child's play - I've also used numerous unix systems and this should also be child's play on them - but there is something going on here and I've no idea what.

Can someone please help us linux noobs?  I can setup ubuntu on a laptop with all kinds of hacks but now I can't even execute an executable - very puzzling :confused:

---

### Post by Anandavala on 2007-07-31
Could it be that these are 32bit executables and we are trying to run them on 64bit chips?

If so, do we have to compile them ourselves from source?

---

### Post by MMoudry on 2007-07-31
Hi,
I think that some of the i386 compiled executables actually run on x86_64 chips, this is due to the fact that the processors can switch to 32 bit mode on the fly. I got this information from this thread :
[http://ubuntuforums.org/showthread.php?t=191205](http://ubuntuforums.org/showthread.php?t=191205)

```
When switching to a 64-bit operating system, there 
are still programs that are not natively compiled for the AMD64 architecture. 
The first thing you can try, if there is a i386 version available, 
is to force the program to install using the i386 architecture. 
For other architectures this does not work (when you for instance
 try to force to install a SPARC compiled application) but 
luckily the AMD64 architecture is backwards compatible with i386, so
 these 32bit applications should run fine. 
The downside of this is that some calls to libraries might not work and need
 their 32-bit version as well. 
If you omit the 'force architecture' option dpkg will tell you:....

```

However I am completely confused since some people managed to get the 4L to work under x86_64... 3rd page of this post : [http://ubuntuforums.org/showthread.php?t=282313&page=3](http://ubuntuforums.org/showthread.php?t=282313&page=3)

however this was under dapper drake. This could be related to Feisty Fawn server edition or some other detail in our configuration. Can you post your specs ? Maybe we need to install some 32 bit library or something..... what is the strace of your software?

Here is my spec :
Ubuntu Server 7.04 (Feisty Fawn) 64 bit
Asus M2N32 WS
AMD X2 64

---

### Post by kuja on 2007-07-31
If I remember right, it *may* be caused by a 32-bit program trying to load 64-bit libs. (though I usually get ELF errors for that). I read something about this the other day that said this anyhow. I'll try to track down what I read and drop you their solution.

---

### Post by kuja on 2007-07-31
Okay, on my trek across google, I came across [this](http://forum.goteamspeak.com/showthread.php?t=29521). It suggests that installing ia32-libs may fix the problem.

---

### Post by MMoudry on 2007-07-31
OK m8, thanks alot that solved it for me. The solution is to install **ia32-libs** package. You're a life saver :)

MM

---

### Post by j_dog on 2007-07-31
So,     ......are you saying your feisty 64 bit is lightscribe enabled ? I thought I read somewhere that wasn't possible.

   Would you be so kind as to outline the procedure. 

Thanks !

---

### Post by Anandavala on 2007-08-01
Brilliant - it works!        Thanks Kuja. :)

---

### Post by MMoudry on 2007-08-07
Yes it works on feisty fawn 64-bit, without the chroot hack that was used on some previous version. The procedure is exactely same like on 32-bit feisty, you only install the ia32 libraries.

MM

---

### Post by John Jason Jordan on 2007-08-07
> **MMoudry said:**
> Yes it works on feisty fawn 64-bit, without the chroot hack that was used on some previous version. The procedure is exactely same like on 32-bit feisty, you only install the ia32 libraries.
I have two LG Lightscribe DVD drives. They have the Lightscribe logo on them, and all over the literature and the boxes they came in. I have the ia32lib package installed (it has always been installed), and I managed to get the LaCie RPMs converted and installed. I can launch the design window, but when I go to print the program cannot find my Lightscribe enabled drives. The drives work fine otherwise.

This is on a fresh install of Feisty amd64. I found artwork for Ubuntu CDs and I'm anxious to make some Feisty live CDs to give out. Does anyone have any suggestions?

---

### Post by Matakoo on 2007-08-07
> **John Jason Jordan said:**
> 
This is on a fresh install of Feisty amd64. I found artwork for Ubuntu CDs and I'm anxious to make some Feisty live CDs to give out. Does anyone have any suggestions?

Two ideas why it won't work for you:

1. The Lacie program need to be run as root, or it won't print. Open a terminal and try: sudo /usr/4L/4L-gui and see if that helps.

If not, 

2. Did you install both packages? The 4l_1.0-1_i386.deb is the program itself, but you also need lightscribe_1.4.136.1-1_i386.deb, which basically is a set of drivers for Lightscribe drives. Don't remember if the latter can be found on Lacies site (it should) but if not it's available on [http://www.lightscribe.com](http://www.lightscribe.com). A new version was posted there just a few days ago.

Still just in rpm-format so you'll have to convert it first.

---

### Post by John Jason Jordan on 2007-08-07
> **Matakoo said:**
> ... ideas why it won't work for you:
1. The Lacie program need to be run as root, or it won't print. Open a terminal and try: sudo /usr/4L/4L-gui and see if that helps.
Yay! Running it as root worked. Thanks!

And I made my first CD with it! An Ubuntu Feisty CD using artwork I found online.

However, the bad news is that it printed the beautiful color image in black and white. In the GUI it appears as color, it's just that the printing is evidently only black and white. Is there any fix for that?

---

### Post by Matakoo on 2007-08-07
> **John Jason Jordan said:**
> 
However, the bad news is that it printed the beautiful color image in black and white. In the GUI it appears as color, it's just that the printing is evidently only black and white. Is there any fix for that?

Lightscribe is black and white only, or greyscale really. There is, unfortunately, nothing to do about that. Well, there is. Sort of. You can buy discs with a different coating color but that's all that's possible to do. And it still won't look as good as on the screen.

The best option, IMO, to get good-looking labels (and in color) is to buy a photo-printer that can print directly onto special discs. Canon's Pixima 4200 is a good, and not too expensive, choice there.

---

