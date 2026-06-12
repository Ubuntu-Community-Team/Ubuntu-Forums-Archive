---
title: "Acroread and AMD64"
date: 2007-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by alanrr_sr on 2007-05-09
Hi

I Am trying run acroread 7.0.9 in my computer, but I get this error:
(acroread:28248): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: wrong ELF class: ELFCLASS64

** ERROR **: file accessible.c: line 550 (spi_accessible_construct): assertion failed: (o)
aborting...
Aborted (core dumped)

if I try to run using linux32 (linux32 acroread), I can not open any document
(acroread:28426): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so: wrong ELF class: ELFCLASS64

I know that the problem is that it is loading 64 bit shared libraries, but how can i solve this in clean way? (I do not want to use i386 :mad: )

Thanks

---

### Post by John Jason Jordan on 2007-05-09
> **alanrr_sr said:**
> I Am trying run acroread 7.0.9 in my computer, but I get this error:
(acroread:28248): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: wrong ELF class: ELFCLASS64
I had exactly the same "ELF class" error message. I can't remember how I solved it and I don't have time right now to go find it, but someone here told me of a particular library that needed to be installed. Search for posts by me a couple months ago and you should find the answer. Sorry, I have an exam Friday. :(

---

### Post by Kilz on 2007-05-10
> **alanrr_sr said:**
> Hi

I Am trying run acroread 7.0.9 in my computer, but I get this error:
(acroread:28248): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: wrong ELF class: ELFCLASS64

** ERROR **: file accessible.c: line 550 (spi_accessible_construct): assertion failed: (o)
aborting...
Aborted (core dumped)

if I try to run using linux32 (linux32 acroread), I can not open any document
(acroread:28426): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so: wrong ELF class: ELFCLASS64

I know that the problem is that it is loading 64 bit shared libraries, but how can i solve this in clean way? (I do not want to use i386 :mad: )

Thanks


When you try and run 32bit applications you need to read the error message when you try and start it in  the terminal. It tells you exactly whats missing.

```
Unable to load image-loading module:/usr/lib/gtk-2.0/2.10.0/loaders/**libpixbufloader-xpm.so**: 
```

That is the 32bit library that is missing. You can then go to the[ Ubuntu package site.]("http://packages.ubuntu.com/") and find out what package to install. Since its a 32bit application you want to look for ia32 packages to see if there is one that containst that library.

---

### Post by Goliath! on 2007-08-23
I have exactly this same problem but I need some help implementing the solution.  When I searched packages.ubuntu.com for libpixbufloader-xpm.so I got:
> You have searched for libpixbufloader-xpm.so in feisty, architecture i386.
Found 4 matching files/directories, displaying files/directories 1 to 4.

FILE                                                       PACKAGE

usr/lib/debug/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so libdevel/libgtk2.0-0-dbg
usr/lib/gdk-pixbuf/loaders/libpixbufloader-xpm.so	    libs/libgdk-pixbuf2 [universe]
usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so	    libs/libgtk2.0-0
usr/lib/vmware-player/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so misc/vmware-player [multiverse]


I used Synaptic to install the package libgdk-pixbuf2 (0.22.0-11).  But I still have the same problem running acroread.

Thanks in advance for any responses.

EDIT:
My bad. I searched on the i386 platform.  When I searched on amd64 I found out the package was ia32-libs-gtk.  But still, I re-installed that from Synaptic and I still have the same error.

---

### Post by Goliath! on 2007-08-25
bump

---

### Post by colo505 on 2007-08-25
You can use Automatix to install Acrobat Reader

---

### Post by Goliath! on 2007-08-25
Automatix is officially considered unsafe because it can screw things up badly.  Search around the forums, you'll find the posts.

Besides, that's how I originally installed acroread :) !!!!

Adobe used to work just fine.  I don't know how I broke it.

---

### Post by meho_r on 2007-08-25
Did you try to reinstall it from medibuntu repository?

---

### Post by John Jason Jordan on 2007-08-25
> **meho_r said:**
> Did you try to reinstall it from medibuntu repository?
The best way I have found to install it is to download the .tar.gz file from:

[http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html)

Then do the following:
tar -xvf AdobeReader_enu-7.0.9-1.i386.tar.gz
cd AdobeReader
./INSTALL

You'll be asked to provide a directory for installation. As far as I know it doesn't matter; I just made one called "Adobe" in my Desktop.

It runs just fine under Feisty amd64, in spite of the fact that it is 32-bit. Fine, that is, except for printing. It is not aware of your printers installed in CUPS. I know a workaround, but I cannot say publicly.

---

### Post by funrider on 2007-08-27
just trying to raise an alternative voice. I always hate adobe reader which takes forever to load up and it is hard to install in ubuntu.

if you've never heard of KPDF, give it a try. It is in the repository. The best thing of this goodie to me is it has "hand tool" function just like adobe, plus it is so much faster and cleaner.

---

### Post by John Jason Jordan on 2007-08-27
> **funrider said:**
> if you've never heard of KPDF, give it a try. It is in the repository. The best thing of this goodie to me is it has "hand tool" function just like adobe, plus it is so much faster and cleaner.
Of course I have heard of kpdf. It is excellent, unless you want to print your PDF file. It uses Ghostscript to print, which makes it slower than the second coming. Not only that, but Ghostscript has bugs here and there. Getting print output that is not what you see on the screen is not cool.

More important, kpdf cannot handle editable PDFs. These days, that is a sine qua non.

If you do any publishing, Adobe Reader is the standard. I don't like that fact, but ignoring it would cost me a fortune.

---

### Post by Cuppa-Chino on 2007-08-27
unfortunately I need acrobat for printing, and now neither manual install nor automatix works, 

what is the best way to purge the system ?

---

### Post by Goliath! on 2007-08-27
I've tried kpdf before since it's in the repositories, and I uninstalled it almost immediately.  Just to make sure it hasn't improved since then, I just installed it again and have already uninstalled it.

Above and beyond all its other failings, the first show-stopper for me was the fact that kpdf won't let you actually select text.  What were they smoking??????????

---

### Post by Goliath! on 2007-08-27
I would still like a response to my original question.  I followed Kilz' solution (his solutions tend to be outstanding):

> **Kilz said:**
> When you try and run 32bit applications you need to read the error message when you try and start it in  the terminal. It tells you exactly whats missing.

```
Unable to load image-loading module:/usr/lib/gtk-2.0/2.10.0/loaders/**libpixbufloader-xpm.so**: 
```

That is the 32bit library that is missing. You can then go to the[ Ubuntu package site.]("http://packages.ubuntu.com/") and find out what package to install. Since its a 32bit application you want to look for ia32 packages to see if there is one that containst that library.

From the Ubuntu package site I found out libpixbufloader-xpm.so is in ia32-libs-gtk, so I used Synaptic to re-install that (it was already installed).  But I still have the exact same error message when I try to start acroread.

Kilz, are you out there?  Any comment - anyone??

---

### Post by Goliath! on 2007-08-27
meho_r, how do I reinstall from medibuntu repository?  What is medibuntu repository?

> **meho_r said:**
> Did you try to reinstall it from medibuntu repository?

---

### Post by meho_r on 2007-08-27
In Medibuntu you can find apps that couldn't be included in Ubuntu because of legal restrictions and stuff. Add medibuntu to your sources.list and you can find acroread in Synaptic. I installed it from there and it's working (but no printer listed, issue with 64-bit) 

You can find instructions here: [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

