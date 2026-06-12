---
title: "Using Citrix Client 10 with Ubuntu 7.10 (64-bit) - Gutsy Gibbon"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by juanhunglow on 2007-10-19
_EDIT: October 24, 2007 - Continued problems_:
It appears I premature in my praise of 7.10 (with respect to the citrix stuff, the remainder of the new version still gleams).  Problems are still persisting and so far one fix has been proffered in post [[COLOR="DarkOrange"]5[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3618527&postcount=5").  

If others have problems look here or in the prior thread as these issues seem to be similar.

**[COLOR="Red"]_Original Post:_[/COLOR]**
This will be a very short post compared to the steps that were used in the thread [[COLOR="DarkOrange"]Using Citrix Client 10.0 - help, anyone have this working (How-to)[/COLOR]]("http://ubuntuforums.org/showthread.php?t=376735").

After my install of the new 7.10, I downloaded the latest citrix client .tar.gz from the [[COLOR="Blue"]download page[/COLOR]]("http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323") (as of today is version 10.6).

1. I extracted the en.linuxx86.tar.gz  (right click --  extract here)
2. In the extracted folder I clicked the setupwfc file and told it to run in a terminal.
3. I chose all the defaults.
4. I opened up Firefox, browsed to my companies citrix login and the presentation server launched.

I DID NOT HAVE TO: (Edit: this is incorrect, 32-bit libs were installed when Flash was installed)
1. install 32-bit Firefox or any other 32-bit libraries as I had before

Someone with more technical knowledge can explain why or how, but this just works now in 7.10.... I am amazed.\\:D/

I remember fighting with this in Dapper and Edgy, finally got better in Feisty, now, it just works.

If others are having problems post here and the community will try to help.

---

### Post by mugstar on 2007-10-21
Following that exact same procedure, I get this: ```
/usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
``` Doing *ls -l `locate libXm.so.3`* gives me
```
lrwxrwxrwx 1 root root   14 2007-10-21 18:23 /usr/lib/libXm.so.3 -> libXm.so.3.0.2
-rw-r--r-- 1 root root 2.7M 2007-05-02 05:24 /usr/lib/libXm.so.3.0.2
```Do you get the same?  Did you install openmotif?

I've been messing around with symlinks for an hour now, and am no further forward.  Would appreciate some help!

---

### Post by pluto1111 on 2007-10-22
I too am experiencing an issue with Citrix and Ubuntu 7.10.  Using Ubuntu 7 .04 and Citrix 10 with the script posed in this forum, I was able to launch my Citrix connection with a desktop icon, which would display a box requesting my user name and password.    However, using Ubuntu 7.10 and trying Citrix 10 (with and without the script) and 10.6 (script states it only works with Citrix 10), I can only access my work sever using Citrix 10.6 and my browser, not the desktop icon.  The issue is work will soon disable access via the browser, and only allow access via (what I call) direct connect, or launching Citrix and entering user name and password via desktop icon.  Any ideas?

Thanks in advance for your help!

---

### Post by tombott on 2007-10-24
> **mugstar said:**
> Following that exact same procedure, I get this: ```
/usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
``` Doing *ls -l `locate libXm.so.3`* gives me
```
lrwxrwxrwx 1 root root   14 2007-10-21 18:23 /usr/lib/libXm.so.3 -> libXm.so.3.0.2
-rw-r--r-- 1 root root 2.7M 2007-05-02 05:24 /usr/lib/libXm.so.3.0.2
```Do you get the same?  Did you install openmotif?

I've been messing around with symlinks for an hour now, and am no further forward.  Would appreciate some help!

Getting the same.

---

### Post by tombott on 2007-10-24
Ok the following fixed the error of the Citrix Presentation Client not loading on Gutsy 32bit on my laptop.

sudo aptitude install libmotif3
sudo aptitude install libxaw7

I was then able to open Citrix without any problems.

---

### Post by juanhunglow on 2007-10-24
> **tombott said:**
> Ok the following fixed the error of the Citrix Presentation Client not loading on Gutsy 32bit on my laptop.

sudo aptitude install libmotif3
sudo aptitude install libxaw7

I was then able to open Citrix without any problems.

I guess I was a bit premature in my praise for 7.10.

It does appear that I installed the Flash for 64 prior to installing the citix client.  Thus, the 32-bit stuff got installed through that process (I was not paying attention, too much excitement over the fresh install).

Regardless, it appears that problems will persist until we get a 64-bit client for linux.

---

### Post by ppoteete on 2007-11-19
How to make Citrix work with Ubuntu 7.10 Gutsy Gibbon 64 bit edition.

1) Get the required libraries for the 64bit edition (just to have them)
$ sudo apt-get install libxaw6 libmotif3

2) Snarf a 32bit version from another ubuntu box of libXm.so.3.
i.e.
scp /usr/lib/libXm.so.3 user@yourhost:/tmp/
I can't upload mine (what a royal PAIN!) the upload manager limits me to 976K zipped/tar'd/bz2 -9.
"Your file of 980.4 KB bytes exceeds the forum's limit of 976.6 KB for this filetype."

3) Create a directory structure that Citrix understands
$ sudo mkdir /lib/i686-linux-gnu/

4) move the 32bit file into that directory (don't bother symlinking the file, just move it).
NOTE: you do NOT want to overwrite your 64bit edition file, just make Citrix use the 32bit edition.

5) Start citrix.
$ /home/<youruser>/ICAClient/linuxx86/wfcmgr

Note:
To trace the search paths for wfcmgr run:
$ ltrace -S ./wfcmgr

---

