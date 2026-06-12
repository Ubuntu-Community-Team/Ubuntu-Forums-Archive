---
title: "Problems installing Matlab under 64-bit Ubuntu 6.06"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by BaffledMollusc on 2006-06-02
EDIT: I've fixed the problems I describe in this post, but I still have other problems - see post #2.


I've been trying to install Matlab version 7, R14, SP2 on my fresh Ubuntu 6.06 OS. Since I have an dual Opteron based system I'm using the AMD64 version of Dapper.

Now, here's the problem: whatever I do, I can't get matlab to work. So far what I've done is to copy all three CDs to seperate temp directories on my hard drive, naviagate to the /usr/local/matlab directory which contains my license file, and then run the install with the command "sudo sh /home/xxx/tmp/cd1/install".

During the install process I choose to install the "Linux x86-64" version of matlab, and to create symbolic links to matlab in /usr/local/bin. The only errors I get are

*****************************************

    The following messages were written to standard error
    while running 'xsetup' the X Window System version
    of 'install'.

sh: /home/xxx/tmp/matlab/cd3/update/install/backend: Permission denied

-------------------------------------------------------------------
/tmp/9958tmwinstall/update/install/main.sh: line 308: /home/xxx/tmp/matlab/cd1/install: Permission denied
/tmp/9958tmwinstall/update/install/main.sh: line 308: exec: /home/xxx/tmp/matlab/cd1/install: cannot execute: Success
****************************************
As far as I can tell, line 308 is just in some cleanup code to clean out temporary install directories, and while I don't know why I'm getting this error, I don't think it should affect anything. the cd3 backend error goes away if I choose to not install the stuff on cd3, which I don't need anyway, and that doesn't affect the problems I'm about to describe.

Now the problems. The first problem is when I type "matlab" the command is not recognized, and there is no symbolic matlab link in /usr/local/bin or any other plausible directory. If I navigate to what I think is the start script, /user/local/matlab/bin/scripts/matlab and run it with ./matlab I get the following error:

/usr/local/matlab/bin/scripts/.matlab7rc.sh: line 199: /usr/local/matlab/bin/bin/util/arch.sh: No such file or directory

This seems to be because the .matlab7rc script assumes that the directory immediately above it is the base matlab directory, which is false. Hence the double /bin/bin in the path above and the error. If I manually hack the script to fix this, I get other similar cascading errors in other scripts which seem to be confused about where various directories are, and I can't fix them all.

So, to sum up: Has anyone successfully installed matlab R14 on a 64 bit version of Ubuntu 6.06? If so, what exactly did you do?

Failing that, does anyone else have any idea what's going on or what I might be doing wrong?

---

### Post by BaffledMollusc on 2006-06-02
Replying to myself here; probably bad form :) 

I fixed the problems I described above. Contrary to the installation instructions, I needed to run the script install_matlab in the /usr/local/matlab directory after the install was complete.

Now things work a bit better, but matlab still doesn't work. Now the error I get on starting it up is 

*** glibc detected *** malloc(): memory corruption: 0x000000000059b770 ***
Aborted

Sigh. I'm going to try and fix this one too, and if I find a solution I'll post back here. But if anyone else already knows what's going on, please post and save me some trouble!

---

### Post by Fully216 on 2006-08-03
Just and FYI, I get the same error.  I wonder if anyone has yet to find a solution.  After searching and trying a few things, I found none to resolve this issue.

---

### Post by Fully216 on 2006-08-03
To fix the memory corruption error when launching MATLAB on a Linux mahcine, you may do the following.  This bug was fixed in release R14SP3 and affects any previous versions.

The following lines are added at the beginning of the .matlab7rc.sh file:

LD_ASSUME_KERNEL=2.4.1
export LD_ASSUME_KERNEL

This fix was provided by MathWorks tech support, solution number 1-130TXF.  

now I get an different error when I try to start matlab.

error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

There is also an error for /bin/uname, and then it eventaully dies because it could not determine the machine architecture for the host.

I have also tried running the options matlab -glnxa65 without any luck.  Any ideas??

---

### Post by Fully216 on 2006-08-04
Replying to myself ... sigh

I found some more information on the libc.so.6 error by doing a general search.  It appears to be an error with java.  I am not surprised considering matlab is highly integrated with jre, and java is not available for amd64.

If I comment out the fix I added to .matlab7rc.sh (about ASSUME_KERNEL), and the run matlab assuming a 32-bit architecture, it seems to do better.  I installed the linux32 package and ran the command:

linux32 /usr/local/matlab701/bin/matlab.

