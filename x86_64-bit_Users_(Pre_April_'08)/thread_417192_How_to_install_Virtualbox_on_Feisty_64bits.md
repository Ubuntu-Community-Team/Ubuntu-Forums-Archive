---
title: "How to install Virtualbox on Feisty 64bits?"
date: 2007-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by pain of salvation on 2007-04-21
How do I install Virtualbox on Feisty 64bits?

---

### Post by Medieval_Creations on 2007-04-21
There isn't a 64bit version of VBox per the VBox website.

There are a couple of threads regarding this and some say they have successfully gotten it to install.  I unfortunately have not.

I can't seem to find the threads at the moment, do a search for them.  If I come across them again I'll post'em.

---

### Post by Medieval_Creations on 2007-04-21
Here's a link to a search of all the VBox threads under 63bit.

[http://ubuntuforums.org/search.php?searchid=18461618](http://ubuntuforums.org/search.php?searchid=18461618)

---

### Post by Kilz on 2007-04-21
> **pain of salvation said:**
> How do I install Virtualbox on Feisty 64bits?

I was able to install the 32bit version of Virtualbox on 64bit Feisty. I used the Edgy deb they supplied. I used the force method.

sudo dpkg -i --force-architecture VirtualBox_1.3.8_Ubuntu_edgy_i386.deb

Then the method I use for all 32bit applications. [I wrote a page that shows how to do it.]("http://tghc.org/32biton64bit.php")

Let me give you the 32 bit packages you will need. Follow the howto and extract all the libs and copy them into /usr/lib32

libqt3-mt_3.3.6-3ubuntu3.1_i386.deb
libuuid1_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb
libxalan110_1.10-3_i386.deb
libxerces27_2.7.0-3_i386.deb
libicu36_3.6-2build1_i386.deb
libmng1_1.0.9-1_i386.deb

That will let the application install and start. I have no idea on how to fix any problems you may experence once started. To me it looks like vmware. Since vmware server is free you may want to try that if this doesnt help you.

---

### Post by Medieval_Creations on 2007-04-21
> **Kilz said:**
> 
sudo dpkg -i --force-architecture VirtualBox_1.3.8_Ubuntu_edgy_i386.deb


Worked like a charm.  As usual.

Is there anything you haven't figured out how to get working in 64bit yet Kilz?
:lolflag:

---

### Post by Kilz on 2007-04-21
> **Medieval_Creations said:**
> Worked like a charm.  As usual.

Is there anything you haven't figured out how to get working in 64bit yet Kilz?
:lolflag:

Some things take a lot of things to copy in, so its not worth it. But as long as its under 10 packages I have gotten everything to work that I have tried.

---

### Post by NullHead on 2007-04-21
Hay I tried this and it doesn't work ...the deppendensies were taken care of. The module was compiled sucsesfully as far as I could tell.

Help

---

### Post by Kilz on 2007-04-21
> **NullHead said:**
> Hay I tried this and it doesn't work ...the deppendensies were taken care of. The module was compiled sucsesfully as far as I could tell.

Help

We see that it installed and that it made the module. Please give me a little information. Exactly what did you do to install everything listed in my post?

---

### Post by NullHead on 2007-04-22
> **Kilz said:**
> We see that it installed and that it made the module. Please give me a little information. Exactly what did you do to install everything listed in my post?

well for one I use Feisty for two all I did was this ```
sudo dpkg -i --force-architecture VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
```considering I'v installed other 32bit apps with no problem.

---

### Post by pain of salvation on 2007-04-22
Didn't worked..

But it installed. Now how can I uninstall it? 

I will try vmware...

I want to try arch linux in some virtual machine...

---

### Post by NullHead on 2007-04-22
> **pain of salvation said:**
> Didn't worked..

But it installed. Now how can I uninstall it? 

I will try vmware...

I want to try arch linux in some virtual machine...

wana uninstall it? try.
```
sudo dpkg -r VirtualBox
```

---

### Post by pain of salvation on 2007-04-22
Thanks!

Now all that I need is know how to use arch on vmware player. I think I need a .vmx file, but I don't know were to find it...

may someone help?

---

### Post by Kilz on 2007-04-22
> **NullHead said:**
> well for one I use Feisty for two all I did was this ```
sudo dpkg -i --force-architecture VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
```considering I'v installed other 32bit apps with no problem.

Please read the post I made again. I also linked to an page I wrote that describes exactly what you have to do, and I gave you the names of the packages you need. You have to do more than just force in a package. Some 32bit applications require you to manually install 32bit libraries.

---

### Post by laxon on 2007-04-22
Hey Kilz,

I tried everything exactly how you describe it in your manual. I added all the lib files from each of the packages into /usr/lib32. I even checked, if they're there. Still, when I run the application, it asks me to reinstall it. And when I install it, with the force-method, it still wants libxalan110 and libxerces27. Both are in /usr/lib32...

marlex@Wotan:~/Desktop$ sudo dpkg -i --force-architecture VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package virtualbox.
(Reading database ... 97778 files and directories currently installed.)
Unpacking virtualbox (from VirtualBox_1.3.8_Ubuntu_edgy_i386.deb) ...
virtualbox-puel-1-2 license has already been accepted.
dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on libxalan110; however:
  Package libxalan110 is not installed.
 virtualbox depends on libxerces27; however:
  Package libxerces27 is not installed.
dpkg: error processing virtualbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox

marlex@Wotan:~/Desktop$ VirtualBox
Could not find VirtualBox installation. Please reinstall.

:confused: 

If you have any suggestions I appreciate it!
Thanks!
Alex

---

### Post by Necreia on 2007-04-22
I did the same thing as Laxon, and am getting the same error.

---

### Post by Kilz on 2007-04-22
Try installing the 64bit versions with apt/synaptic. This should let the application install. But since they will be in /usr/lib and you placed the 32bit versions in /usr/lib32 they wont get overwritten.

---

### Post by Necreia on 2007-04-22
> **Kilz said:**
> Try installing the 64bit versions with apt/synaptic. This should let the application install. But since they will be in /usr/lib and you placed the 32bit versions in /usr/lib32 they wont get overwritten.

Can you go into more detail please, how exactly do I use apt/synaptic?  And by 64bit versions, do you mean those same packages that you listed in the start, find 64 bit versions of those and do those steps over again with this apt/synaptic?

I'm still very new at linux, so please excuse the level of newbie in my questions.

---

### Post by Kilz on 2007-04-22
> **Necreia said:**
> Can you go into more detail please, how exactly do I use apt/synaptic?  And by 64bit versions, do you mean those same packages that you listed in the start, find 64 bit versions of those and do those steps over again with this apt/synaptic?

I'm still very new at linux, so please excuse the level of newbie in my questions.

Synaptic is the gui version of apt. [You can go here to learn how to use it.]("http://www.monkeyblog.org/ubuntu/installing/#installing_with_synaptic") Search for libxalan110 and libxerces27 and install them. Then try to install virtualbox again. You can only install 64bit versions with synaptic.

---

### Post by laxon on 2007-04-22
Thanks Kilz, that was the missing link!!

Although after installing these two libs in 64bit and starting VirtualBox it came with several VBox***.so libs missing error messages. I found all these in /usr/lib and after copying them to /usr/lib32 it worked!!

By the way: there is now a feisty-version on virtualbox.org in the download section. but seems like a 32-bit-version. I installed this one instead of the edgy version now and it works too!

Thanks again for your help Kilz!

Alex

---

### Post by Necreia on 2007-04-22
Thanks for your help, it worked!

By the way, how do/would I remove it if I chose to do so?  I don't see it in either Synaptic or the normal app install gui.  I tried some commands such as "sudo apt-get remove VirtualMachine" but that can't find it either.

---

### Post by NullHead on 2007-04-22
> **Necreia said:**
> Thanks for your help, it worked!

By the way, how do/would I remove it if I chose to do so?  I don't see it in either Synaptic or the normal app install gui.  I tried some commands such as "sudo apt-get remove VirtualMachine" but that can't find it either.

try this.
```
sudo dpkg -r VirtualBox
```

---

### Post by NullHead on 2007-04-22
Well Kilz I used your very helpfull howto but with out success. It installed unsuccessfully with this error. 
```
/opt/VirtualBox-1.3.8/VirtualBox: error while loading shared libraries: libuuid.so.1: wrong ELF class: ELFCLASS64

``` 
Now I copied  libuuid.so.1 into the /usr/lib32 directory it gives me the error above ... and when I don't have 'em inthere it says. ```
/opt/VirtualBox-1.3.8/VirtualBox: error while loading shared libraries: libuuid.so.1: cannot open shared object file: No such file or directory

```

---

### Post by Kilz on 2007-04-22
> **NullHead said:**
> Well Kilz I used your very helpfull howto but with out success. It installed unsuccessfully with this error. 
```
/opt/VirtualBox-1.3.8/VirtualBox: error while loading shared libraries: libuuid.so.1: wrong ELF class: ELFCLASS64

``` 
Now I copied  libuuid.so.1 into the /usr/lib32 directory it gives me the error above ... The reason is , you are copying a 64bit library into the folder for 32bit libraries. You need to extract the 32bit library from the 32bit package and copy it into the 32bit folder. Thats is what the page I linked to tells you to do.

> **NullHead said:**
> and when I don't have 'em inthere it says. ```
/opt/VirtualBox-1.3.8/VirtualBox: error while loading shared libraries: libuuid.so.1: cannot open shared object file: No such file or directory

```
Thats because the 32bit version doesnt exist on your machine. Simply copying in a 64bit library isnt enough. I hope you did read that page and didnt try and force in 32bit libraries, if you do you can ruin the ubuntu install.

---

### Post by NullHead on 2007-04-22
Oh! :shock: ...well I didn't ... I just copied the ones from /lib into /usr/lib32 ... did I do a bad thing?:-s
I did read the page. Should I download the 32bit lib and extract it as the page said?

---

### Post by Kilz on 2007-04-23
> **NullHead said:**
> Oh! :shock: ...well I didn't ... I just copied the ones from /lib into /usr/lib32 ... did I do a bad thing?:-s
I did read the page. Should I download the 32bit lib and extract it as the page said?

That might be a good idea if you want this program to start.

---

### Post by NullHead on 2007-04-24
> **Kilz said:**
> That might be a good idea if you want this program to start.

Well after trial and error I got it to run ...however it doesn't work. It gives me this error.
```
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device

```
Should I post a new thread for this?

---

### Post by Kilz on 2007-04-24
> **NullHead said:**
> Well after trial and error I got it to run ...however it doesn't work. It gives me this error.
```
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device

```
Should I post a new thread for this?

Since we just got the application to load. You may want to try other vm software that is known to work.

---

### Post by NullHead on 2007-04-24
> **Kilz said:**
> Since we just got the application to load. You may want to try other vm software that is known to work.

Good diea I think I'll use Qemu.

Thanks for your effort and pashents with me.

---

### Post by Medieval_Creations on 2007-04-24
I was able to get VBox to install, but now when I try to run it I get this error.

/opt/VirtualBox-1.3.8/VirtualBox: error while loading shared libraries:
 libqt-mt.so.3: cannot open shared object file: No such file or directory



I tried changing the permissions on that lib and verified that it is installed.  Not sure what I missed.

---

### Post by Necreia on 2007-04-24
> **Medieval_Creations said:**
> I was able to get VBox to install, but now when I try to run it I get this error.

/opt/VirtualBox-1.3.8/VirtualBox: error while loading shared libraries:
 libqt-mt.so.3: cannot open shared object file: No such file or directory



I tried changing the permissions on that lib and verified that it is installed.  Not sure what I missed.

I didn't get that.  Following what was outlined here, I was able to get it fully installed (or so it appeared) and was able to go through the steps to create the instance.  It wasn't until I actually ran the instance to install Windows that I got an error:

VERR_INVALID_PARAMETER

---

### Post by NullHead on 2007-04-24
> **Medieval_Creations said:**
> I was able to get VBox to install, but now when I try to run it I get this error.

/opt/VirtualBox-1.3.8/VirtualBox: error while loading shared libraries:
 libqt-mt.so.3: cannot open shared object file: No such file or directory



I tried changing the permissions on that lib and verified that it is installed.  Not sure what I missed.

You might want to read Kilz 32bit app install HOW-TO on [his website]("http://tghc.org/32biton64bit.php")

---

### Post by littlerob on 2007-04-27
Hi,
I've some trouble with the librairies 32bits. I tried to follow what Kilz told us to do, but still I've some problem. When I launch VirtualBox I've got this :

**/opt/VirtualBox-1.3.8/VirtualBox: error while loading shared libraries: libxalan-c.so.110: cannot open shared object file: No such file or directory**

Indeed in /usr/lib32 there is not this file but only **libxalan-c.so.110.0**.
Apparently I've got a problem with the symbolic link...I tried to recreate one ( **ln -s libxalan-c.so.110.0 libxalan-c.so.110** ), but same error message.

Anybody knows what to do ?

---

### Post by saceirdoth on 2007-04-27
> **Necreia said:**
> I didn't get that.  Following what was outlined here, I was able to get it fully installed (or so it appeared) and was able to go through the steps to create the instance.  It wasn't until I actually ran the instance to install Windows that I got an error:

VERR_INVALID_PARAMETER

+1

---

### Post by NullHead on 2007-04-27
> **littlerob said:**
> Hi,
I've some trouble with the librairies 32bits. I tried to follow what Kilz told us to do, but still I've some problem. When I launch VirtualBox I've got this :

**/opt/VirtualBox-1.3.8/VirtualBox: error while loading shared libraries: libxalan-c.so.110: cannot open shared object file: No such file or directory**

Indeed in /usr/lib32 there is not this file but only **libxalan-c.so.110.0**.
Apparently I've got a problem with the symbolic link...I tried to recreate one ( **ln -s libxalan-c.so.110.0 libxalan-c.so.110** ), but same error message.

Anybody knows what to do ?

well what I would do is download the 32bit version of "libxalan" ...just use [this]("http://packages.ubuntu.com/") link to look for it...it's at the ubuntu packages website. Then extract the data>user>lib> into /userlib32
That should to the trick repeat as necessary.

---

### Post by borghal on 2007-04-29
Hi,

I tried to install following your howto. I installed all 32-lbraries but get this error when:

sudo dpkg -i --force-architecture VirtualBox_1.3.8_Ubuntu_feisty_i386.deb 

dpkg - Warnung: Problem wird übergangen, weil --force angegeben ist:
 Paket-Architektur (i386) passt nicht zum System (amd64)
(Lese Datenbank ... 112893 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von virtualbox 1.3.8_Ubuntu_feisty (durch VirtualBox_1.3.8_Ubuntu_feisty_i386.deb) ...
 * Stopping VirtualBox kernel module vboxdrv                                                   [ OK ] 
virtualbox-puel-1-2 license has already been accepted.
Entpacke Ersatz für virtualbox ...
Richte virtualbox ein (1.3.8_Ubuntu_feisty) ...
 * Starting VirtualBox kernel module vboxdrv                                                          
FATAL: Error inserting vboxdrv (/lib/modules/2.6.20-15-generic/misc/vboxdrv.ko): Invalid module format

Can you help me?

---

### Post by NullHead on 2007-04-29
I got that too with the feisty .deb so try the [Edgy one.]("http://http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb")
I can't take any of the credit all of the how-to I learned from Kilz. Read the whole thing on [his website.]("http://http://tghc.org/32biton64bit.php")

---

### Post by ewing on 2007-04-29
:lolflag:  thanks Kilz , works great,
 just remember  you need to extract the virtualbox debian package and copy the lib to usr/lib32 too.

---

### Post by littlerob on 2007-04-30
> **NullHead said:**
> well what I would do is download the 32bit version of "libxalan" ...just use [this]("http://packages.ubuntu.com/") link to look for it...it's at the ubuntu packages website. Then extract the data>user>lib> into /userlib32
That should to the trick repeat as necessary.

Actually, I exactly do this. My problem is that when I extract, some files are missing. Apparently I don't have permission to preserve the "symbolic link" (I tried as root, but same error). By the way, with "libxalan" when I extract, I have data>lib instead of data>user>lib (there is not the user directory), maybe that's the problem...

---

### Post by borghal on 2007-04-30
I got a full install (or so it seems) but I ran into the same error when I tried to open/create a windows isntalnce:


Unknown error initializing kernel driver (VERR_INVALID_PARAMETER).
VBox status code: -2 (VERR_INVALID_PARAMETER).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Did anyone get around this one?

---

### Post by NullHead on 2007-04-30
> **borghal said:**
> I got a full install (or so it seems) but I ran into the same error when I tried to open/create a windows isntalnce:


Unknown error initializing kernel driver (VERR_INVALID_PARAMETER).
VBox status code: -2 (VERR_INVALID_PARAMETER).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Did anyone get around this one?

I haven't ... this is as far as I have gotten. I use qemu and qemu launcher they are in the repository and work great.

---

### Post by farbird on 2007-05-11
managed to get mine working...

thanks

---

### Post by farbird on 2007-05-11
> **farbird said:**
> managed to get mine working...

thanks


Vbox loaded up all arite ,, but when i try to run a guest os..

It gave me an error box..

Failed to start Virtual Machine "testguest"
Unknown error initializing kernel driver
{VERR_INVALID_PARAMETER}

sigh

---

### Post by NullHead on 2007-05-11
> **farbird said:**
> Vbox loaded up all arite ,, but when i try to run a guest os..

It gave me an error box..

Failed to start Virtual Machine "testguest"
Unknown error initializing kernel driver
{VERR_INVALID_PARAMETER}

sigh

I get the same problem and I don't know how to fix it. You might try qemu and qemu launcher you can find those in the repository for feisty.

---