### Post by romeyde on 2007-11-21
Any of you ever have window display issues with citrix?  Not always, but frequently I get problems with the windows displaying correctly when I try to switch to them via "alt-tab" or by clicking on them in the programs bar (what is that called anyway).    The window will display but just the frame.  I have to minimize and then maximize it again to get it to display.

Not a big deal, just annoying.

---

### Post by crocd on 2007-11-21
All

When opening a ica file from a citrix webpage remember to associate the wfica to it. Presentation server client opens and works fine. I am running this on Gutsy 64 bit.

---

### Post by sunyan1999 on 2007-11-29
I followed the procedures laid out here. First installed the libs and then extracted the linuxx86.tar.gz. But when I run ./setupwfc, I got the following:
/tmp/citrix/en.linuxx86/linuxx86/hinst: 236: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 237: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 238: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 239: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4011: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4027: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found


Can anybody help? I have been able to install Citrix 10.6 on another computer with Gutsy 32bit without any problem. Thanks.

---

### Post by node42 on 2008-01-02
> **sunyan1999 said:**
> I followed the procedures laid out here. First installed the libs and then extracted the linuxx86.tar.gz. But when I run ./setupwfc, I got the following:
/tmp/citrix/en.linuxx86/linuxx86/hinst: 236: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 237: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 238: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 239: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4011: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4027: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found
/tmp/citrix/en.linuxx86/linuxx86/hinst: 4043: /tmp/citrix/en.linuxx86/linuxx86/echo_cmd: not found


Can anybody help? I have been able to install Citrix 10.6 on another computer with Gutsy 32bit without any problem. Thanks.


To get around this I just bypassed their echo_cmd command. If you edit **setupwfc** and look at line # 546 you should see:

[FONT="Courier New"]**ECHO_CMD=${PLATFORM_PACKAGE_DIR}/$TR_FILE export ECHO_CMD**[/FONT]

Comment that out with a leading "#" and put this in it's place:

[FONT="Courier New"]**ECHO_CMD=echo**[/FONT]

Seems to be working for me...

---

### Post by chaosman on 2008-01-10
Also, download the java runtime enviorment...after hours upon hours of fooling around doing what everyone said...when i did that Citrix client worked...

---

### Post by josel777 on 2008-01-26
Your procedure worked for me. :)

---

### Post by romeyde on 2008-02-27
Just wanted to update what I've discovered about this issue.   I was having an unrelated problem with viewing videos so as a test I turned off the restricted video drivers.   This kills a lot of my fancy desktop functionality but did fix my video issue and also fixed this citrix problem I was having.


> **romeyde said:**
> Any of you ever have window display issues with citrix?  Not always, but frequently I get problems with the windows displaying correctly when I try to switch to them via "alt-tab" or by clicking on them in the programs bar (what is that called anyway).    The window will display but just the frame.  I have to minimize and then maximize it again to get it to display.

Not a big deal, just annoying.

---

### Post by n8bounds on 2008-03-22
> **ppoteete said:**
> How to make Citrix work with Ubuntu 7.10 Gutsy Gibbon 64 bit edition.

1) Get the required libraries for the 64bit edition (just to have them)
$ sudo apt-get install libxaw6 libmotif3

2) Snarf a 32bit version from another ubuntu box of libXm.so.3.
i.e.
scp /usr/lib/libXm.so.3 user@yourhost:/tmp/
I can't upload mine (what a royal PAIN!) the upload manager limits me to 976K zipped/tar'd/bz2 -9.
"Your file of 980.4 KB bytes exceeds the forum's limit of 976.6 KB for this filetype."

3) Create a directory structure that Citrix understands
$ sudo mkdir /lib/i686-linux-gnu/

4) move the 32bit file into that directory (don't bother symlinking the file, just move it).
NOTE: you do NOT want to overwrite your 64bit edition file, just make Citrix use the 32bit edition.

5) Start citrix.
$ /home/<youruser>/ICAClient/linuxx86/wfcmgr

Note:
To trace the search paths for wfcmgr run:
$ ltrace -S ./wfcmgr
ppoteete, Thanks man. That was the majik I needed.

PS, download the 32 bit libXm here:

[http://ngbnet.homelinux.com/repository/unrestricted/linux/ica-client-wfcmgr/libXm.so.3](http://ngbnet.homelinux.com/repository/unrestricted/linux/ica-client-wfcmgr/libXm.so.3)

---

### Post by stash1071 on 2008-03-24
I'm getting something even more maddening (Gutsy Gibbon 7.10 x86_64).

```

root@:/usr/lib/ICAClient# ls -l wfcmgr
-r-xr-xr-x 1 root root 993656 2008-03-24 22:06 wfcmgr
root:/usr/lib/ICAClient# ./wfcmgr
bash: ./wfcmgr: No such file or directory

```

Also when running an application when logged into the Citrix server, I try to open launch.ica with wfica and nothing happens in Firefox.

I've followed the instructions with regards to libXm.so.3 above, thinking part of the more descriptive message may have been left off.

```

lrwxrwxrwx 1 root root 27 2008-03-24 22:06 /usr/lib/firefox/plugins/npica.so -> /usr/lib/ICAClient/npica.so

```

I can only imagine that I'm missing something really silly here...

---

### Post by mattfaulk on 2008-03-25
I think you need to install the i386 libc6 components.

'apt-get install libc6-i386'

---

### Post by stash1071 on 2008-03-27
That did it, but not sure why, as nothing appeared to be updated or installed after I ran it, I'll take it though, thanks

```

sudo apt-get install libc6-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6-i386 is already the newest version.
libc6-i386 set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

---

