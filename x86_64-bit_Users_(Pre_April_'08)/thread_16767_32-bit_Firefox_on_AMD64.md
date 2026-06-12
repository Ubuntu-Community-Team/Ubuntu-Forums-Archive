---
title: "32-bit Firefox on AMD64"
date: 2005-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by benash on 2005-02-23
Hi, I'm running Ubuntu Warty 2.6.8.1-4-amd64-generic kernel.  I'm trying to install the current 32-bit version of Firefox onto my 64-bit machine.  However, the installer gives me the following error:

> error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

Synaptic shows that I have libgtk2.0-0 installed, but I assume I only have the 64-bit version of the library.  Do I need the 32-bit version to get Firefox to install?  If so, how can I get it?

Thanks,
Ben

---

### Post by Gorf on 2005-02-26
This exact same error occurs for me on Thunderbird.  Nothing I can do thus far has managed to make the error go away.  

I am getting tempted to going back to all 32bit.

---

### Post by my64 on 2005-02-28
[QUOTE=benash]Hi, I'm running Ubuntu Warty 2.6.8.1-4-amd64-generic kernel.  I'm trying to install the current 32-bit version of Firefox onto my 64-bit machine.  However, the installer gives me the following error:



Synaptic shows that I have libgtk2.0-0 installed, but I assume I only have the 64-bit version of the library.  Do I need the 32-bit version to get Firefox to install?  If so, how can I get it?

Thanks,
Ben[/QUOTE]

Yes 32 bits executable with 64 bits library will not work. You must either change the place where the program search llnks for the library (LD_LIBRARY_PATH or ld.so.conf), or install a chroot environment  as indicated [here](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Setup_chroot).

I have not tried the first method but it should work provided that you use a script to launch your firefox to  set the LD_LIBRARY_PATH  only temporay.

---

### Post by subterrific on 2005-03-02
The ia32-libs-gtk package gives you that library in 32bit form. Search for ia32 in Synaptic.

---

### Post by artimess on 2005-03-02
I sincerely hope, for those of us not experts, Ubuntu adopts similair way to what Fedora does.  The execution of 32bit and 64 bit programs are transparent and there is no need to do any extra work to get them run.

Ubuntu is a great distribution, but for none experts dealing with such exceptions really defeats the value of Ubuntu.

Please no flames.

---

### Post by Pse on 2005-03-06
Hey, there. Sorry for revivng this thread, but I'm having problems installing the binary 32-bit Firefox package I downloaded from its page. The installer says it's looking for some libraries in /usr/lib. Of course, it can't find them because they are in /usr/lib32 (I've the ia32 packages installed). How can I make the installer look for the libraries in the correct place?
I've tried modifying the installer script, but I'm not good using bash =(

---

### Post by my64 on 2005-03-06
[QUOTE=Pse]Hey, there. Sorry for revivng this thread, but I'm having problems installing the binary 32-bit Firefox package I downloaded from its page. The installer says it's looking for some libraries in /usr/lib. Of course, it can't find them because they are in /usr/lib32 (I've the ia32 packages installed). How can I make the installer look for the libraries in the correct place?
I've tried modifying the installer script, but I'm not good using bash =([/QUOTE]


Try to add a the beginning of your script:
export LD_LIBRARY_PATH=/lib32:/usr/lib32

---

### Post by Pse on 2005-03-06
Thanks, my64, but that doesn't work =(
Here's one of the many lines that show up in a terminal:

```
** (firefox-installer-bin:9165): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
```

That file is in "/usr/lib32", but as you may have noticed, the installer keeps looking for it in "/usr/lib/".

Here's the original code from the script:

```
LD_LIBRARY_PATH=.${LD_LIBRARY_PATH+":$LD_LIBRARY_PATH"}
LIBPATH=.${LIBPATH+":$LIBPATH"}
export LD_LIBRARY_PATH LIBPATH
unset MOZILLA_FIVE_HOME

PATH=.${PATH+":$PATH"}
export PATH

BASEDIR=`dirname $0`
BINNAME=`basename $0`

if [ "$BASEDIR" = "" ]; then
    echo "dirname is not in your PATH"
    ./${BINNAME}-bin $@
else
    cd ${BASEDIR:-.}
    ./${BINNAME}-bin $@
fi
```

I've tried changing the LD_LIBRARY_PATH setting, but it doesn't seem to be working...and as I don't understand sh scripting very well, I still don't get why there are dots and colons there :-k. I'd appreciate any help =)

---

### Post by my64 on 2005-03-07
[QUOTE=Pse]Thanks, my64, but that doesn't work =(
Here's one of the many lines that show up in a terminal:

```
LD_LIBRARY_PATH=.${LD_LIBRARY_PATH+":$LD_LIBRARY_PATH"}
LIBPATH=.${LIBPATH+":$LIBPATH"}
export LD_LIBRARY_PATH LIBPATH
unset MOZILLA_FIVE_HOME

PATH=.${PATH+":$PATH"}
export PATH

BASEDIR=`dirname $0`
BINNAME=`basename $0`

if [ "$BASEDIR" = "" ]; then
    echo "dirname is not in your PATH"
    ./${BINNAME}-bin $@
else
    cd ${BASEDIR:-.}
    ./${BINNAME}-bin $@
fi
```

I've tried changing the LD_LIBRARY_PATH setting, but it doesn't seem to be working...and as I don't understand sh scripting very well, I still don't get why there are dots and colons there :-k. I'd appreciate any help =)[/QUOTE]

Can you please add the line  :
```
echo $LD_LIBRARY_PATH
``` 

just before the
```
 if [ "$BASEDIR" = "" ]; then
``` 
and check that the value is correctly set ?

---

### Post by Pse on 2005-03-07
Thanks, again, my64. Now, this is really strange. I've added the line you mentioned to the original script, and the only thing that appeared was "." (a dot), just before all the failure codes from the binary installer that the script calls. I've echoed myself LD_LIBRARY_PATH on a clean console just to see what was the standard setting in my environment and nothing was displayed (doing "echo $LD_LIBRARY_PATH" showed nothing as a result, only a blank line). As everything has worked fine so far, I guessed that wasn't really a problem. Then I checked ld.so.conf to see what was in it, and to ny surprise this is what I found:
```
/usr/X11R6/lib
/lib32
/usr/lib32
/usr/X11R6/lib32
```

Well, I've already tried every possible combination of paths, and after setting LD_LIBRARY_PATH to everything I could come up with, the installer still couldn't find the pango library it was looking for... So I guess I'm out of luck =(. I'll try to get another browser just for the flash content... Firefox will stay 64-bits ;)

