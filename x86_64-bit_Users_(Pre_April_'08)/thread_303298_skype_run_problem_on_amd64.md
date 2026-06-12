---
title: "skype run problem on amd64"
date: 2006-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by xss on 2006-11-20
I have installed skype 1.3.0.53-1 on amd64, but when i try to run skype it says.. skype: error while loading shared libraries: libXext.so.6: cannot open shared object file: No such file or directory.
but i have that lib.. in /usr/lib

ldd says:
>   linux-gate.so.1 =>  (0xffffe000)
        librt.so.1 => /lib32/librt.so.1 (0xf7f5a000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7ea5000)
        libqt-mt.so.3 => /usr/lib32/libqt-mt.so.3 (0xf76bb000)
        libXext.so.6 => not found
        libX11.so.6 => not found
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf76a8000)
        libstdc++.so.5 => not found
        libm.so.6 => /lib32/libm.so.6 (0xf7681000)
        libgcc_s.so.1 => not found
        libc.so.6 => /lib32/libc.so.6 (0xf754d000)
        /lib/ld-linux.so.2 (0xf7f6f000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7549000)
        libfontconfig.so.1 => not found
        libaudio.so.2 => not found
        libXt.so.6 => not found
        libjpeg.so.62 => not found
        libpng12.so.0 => not found
        libz.so.1 => not found
        libXi.so.6 => not found
        libXrender.so.1 => not found
        libXrandr.so.2 => not found
        libXcursor.so.1 => not found
        libXinerama.so.1 => not found
        libXft.so.2 => not found
        libfreetype.so.6 => not found
        libXext.so.6 => not found
        libX11.so.6 => not found
        libSM.so.6 => not found
        libICE.so.6 => not found
        libstdc++.so.6 => not found
        libgcc_s.so.1 => not found

Any way to run skype? I have installed all that libs, tryed to reinstall skype

---

### Post by tymek666 on 2006-11-20
Check first sticky post, there's info how to install skype 1.3.

---

### Post by dbw on 2007-01-15
I think tymek666 means [[COLOR="Magenta"]this post[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=77069&highlight=skype+libxcursor").  Though be sure to install the (unmentioned) dependencies:
```
sudo aptitude install linux32 ia32-libs ia32-libs-gtk 
```

---

### Post by mrdean on 2007-01-17
Automatix2 has an option to install Skype 32 bit on amd64 installation. It works for me!

---

### Post by kuja on 2007-01-18
just install all of the ia32-libs packages (yes, you heard me, all of them), it will alleviate this problem, and perhaps other problems as well.

---

### Post by mkgs on 2007-04-27
Installing automatix2 should solve this problem although first time I got 
- ./skype: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

After uninstalling skype and reinstall worked for me.

Fonts and icons are big and the UI is little bit ugly but I don't care as long as it works.

---

### Post by resonantworks on 2007-05-03
I fixed my Skype UI by doing this:
1. Install "qt3-qtconfig" + "qt4-qtconfig".
2. At the command line execute "qtconfig"
3. Choose a decent GUI style and set the default font point size to 8 or 9
4. On the menu File->Save then Exit
5. Restart Skype

(Running Ubuntu Feisty AMD64)

**EDIT**
Btw, if this messes up the rest of your KDE apps, then do the following:
1. Install "kdebase"
2. At the command line execute "kcontrol"
3. Config the GUI in "Appearance & Themes"

---

### Post by Sladi on 2007-05-19
> **mkgs said:**
> Installing automatix2 should solve this problem although first time I got 
- ./skype: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

After uninstalling skype and reinstall worked for me.

I get the same error. I used this howto: [link]("http://ubuntuforums.org/showpost.php?p=2588640&postcount=1")

I don't know how to uninstall Skype. Do I have to do the whole procedure again? 


Regards, 
Sladi

---

### Post by Cappy on 2007-05-19
You should have posted on my guide instead of here.
```
sudo apt-get install lib32asound2
```

And no, you don't have to redo anything.

---

### Post by Sladi on 2007-05-19
Thank you very much Cappy! :KS

It works and it's nice. 


Regards, 
Sladi

---

