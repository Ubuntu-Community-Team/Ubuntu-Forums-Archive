---
title: "where do I download intel 64bit unbuntu"
date: 2009-01-28
forum: x86 64-bit Users
---

### Post by chipppy on 2009-01-28
Seems like a bit of a silly question but there is logic.

I downloaded the CD image from the download site ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)) after selecting the 64bit version via the Custom options radial button.

I have a brand new system 
Intel E8500 dual core
4GB ram 
500GB and 1000GB HDD
Asus 9400GT silent
Asus P5Q SE/R motherboard
Divco Fusin HDTV dual channel TV card

All working great execpt the TV card but slowly getting that fixed.

I went to install flash player from the adobe site and i get an error saying that I have AMD?

this is strange.  so i looked through the download page and I find that the above takes me to the URL [http://ftp.iinet.net.au/pub/ubuntu-releases/intrepid/ubuntu-8.10-desktop-amd64.iso](http://ftp.iinet.net.au/pub/ubuntu-releases/intrepid/ubuntu-8.10-desktop-amd64.iso).  Note the amd64 here.

So that has lead to my strange question.

Also i have read that it is possible to complier the code somehow for only a specific CPU architecture (eg intel core2).  not knowing much about compiling and the like.  
Is this possible?
Is this worth the work?
Is the easy, medium, hard?

Cheers
chipppy

---

### Post by Tubes6al4v on 2009-01-28
I can't be much of a help as I am running AMD. But I am pretty sure that *buntu 64 will install on both intel and AMD. If you want to install flash, have you tried the version in the ubuntu repositories? There is a sticky about it in the X86_64 bit forum.

---

### Post by sanderj on 2009-01-28
Indeed:

1) AMD64 is for both AMD and Intel X86_64 processors. Apparently that name is getting quite confusing for users.

2) Just use the Ubuntu repositories for installing software. Installing flash that way just works.

HTH

---

### Post by sisco311 on 2009-01-28
> **sanderj said:**
> Indeed:

1) AMD64 is for both AMD and Intel X86_64 processors. Apparently that name is getting quite confusing for users.


+1