This gave me a warning that matlab could not locate Java Runtime Environment (JRE).  Well, this is bacause it cannot be installed on my machine, so no surprise there.  I can always fix this by running the tag -nojvm so that java is not enabled.

The next error it gives is the following:

  matlab: No MATLAB executable for this machine architecture.
  /usr/local/matlab701/bin/glnx86/MATLAB does not exist!

This is interesting because I have an amd64 architecture, which the matlab install found when running /usr/local/matlab701/install_matlab.  Hmmm ...

So now to figure out why it is chooses the glnx86 directory instead of glnxa64, where it should be looking.

Anyone have any ideas??

---

### Post by Fully216 on 2006-08-04
So unfortunately adding the -glnxa64 swich just puts me back at a glibc error, which if I got back to the temporary fix, ASSUME_KERNEL, leads me into the same error as before; a seemingly never ending circle.  Arrgg!

---

### Post by Fully216 on 2006-08-07
I still have not figured out how to get MATLAB running ... booo.

As an alternative, I have been looking into octave.  This seems like a good option because it can run all the code that I have already written in MATLAB.

So I checked out the website & wiki for octave, and decided to go ahead and give it a try.  Using synaptic, I was able to install the packages with no problems.  I am able to run octave from the command line without any problems, but the graphical version (koctave), crashes every time.  Occationally I can start the program partially before the crash, while other times it doesn't start at all.  Plotting from the command line also causes a crash.

Has anyone one else experienced the same behavior on amd64 systems?  I wonder if this is because it needs java installed, just as matlab does as well.  I think I might try compiling it from source on my system, to see if that fixes the problem.  I believe you can only use the GNU-c compiler.  In any case, hopefully I will get full functionality from either MATLAB or octave soon!

---

### Post by a-musing amazon on 2006-08-07
Regarding Java. You can get the 64-bit Blackdown Java (j2re1-4). Also the Blackdowen SDK if you need it. I've installed the RJE and it works OK (including the Firefox plugin).

As to the effect of adding
LD_ASSUME_KERNEL=2.4.1
export LD_ASSUME_KERNEL

There was a direction to add this (or a very similar kernel version) as a fix in the googlearth installation (which is 32-bit, and which seg-fault on my PC), with similar results. I must assume it does works on someone else's distribution.

---

### Post by Fully216 on 2006-08-08
Thanks for that info about java.  I was able to install java, which works beautufully!  ;)   For others new to linux like me, I followed a modified version of 

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

As you recommended, I used the blackdown package, obtained from synaptic.  To link the firefox plugins, it was slightly different than the posted directions.

sudo ln -sf /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib/mozilla/plugins/libjavaplugin_oji.so

sudo ln -sf /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so

I had previously installed support for 32-bit applications, easily done however by running the following.

udo apt-get install ia32-libs ia32-libs-gtk linux32

This did not fix the glibc problem, but I do appreciate the help!  At least I have java installed ~ Yea!

---

### Post by qball on 2006-08-08
Thx, I have to try this.. 

I worked around it by using 32bit version.. (and link the binary to trick the cpu detection)

---

### Post by hizaguchi on 2006-08-09
> **Fully216 said:**
> So I checked out the website & wiki for octave, and decided to go ahead and give it a try.  Using synaptic, I was able to install the packages with no problems.  I am able to run octave from the command line without any problems, but the graphical version (koctave), crashes every time.  Occationally I can start the program partially before the crash, while other times it doesn't start at all.  Plotting from the command line also causes a crash.

Has anyone one else experienced the same behavior on amd64 systems?  I wonder if this is because it needs java installed, just as matlab does as well.  I think I might try compiling it from source on my system, to see if that fixes the problem.  I believe you can only use the GNU-c compiler.  In any case, hopefully I will get full functionality from either MATLAB or octave soon!
I never liked koctave.  Kate is a much better Matlab/Octave editor because you can run command line Octave in the built-in Konsole and have everything all in one tidy window.

Oh yeah, and don't forget to install gnuplot so you can make graphs.

---

### Post by dukeleto on 2006-09-19
FWIW, matlab install on amd64 dapper worked flawlessly here: matlab 64bit (7.2 R2006a) works straight off.
Hope you get lucky!

Olivier

---

### Post by daimon00 on 2006-09-25
Tengo la solución:
Adjunto unos post que lo explican. En el primero nos dice que las versiones antiguas de Matlab pueden emular una maquina 32bits y asi no necesitan que matlab soporte 64bits. Lo unico que hay que hacer es meter una intrucción distinta. 
En el segundo post, nos explican como instalar con dicha instrucción y como ejecutarlo. Funciona estupendamente. 

Como estan en ingles, os pongo mi versión de lo que he hecho, a continuación.

