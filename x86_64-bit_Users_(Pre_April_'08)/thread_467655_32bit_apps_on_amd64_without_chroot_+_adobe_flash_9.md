---
title: "32bit apps on amd64 without chroot + adobe flash 9 on 64bit browsers"
date: 2007-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by maddocks on 2007-06-07
I have been running wine, opera, flash,acroread etc. all without chroot. Simply installed all the ia32* packages plus linux32.NOTE all these apps worked fine using this same install process on both Edgy and Feisty.After installing these packages 32bit binarys should run without any additional help.IE 32bit binary text.bin that wouldnt run before now should start with ./text.bin. To get this to work the packages you just installed created a wrapper which tells all 32bit binarys that the kernel is a x86 386, then all of the 32bit library requests get sent to /lib32 and /usr/lib32. The ia32lib* packages give many of the most common 32bit librarys but not nearly enuff for all the apps I have listed.Unfortunately the only way for sure to get every app working is to run it from the command line when or if it fails it will give the name of the missing library goto packages.ubuntu.com search for it. When you find it open it with Archive Manager then open the data.tar.gz now only extract files found in folders /lib and /usr/lib.Once those extracted copy all of them to /lib32.Now rerun the app if it fails for another library go thru the whole process again.Sum helpfull hints when I first upgraded to Feisty I continued to use my Edgy 32bit librarys and all my 32bit apps ran fine.If your programs run but have blocks or other funny symbols where text should be its your version of ia32-libs-gtk try earlier versions.
     To get adobe's pdf reader going you must edit /usr/bin/acroread goto the end find the line "if [ -f "$ACRO_EXEC_CMD" ] ; then" we need to add a line just after this one so it will look like;
if [ -f "$ACRO_EXEC_CMD" ] ; then
GCONV_PATH=/usr/lib32/gconv LD_PRELOAD=/usr/lib32/libpangohack.so.0.0 GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders32 exec "$ACRO_EXEC_CMD" ${1+"$@"}

Now adobe reader should work. to get 32bit plugins to work on 64bit browsers checkout [http://ubuntuforums.org/showpost.php?p=2072904&postcount=30](http://ubuntuforums.org/showpost.php?p=2072904&postcount=30) which will walk you thru using nppluginwrapper.Ive seen many sites claiming wine will only run via chroot but I run it everyday also nero, netscape beta 9, vmware, and many others.If there is a reason why chroot is "Better" Im willing to listen.Hope this helps someone.

---

### Post by maddocks on 2007-06-07
to get opera's text to appear on the transfers page I had to edit /etc/environment and change LANG="en_US.UTF-8" to LANG=C. and both Firewire and Limewire failed with  the same error cant find display information. So I wrote a script gedit fwire
#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

chmod 755 fwire
cp fwire /bin
this should work for both but only for frostwire on my machine.

---

