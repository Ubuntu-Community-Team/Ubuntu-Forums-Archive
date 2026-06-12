---
title: "How to upgrade wxGTK to version2.6.3 ?"
date: 2006-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by ivangotoy on 2006-04-09
basically i have a vague idea of what c++ gtk things  are but they are essential for

compiling aMule client on Ubuntu :)

so i would like to get wxGTK 2.6.3 cause the current version on my pc seems to be wxGTK 2.6.1 

so i downloaded the officialy released sources for that project and some strange 

output come after the ./configure command (the crashing end of it ) :

checking for XML_ParserCreate in -lexpat... yes
checking mspack.h usability... no
checking mspack.h presence... no
checking for mspack.h... no
checking for GTK+ version...
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.

So... i tried to understand what is that gtk+ - i tried to find it in the synaptic 

manager but i have no idea what exactly i am looking for - i feel totally lost

if the newest wxGTK 2.6.3 is availble for Ubuntu it would be enough to know how to 

get it precompiled with apt-get or other way :)

---

### Post by ivangotoy on 2006-04-09
i managed to download the newest gtk+ for ubuntu from the Ubuntu frp resourse 

site - while trying to compile it complained about TIFF loader - and when i tried to 

dpkg the deb packge of tiff-dev  for amd64 - it complained that the version of TIFF i 

have is lower and the installation did not occur - i feel like i am falling in eternal 

dependencies hole

so... if there are new version of the currently installed software on my machine i 

wonder how to make apt-get or the synaptic to REALLY fetch them and install 

automatically

---

### Post by MichaelZ on 2006-04-18
[quote=ivangotoy]i managed to download the newest gtk+ for ubuntu from the Ubuntu frp resourse 

site[/quote] 
Hello,

Could I ask you which is the address of the ftp site?

Thank you very much.

Best wihses,
Michael

---

### Post by ivangotoy on 2006-04-19
now i am using ubuntu breezy amd 64 and i did the following
from synaptic i installed gtk-like packages that have the gtk+ or gtk2 information then i focused on libgtk packages and installed them too 
if u manage to do it the right thing please be sensible enough to UNINSTALL previously install wxGTK 2.* if any of course :)
then you know the compilation procedure for wxGTK 2.6.3 from sources
for libgtk: i advice you to install libtk2 pakcages and *dev ones :)
for gtk : some gtk2 engines if you need them
i use wxGTK for aMule compilation and i want to say i am new to linux in general - a month and a half in linux environment
success

---

### Post by MichaelZ on 2006-04-19
Hello,

Thank you very much for your reply :). wxGTK libraries that come with Ubuntu are a bit old. I hope they will be updated for Dapper.

Anyway, I am relatively new to Linux too. My first experience with it was around 5 years ago with an old RedHat distro. Then a Windows break and since quite 2 months again in Linux (Ubuntu) :).

Best wishes,
Michael

---

### Post by ivangotoy on 2006-04-19
I hope you met no problems getting latest wxGTK to work for you :)

i am having great time compiling aMule every day from cvs and as far as i see most 

of the problematic bugs in older wxGTK are cleared now . I think so because i have 

never met a problem while compiling with wxGTK 2.6.3 :) my aMule feels great with 

them.

Problems may occur if you have wxGTK 2.6.1 (synaptic or apt-get installed) and then 

you compile successfullu wxGTK 2.6.3 - while trying to use wxGTK a bunch of error

 messages pop up telling you of some mistaken libraries and reminding you to 

consider relinking - i have no idea how can you relink libs but the normal way to 

get out of that situation is to have only ONE wxGTK version on your Linux :)

Now i am determined to subdue Skype sound to my will but it won't be easy as i 

see - Skype taking sound only for itself - not fair at all :)

---

### Post by MichaelZ on 2006-04-19
If you use wxGTK 2.6.3 you may would like to install the patches for it :). I think wxGTK 2.6.2 is more reliable, at least for some time.

In my case the problem is that I use Ubuntu wxGTK to build deb Package of [CodeBlocks]("http://www.codeblocks.org") and I do not want to mess up my system or to make the installation of the package too complicate (e.g., installation of wxGTK 2.6.3) :(.

Anyway, building an application from the source is a good opportunity to learn about how it works :).

---