NOTA: Si tienes matlab para 64 bits es obvio que funciona sin hacer nada especial.


MI SOLUCION:
1) Crear directorio donde se instalará:

sudo mkdir /usr/local/matlab7  <--- Recomendado

sudo mkdir /opt/matlab7  <--- Otra posibilidad

Nota: No instalar una versión encima de otra!!

2) Copiar el archivo license.dat a ese directorio, si tienes licencia. Si no, creo que te crea una nueva.

cp license.dat /usr/local/matlab7/

3) Montar imagen del CD1:

mount -o loop archivo1.iso /mnt

4) Instalar CD1:

 sudo /mnt/install* -glnx86 -nocp

 Darle a todo que si. Que nos cree los scripts.
 ¡¡¡Cuando pida el CD2 pulsar: Skip CD2!!
 Con el 3 igual. 
 ¡¡¡Solo se puede instalar 1 CD cada vez!!!
 Repetir pasos 3 y 4 para los otros CDs. 

5) Valida la licencia.

6) Matlab instalado. Solo queda una cosa. En la linea de comandos:
	alias matlab='matlab -glnx86' <--- Solución temporal

  First I've to check what shell I'm using
  $ echo $SHELL
  /bin/bash

  I've to edit my .bashrc file with an editor like vim
  vim ~/.bashrc
  Aqui hay un apartado que me dice que cree otro fichero, y lo meta ahí dentro. 

  Now I can add an alias to the file
  alias matlab='matlab -glnx86'

  Then I need to restarted the shell with the source command on the .bashrc file
  source .bashrc

  Así he creado un 'alias' permanente para mi usuario. Me ahorro tener que escribir:
  matlab -glnx86
  y es simplemente : matlab

7) Para ejecutar, escribir en la terminal: matlab



PRIMER POST:
"Subject:

Does MATLAB have 64-bit processor support for the Linux platform?
Problem Description:

I would like to know if MATLAB has 64-bit processor support for the Linux platform.

Solution:

The previous versions of MATLAB, MATLAB 7.0 (R14) and 7.0.4 (R14SP1), provide support for 64-bit Linux machines. These versions run MATLAB in 32-bit emulation mode.

