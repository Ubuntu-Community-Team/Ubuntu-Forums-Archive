---
title: "Ubunto64 and Wine? (newbie)"
date: 2004-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by WakkiTabakki on 2004-10-23
Hello, 
I have just installed Ubuntu 64 and am very happy with the result; stable, smooth and beautiful! And it seems to work, as well!!!
I would like to install Wine, but can't seem to find it anywhere. I have included all the repositories in Synaptics, but when searching on wine, all I get is the documentation (wine-doc).

How do I install wine om ubuntu 64? Is it even possible?

Cheers
N

---

### Post by jdong on 2004-10-24
Ack, one of many reasons I don't run a 64-bit os on my AMD64.

Try pulling a wine off packages.debian.org, see if that'll install via dpkg.

---

### Post by WakkiTabakki on 2004-10-24
Well, I've downloaded the install package off [www.winehq.org](www.winehq.org) ment for Debian, but it tells me that I have the wrong architecture for that one.
Pulling it off packages.debian.org, would that be a different package? 

How exactly do you "pull a package off..."? 
I'm new to ubuntu and debian (been trying out Suse and Mandrake a lot, though).

Cheers 
N

---

### Post by jdong on 2004-10-24
yeah, what I meant was grab that .deb file. Can you force it to install with **dpkg --force-all --install wine-package-whatever.deb**?

Personally I'd recommend you to run 32-bit Ubuntu unless you have a good reason to run 64-bit.

---

### Post by BoyOfDestiny on 2004-10-25
Hi, I'm a newbie as well. I have not yet installed ubuntu amd64 on my opteron. However, I have installed debian 64...and I do believe what you want is possible. I registered on the forum due to the pessemistic reponses. Firstly download the source code release of wine. Usually all you need after that is...uncompress it. then
./configure
make
sudo make install (I think this last line is right with ubuntu)
Also make sure in synaptic you have universe etc, and look for something conatining the word emulation or 32, and find the 32-bit emu libraries. I'm not sure if u need them...since the architecture still has x86 compatibility (I'm a n00b too!).
Anyway best of luck, I do hope it works. I do advise to google debain 64 and wine, as the solution should be similar. Just in case there are any other naysayers...I believe even people on macosx can use WINE, with QEMU (to emulate x86 chip). 

Good luck, and please post how it turns out!

---

### Post by jdong on 2004-10-25
Your commands will compile a **64-bit** version of WINE, which **will NOT emulate 32-bit Windows binaries!**

A quick workaround suggestion I have is to go to Wine's site, grab a Slackware .tgz package, and unpack it to the correct location (usually /, but check the .tgz file!). Not the greatest idea to taint a Deb system with unpackaged files, but it'll work.

---

### Post by BoyOfDestiny on 2004-10-25
Oh well... This sheds some light on it
[http://www.kerneltraffic.org/wine/wn20040625_228_print.html#4](http://www.kerneltraffic.org/wine/wn20040625_228_print.html#4)

As I understand it there is something called checkinstall that can be used to create your own deb. In case there is no make uninstall.

---

### Post by WakkiTabakki on 2004-10-26
Peeuw, this is getting complicated...
Ok, this is what I've done. I got the .deb package off winehq and installed with the --force-all option, and it worked (did the same for libwine and a few other packages that apparently were needed).
In that process I apparently managed to mess up the 'xbase-clients'-package, which Ubuntu promply told me, and offered to fix it and then ACTUALLY did! Wow! Great work Ubunto, I'm really impressed by this distribution (and I've tried a few) =D> 

Anyways, this got the whole shebang installed, but it won't run properly. It tells med that it cant create a display (?), or something like that. Asking me to check the $DISPLAY variable.
I have gotten the idea that this is an unrelated problem, since I get that black window with the green text, saying it's trying to run something and then that it failed. Thus, it seems that wine is actually running, but is configured badly...

Any ideas?

Thanks a bunch for all the input
N

---

### Post by jdong on 2004-10-26
err, you did grab all of WINE's dependency debs,right? (i.e. libwine-*, winesetuptk, etc)

---

### Post by dmatrix on 2004-10-26
I have found normal wine or Cedega/WineX does not work that good on AMD64. Some games will work (not very well) others will refuse to run all together. It sure would be nice if ia32-libs had all the libs to run wine/cedega or possibly if there was a ia32-libs-wine package similar to the openoffice.org ia32-libs package.

Anyways I have found the easiest way to run wine/cedega on AMD64 is with a 32bit chroot. You can find instructions here for Ubuntu. This is a work in progress and will have more information soon.

[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

---

### Post by jdong on 2004-10-26
why use a 64-bit OS just to install a 32-bit OS inside of it? can someone please give me a "practical application" for a 64bit OS?

---

### Post by dmatrix on 2004-10-27
Ya it seems kinda pointless, but since win32 games and applications are 32 bit you need 32bit libs to run them. It would be nice if there was a ia32-libs-wine to put all the right libraries into /usr/lib32 and /usr/X11R6/lib32. Since there is not a packge like this yet the only other way is to build a 32 bit chroot. I still have to run a 32 bit chroot for the Flash plugin on a 32 bit Firefox so adding in libraries for wine/cedega is not a huge deal.

64 bit for me is good for UT2004 with 64bit patches and mencoder. It is too bad there is not more software to take advantage of 64bit today, but I am sure there will be in time.

---

### Post by jdong on 2004-10-30
[QUOTE=dmatrix]but I am sure there will be in time.[/QUOTE]

and *that* will be when I switch to 64-bit!

---

### Post by Samurai on 2004-11-01
well I would love to be able to install and run the 386 version of ubuntu but my computer does not like it much... IE it freezes looking at my folders... let alone all the other problems I can't even find yet(can't keep it running that long).  Only the amd64 version works ...and works flawlessly.  so i guess i'm just sol unless anyone has any ideas on how to make it work ... i guess this would be a good example to use the 64 bit version :p

---

### Post by jdodson on 2004-11-03
[QUOTE=jdong]why use a 64-bit OS just to install a 32-bit OS inside of it? can someone please give me a "practical application" for a 64bit OS?[/QUOTE]

i guess if you want more than 4 gigs of ram.  this is a pretty big deal for servers now that are growing beyond this limitation.   i think games will hit this peak in the new few years as well.  though the switch is going to be painful as vedors will be really slow to put out 32bit and 64bit versions of things.   practicality aside i am going to purchse and AMD64 and i think its cool people are pioneering this processor space as users.  rock on my ubuntu 64 sisters and brothers:mrgreen: 

[wikipedia talks about it here](http://en.wikipedia.org/wiki/64-bit#Memory_Limitations)

---

### Post by Rink on 2004-11-09
Worth remembering that, before the Apple Mac, computers were very specific as to their tasks.

If you needed word processing, you bought a word processor.

Now we expect our 64 bit machine to run, not only the 64 bit software, but everything else as well.

Now, if I can just get wine to run......

---

