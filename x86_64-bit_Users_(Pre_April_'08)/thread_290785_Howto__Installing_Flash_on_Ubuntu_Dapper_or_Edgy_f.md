---
title: "Howto : Installing Flash on Ubuntu Dapper or Edgy for x86_64"
date: 2006-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by pvalois on 2006-11-01
_Fetching the prerequisites _

Get the Mandrake nspluginwrapper packages 

[INDENT]
[http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.3-1.x86_64.rpm](http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.3-1.x86_64.rpm)
[http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.3-1.x86_64.rpm](http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.3-1.x86_64.rpm)
[/INDENT]

Get Flash 9 from Adobe

[INDENT]
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
[/INDENT]
Unpack the installer, and locate the **libflashplayer.so** file

_Install the 32 bit wrapper (linux32) and the package conversion tool (alien)_

> 
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32
sudo apt-get install alien


_Proceding with the installation for gnome browsers_

> 
sudo ln -s /usr/lib/nspluginwrapper/x86_64/npconfig /usr/bin/nspluginwrapper
sudo alien -d nspluginwrapper*.rpm 
sudo dpkg -i nspluginwrapper*.deb
sudo mkdir /usr/lib/mozilla/plugins32
sudo cp *{path to}*/libflashplayer.so /usr/lib/mozilla/plugins32
sudo nspluginwrapper -i /usr/lib/mozilla/plugins32/libflashplayer.so


_Making the plugin available for Firefox_

> 
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.so /usr/lib/mozilla-firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/


_WHY ..._
Unless some other tutorials you can read on the net, i made a special directory for the 32 bits plugins, because even if it doesn't make firefox explode, the fact that the 32bits plugin is in a directory checked on **firefox** startup raise and error telling that this plugin can't be loaded.

You can see it by lauching **firefox** from a terminal.

---

### Post by pvalois on 2006-11-01
_Appendix :_ 

For those who don't understant i use a link in the **/usr/lib/mozilla-firefox/plugins** instead of installing the wrapper directly for **Firefox** (some pleople don't use **Epiphany,** and don't care about flash working for it), here is why : 

**nspluginwrapper** force the **nswrapper-libflashplayer.so** to be created in **/usr/lib/mozilla/plugins** when you run "nspluginwrapper -i".

so then, the only way you have left, is linking the new created plugin wrapper to make it available for **Firefox**

---

### Post by Kilz on 2006-11-01
Alternatly you could install the 32bit Firefox, Flock, or Iceweasel by the howto\script in my signature and then just copy in the flash plugin file.

---

### Post by pvalois on 2006-11-01
well in fact, the point is more to get flash working with 64 bits browsers than to simply have flash.

and i made this howto seeing people always asking for some details about how the other succedeed installing it with barefoots.

plus the little "plugin32" detail of course.

---

### Post by Kilz on 2006-11-01
> **pvalois said:**
> well in fact, the point is more to get flash working with 64 bits browsers than to simply have flash.

and i made this howto seeing people always asking for some details about how the other succedeed installing it with barefoots.

plus the little "plugin32" detail of course.

Thats great, I'm glad that someone is working on getting the nspluginwrapper working. From what I have read though, it still is in beta. Is it still crashing the browser on some sites?

---

### Post by pvalois on 2006-11-09
i never crashed badly.
the main problem i encountered is nspluginviewer taking up to 100% cpu, and when i kill it, it became zombie.

as a zombie, he still goes nuts, and i need to terminate the browser to get the zombie leave.

it still happens not that often.

---

### Post by greyghostx on 2006-11-09
This is for flash player on 64bit firefox browser right?

what's this mean

Netscape 4 Plugins Wrapper

    File name: /usr/lib/nspluginwrapper/x86_64/npwrapper.so
    nspluginwrapper 0.9.90.3 adds support for i386 compiled Netscape 4 plugins.
    This is beta software available under the terms of the GNU General Public License.

MIME Type 	Description 	Suffixes 	Enabled
unknown/mime-type 	Do not open 	none 	Yes

---

### Post by forteller on 2006-11-09
Hi, sorry, I'm a totall neewb on Linux, so what am I supposed to do with those two .rpm-files? I get an error when I try to open them in the package manager. Should I just unzip them? where?

---

### Post by gmike on 2006-11-10
i got package not supported error, am i missing something?

---

### Post by balaram on 2006-11-10
I tried the instructions on this post yesterday and I couldn't get it to work either. Then I found this address
http/www.ubuntuforums.org/showthread.php?p=1174435
and I followed the instructions to the letter and  it worked. Be exact; I did it wrong the first time but on the second try I was successful. Read every step, although you probably won't need to do everything they talk about. First time around I overlooked the section about installing the 32-bit version of Firefox onto 64-bit Edgy  and of course it failed to work.

---

### Post by zzarr on 2006-11-14
> **forteller said:**
> Hi, sorry, I'm a totall neewb on Linux, so what am I supposed to do with those two .rpm-files? I get an error when I try to open them in the package manager. Should I just unzip them? where?

Hi!

Run following:

Put the files on the Desktop (~/Desktop).
(putting the files on the desktop is not realy necessary, it's just to make it easyer to explain)

sudo apt-get install alien
sudo alien -d --script Desktop/nspluginwrapper*.x86_64.rpm
sudo dpkg -i Desktop/nspluginwrapper*amd64.deb

Well this is only a near copy of pvalois first post, except for the "--script" flag on alien.

So read the first post, and do as it say.
PST: if you have a wheel-mouse you can mark a line in your browser, focus a terminal and klick on the wheel. And whola! It paste the line in. :)

I'm NOT telling you IT WILL WORK.
I'm just telling you how to make it possibly work.

Well now to my problem.

I have tryed everything, but firefox still complains about the pluggins.

I have even in a desperate try to download the 32 bit .deb package and installed it with "dpkg --force-architecture -i" which didn't seam to do a thing.

I feel there I'm out of bullets, what to do... ahh yes I followed pvalois hint, but it didn't work ether.

I even installed the gpl flash plugin I found in synaptic (can use apt-cache search flash or aptitude to) and works on some pages and some not.

It's a alternative to getting flash work on a 64 bit system.

Greetings Zzarr

---

### Post by xlash on 2006-11-14
Hey guys! 

All the steps are working fine, but my firefox is still not seeing flash plugins. Here are the error message when the plugin is accessed from a web page. Can anybody guide me to resolution? 

Much appreciated! 

```
~/Desktop$ firefox 
/usr/lib/nspluginwrapper/i386/npviewer.bin: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)


```

---

### Post by neighborlee on 2006-11-15
> **xlash said:**
> Hey guys! 

All the steps are working fine, but my firefox is still not seeing flash plugins. Here are the error message when the plugin is accessed from a web page. Can anybody guide me to resolution? 

Much appreciated! 

```
~/Desktop$ firefox 
/usr/lib/nspluginwrapper/i386/npviewer.bin: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)


```

I followed directions to letter as well and no flash working in 64bit firefox..aren't these things tested a bit more before unleashing on unsuspecting users ? ;)

cheers
neighborlee()

---

### Post by neighborlee on 2006-11-15
> **balaram said:**
> I tried the instructions on this post yesterday and I couldn't get it to work either. Then I found this address
http/www.ubuntuforums.org/showthread.php?p=1174435
and I followed the instructions to the letter and  it worked. Be exact; I did it wrong the first time but on the second try I was successful. Read every step, although you probably won't need to do everything they talk about. First time around I overlooked the section about installing the 32-bit version of Firefox onto 64-bit Edgy  and of course it failed to work.

your link isnt working do you recall it  ?

cheers
neighborlee()

---

### Post by Kilz on 2006-11-15
> **neighborlee said:**
> your link isnt working do you recall it  ?

cheers
neighborlee()

The url is missing a :/ after http. I just checked and its to my howto for 32bit firefox. Here is a working url.

[http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435)

---

### Post by artik on 2006-11-17
Hello I've tryed to install flash according to this instructions.

(Actually I need Flash for Epihpany, I don't use Firefox because of keyboard shortcuts issue with non-latin layout - so installation of 32 bit version will not help).

I've got the following error message and no flash (for firefox and epiphany):

Cant execute: /usr/lib/nspluginwrapper/i386/npviewer.bin:  No such file or directory

I've tryed for both Flash 7 and 9.
I must admit that 
$ file /usr/lib/nspluginwrapper/i386/npviewer.bin
tells that it is 32bit shared object and not executable.

Can anybody tell the exact instructions to run Flash 7 or 9 with nsplugingwarpper on Epiphany?

---

### Post by tall-male on 2006-11-17
I don't get the hassle with nspluginwrapper, chrooted firefox and whatever. ](*,)  I'm running Ubuntu Edgy AMD64 on a Intel Core 2 Duo. I'm able to run Firefox 32 bit, Flash 9 WITH sound, Java out of the box. It turned out to be very simple:

- Install Firefox from [www.mozilla.com](www.mozilla.com) in /opt/firefox.
- Download Flash 7 and put al the file in /opt/flash
- Download Flash 9 beta, put the files also in /opt/flash
- In ~/.mozilla/plugins I made symbolic links:

[SIZE="1"]lrwxrwxrwx 1 ubu ubu     26 2006-10-30 14:15 flashplayer.xpt -> /opt/flash/flashplayer.xpt
lrwxrwxrwx 1 ubu ubu  28 2006-10-30 14:15 libflashplayer.so -> /opt/flash/libflashplayer.so[/SIZE]

- In installed alsa-oss AND, important, **lib32asound2**. You need the 32 bit libraries in order to get sound with 32 bit Flash. Believe it or not: Flash 9 just works, with sound, no hassle...! :mrgreen: 

The same I did for Java. Download Java 32 bit from [www.java.com](www.java.com) and install in /opt/java32. In ~/.mozilla/plugins create a symbolic link:
[SIZE="1"]lrwxrwxrwx 1 ubu ubu      60 2006-10-28 15:28 libjavaplugin_oji.so -> /opt/java32/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so[/SIZE]

Java runs perfectly as well; tested it at [http://java.com/en/download/help/testvm.xml](http://java.com/en/download/help/testvm.xml) :-D

---

### Post by artik on 2006-11-19
If I wanted to use Firefox I would not ask.
I need **Epiphany**. Why? Keyboard shortcuts do not work under non-latin keyboard layout in firefox.

So firefox is really not an option!

---

### Post by artik on 2006-11-19
Ok the solution was much simpler then I thought

Edgy comes without ia32 libraries - so acatually I couldn't run any 32bit application. After I had installed then
```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32
```
All works perfectly well.
I had installed Flash 9 using latest rpms - 0.9.90.4 and flash works well in both FF and Epipany including sound and video in YouTube.

---

### Post by transgress on 2006-11-22
i get the following error


(npviewer.bin:9703): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
*** NSPlugin Viewer  *** ERROR: -info: cannot open shared object file: No such file or directory

---

### Post by holy_bazooka on 2006-11-22
i get this error.


```
LoadPlugin: failed to initialize shared library /usr/local/firefox32/plugins/libnullplugin.so [/usr/local/firefox32/plugins/libnullplugin.so: wrong ELF class: ELFCLASS32]

```

i am on edgy and using flash 9 beta.

---

### Post by guduri on 2006-11-26
> **transgress said:**
> i get the following error


(npviewer.bin:9703): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
*** NSPlugin Viewer  *** ERROR: -info: cannot open shared object file: No such file or directory

I had the same error and I got around it by getting the latest nspluginwrapper from [http://gwenole.beauchesne.info/en/projects/nspluginwrapper](http://gwenole.beauchesne.info/en/projects/nspluginwrapper)

Only thing is, I still see the locale message and some other WARNINGS but flash works in the browser.

---

### Post by stranger1121 on 2006-12-03
(npviewer.bin:8027): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
*** NSPlugin Viewer  *** ERROR: -info: cannot open shared object file: No such file or directory

:-?

---

### Post by nbppp2 on 2007-01-02
When I try to follow the steps here, when I try to install ia32-libs-gtk this is what I get

:~/Desktop$ sudo dpkg -i ia32-libs-gtk_1.0_amd64.deb 

Selecting previously deselected package ia32-libs-gtk.
(Reading database ... 88190 files and directories currently installed.)
Unpacking ia32-libs-gtk (from ia32-libs-gtk_1.0_amd64.deb) ...
dpkg: dependency problems prevent configuration of ia32-libs-gtk:
 ia32-libs-gtk depends on ia32-libs (>= 1.18); however:
  Version of ia32-libs on system is 1.5ubuntu5.
dpkg: error processing ia32-libs-gtk (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ia32-libs-gtk
 
What can I do to resolve this and get flash working for amd64 edgy?

Thanks

---

### Post by Malithorne on 2007-01-09
> **pvalois said:**
> well in fact, the point is more to get flash working with 64 bits browsers than to simply have flash.

Thank you! For the benefit of those who may not figure out the adjustments needed, I got it working on mine after updating the nspluginwrapper from:
[The nspluginwrapper Site...]("http://gwenole.beauchesne.info/en/projects/nspluginwrapper#documentation")

Then re-issuing the commands again to convert and install them:
sudo alien -d nspluginwrapper*.rpm
sudo dpkg -i nspluginwrapper*.deb

And finally re-installing the Flashplayer plugin:
sudo nspluginwrapper -i /usr/lib/mozilla/plugins32/libflashplayer.so

Still am seeing some errors but everything seems to work so far. After uninstalling a Ubuntu 6.06 installation where I had a nice 32-bit chroot to do the same, I was bummed when the same did not apply to edgy cleanly. This is an acceptable workaround. If I wanted to back out of the nspluginwrapper configuration, is it just a matter of removing the plugin32 directory from Firefox?

---

### Post by xelra on 2007-01-14
I did this on a fresh install of Edgy. For the npviewer.bin to be executed you need the following:

sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32

Else nspluginwrapper will give you an error, that npviewer.bin cannot be executed.

Regards

Xel'Ra

---

### Post by joepotter on 2007-01-15
> **pvalois said:**
> well in fact, the point is more to get flash working with 64 bits browsers than to simply have flash.

and i made this howto seeing people always asking for some details about how the other succedeed installing it with barefoots.

plus the little "plugin32" detail of course.


Thanks for the how-to. 

I am using Feisty (64 bit) and it works fine here. I also note that opening many tabs at once is a lot faster on 64 bit Firefox. So much faster that it is worth the effort to do flash this way.

---

### Post by prince_niceguy on 2007-01-16
Works great my lappy.... am using edgy on my inspiron core2duo...

thanks OP...

---

### Post by Nite23 on 2007-01-21
thanks for the guide...
it seems to work for me so far, but i get these warnings on every new instance of flash:
> Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(npviewer.bin:20094): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so: wrong ELF class: ELFCLASS64

(npviewer.bin:20094): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed


---

### Post by nlogax on 2007-01-27
I have just installed this and it works very well (although it does cause Epiphany to freeze, necessitating 'sudo pkill npviewer.bin' to restore it).

I have amended the instructions slightly, as follows:

1. Linked to newer versions of nspluginwrapper
2. Removed creation of the symbolic link to /usr/bin/nspluginwrapper as it already existed after I installed the .debs
3. added instructions to make it work on Epiphany.


**Fetching the prerequisites**

_1.  Get the Mandrake nspluginwrapper packages (both are required)_

   [nspluginwrapper plugin]("http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.2-1.x86_64.rpm")
  [nspluginwrapper viewer]("http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm")


_2.  Get Flash 9 from Adobe_

  [Download Flashplayer installer]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")


_3.  Unpack the installer, and locate the libflashplayer.so file_

> 
e.g. tar xvfz install_flash_player_9_linux.tar.gz



_4.  Install the 32 bit wrapper (linux32), IA32 libraries and the package conversion tool (alien)_

> 
sudo apt-get install linux32 alien ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11



_5.  Proceed with installation for Mozilla-based browsers_

> 
sudo alien -d nspluginwrapper*.rpm
sudo dpkg -i nspluginwrapper*.deb
sudo mkdir /usr/lib/mozilla/plugins32
sudo cp {path to}/libflashplayer.so /usr/lib/mozilla/plugins32
sudo nspluginwrapper -i /usr/lib/mozilla/plugins32/libflashplayer.so



_6.  Making the plugin available for Firefox_

> 
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.so /usr/lib/mozilla-firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/



_7.  ...and for Epiphany_

> 
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.so /usr/lib/epiphany/2.16/plugins/
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/epiphany/2.16/plugins/


---

### Post by Ravanous on 2007-02-09
**nlogax**, your instructions worked perfectly for me under Kubuntu. :guitar:

Thanks for taking the time to update the original post

---

### Post by lobo_cobra on 2007-03-26
Thanks for this great tutorial! As some had problems to install with it, I made a step by step howto out of it. Please always check directories and path on howtos and do not just execute... then  they work... ;-) btw... it is for Kubuntu but path should be same for ubuntu.

here on my webpage: [http://tools.schriber.bz/linuxwiki/index.php/Ubuntu64#Flash_32bit_on_Firefox_64bit](http://tools.schriber.bz/linuxwiki/index.php/Ubuntu64#Flash_32bit_on_Firefox_64bit)  or...

Flash 32bit on Firefox 64bit

    * cd /usr/local/src; mkdir flash32; cd flash32 

    * get the needed files 

wget [http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.3-1.x86_64.rpm](http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.3-1.x86_64.rpm)
wget [http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.3-1.x86_64.rpm](http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.3-1.x86_64.rpm)
wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

    * unpack flash player 

tar -zxvf install_flash_player_9_linux.tar.gz

    * install tools 

alien converts rpm to apt packages, the linux32 wrapper is needed too

sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32
sudo apt-get install alien

    * install rpms 

sudo alien -d nspluginwrapper*.rpm
sudo dpkg -i nspluginwrapper*.deb

    * prepare a separate directory 

sudo mkdir /usr/lib/mozilla/plugins32

sudo cp {path to}/libflashplayer.so /usr/lib/mozilla/plugins32 sudo nspluginwrapper -i /usr/lib/mozilla/plugins32/libflashplayer.so

    * check if link exist (should be there) 

==> check or create: sudo ln -s /usr/lib/nspluginwrapper/x86_64/npconfig /usr/bin/nspluginwrapper

    * cp flashplayer.so into new plugin dir 

cp install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins32/  

    * wrap flash 

sudo nspluginwrapper -i /usr/lib/mozilla/plugins32/libflashplayer.so

    * Make plugin available for Firefox 

sudo ln -s /usr/lib/mozilla/plugins/npwrapper.so /usr/lib/mozilla-firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/

WHY ... (by [http://ubuntuforums.org/showthread.php?t=290785](http://ubuntuforums.org/showthread.php?t=290785)) improved by lobo_cobra Unless some other tutorials you can read on the net, i made a special directory for the 32 bits plugins, because even if it doesn't make firefox explode, the fact that the 32bits plugin is in a directory checked on firefox startup raise and error telling that this plugin can't be loaded.

You can see it by lauching firefox from a terminal.

---

### Post by dada1958 on 2007-03-26
Great, it works here ... tnx!

---

### Post by dada1958 on 2007-03-30
And it broke with the latest updates which they have fixed the next day so it's working again :)

---

### Post by DaylanDarby on 2007-04-02
Thansk lobo_cobra , your instructions worked for my AMD 64 Edgy

---

### Post by Kilz on 2007-04-02
> **lobo_cobra said:**
> Thanks for this great tutorial! As some had problems to install with it, I made a step by step howto out of it. Please always check directories and path on howtos and do not just execute... then  they work... ;-) btw... it is for Kubuntu but path should be same for ubuntu.
.

There is only one problem with nspluginwrapper, what if I need  a java plugin?

---

### Post by UltimaDude on 2007-04-03
Simple64 can install Java if i'm right though it only works on the 32 Bit firefox and Opera, same with Flash on Simple64.

---

### Post by f3d on 2007-04-26
Hi,

One point could be added to this howto... :rolleyes: 

You need to have IA32 emulation compiled into the kernel (Executatble file formats / Emulations), It might save some time to people who played with the .config of their kernel like I did.

Cheers.

---

### Post by jonathanku on 2007-04-26
Thank you pvalois! Works well. JK
AMD64 // Asus M2N3-SLI  //  2GB

---

### Post by Enverex on 2007-04-26
This isn't working. I'm trying to do it but when it comes to the nspluginwrapper -i part I keep getting a message about missing .so files (yes, I have app the dep packages installed).

I'm going through finding each one then linking it each time but it's getting really frustrating.

Example:
nspluginwrapper -i /usr/lib/mozilla/plugins32/libflashplayer.so
*** NSPlugin Viewer  *** ERROR: libXext.so.0: cannot open shared object file: No such file or directory

---

### Post by Kilz on 2007-06-14
> **paranoid87 said:**
> i also cudnt make it work!??is there some seriuos bug?

While I applaud you for searching for posts, resurrecting a post that is older than a few months is not a good idea. As for the flash question A look back at the last few pages should give you multiple ways to make it work. You can also choose one of the 2 ways linked in my signature. Both have auto install scripts.

---

### Post by goldemaire on 2007-06-27
*****************************************************************************************
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.so /usr/lib/mozilla-firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/
*****************************************************************************************

**[COLOR="Blue"][SIZE="3"]Although it took most of my day to get this thing installed, its worth my time. Thanks for this forum! :)[/SIZE][/COLOR]**

---

### Post by jjstiff on 2007-09-15
pvalois!

Thanks dude. You're solution worked great. Just a few things that threw me off:

1) Download the two packages to the Desktop, don't try to open them with archive manager.

2) I used Synaptic Package manager instead of apt-get. Just type those packages in the search function and you can get em quick.

3) I don't know why you put the first line in the second box: 'sudo ln -s /usr/lib/nspluginwrapper/x86_64/npconfig /usr/bin/nspluginwrapper' since /usr/lib/nspluginwrapper/ does not exist at that point.... so i just skipped that step and everything works fine.

--------------

Yeah.. i was trying to get gnash to work... so i got all the build-essential files and everything.... I didn't realize alien converted rpm to deb so i was trying to compile nspluginwrapper.... just do what PVALOIS says guys. Yes: it certainly does work.

AMD ATHLON 64 / Ubuntu 7.04

---

### Post by Robert Easter on 2008-04-21
Following along on this routine.  I did, mentioning this just in case, skip the part with the rpm and deb versions of the wrapper package, as this is already installed, but here's the question:  I get as far as creating the symbolic link, and here's the picture:

robert@ubuntu:~/Desktop$ sudo ln -s /usr/lib/mozilla/plugins/npwrapper.so /usr/lib/mozilla-firefox/plugins 
ln: creating symbolic link `/usr/lib/mozilla-firefox/plugins' to `/usr/lib/mozilla/plugins/npwrapper.so': No such file or directory
robert@ubuntu:~/Desktop$ ls /usr/lib/mozilla/plugins
flashplugin-alternative.so  libtotem-basic-plugin.xpt  libtotem-mully-plugin.xpt        npwrapper.libflashplayer.so
libflashplayer.so           libtotem-gmp-plugin.so     libtotem-narrowspace-plugin.so
libjavaplugin.so            libtotem-gmp-plugin.xpt    libtotem-narrowspace-plugin.xpt
libtotem-basic-plugin.so    libtotem-mully-plugin.so   libvlcplugin.so
robert@ubuntu:~/Desktop$ sudo ln -s /usr/lib/mozilla/plugins/npwrapper.so /usr/lib/mozilla-firefox/plugins/
ln: target `/usr/lib/mozilla-firefox/plugins/' is not a directory: No such file or directory
 
I get that the target directory does not exist, even though I can ls right to it.  What do  I do with this?

---

