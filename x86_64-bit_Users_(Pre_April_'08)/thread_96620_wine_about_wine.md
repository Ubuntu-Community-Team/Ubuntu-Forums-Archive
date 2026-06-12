---
title: "wine about wine"
date: 2005-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by TICK66 on 2005-11-29
I have searched and searched tried setting up repository and it says that wine has been moved or is obsolete. Just cannot seem to get it installed. I even tried the Automatrix thing to install but no luck same error.

---

### Post by Remmelas on 2005-11-29
Latest wine available from this repository, just updated last night.

#wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

add those to your /etc/apt/sources.list and update apt, then you should be able to install wine.

---

### Post by TICK66 on 2005-11-29
Tried this is what i get I guess it is because i am using 64 bit version. Kinda sucks.... I am guessing that there is no problem on the 32 bit install

tick66@leviathon:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
tick66@leviathon:~$

---

### Post by RAOF on 2005-11-29
You can install the 32bit version manually quite easily.  Like so:

1) Download the i386 .deb from [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/)
2) Install various 32bit compatibility libraries:
```
sudo apt-get install ia32-libs*
```
3) Install wine:
```
sudo dpkg -i --force-architecture <thenameofthewinedeb>.deb
```
4) Watch your friends be amazed!

---

### Post by TICK66 on 2005-11-29
Yeah I got stupid and reinstalled the 32 bit version. Been a while since I have been on  
linux. I got to say that I like it. I have a lot of learning to do. Just installed Chix using the same way.  Wine works great. 
Thanks

---

### Post by rossigee on 2005-12-03
[QUOTE=RAOF]4) Watch your friends be amazed![/QUOTE]

I'm still waiting to be amazed myself :)

Got this far (ia32 libs and i386 wine deb installed), but now it don't do much more...

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.

Saw this in another similar (more recent) thread here on ubunuforums. I added the path to the '/usr/lib' from my 32bit partition and ran 'ldconfig', and 'ldd /usr/lib/wine/winex11.drv.so' to check all the deps were satisfied. Great, got past that.

Now, I get:

[email]rossg@localhost:~/.wine[/email]$ wine notepad.exe
/usr/bin/wine-pthread: relocation error: /usr/bin/wine-pthread: symbol wine_pthread_set_functions, version WINE_1.0 not defined in file libwine.so.1 with link time reference

That one was because I had wine installed on my 32bit partition, so winex11.drv.so was finding an older 'libwine' from there instead of the current one from the real /usr/lib. I added /usr/lib above the line for my 32-bit partion in /etc/ld.so.conf, re-run 'ldconfig', and got further.

Now I'm starting to feel amazed! Amazed I managed to finally figure it out ;)

---

### Post by RAOF on 2005-12-04
[QUOTE=rossigee]...I'm still waiting to be amazed myself :)
...[/QUOTE]
Yeah, sorry.  Looks like a more recent wine version broke my howto :(

You should be able to fix that by manually downloading the 32bit libXxf86dga deb from an Ubuntu repository, unpacking it as an archive (**do not install it**), copying the libXxf86dga.so file to your /lib32 directory, and then running ldconfig.

You can try that, and see if it works :)

---

### Post by thenoobest1 on 2005-12-06
[QUOTE=RAOF]
You should be able to fix that by manually downloading the 32bit libXxf86dga deb from an Ubuntu repository, unpacking it as an archive (**do not install it**), copying the libXxf86dga.so file to your /lib32 directory, and then running ldconfig.
[/QUOTE]

uhhhhhh:confused: 

not to hijack the thread or anything but im a noob having a similar problem. any suggestions in lamens terms lol

---

### Post by Josef K. on 2005-12-06
[QUOTE=RAOF]Yeah, sorry.  Looks like a more recent wine version broke my howto :(

You should be able to fix that by manually downloading the 32bit libXxf86dga deb from an Ubuntu repository, unpacking it as an archive (**do not install it**), copying the libXxf86dga.so file to your /lib32 directory, and then running ldconfig.

You can try that, and see if it works :)[/QUOTE]

