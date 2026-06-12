---
title: "XBMC on Hardy x86_64?"
date: 2008-05-27
forum: x86 64-bit Users
---

### Post by dboot on 2008-05-27
Has anyone had any luck installing XBMC on Hardy 64-bit?

---

### Post by OoooMatron on 2008-05-27
> **dboot said:**
> Has anyone had any luck installing XBMC on Hardy 64-bit?

Nope, I have missing dependencies and cannot compile it. Will keep a keen eye on this thread though. I didn't have the will to spend my entire Sunday trying to get it to work :lolflag:

---

### Post by mad_max0204 on 2008-05-27
There is a xbmc for linux if I'm not mistaken. I think I read it somewhere. I was interested in this some time ago for a media center pc in my living room.

---

### Post by OoooMatron on 2008-05-27
> **mad_max0204 said:**
> There is a xbmc for linux if I'm not mistaken. I think I read it somewhere. I was interested in this some time ago for a media center pc in my living room.

yeah, we've already established that. The question is getting it to run on x64, not if XBMC exists for linux or not :lolflag:

---

### Post by dboot on 2008-05-27
From their [Wiki]("http://xbmc.org/wiki/?title=HOW-TO_compile_XBMC_for_Linux_from_source_code"): > Supported Linux Operating-System installed on a supported computer, currently supported OS are:

    * Ubuntu Desktop Edition 8.04 (Hardy Heron) 32-bit for x86

          o Note that it is also possible to compile and run 32-bit XBMC under 64-bit (AMD64/EMT64) Ubuntu if you run it in a 32bit chroot. 


I'm not sure how to "run in a 32bit chroot." I'm hoping this means it's possible.

---

### Post by mulpac on 2008-05-27
I have not upgraded to Hardy yet, but I recently got XBMC up and running on Gutsy AMD64 by first downloading the deb files (for i386) and installing them with 
dpkg --force-depends --force-architecture -i (name of .deb-file here)
and then get the necessary libraries by
getlibs /usr/share/xbmc/xbmc.bin

I could play some music and watch movies without any tweaking. One annoying thing I noticed so far is that when running it full screen on my TV, it won't allow me to move the mouse to the monitor as I usually can, even when running VDR full screen. Thus, I cannot listen to music with XBMC full screen on the TV and surf on the monitor at the same time.

---

### Post by dboot on 2008-05-27
Where did you find the deb's?

---

### Post by mulpac on 2008-05-27
> **dboot said:**
> Where did you find the deb's?

Packages for Hardy are found here
[http://ppa.launchpad.net/team-xbmc-hardy/ubuntu/dists/hardy/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu/dists/hardy/main/binary-i386/Packages)
and all the .deb files are available on [http://ppa.launchpad.net](http://ppa.launchpad.net)

---

### Post by dboot on 2008-05-27
Ah, thanks! Here's a link to the site: [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu/pool/main/x/xbmc/](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu/pool/main/x/xbmc/).

Which deb did you install? xbmc_2.1a2-hardy2_i386.deb?

---

### Post by mulpac on 2008-05-27
> **dboot said:**
> Ah, thanks! Here's a link to the site: [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu/pool/main/x/xbmc/](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu/pool/main/x/xbmc/).

Which deb did you install? xbmc_2.1a2-hardy2_i386.deb?

xbmc-skin-default
xbmc-scripts
xbmc-common
xbmc_2.1

---

### Post by dboot on 2008-05-28
It installed following your instructions!

I'm having trouble using the feature that I wanted to use: stream backed up movies on an FTP server. Oh, well. This is the first step.

---

### Post by OoooMatron on 2008-05-28
Great stuff. I have a USB adapter for my xbox controller. Does anyone know if it can be made to work with the linux edition? Or is it possible to use the original xbox dvd remote or some generic remote? It would be awesome to start building a small ubuntu based media player and scrap the xbox now.

---

### Post by mulpac on 2008-05-31
I found that the image viewer in XBMC does not work on my AMD64 Gutsy. When running 32-bit Gutsy it works, so it seems the images are handled by XBMC. A little bit strange, since listening to mp3 and watching movies work. I tried uninstalling libsdl1.2 libsdl-gfx1.2 libsdl-image1.2 and ia32-libs and then ran getlibs /usr/share/xbmc/xbmc.bin again and it downloaded a lot of libraries, but then got stuck on libX11.so.6: captury and when running xbmc it says "error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory". In /usr/lib I have
1,1M -rw-r--r-- 1 root root 1,1M 2007-10-05 02:08 /usr/lib/libX11.so.6.2.0
   0 lrwxrwxrwx 1 root root   15 2008-04-08 17:40 /usr/lib/libX11.so.6 -> libX11.so.6.2.0
so I do not know why it says "No such file", but it might be wrong architecture or something like that.
 After letting aptitude install all missing libraries to fulfill the dependencies again, I am back to square one where xbmc works, except image viewer. No previews in the image folders either. Anybody knows what libraries are needed for the image viewer and if there is something I can try to (re)install to get it working?

---

### Post by mulpac on 2008-05-31
I solved it by installing a 32 bit chroot and xbmc works fine now. It seems like getlibs does not work perfectly with xbmc for some reason.

---

### Post by dboot on 2008-06-02
Could you go into detail how you installed xbmc using a 32 bit chroot?

---

### Post by mulpac on 2008-06-02
I read that a 64 bit package is available in [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) which means that a 32 bit chroot might not be necessary to run xbmc anymore. However, when setting up a 32 bit chroot I just followed this guide: [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot) 
Then I added the xbmc repository and installed xbmc with the package manager inside the chroot.

---