For MATLAB versions 7.0.4 (R14SP2) and later, emulation mode is not supported. You will need to install 64-bit MATLAB for use with a supported 64-bit processor. MATLAB 7.0.4 (R14SP2) and later provide native 64-bit support for the Linux operating system under the AMD Opteron, AMD Athlon 64 and Intel EM64T architectures. For more details, review the system requirements for MATLAB at the following URL:
[http://www.mathworks.com/support/sysreq/index.html?parenttopic=System%20Compatibility](http://www.mathworks.com/support/sysreq/index.html?parenttopic=System%20Compatibility)


SEGUNDO POST:

Subject:

How do I install 32-bit MATLAB 7.0 (R14) on my 64-bit AMD Opteron machine running Linux?
Problem Description:

When running the installation, I run across errors such as:

cp: cannot stat `/devel/Arel/R14n/cdimages/unix/cdrom1/update/bin/glnxa64/*': No
such file or directory
Error writing to /tmp/31122tmwinstall
The installer is unable to copy files to /tmp.
Make sure that /tmp exists, is writable, and has
at least 5 megabytes of available space.

Solution:

In order to install 32-bit MATLAB 7.0 (R14) on 64-bit AMD Opteron machines running Linux, it is necessary to use one of the following workarounds. ELIGE UNA OPCION. LA 2 ES BUENA EN MI CASO:

1) Download the products from our downloads site at the following URL:

[http://www.mathworks.com/web_downloads/](http://www.mathworks.com/web_downloads/)

Once downloaded, start the installation script as follows:


./install -glnx86 




2) If it is necessary to install from CD, run the installer as follows:


./install -glnx86 -nocp

Mi versión :  sudo /mnt/install* -glnx86 -nocp

If installing products from multiple CD's, it will be necessary to stop the installation process after each CD by clicking the "Skip CD X" button (where X is the next CD number). This process will then need to be repeat for each of the CD's.

3) Copy all 3 CD's into a single directory on your local hard drive and then run the installer with the -glnx86 and -nocp flags. Note some files will be overwritten during this process.

Once the installation procedure is complete, the Flexlm License Manager will have to be properly configured. To do this, go to the MATLAB root directory and run the following command:


./install_matlab 4 -glnx86

NOTE: The -glnx86 flag is required for all license manager scripts (lmstart, lmdown, lmstat, etc...) as well as for starting MATLAB.

---

### Post by Fully216 on 2006-09-25
Voy a tener que intentar esto cuando consigo casero. Gracias por el poste maravilloso. Seré seguro le dejo saber va. 

Picosegundo - alegre hablo un poco español.

---

### Post by Relain on 2006-09-26
Just wanted to say that i installed matlab 7.3.0 yesterday with absolutely no problems. The literature that comes with the disks is really good and totally fixed everything, even tells you how to mount a disk :)

---

### Post by Fully216 on 2006-09-26
So I still haven't got around to fixing the installation issues.  With the newest release of matlab, almost all combatibility issues with 64-bit systems have been fixed (especially on amd systems).  

Unfortunately, my copy of matlab is a bit older so it looks like I will have to struggle through fixing it.  It is not a pressing matter for me right now, so all in due time.

Glad you got your copy working; it is good to know that it can be done.  8)

---

### Post by neologisma on 2006-10-15
Does anyone knows where can I find a cracked version for matlab 2006a/b or at least the license.dat file?

---

### Post by Fully216 on 2006-10-16
This is not the place to ask such things.

You can however buy a license via [http://www.mathworks.com/index.html](http://www.mathworks.com/index.html)

---

### Post by ggrecoster on 2006-10-18
Creo que se puede resolver parte del problema copiando los scripts que están la carpet "scripts" a la carpeta "bin".

Saludos

---

### Post by dnight on 2007-04-04
Hey guys

I was experiencing this error installing matlab 7 64 bits (SP1) in edgy:

*** glibc detected *** /usr/local/share/matlab/bin/glnxa64/MATLAB: malloc(): memory corruption: 0x0000000000595140 ***

Tried the assume_kernel thing:

LD_ASSUME_KERNEL=2.4.1
export LD_ASSUME_KERNEL

and got another problem:
/bin/sh: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

then after some research i found a anonymous post somewhere saying this simple trick:
MALLOC_CHECK_=4 matlab

:lolflag: 

it worked!

cheers

---

### Post by weak_solution on 2007-04-12
I have MATLAB 6.5 (r13) student version.  Is it possible to install this on Ubuntu Edgy amd64?

---

### Post by torpedo on 2007-04-23
Hi - I am posting in relation to the first problem that was reported in this thread, about the launcher looking in the wrong directory with /bin/bin etc. I also encountered that problem, and had discovered that one needs to run install_matlab from the $MATLAB directory. However I was then trying to launch Matlab from inside the MATLAB directory, I think it was in $MATLAB/bin/scripts. That's what I had read on some blog (where I had found out that I had to run install_matlab first). Still didn't work, same problem. So after wasting about 3 hours and looking around, I attempted to run it from the matlab file in usr/local/bin, NOT within the MATLAB dir. It worked perfectly, and I have had no problem using Matlab so far.

---

### Post by louisgag on 2007-10-03
installing from the matlab7 directory worked for me on gutsy 64 using this command: sudo /path_to/install -glnx86 -nocp

although java won't work so I am using commandline, which is just as fine since plots work with commandline.

---

### Post by ario on 2008-04-20
> **BaffledMollusc said:**
> Replying to myself here; probably bad form :) 

I fixed the problems I described above. Contrary to the installation instructions, I needed to run the script install_matlab in the /usr/local/matlab directory after the install was complete.

Now things work a bit better, but matlab still doesn't work. Now the error I get on starting it up is 

*** glibc detected *** malloc(): memory corruption: 0x000000000059b770 ***
Aborted

Sigh. I'm going to try and fix this one too, and if I find a solution I'll post back here. But if anyone else already knows what's going on, please post and save me some trouble!

I have had same problems you said. Searched for that and found this page. Thanks you for saying that runnig the holy install_matlab script. It saved me! but now I have no problem any more.
This runs for me. I'm running on Ubuntu 7.10 AMD64.
I say that when i run matlab from a gnome menu shortcut that i have created it myself matlab fails to start with no visible error message. But when running the command "matlab" from a terminal in gnome it runs! I don't know why and what is the different between running a command from gnome main menu and from a terminal:(
By the way: Thank you!

---

### Post by jw5801 on 2008-04-20
> **ario said:**
> I have had same problems you said. Searched for that and found this page. Thanks you for saying that runnig the holy install_matlab script. It saved me! but now I have no problem any more.
This runs for me. I'm running on Ubuntu 7.10 AMD64.
I say that when i run matlab from a gnome menu shortcut that i have created it myself matlab fails to start with no visible error message. But when running the command "matlab" from a terminal in gnome it runs! I don't know why and what is the different between running a command from gnome main menu and from a terminal:(
By the way: Thank you!

To run matlab without having it attached to a terminal you need to use the -desktop switch. So if you alter the command in your menu entry to:
```
matlab -desktop
```
Your menu entry should work!

---

