---
title: "mistake in folder &quot;/lib32&quot;"
date: 2009-03-22
forum: x86 64-bit Users
---

### Post by ClaudioX on 2009-03-22
Hi,

Im trying install wine 64, and finished make things wrong..

I execute this script in the "/" folder:

```

mkdir -p `pwd`/lib32
ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so
ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so
ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so
ln -s /usr/lib32/libfontconfig.so.1 `pwd`/lib32/libfontconfig.so
ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so
ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so
ln -s /usr/lib32/libXrender.so.1 `pwd`/lib32/libXrender.so
ln -s /usr/lib32/libXinerama.so.1 `pwd`/lib32/libXinerama.so
ln -s /usr/lib32/libXxf86vm.so.1 `pwd`/lib32/libXxf86vm.so
ln -s /usr/lib32/libXi.so.6 `pwd`/lib32/libXi.so
ln -s /usr/lib32/libXrandr.so.2 `pwd`/lib32/libXrandr.so
ln -s /usr/lib32/liblcms.so.1 `pwd`/lib32/liblcms.so
ln -s /usr/lib32/libpng12.so.0 `pwd`/lib32/libpng.so
ln -s /usr/lib32/libcrypto.so.0.9.8 `pwd`/lib32/libcrypto.so
ln -s /usr/lib32/libssl.so.0.9.8 `pwd`/lib32/libssl.so
ln -s /usr/lib32/libxml2.so.2 `pwd`/lib32/libxml2.so
ln -s /usr/lib32/libjpeg.so.62 `pwd`/lib32/libjpeg.so
ln -s /usr/lib32/libXcomposite.so.1 `pwd`/lib32/libXcomposite.so
ln -s /usr/lib32/libcups.so.2 `pwd`/lib32/libcups.so
ln -s /usr/lib32/libXcursor.so.1 `pwd`/lib32/libXcursor.so
ln -s /lib32/libdbus-1.so.3 `pwd`/lib32/libdbus-1.so
ln -s /usr/lib32/libhal.so.1 `pwd`/lib32/libhal.so
ln -s /usr/lib32/libsane.so.1 `pwd`/lib32/libsane.so
ln -s /usr/lib32/libgphoto2.so.2 `pwd`/lib32/libgphoto2.so
ln -s /usr/lib32/libgphoto2_port.so.0 `pwd`/lib32/libgphoto2_port.so
ln -s /usr/lib32/libldap-2.4.so.2 `pwd`/lib32/libldap.so
ln -s /usr/lib32/libldap_r-2.4.so.2 `pwd`/lib32/libldap_r.so
ln -s /usr/lib32/liblber-2.4.so.2 `pwd`/lib32/liblber.so
ln -s /usr/lib32/libxslt.so.1 `pwd`/lib32/libxslt.so
ln -s /usr/lib32/libcapi20.so.3 `pwd`/lib32/libcapi20.so
ln -s /usr/lib32/libjack.so.0 `pwd`/lib32/libjack.so
ln -s /usr/lib32/libodbc.so.1 `pwd`/lib32/libodbc.so
ln -s /usr/lib32/libgnutls.so.26 `pwd`/lib32/libgnutls.so

```

How can i fix that?

Thx a lot!!!

---

### Post by 3Miro on 2009-03-22
Did you install it from the repositories or did you build it from source?

---

### Post by ClaudioX on 2009-03-22
The script i get from [http://wiki.winehq.org/WineOn64bit#head-cd47030932ae0f18400cf837c4cc1a267ab374af]("http://wiki.winehq.org/WineOn64bit#head-cd47030932ae0f18400cf837c4cc1a267ab374af"), the folder lib32 i think is ubuntu default, the wine from [git clone git://source.winehq.org/git/wine.git ~/wine-git]("git clone git://source.winehq.org/git/wine.git ~/wine-git").

In the really, i follow this two tutorial:

1) [http://ubuntuforums.org/showthread.php?t=1034649]("http://ubuntuforums.org/showthread.php?t=1034649")

And when i try make de ./configure i have the error with de lib32, so fix that i try follow the (2) [http://wiki.winehq.org/WineOn64bit#head-cd47030932ae0f18400cf837c4cc1a267ab374af]("http://wiki.winehq.org/WineOn64bit#head-cd47030932ae0f18400cf837c4cc1a267ab374af"), but i do the mistake to run the script in "/" folder, and now the ./configure run without erros, but the 'make' dont do anithing, returning:

```

Makefile:455: aviso: impondo comandos para o alvo `config.status'
Makefile:88: aviso: ignorando comandos antigos para o alvo `config.status'
make[1]: Entrando no diretório `/home/claudio/wine-git/tools'
../tools/makedep -C. -S.. -T.. -I/usr/include/freetype2 fnt2bdf.c fnt2fon.c make_ctests.c makedep.c relpath.c sfnt2fnt.c                   
make[1]: Saindo do diretório `/home/claudio/wine-git/tools'
make[1]: Entrando no diretório `/home/claudio/wine-git/tools'
make[1]: `makedep' está atualizado.
make[1]: Saindo do diretório `/home/claudio/wine-git/tools'
make[1]: Entrando no diretório `/home/claudio/wine-git/libs'
make[1]: *** Sem regra para processar o alvo `configure', necessário por `config.status'.  Pare.
make[1]: Saindo do diretório `/home/claudio/wine-git/libs'
make: ** [libs] Erro 2

```

The output is write in portuguese, if u need i can try traslate to english.

Really thanks for the help!

---

### Post by 3Miro on 2009-03-22
There is Linux (in general) that is 32-bit and 64-bit. There is wine that works under Linux 32-bit and runs 32-bit windows apps, there is wine that works under Linux 64-bit and runs 32-bit windows apps. Both of those could be installed via the repositories (either the standard ones for wine-1.0 or the one that you get from winehq). Then there is a version of wine that runs windows 64-bit apps (I am not sure if it requires a 64-bit Linux). The version of wine for 64-bit windows emulation is experimental and I have no experience with it or whatsoever. You will probably have more luck trying a wine specific forum then the general one here.

I have only been using wine to run 32-bit windows programs (mostly games and couple of chat clients). I have been doing that on both 32 and 64-bit Linux.

The script seems to only create symlinks to a lib32 in the sub-folder where you started the script. Executing in / was a wrong thing to do, it might have overwritten something inside lib32. On the other hand it might have simply rewritten something that was there before. So I don't know of a nice way to fix that, I hope your system isn't running funny after you executed the script.

---

### Post by ClaudioX on 2009-03-22
Thanks for the reply 3Miro,

The system stay ok, but, the "configure" command dont... probably because the overwritten.

I will reinstall the ubuntu and try again. :(

See ya.

So, can you explain to me how to do the help of IntuitiveNipple in this post [http://ubuntuforums.org/showthread.php?p=6078708]("http://ubuntuforums.org/showthread.php?p=6078708")?

I start using the repositories (version 1.0), but the program i try install need the version 1.1+ and put somes fixes, i make that type of install because that.

Thx again!

---

### Post by 3Miro on 2009-03-22
Is the program that you are trying to run a 32 or 64 bit windows program?

If it is a 32-bit windows program, you need to go to winehq and add their repository to your system:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Then it would work normally without the need to recompile. The version wine-1.17 is actually a beta and every couple of weeks you will get a new version and it is possible that the new version breaks what was working with the previous one.

---

