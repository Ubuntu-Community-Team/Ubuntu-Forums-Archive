---
title: "Ubuntu 64-bit differences"
date: 2009-04-20
forum: x86 64-bit Users
---

### Post by Mistoffeles on 2009-04-20
I am trying to understand the differences between Ubuntu's 64-bit Linux and other 64-bit Linuxes I have used before. When I go to download Ubuntu 64-bit, the filename says "amd64". When I come to the forums, they are subtitiles "x64 64-bit users: for the discussion of Ubuntu on the AMD 64 platform".

Now I know, and expect you know, that AMD is far from the only source of 64-bit CPUs, indeed you would be hard pressed to find a 32-bit Intel processor new these days. What I don't know is how the naming of Ubuntu works. Is this only for AMD 64-bit processors? Do I have to go elsewhere to get a 64-bit Ubuntu that will run on a Core 2 Duo? There seems to be a schism here as to whether this forum and the associated release is for "AMD 64" processors or "x86 64-bit" processors.

---

### Post by logos34 on 2009-04-20
"amd64" is a misnomer--it runs on Intel x64 desktop (but not server IA64).  

It's probably called that because amd was the first to introduce x64 processor for desktop.

Linux technically refers to it as "x86_64"

---

### Post by rJ~ on 2009-04-20
Well AMD designed the 64 bit instruction set and named it AMD64. Similarly the 32 bit distro is named i386, which is short for intel 386, which was designed by Intel.

---

### Post by Therion on 2009-04-20
> **Mistoffeles said:**
> Do I have to go elsewhere to get a 64-bit Ubuntu that will run on a Core 2 Duo? 
In short no, you don't.  Jaunty 64-bit runs like a scalded cat on my Intel E8400 C2D.  As did Hardy 64-bit.

---

### Post by 3Miro on 2009-04-20
AMD64 is just the name of the standard. It works on both Athlon\Phenom 64-bit and Intel Core 2 Duo as well as some old Pentiums (with EMT64 enabled).

I run AMD64 on both Athlon 64 X2 (desktop) and Core 2 Duo (laptop).

Alphas (IA64) is a different architecture.

---

### Post by logos34 on 2009-04-20
Regardless of how the industry commonly designates the architecture (with the company name that first developed it), why does ubuntu do the same?  It causes a fair amount of confusion.  Why not just "x64" or "x86_64" (which is what uname -a ouputs)?

---

### Post by Slim Odds on 2009-04-20
> **Therion said:**
> ....  Jaunty 64-bit [COLOR=Red]runs like a scalded cat[/COLOR] on my Intel E8400 C2D....

Please, try not to scare the customers away... :D

---

### Post by Yellow Pasque on 2009-04-21
[http://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id250846](http://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id250846)

---

### Post by Jimmyfj on 2009-04-21
The Ubuntu_AMD64 install runs very well on my Intel Core 2 Duo CPU. And has done so for the last five edditions.

---

### Post by FredB on 2009-04-22
AMD64 and EM64T are something like twins technology.

---

### Post by Mistoffeles on 2009-04-22
> **Slim Odds said:**
> Please, try not to scare the customers away... :D

Are you kidding? I would love my 8400 to run like a scalded cat. It certainly doesn't under 64-bit Vista.

How is the nVidia SLI support? I have two 9800 GT's, or GT-something's.

---