2) You can download the new flash 10 alpha from:[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")
([Download 64-bit Plugin for Linux - direct link]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz"))


[list=i]
[*] make sure that you uninstall first any old version of the Flash player.
[*] extract the libflashplayer.so file in the ~/.mozilla/plugins directory(create it if doesn't exist)
[*] restart firefox
[/list]

.mozilla is a hidden directory in your home directory, press Ctrl+H in your file manager to list it.

---

### Post by chipppy on 2009-01-28
Cool that answer that question. A little better labelling of the file name would reduce that confusion.

Now moving onto the second question about is it possible to download the source and compile for an intel only?
Is it worth it?
What are the benifits/risks/losses

Anyone know enough about this stuff to have a look at that one, because I sure dont but it is interesting.

Cheers
chipppy

---

### Post by sanderj on 2009-01-28
> **chipppy said:**
> 
Now moving onto the second question about is it possible to download the source and compile for an intel only?
Is it worth it?


Probably not. If you want to try, try Gentoo Linux ([http://www.gentoo.org/](http://www.gentoo.org/)): Gentoo is meant for self-compiling and tweaking. Good luck.

---

### Post by sisco311 on 2009-01-28
Compile what?

The flash player is closed source. Adobe only provides binary files. So you can not download the code and compile it. This is why is so buggy :). 


You can compile a new kernel and optimize it for your architecture:
[Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158")

[uhelp]community/Kernel[/uhelp]
[uhelp]community/Kernel/Compile[/uhelp]

It's not so easy to optimize it (even for experienced user).

[quote=wiki]
Reasons for compiling a custom kernel[list]
[*]You are a kernel developer. 
[*]You need the kernel compiled in a special way, that the official kernel is not compiled in (for example, with some experimental feature enabled). 
[*]You are attempting to debug a problem in the stock Ubuntu kernel for which you have filed or will file a bug report. 
[*]You have hardware the stock Ubuntu kernel does not support. 
[/list]
Reasons for NOT compiling a custom kernel[list]
[*]You merely need to compile a special driver. For this, you only need to install the linux-headers packages. 
[*]You have no idea what you are doing, and if you break something, you'll need help fixing it. Depending on what you do wrong, you might end up having to reinstall your system from scratch. 
[*]You got to this page by mistake, and checked it out because it looked interesting, but you don't really want to learn a lot about kernels.[/list][/quote]

---

### Post by Thelasko on 2009-01-28
> **sanderj said:**
> AMD64 is for both AMD and Intel X86_64 processors. Apparently that name is getting quite confusing for users.

[I filed a bug report.]("https://bugs.launchpad.net/ubuntu/+bug/322372")

---

### Post by clhsharky on 2009-01-28
Confusing - Yes
Bug - I don't think so

From Wikipedia

> The x86-64 specification was designed by Advanced Micro Devices (AMD), who have since renamed it AMD64. Intel has implemented it under the name Intel 64 (formerly EM64T or IA-32e) in its own x86 processors. The names x86-64 or x64 are often used as vendor-neutral terms to collectively refer to x86-64 processors from any company.

x86-64 should not be confused with the Intel Itanium (formerly IA-64) architecture, which is not compatible on the native instruction set level with the x86 or x86-64 architecture
 
[http://en.wikipedia.org/wiki/X86_64]("http://en.wikipedia.org/wiki/X86_64")

They are one in the same.

---

### Post by Thelasko on 2009-01-28
> **clhsharky said:**
> Confusing - Yes
Bug - I don't think so

From Wikipedia


 
[http://en.wikipedia.org/wiki/X86_64]("http://en.wikipedia.org/wiki/X86_64")

They are one in the same.

Then why isn't the Wikipedia article titled "AMD64"?

I say it's a bug.  It should have never been called that in the first place.

Anywho, here's the [Brainstorm page.]("http://brainstorm.ubuntu.com/idea/17720/")

---

### Post by hyperdude111 on 2009-01-28
Ubuntu referes to all 64 bit as AMD64 i dont know why. Just use the **64bit**flash plugin from adobe or use 
" sudo apt-get install ubuntu-restricted-extras" in terminal and that will install all the codecs for flash, mp3, java, divx.

---

### Post by stchman on 2009-01-28
The AMD64 will work on all 64 bit x86 CPUs.

To install Flash 10 64 bit use my tutorial.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

I run Flash 10 on (3) 64 bit boxes with no problems.

---

### Post by jocko on 2009-01-29
> **Thelasko said:**
> Then why isn't the Wikipedia article titled "AMD64"?

I say it's a bug.  It should have never been called that in the first place.

Anywho, here's the [Brainstorm page.]("http://brainstorm.ubuntu.com/idea/17720/")

Even if the term AMD64 is not wrong, as it refers to the 64 bit architecture that amd specified (to distinguish it from Intel's Itanium 64 bit architecture), it is confusing.
As x86-64 and AMD64 refer to the same architecture, it would probably be much less confusing to use the vendor-neutral term x86-64.
But the simplest thing would be to just put a little text on the download page, explaining that the AMD64 version is for **all** x86 compatible 64bit processors.

---

### Post by novafluxx on 2009-01-29
> **jocko said:**
> Even if the term AMD64 is not wrong, as it refers to the 64 bit architecture that amd specified (to distinguish it from Intel's Itanium 64 bit architecture), it is confusing.
As x86-64 and AMD64 refer to the same architecture, it would probably be much less confusing to use the vendor-neutral term x86-64.
But the simplest thing would be to just put a little text on the download page, explaining that the AMD64 version is for **all** x86 compatible 64bit processors.

Seems logical to me, UNLESS 64bit Ubuntu is ONLY compiled for AMD64 and not universally for all x86_64 chips

---

### Post by jespdj on 2009-01-29
> **Thelasko said:**
> [I filed a bug report.]("https://bugs.launchpad.net/ubuntu/+bug/322372")
And it's set to "Won't fix"... :(

I agree that it should not be named "amd64", because that's too confusing.

By the way, the [download page](http://www.ubuntu.com/getubuntu/download) doesn't mention "amd64".

---

### Post by jfr1tz on 2009-01-29
It's called amd64 since AMD was the first to implement a processor with that specification and got to label it. If you read the Wikipedia you see that the amd64 name is interchangeable for x86-64 and is a general indicator of the architecture, just like i386 or ppc is. Both of which have no direct connection with a specific processor, as there are literally hundreds of processors (VIA chips,Atoms, pentiums etc) that support an i386 architecture.

However there are 64Bit systems that do not support amd64(Itanium, Sparc, etc), so simply calling a distribution 64 bit is not practical as it doesnt provide information about what architecture is supported.

---

### Post by Thelasko on 2009-01-29
> **jfr1tz said:**
> However there are 64Bit systems that do not support amd64(Itanium, Sparc, etc), so simply calling a distribution 64 bit is not practical as it doesnt provide information about what architecture is supported.
Which is why I propose we call it x86-64 and not simply 64-bit.

---

### Post by chipppy on 2009-01-29
WOW!  What i thought was a simple question has turned out to have a really interesting answer.  
Whom ever knew a computer question could be so complicated (hahahaha)

cheers
chipppy

---

### Post by saru411 on 2009-01-30
This is a reoccurring topic that should never have been posted. Please use the search function.

---