opening the deb, libXxf86dga.so seems a broken link :confused: 
where this file is supposed to be?

---

### Post by RAOF on 2005-12-06
[QUOTE=Josef K.]opening the deb, libXxf86dga.so seems a broken link :confused: 
where this file is supposed to be?[/QUOTE]
There should be something that isn't a broken link.  Maybe it's called libXxf86dga.so.1 or something.  Whatever lib it is that is not a link, copy that into the /lib32 directory.

---

### Post by redsmoke on 2005-12-06
I am trying to install wine as well using above mention methods i copied the file into the /lib32 folder as suggested and ran ldconfig but I still get this output does anyone have any suggestions:

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
fixme:actctx:CreateActCtxW stub!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

---

### Post by Suger on 2005-12-07
Go to packages.ubuntu.com, get the 32-bits version of libXxf86dga, then do the following :

ar -x libXxf86dga1.deb
tar xvf data.tar.gz
sudo cp usr/lib/* /usr/lib32 [the first one is usr/lib/*, not /usr/lib/*, be careful]
sudo ldconfig
rm -rf usr [not /usr, but don't sudo, you should be ok]
rm -rf data.tar.gz
rm -rf libXxf86dga1.deb

You may have to repeat for another lib, I don't quite remember.

---

### Post by Josef K. on 2005-12-07
I can just see libXxf86dga.a
is this one? should I rename it?

---

### Post by Suger on 2005-12-07
It is the one you find here

[http://packages.ubuntu.com/breezy/libs/libxxf86dga1](http://packages.ubuntu.com/breezy/libs/libxxf86dga1)

Here is a direct link to one of the mirrors

[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_7.0.0-3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_7.0.0-3_i386.deb)

---

### Post by YokoZar on 2005-12-08
There is no 64 bit version of the Wine package because Wine doesn't build in 64 bit yet.  Also, I don't have a 64 bit machine to play with.

Don't do the library hack above, things might start silently breaking.  The only real way to get Wine working properly (and usably) in a 64-bit setup is to do it in a 32-bit chroot environment.  There's a howto for this on the Wiki somewhere, I think.

---

### Post by RAOF on 2005-12-08
What might silently break?  The dynamic linker seems to be smart enough to distinguish between 32 & 64bit libraries, and using that library trick stuff runs in wine for me.  Only some stuff, so I suppose there could be a problem with the library trick, but it's difficult to tell.  So much stuff just doesn't run in wine anyway :)

---

### Post by mesilliac on 2005-12-14
Hey, thanks RAOF for those instructions, I just got wine 0.9.3 working with the ia32-libs. I had to also get the 32bit libXxf86vm.so from:
[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/libxxf86vm1_7.0.0-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/libxxf86vm1_7.0.0-2_i386.deb)

I didn't install ia32-libs*... just ia32-libs (which was already installed).

---

### Post by gil-galad on 2005-12-15
I can't get the wine deb to install for some reason.  

```

#sudo dpkg -i --force-architecture wine_0.9.3-winehq-1_i386.deb

dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 75858 files and directories currently installed.)
Unpacking wine (from wine_0.9.3-winehq-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing wine_0.9.3-winehq-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/wine/user32.dll.so')
Errors were encountered while processing:
 wine_0.9.3-winehq-1_i386.deb
```

---

### Post by gil-galad on 2005-12-15
Er..I think my download was corrupt for some reason.  Trying again.

---

### Post by Josef K. on 2005-12-24
[QUOTE=Suger]Go to packages.ubuntu.com, get the 32-bits version of libXxf86dga, then do the following :
[..]
You may have to repeat for another lib, I don't quite remember.[/QUOTE]

now I got this error :( 

```

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86vm.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86vm.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

---

### Post by gil-galad on 2005-12-24
Now you need to get the 32bit version of libXxf86vm ;)

---

### Post by Randomskk on 2006-01-06
I'm having the same problem.
Wine notepad.exe produces:
```

adam@random:~/Desktop/Downloads$ wine notepad.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86vm.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86vm.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

I followed suger's guide to getting the libXxf86vm package, and I got the 32bit version. 

sudo ldconfig produces:
```
adam@random:~/Desktop/Downloads$ sudo ldconfig
ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link
```

Any idea what's up?

---

### Post by deangl on 2006-01-07
Hi,

This works great and is a lot easier than setting up a chroot for wine.

The library location on ubuntu is:
[http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86dga/](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86dga/)

I did run into an additional error regarding libxxf86vm.  So I did the same download, extract, and copy for that library into /lib32, ran ldconfig, and voila...
[http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/)

Thank you so much!

Dale   :eek:

---

### Post by deangl on 2006-01-07
Is it possible to get xwine working the same way?

I am getting the following errors, but wine seems to be working....

Thanks,
Dale   :-)

> dale@ourmach:~/Desktop$ wine /home/dale/.wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:imm:ImmGetContext (0x10064): stub
fixme:imm:ImmGetContext (0x1007a): stub
fixme:imm:ImmGetContext (0x20032): stub
err:clipboard:CLIPBOARD_CloseClipboard Failed to set clipboard.

---

### Post by Randomskk on 2006-01-07
I've downloaded the file from there (libxxf86dga1_7.0.0-3_i386.deb) and follow the ar -x, tar xf data.tar.gz, sudo cp guide, but when I get to ldconfig:
```

adam@random:~/Desktop/Downloads$ ar -x libxxf86dga1_1.0.0-0ubuntu1_i386.deb
adam@random:~/Desktop/Downloads$ tar xvf data.tar.gz
./
./usr/
./usr/share/
./usr/share/doc/
./usr/share/doc/libxxf86dga1/
./usr/share/doc/libxxf86dga1/copyright
./usr/share/doc/libxxf86dga1/changelog.Debian.gz
./usr/lib/
./usr/lib/libXxf86dga.so.1.0.0
./usr/lib/libXxf86dga.so.1
adam@random:~/Desktop/Downloads$ sudo cp usr/lib/* /usr/lib32
Password:
adam@random:~/Desktop/Downloads$ sudo ldconfig
ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link

adam@random:~/Desktop/Downloads$

```

edit: I noticed I used the 1.0.0-0 file, but the 7.0.0-3 file produces the same results.

---

### Post by deangl on 2006-01-08
[QUOTE=Randomskk]I've downloaded the file from there (libxxf86dga1_7.0.0-3_i386.deb) and follow the ar -x, tar xf data.tar.gz, sudo cp guide, but when I get to ldconfig:
```

adam@random:~/Desktop/Downloads$ ar -x libxxf86dga1_1.0.0-0ubuntu1_i386.deb
adam@random:~/Desktop/Downloads$ tar xvf data.tar.gz
./
./usr/
./usr/share/
./usr/share/doc/
./usr/share/doc/libxxf86dga1/
./usr/share/doc/libxxf86dga1/copyright
./usr/share/doc/libxxf86dga1/changelog.Debian.gz
./usr/lib/
./usr/lib/libXxf86dga.so.1.0.0
./usr/lib/libXxf86dga.so.1
adam@random:~/Desktop/Downloads$ sudo cp usr/lib/* /usr/lib32
Password:
adam@random:~/Desktop/Downloads$ sudo ldconfig
ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link

adam@random:~/Desktop/Downloads$

```

edit: I noticed I used the 1.0.0-0 file, but the 7.0.0-3 file produces the same results.[/QUOTE]


Randomskk,

I am not sure if it is important.  My directory was /lib32.  Also, I didn't copy the symlink file, just the real library file.

FWIW,
Dale   :-)

---

### Post by ewok on 2006-01-12
anyone know whats up with mine? i have done all the things listed... still fubar

ewok@ewok:~/Desktop$ sudo dpkg -i --force-architecture wine_0.9.5-winehq-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 98510 files and directories currently installed.)
Unpacking wine (from wine_0.9.5-winehq-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing wine_0.9.5-winehq-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/wine/gdi32.dll.so')
Errors were encountered while processing:
 wine_0.9.5-winehq-1_i386.deb

whats the deal? 

cheers
tyler

---

### Post by deangl on 2006-01-12
[QUOTE=ewok]anyone know whats up with mine? i have done all the things listed... still fubar

ewok@ewok:~/Desktop$ sudo dpkg -i --force-architecture wine_0.9.5-winehq-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 98510 files and directories currently installed.)
Unpacking wine (from wine_0.9.5-winehq-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing wine_0.9.5-winehq-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/wine/gdi32.dll.so')
Errors were encountered while processing:
 wine_0.9.5-winehq-1_i386.deb

whats the deal? 

cheers
tyler[/QUOTE]
Tyler, 

When I saw that error my download file appeared to be abbreviated/corrupt.  You might confirm size (and maybe md5sum) of your local copy and the original archive site.

FWIW,
Dale   :-)

---

### Post by RAOF on 2006-01-13
[QUOTE=deangl]Tyler, 

When I saw that error my download file appeared to be abbreviated/corrupt.  You might confirm size (and maybe md5sum) of your local copy and the original archive site.

FWIW,
Dale   :-)[/QUOTE]
I've noticed that the wine sourceforge site frequently (as in **almost always**) drops before the download is complete, leaving you with a .deb that won't install.  If you download with something that knows about resuming (like wget), you should end up with a working deb.

---

### Post by jsteve54302 on 2006-01-14
[QUOTE=Suger]Go to packages.ubuntu.com, get the 32-bits version of libXxf86dga, then do the following :

ar -x libXxf86dga1.deb
tar xvf data.tar.gz
sudo cp usr/lib/* /usr/lib32 [the first one is usr/lib/*, not /usr/lib/*, be careful]
sudo ldconfig
rm -rf usr [not /usr, but don't sudo, you should be ok]
rm -rf data.tar.gz
rm -rf libXxf86dga1.deb

You may have to repeat for another lib, I don't quite remember.[/QUOTE]

The other required lib is libXxf86vm.so (wine will let you know by giving the same errors, but with the vm instead of dga, after comleting these intructions).  I finally got wine to work (at least with notepad) with these instructions, and I didn't even have to install 32-bit ubuntu.:D   Now I wonder what my chances of getting DirectX games to run are...

Thanks, everyone...  The only thing I have left to do is get my mp3s ripped in iTunes to play on ubuntus default music player (or re-rip them at a better quality than the rediculous settings iTunes seems bent on and find a nice IDE for Java...

---

### Post by RAOF on 2006-01-14
[QUOTE=jsteve54302]The other required lib is libXxf86vm.so (wine will let you know by giving the same errors, but with the vm instead of dga, after comleting these intructions).  I finally got wine to work (at least with notepad) with these instructions, and I didn't even have to install 32-bit ubuntu.:D   Now I wonder what my chances of getting DirectX games to run are...

Thanks, everyone...  The only thing I have left to do is get my mp3s ripped in iTunes to play on ubuntus default music player (or re-rip them at a better quality than the rediculous settings iTunes seems bent on and find a nice IDE for Java...[/QUOTE]
The packages you're after there are:
gstreamer-plugins
gstreamer-plugins-multiverse
for media playback.  As for a java IDE, there's Eclipse?

---

### Post by jso on 2006-01-17
I followed Suger's instructions for both the ...dba.so.1 and ...vm.so.1 files.  With both, I got errors saying that they weren't symbolic links when I ran ldconfig.  Now, I still can't run winecfg:

```
# winecfg
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

Any suggestions?  Might the symlink error be causing this one?  I'm not sure what to do here.  Thanks.

---

### Post by jso on 2006-01-20
bump

---

### Post by qaqa on 2006-01-21
I've installed wine 0.9.4 and have MS Office running well on that.

Is there any way to integrate wine with konqueror? Clicking on a .xls/.doc/.ppt should open it in winword, excel etc through wine. 
I tried the usual "open with" dialog in konqueror, but the office apps do not seem to understand the path given by konqueror.  (I think the "drives" that wine sees are quite different from the unix paths that konqy gives)

Is there any way to fix this?

---

