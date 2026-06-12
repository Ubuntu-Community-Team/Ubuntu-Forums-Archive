---
title: "Can't play encrypted files in amd64"
date: 2009-02-15
forum: x86 64-bit Users
---

### Post by rrofes on 2009-02-15
Hello,
I can't reproduce encrypted dvd files in my amd64 ubuntu 8.10.
I followed all steps in [https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)
and I have all needed packages.
I think that it is not a region related problem (as I've seen in other people's posts) because my problem is with dvd files, not discs. I mean that I can not see .wmv encrypted files.
When play starts it becomes total junk to view on VLC.
On Mplayer-Xine and Totem I receive the notice “The stream is encrypted and decryption is not supported”.
I don't know what else to do, I've been looking for information & trying suggested things for a week. No luck. If someone can help me would be great! Thanks

---

### Post by lensman3 on 2009-02-15
You need to go and find "libdvdcss" tar ball.  Configure it and install it.  This has to do with "Digital Rights Management".  The decryption libary is not installed automatically.  You have to install it yourself.

---

### Post by rrofes on 2009-02-16
Thanks. How do I configure libdvdcss? Could you explain with more detail?

---

### Post by stchman on 2009-02-16
> **rrofes said:**
> Hello,
I can't reproduce encrypted dvd files in my amd64 ubuntu 8.10.
I followed all steps in [https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)
and I have all needed packages.
I think that it is not a region related problem (as I've seen in other people's posts) because my problem is with dvd files, not discs. I mean that I can not see .wmv encrypted files.
When play starts it becomes total junk to view on VLC.
On Mplayer-Xine and Totem I receive the notice “The stream is encrypted and decryption is not supported”.
I don't know what else to do, I've been looking for information & trying suggested things for a week. No luck. If someone can help me would be great! Thanks

Install the Medibuntu repos.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

You will be watching encrypted DVDs in no time.

---

### Post by rrofes on 2009-02-19
Thanks stchman, it did not work, I had all packages in your procedure already installed, anyway I tried it but same result.
lensman3: if you tell me how to configure the package I will try it. 
Any other help?
Thanks!

---

### Post by lensman3 on 2009-02-19
1.  Get the libcss file.  The one I downloaded was "libdvdcss-1.2.10.tar.bz2" and save it in a directory/folder.

2. untar it:  "tar vjxf libdvdcss-1.2.10.tar.bz2".  This will install the source files in a directory called->libdvdcss-1.2.10. 

3. cd to libdvdcss-1.2.10 by entering the  command in a text window: "cd libdvdcss-1.2.10".  In this file is another file called INSTALL.  Go ahead and read it.

4. As root run the command "./configure --prefix=/usr".  It will eventually finish.  If there are any dependencies needed, that is, libraries missing, you will have to stop and install them first.

5.  At the root command prompt, type in "make".  The make program will build the libraries.  If something goes wrong here, it is probably that your are missing the C/C++ or gcc/g++ compilers.  You will have to install these programs.

6.  At the root command type in: "make install".  This will install the libraries in the correct folders.  

7.  This step tells the kernel and the program loaders where to find the css library.  If you reboot this step is required.   At the command prompt type "ldconfig -v".  This setup a file that so that the program loader can/will load the libcss into the system.

8.  Play a dvd and enjoy.  The INSTALL file has all of this info.

---

### Post by stchman on 2009-02-20
> **rrofes said:**
> Thanks stchman, it did not work, I had all packages in your procedure already installed, anyway I tried it but same result.
lensman3: if you tell me how to configure the package I will try it. 
Any other help?
Thanks!

Did you install the libdvdcss2 package from Medibuntu?

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

It works on all my boxes playing encrypted Hollywood DVDs.

---

### Post by lensman3 on 2009-02-20
I googled "libdvdcss" and went to a non-ubuntu site.  I recently had be rebuild mplayer/mencoder from the csv source and looking through the code, the dvdcss had been pulled from the distribution.  Because of that, I have assumed that the only safe source was from the original developers.  DRM and RIAA have been too greedy so I pulled from an off shore host.

---

### Post by Therion on 2009-02-20
Just install the **ubuntu-restricted-extras** package via synaptic.

or:```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by andrew.46 on 2009-02-21
Hi lensman3,

> **lensman3 said:**
> I recently had be rebuild mplayer/mencoder from the csv source and looking through the code, the dvdcss had been pulled from the distribution. 

No it is still there under /libdvdcss in the svn source. If you compile from this source MPlayer will use this internal libdvdcss an the internal libdvdreadread4 to enable dvd reading.

Andrew

---

### Post by rrofes on 2009-02-21
Hi lensman3, thanks for your detailed explanation.
When I do ./configure --prefix=/usr I get following error:
configure: error: cannot find install-sh or install.sh in .auto "."/.auto
Do I have to install some library? Which one?
Another question: I downloaded "libdvdcss-1.2.10.tar.bz2" but I don't know if it is for amd64, or maybe it doesn't matter because I will compile it on my amd64 PC?

To Therion: I already have ubuntu-restricted-extras installed
To stchman: "Did you install the libdvdcss2 package from Medibuntu?" yes I did.
Thanks to all

---

### Post by rrofes on 2009-02-24
I finally managed to compile & install libdvdcss-1.2.10 (following procedure from lensman3), but I get exactly the same result: totem says that decryption is not supported. I really don't understand why I have this problem, it seems it only happens to me.
I don't know what to do, any other ideas?

---

### Post by lensman3 on 2009-02-24
What happens when you do:

"which mplayer"   This will tell you which mplayer program you are really executing.  It should be the new one.   If it is not the new one, find the new one and execute it and see if the problem is fixed.


"ldd /usr/bin/mplayer"   Try this command.  This will list the shared libraries mplayer is bringing in for execution.  If the new copy is in another location than /usr/bin run "ldd" against it.  See if libcss is in the long list of libraries.

To an earlier poster, I noticed my version that I built using csv doesn't have libdvdcss in it.  So you are right, the csv uses the builtin directory, while the rpm's and other tar balls must have the library removed. A duh to me.

---

### Post by rrofes on 2009-02-25
"which mplayer" returns /usr/bin/mplayer
But I don't understand what you mean by "new one". I think that /usr/bin/mplayer is the only one that I have, but not sure 100%
"ldd /usr/bin/mplayer" returns a lot of library names but there is NOT libcss...

---

### Post by rrofes on 2009-02-27
lensman3, any idea about what I explained in my last post?

---

### Post by lensman3 on 2009-02-27
> **rrofes said:**
> "which mplayer" returns /usr/bin/mplayer
But I don't understand what you mean by "new one". I think that /usr/bin/mplayer is the only one that I have, but not sure 100%
"ldd /usr/bin/mplayer" returns a lot of library names but there is NOT libcss...

The "ldd ..." is not using the libdvdcss library so it is using the built in library.

I meant by new one as the recently compiled one.  Do a "find / -name "mplayer" -print" and see if there might be 2 mplayers on your machine.  If there are then try running the second one.  The date on the /usr/bin/mplayer should be the date you compiled it.

Hope this help.  I'm fishing!!!!

---

### Post by rrofes on 2009-02-28
"find / -name "mplayer" -print" returns several occurrences but only one executable, that is dated 26 oct 08.
I should have compiled some mplayer? When? When I installed libdvdcss?

---

