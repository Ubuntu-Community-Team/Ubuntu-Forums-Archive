---
title: "Linux equivilent of window's WOW64?"
date: 2008-07-30
forum: x86 64-bit Users
---

### Post by wtfacoconut on 2008-07-30
Ladies and gentleman, boys and girls of all ages.... 64-bit linx is really beginning to tick me off...God knows that I hold ubuntu/linux near and dear to my heart but the amount of applications (especially very popular ones) available tor linux  x64 platform is (please excuse the exageration.) almost non-existant. Windows 64-bit edition(eww, but livable) seems like the a more logical choice of an OS (aside from mac) for personal non-server, gaming use. granted there's alot of issues with it but still, it has closed a big gap...enough of what seems like ranting and on the the main subject....
Windows has WOW64 ("Windows On Windows-64") to help with the 32-bit interoperability issue. DOes anyone know of a linux equivelent of this or know of a project attempting to do something similar to this? Or maybe I just stupid and and there is something I'm not understanding. For those who don't know what this is, it's supposedly a 32-bit emulator thingy that windows 64-bit has that alows 32-bit programs to run in 64-bit windows by keeping the code seperate. to make a long story, here's an example: (32-bit dll's for 32-bit programs MUST only with other 32-bit applications. 32 and 64-bit code can't mix apperantly. (32-bit mama bear must be sooo disapointed in 64-little bear for not wanting to play with 32-bit jimmy bear. lol. That made no sense)

---

### Post by Jouke74 on 2008-07-30
Check out the IA-32 libraries under synaptic and install them. Subsequently most 32 bit programs will run on your 64 bits Ubuntu. The big question remains : what programs? as many are available through synaptic as well. There are also websites with Linux alternatives for Windows programs.

---

### Post by jocko on 2008-07-30
> **wtfacoconut said:**
> DOes anyone know of a linux equivelent of this or know of a project attempting to do something similar to this? Or maybe I just stupid and and there is something I'm not understanding.You're probably not stupid (at least not for not knowing this) but the package ia32-libs does exactly what you're asking for.

For a more advanced method, [see this thread]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs").

---

### Post by flick on 2008-07-30
@ original poster : I've been running 64 bit Linux, Ubuntu and Arch, for a couple of years now, and the situation regarding applications ported to the 64 bit architecture has only improved. And in my experience, it was never all that bad to begin with. I'm just a casual desktop user, web surfing, music, photo editing, that sort of thing. Not a hardcore gamer, but I've been more than happy with games like Alien Arena and Warsow.

What applications, or category of applications, are you finding so lacking in Ubuntu's 64 bit varieties? I'd be happy to help look for/point you in the right directions if I had a better idea of what you're looking for.

---

### Post by schmitty2005 on 2008-07-30
How about installing a 32-bit Virtual PC with VMware or Qemu?  What 64-bit programs do you use?  The only use I really found for 64 bit is audio/video conversion and compression, and regular file compression.  OH, and photo editing in 64 bit.  Other than that, (which I don't do a lot of), I only have the 64 bit version installed so I can also run a certain Java App in 64 bit. I am trying to delay on buying a new PC for as long as possible.

---

### Post by PC_load_letter on 2008-07-31
> **flick said:**
> ...What applications, or category of applications, are you finding so lacking in Ubuntu's 64 bit varieties? I'd be happy to help look for/point you in the right directions if I had a better idea of what you're looking for.

+1. I am a 64bit only user since Feisty and I have no problems whatsoever finding the apps I need. The only reason I'm still using Windoze is for playing and recording music. I'm tempted to install a 32bit Ubuntu just to see how easy wineasio works.

---

### Post by o.besner on 2008-07-31
Pretty much everything works on 64-bit right now, unless you've got something specific in mind ???

I've been a 64-bit user since the start and except for flash everything on my pc is 64 bit.

---

### Post by wtfacoconut on 2008-07-31
Lol...Ummm I pretty much do a bit of everything that was mentioned above. Not only is flash a BIG MUST but because I work as a computer-tech/network intern at a local Computer store, my 'ace in the sleeve' so has been to use linux/ubuntu to remove malware and other Bull5h17 from customers PC's with out risking the integraty of any other windows pc. all that aside I'm a casual gamer and the bigest thing for me is the full usage of all 8 gigs of ram that I have for everything from multimedi editing, comp servicing, server, Ginny pig'ing (experimenting), to what ever else you can think of except for writing code. one thing that I did find pretty interesting though was, was how the distribution Ulteo has this cool linux VM for windows and how your able to use linux apps almost seamlesly within windows. I havn't installed and tried the IA-32 libraries yet, but it would be kool if there was something as simple as that for my 32-bit issue. Oh well... i'm gonna find out very quick anyways. :guitar:

---

### Post by jocko on 2008-08-01
> **wtfacoconut said:**
> Not only is flash a BIG MUST...

...the distribution Ulteo has this cool linux VM for windows and how your able to use linux apps almost seamlesly within windows.

32 bit flash works very well on 64 bit hardy. Just install the package "flashplugin-nonfree".

And for ulteo... There are several free (some open source, some proprietary) programs that you can run virtual machines in: virtualbox, qemu, vmware, ... No need to specifically use ulteo for that.
In virtualbox (available for linux, windows mac and solaris) you can install any 32 bit pc-compatible os, and at least you can run windows programs seemlessly in linux, I'm not sure about the other way (about the seemless part). The same is true for qemu (but that's a bit harder to learn how to use than virtualbox or vmware).

---