---

### Post by my64 on 2005-03-07
[QUOTE=Pse]Thanks, again, my64. Now, this is really strange. I've added the line you mentioned to the original script, and the only thing that appeared was "." (a dot), just before all the failure codes from the binary installer that the script calls. I've echoed myself LD_LIBRARY_PATH on a clean console just to see what was the standard setting in my environment and nothing was displayed (doing "echo $LD_LIBRARY_PATH" showed nothing as a result, only a blank line). As everything has worked fine so far, I guessed that wasn't really a problem. Then I checked ld.so.conf to see what was in it, and to ny surprise this is what I found:
```
/usr/X11R6/lib
/lib32
/usr/lib32
/usr/X11R6/lib32
```

Well, I've already tried every possible combination of paths, and after setting LD_LIBRARY_PATH to everything I could come up with, the installer still couldn't find the pango library it was looking for... So I guess I'm out of luck =(. I'll try to get another browser just for the flash content... Firefox will stay 64-bits ;)[/QUOTE]

ok, tonight I tried to launch firefox 32 bits from the / of my 64 bits system with the LD_LIBRAY_PATH set and without chroot.  It launches well and works fine.... except the flash media player which does not work. There is no error saying "missing plugin", but just the page where the flash drawing should appear stay blank.
This is bad news. I tried to reinstall manually the flash plugin with no success.
I still don' understand why.

By the way, if you modify the ld.so.conf, you must run ldconfig to take make it work.

To try this, remove the LD_LIBRAY_PATH from your script, just open a terminal and do
```
# export LD_LIBRARY_PATH=/lib32:/usr/lib32
# firefox


``` 

So, for now the solution which work at least for me is by doing a chroot environment.

---

### Post by Pse on 2005-03-07
Well, I've succeeded in installing a i386 binary of Opera...and after messing a bit with the X11 32-bit libraries (/usr/X11/lib32), I've gotten Falsh support ;)
Apparently, Opera needs Motif to make the Flash plugin work, so libXm.so.2 has to be installed. I grabbed the file from a i386 binary of OpenMotif ([http://www.opera.com/download/linux/motif/openmotif-2.1.30-linux-i386.tgz](http://www.opera.com/download/linux/motif/openmotif-2.1.30-linux-i386.tgz)) and installed it in Opera's library path (/opera/lib) since I didn't want to start putting crap in my .../X11/lib32/ directory. Now I've got Flash =) And it works like a charm! I'll use Firefox mostly, but when I really need to see some flash content, I'll just fire up the Opera binary. BTW, Opera's really cool in providing binaries in MANY packages, even statically linked ones! So I just created a folder and extracted the contents of the binary tar.gz, put the Flash plugin in the plugin direcotry, put the missing library in Opera's lib directory, and that's it =).
Thanks anyway, I really want to avoid chrooting to a 32-bit installation.

[EDIT]
I'll try to get a 32-bit Firefox binary to do the same.

---

