---
title: "Install Gyachi"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by Sef on 2008-04-26
How do you get Gyachi installed under Hardy Heron?  I found [one tutorial]("http://ubuntuforums.org/showthread.php?t=609336&highlight=gyachi+64-bit+Ubuntu"), but it was for Gutsy.  Also the Gyachi debs are for Gutsy.

---

### Post by loell on 2008-04-27
hi, you could compile it in 64, by passing a configure parameter as ```
 --disable-wine
``` 

or would like to have a 32 bit deb package for hardy?

---

### Post by Sef on 2008-04-28
I would prefer to compile it as a 64-bit.   What would be the configure parameter?

---

### Post by hhpeter on 2008-04-28
> **loell said:**
> hi, you could compile it in 64, by passing a configure parameter as ```
 --disable-wine
``` 

or would like to have a 32 bit deb package for hardy?

Sorry to hijack this tread, can you tell me if there is a .deb package for Hardy and where I can find it ... I tried to install gyachi with a tar.gz package but everytime I get errors...thanks

---

### Post by loell on 2008-04-28
> **Sef said:**
> I would prefer to compile it as a 64-bit.   What would be the configure parameter?

```
./configure --prefix=/usr --disable-wine
```

---

### Post by Sef on 2008-04-28
> Sorry to hijack this tread, can you tell me if there is a .deb package for Hardy and where I can find it ... I tried to install gyachi with a tar.gz package but everytime I get errors...thanks

Not currently, which is why I posted my thread.  Last deb took about a month to show up.

---

### Post by loell on 2008-04-28
I'm kinda still holding out in building a hardy deb package as i would like some polishing to get into gyachi's CVS, but since someone is asking i will then be compelled to build it. a little later   :mrgreen:

---

### Post by maxxum on 2008-04-28
Hi,
I tried installing is on x86_64 version of Ubuntu 8.04. It fails:
```
xxxx@xxxx:~/Unzips/gyachi-1.1.0$ ./autogen.sh 
searching for GNU gettext intl directory...
 -> /usr/share/gettext/intl ... found it
copying gettext intl files ...
running aclocal ...
configure.ac:12: warning: macro `AM_DISABLE_STATIC' not found in library
configure.ac:13: warning: macro `AM_PROG_LIBTOOL' not found in library
configure.ac:25: warning: macro `AM_PATH_GTK_2_0' not found in library
configure.ac:26: warning: macro `AM_PATH_GLIB_2_0' not found in library
configure.ac:14: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:389: AC_USE_SYSTEM_EXTENSIONS is expanded from...
/usr/share/aclocal/lock.m4:29: gl_LOCK_EARLY_BODY is expanded from...
/usr/share/aclocal/lock.m4:22: gl_LOCK_EARLY is expanded from...
/usr/share/aclocal/lock.m4:253: gl_LOCK is expanded from...
/usr/share/aclocal/intl.m4:186: gt_INTL_SUBDIR_CORE is expanded from...
/usr/share/aclocal/intl.m4:25: AM_INTL_SUBDIR is expanded from...
/usr/share/aclocal/gettext.m4:57: AM_GNU_GETTEXT is expanded from...
configure.ac:14: the top level
configure.ac:14: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
configure.ac:14: warning: AC_COMPILE_IFELSE was called before AC_GNU_SOURCE
../../lib/autoconf/specific.m4:331: AC_GNU_SOURCE is expanded from...
configure.ac:14: warning: AC_RUN_IFELSE was called before AC_GNU_SOURCE
configure.ac:14: warning: AC_COMPILE_IFELSE was called before AC_AIX
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.ac:14: warning: AC_RUN_IFELSE was called before AC_AIX
configure.ac:14: warning: AC_COMPILE_IFELSE was called before AC_MINIX
../../lib/autoconf/specific.m4:460: AC_MINIX is expanded from...
configure.ac:14: warning: AC_RUN_IFELSE was called before AC_MINIX
running libtoolize ...
./autogen.sh: line 86: libtoolize: command not found
libtoolize failed, stopping.

```
I have build-essential package installed. What else do I need?

---

### Post by hhpeter on 2008-04-28
I finally succeeded on installing gyachi on hardy...I installed gyachi v1.1.31 from CVS, it was the first time I did something like this, now that I've done it, it seems easy ....however when I click *start my webcam* the LED next to the webcam its on, but I get this error:  
[I]Gyachi (webcam broadcaster):
Error while capturing initial image.[/I]
Anybody knows why I get this error ?

---

### Post by loell on 2008-04-28
youre having that error, probably because your webcam is a v4l2 based webcam. does your webcam show up with other webcam application?

---

### Post by loell on 2008-04-28
> **maxxum said:**
> Hi,
I tried installing is on x86_64 version of Ubuntu 8.04. It fails:
I have build-essential package installed. What else do I need?
try installing **autoconf** and **libtool**

---

### Post by hhpeter on 2008-04-28
you're right its a v4l2 webcam...its a syntek
works good with kopete, ekiga, camorama
in gutsy I had hard time to make it work but in hardy works out of the box, upside down though ...
is there a way to make it work with gyachi?

---

### Post by loell on 2008-04-28
yes, lately theres a work around that came up, but its bit difficult for a new user, you need to compile [http://www.swift-tools.net/Flashcam/]("http://www.swift-tools.net/Flashcam/")

---

### Post by ShelJ on 2008-04-29
Yeah, I would like one too please.  I'm trying to find something to use Yahoo features w/, and everything seems to point to GyachI.

Thanks,
Shel

P.S.  When i do try to force the install, I get the msg:```
gyachi depends on xmms (>= 1.2.10+20070501); however:
  Package xmms is not installed.
```  But, I have xmms2 and xmms is no longer in the repos.

---

### Post by loell on 2008-04-29
[32bit deb package for hardy heron]("http://www.mediafire.com/?nlrmdlub4tv")

support thread for 32bit questions

[http://ubuntuforums.org/showthread.php?t=773802]("http://ubuntuforums.org/showthread.php?t=773802")

---

### Post by hhpeter on 2008-04-29
I installed gyachi 1.1.31 yesterday and noticed that all my hotmail contacts, I added  them in yahoo messenger(windows), appear always online even though they are offline is this some sort of bug or just a setting that I need to do?

---

### Post by loell on 2008-04-29
yes most probably its a bug, whats the statuses when you try pidgin?

---

### Post by hhpeter on 2008-04-29
> **loell said:**
> yes most probably its a bug, whats the statuses when you try pidgin?

pidgin works good it shows them offline when they are offline, and online when they are online
I like gyachi better then pidgin though is there a workaround for this?

---

### Post by loell on 2008-04-29
no work around yet, i don't have  msn/hotmail contacts on my buddy list and as far as I know the developer doesn't have one either,  I'll try to talk to him when he isn't busy, see if it can be added in his long **TODO**list :)

or you can also bring this up in gyachi [http://gyachi.sourceforge.net/forums.shtml]("http://gyachi.sourceforge.net/forums.shtml") :)

---

### Post by ShelJ on 2008-04-29
[QUOTE=loell;4831013][32bit deb package for hardy heron]("http://www.mediafire.com/?nlrmdlub4tv")


Ok, I used this link, now I have GyachE Improved in my menu, but nothing happens when I click on it.  Also I get the following when I try to run it from a terminal 

```
~$ gyach
gyach: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory
~$ gyachi
gyachi: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

```

So, I did a search in SPM and could not find these programs, what dependencies are needed and can I find them in one nice neat package?

Thanks for your help.

After spending time w/ Google (man I need a gf!!) I came across this [HTML]http://sevencapitalsins.wordpress.com/2007/11/01/error-while-loading-shared-libraries-libexpatso0-cannot-open-shared-object-file-no-such-file-or-directory/[/HTML]

[HTML]Here’s how I solved the problem:

1) First of all, I found the path to libexpat.so: it’s /usr/lib/libexpat.so

root@smokey# ls -l /usr/lib/libexpat*
-rw-r--r-- 1 root root 250620 Oct 29 14:17 /usr/lib/libexpat.a
-rw-r--r-- 1 root root    795 Oct 29 14:16 /usr/lib/libexpat.la
lrwxrwxrwx 1 root root     17 Oct 29 14:17 /usr/lib/libexpat.so -> libexpat.so.1.5.2
lrwxrwxrwx 1 root root     17 Oct 29 14:17 /usr/lib/libexpat.so.1 -> libexpat.so.1.5.2
-rwxr-xr-x 1 root root 141456 Oct 29 14:17 /usr/lib/libexpat.so.1.5.2

2) As you can see, there’s no such thing as a libexpat.so.0 in /usr/lib. But there is a libexpat.so.1 referenced by libexpat.so itself. So I made a symbolic link named libexpat.so.0 pointing to libexpat.so:[/HTML]

B4 I got hacking into my system, i would like to know if this would be the right sol'n??

---

### Post by shane2peru on 2008-04-29
Has Gyachi improved any?  It used to be bulky and a bit on the ugly side.  I'm going to download and compile it to give it a try.  It has been a while since I gave it a try.  

Shane

---

### Post by loell on 2008-04-29
well, it now support themes. so i don't know if it is still ugly from your perspective, download the hardy package available in the second page of this thread. 

its default login protocol is now YMSG 15 and it now supports the full implementation of YM photosharing.

---

### Post by shane2peru on 2008-04-30
> **loell said:**
> well, it now support themes. so i don't know if it is still ugly from your perspective, download the hardy package available in the second page of this thread. 

its default login protocol is now YMSG 15 and it now supports the full implementation of YM photosharing.

ha ha, throw me for a loop there, we are on page 2. :lolflag:  Anyway, I figured out you meant the first page.  I did get the deb, but ... it isn't 64bit  :|  I don't mind compiling (when it works).  And in the configure I get this error:
```

./configure: line 30245: AM_PATH_GTK_2_0: command not found
./configure: line 30246: AM_PATH_GLIB_2_0: command not found
checking for X... no
configure: error: X development libraries not found

```
hmm, anyone know what the X development libraries would be?  Thanks for the info loell!  Hey does the file sharing part work too?

Shane

---

### Post by loell on 2008-04-30
oh, i forgot its page one :),
do the **./autogen.sh** then **./configure --prefix=/usr --disable-wine** , see if it will look for x development again. if you meant file transfer? yes its working. with progress bars and download manager.

---

### Post by shane2peru on 2008-04-30
> **loell said:**
> oh, i forgot its page one :),
do the **./autogen.sh** then **./configure --prefix=/usr --disable-wine** , see if it will look for x development again. if you meant file transfer? yes its working. with progress bars and download manager.

loell,

Yep those are the commands I gleaned from this thread.  Ran both, and that is where I got the error from.  Sorry  :oops:  I probably should have stated that. :)

Shane

---

### Post by loell on 2008-04-30
i seldom have this X dev dependency showed up, whenever this happens i think i always check for either libtool or autoconf if its installed or not.

---

### Post by shane2peru on 2008-04-30
> **loell said:**
> i seldom have this X dev dependency showed up, whenever this happens i think i always check for either libtool or autoconf if its installed or not.

loell,

yep, got those installed and automake, and build-essential.  Odd,  I looked up X and dev and found xorg-dev but that required a lot of packages, and many had to do with Xorg, I'm not sure I'm ready to mess up my desktop already. :)

Shane

---

### Post by ShelJ on 2008-05-01
Got it working, just used getlibs to install lib dependancies.  Thanks so much for all the help!!

---

### Post by shane2peru on 2008-05-01
> **ShelJ said:**
> Got it working, just used getlibs to install lib dependancies.  Thanks so much for all the help!!

Shelj,  Can you expand on that?  What is getlibs?  Is it a package, is it  something for apt-get?  did you download it from the gyachi web site?

Shane

---

### Post by ShelJ on 2008-05-02
I followed from another thread, but simply put, it's in the repos. Try ```
sudo getlibs /usr/bin/gyachi
``` if you don't have it ```
sudo apt-get install getlibs
```


Now, how do I get my cam working.  When I tried it the other person got "webcam not available." and I got the same message when I tried voice chat.

---

### Post by shane2peru on 2008-05-02
> **ShelJ said:**
> I followed from another thread, but simply put, it's in the repos. Try ```
sudo getlibs /usr/bin/gyachi
``` if you don't have it ```
sudo apt-get install getlibs
```


Now, how do I get my cam working.  When I tried it the other person got "webcam not available." and I got the same message when I tried voice chat.

Oooh, I'm still back on step one, Compiling. :)  Won't compile for me.

Shane

---

### Post by ShelJ on 2008-05-02
Yeah, I know how you feel, I tried 3 package versions b4 I got this far, and onl in 5 short days!!!  lol.

---

### Post by Sef on 2008-05-02
When I went to install get libs, I got this message:

> sef@jokat:~$ sudo apt-get install getlibs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package getlibs


I can't find it in Synaptic either. :confused:

---

### Post by ShelJ on 2008-05-03
Sorry, but it worked in mine, both ways.  Either it's new or something to do wit my settings.  I'ts maintained by Cappy in the repos according to SPM.

---

### Post by loell on 2008-05-03
you mean this one? [http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")

neat script btw :)

---

### Post by Sef on 2008-05-03
Thanks for that link loell.  I got Gyachi up and running now.  :)

---

### Post by ShelJ on 2008-05-03
> **loell said:**
> you mean this one? [http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")

neat script btw :)

Yeah, Thanks.  I got it through another thread that was to do w/ installing Skype and it led me in the right direction, but when i followed the directions i found that I had it installed already, but I didn't install it myself.

Any idea how i can get the webcam and voice chat features working?

---

### Post by ralyon on 2008-05-15
> **loell said:**
> oh, i forgot its page one :),
do the **./autogen.sh** then **./configure --prefix=/usr --disable-wine** , see if it will look for x development again. if you meant file transfer? yes its working. with progress bars and download manager.

I'm going to try to compile on my x64 soon, but I wanted to know why you have --disable-wine. Is there any functionality loss with doing this? I ask because I have wine installed and running fine.

Also, I'd be happy to create a deb for the x64 version. I've not created one before but I think its about time I learned. Hardy is the first version I've seen where the x64 seems to have everything working finally so I think we are going to start seeing more people using it now since pretty much all modern processors are x64 enabled. Send me the info on how to create a deb and I'll do it as soon as I can.

ralyon

---

### Post by Sef on 2008-05-15
Reinstalled Ubuntu and got Gyachi reinstalled, but when I click on it, nothing happens.  I got the icon up, but what else do I need to do?

---

### Post by Yellow Pasque on 2008-05-15
Permissions problem? Try starting gyachi in the terminal.

---

### Post by loell on 2008-05-15
> **ralyon said:**
> I'm going to try to compile on my x64 soon, but I wanted to know why you have --disable-wine. Is there any functionality loss with doing this? I ask because I have wine installed and running fine.

Also, I'd be happy to create a deb for the x64 version. I've not created one before but I think its about time I learned. Hardy is the first version I've seen where the x64 seems to have everything working finally so I think we are going to start seeing more people using it now since pretty much all modern processors are x64 enabled. Send me the info on how to create a deb and I'll do it as soon as I can.

ralyon

yes there will be a missing functionality when you disable-wine its an old code from wine highly stripped to fit gyachi. the room voice chat won't function. 

yes, it would be nice to have x64 package, i'll be giving you a rough guide on what to invoke plus i'll give a debianize source. but before that do make sure that you can compile the source, so we'll concentrate on packaging questions.

---

### Post by Sef on 2008-05-15
> Permissions problem? Try starting gyachi in the terminal. 

This is what I get when I start from the terminal:

> gyachi: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory


So what do I do to fix it?  Thank you in advance.

---

### Post by loell on 2008-05-16
maybe install libgkthml package via getlibs?

---

### Post by Yellow Pasque on 2008-05-16
Sef, on my system, that file is a symbolic link to libgtkhtml-2.so.0.0.0  As loell pointed out, that should be created automatically when you:
```
sudo apt-get install libgtkhtml2-0
```
If not, make sure you have the file and create your own link:
```
cd /usr/lib
file libgtkhtml-2.so.0.0.0
sudo ln -s libgtkhtml-2.so.0.0.0 libgtkhtml-2.so.0
```

---

### Post by Sef on 2008-05-16
Still the same results.

Here is the results of posting the codes:

> sef@jokat1:~$ sudo apt-get install libgtkhtml2-0
[sudo] password for sef: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtkhtml2-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sef@jokat1:~$ cd /usr/lib
sef@jokat1:/usr/lib$ file libgtkhtml-2.so.0.0.0
libgtkhtml-2.so.0.0.0: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), stripped
sef@jokat1:/usr/lib$ sudo ln -s libgtkhtml-2.so.0.0.0 libgtkhtml-2.so.0
ln: creating symbolic link `libgtkhtml-2.so.0': File exists
sef@jokat1:/usr/lib$ 


Everything seems to be in order.

---

### Post by Sef on 2008-05-16
> maybe install libgkthml package via getlibs? 

How would I do that?

---

### Post by loell on 2008-05-16
from the getlibs thread, more likely it would be

```
getlibs -l libgtkhtml-2.so.0
```

---

### Post by Sef on 2008-05-16
```
getlibs -l libgtkhtml-2.so.0
```

Thank you. That worked.

---

### Post by ralyon on 2008-05-17
Ok, after satisfying all the dependencies for autogen I was able to get it installed. It loads, but its not connecting. Here is a debug I got but it doesn't appear to have anything useful.

```

GyachE Improved, version 1.1.31
Copyright (c) 2007-2008 Gregory D. Hosler
Copyright (c) 2006 Stefan Sikora
Copyright (c) 2003-2005, Erica Andrews
http://gyachi.sourceforge.net/
License: GNU General Public License

CONNECTION LOG
05/16/2008 23:50:38
_____________________


[05/16/2008 23:50:38] TEXT BUFFER ADDITION: [2m[#8F4CB1mGyachE Improved 1.1.31 
http://gyachi.sourceforge.net/[x2m[30m


[05/16/2008 23:50:38] TEXT BUFFER ADDITION:  Plugin Loaded[#8F4CB1m:  'Blowfish-Internal' 
[30m

[05/16/2008 23:50:38] TEXT BUFFER ADDITION:  Plugin Loaded[#8F4CB1m:  'Gpgme' 
[30m

[05/16/2008 23:50:38] TEXT BUFFER ADDITION:  Plugin Loaded[#8F4CB1m:  'MCrypt' 
[30m

[05/16/2008 23:50:38] TEXT BUFFER ADDITION:  Plugin Loaded[#8F4CB1m:  'GyachI-libNotify' 
[30m

[05/16/2008 23:50:38] TEXT BUFFER ADDITION: [#73B7DBm Loaded 4 plugins from '/usr/lib/gyachi/plugins'.

[30m

[05/16/2008 23:51:02] STARTING CONNECTION - CONNECTION SETTINGS:
Using Web Login Method: No
User: ralyon96
Host: scs.msg.yahoo.com
Port: 5050
Initial Chat Room: Linux, FreeBSD, Solaris:1
Packet Debugging: Yes
Initially Invisible: No


[05/16/2008 23:51:02] OUTGOING PACKET SENT: Size: 33, Data: [YMSG
W]

[05/16/2008 23:51:21] TEXT BUFFER ADDITION:   

[05/16/2008 23:51:21] TEXT BUFFER ADDITION:   [#C81447m** Could not login: Connection timed out. [ Could not login: Connection timed out. ] **[30m


[05/16/2008 23:51:21] TEXT BUFFER ADDITION:   [#0000D9m[1mDisconnected from Yahoo!    See Ya![x1m[30m  Online for  0 : 00 : 19



[05/16/2008 23:51:21] INFO-DIALOG MESSAGE: 'Could not login: Connection timed out.'
```

Also, I tried first configuring without the disabled-wine switch and this is what I got with make:

```
In file included from wine/winbase.h:5,
                 from afl.c:24:
wine/winnt.h:625:2: error: #error You need to define a CONTEXT for your CPU
In file included from wine/winbase.h:5,
                 from afl.c:24:
wine/winnt.h:628: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
wine/winnt.h:754:2: error: #error You need to define DEFINE_REGS_ENTRYPOINT macros for your CPU
wine/winnt.h:765:3: error: #error You must define GET_IP for this CPU
wine/winnt.h:1021: error: expected specifier-qualifier-list before ‘PCONTEXT’
wine/winnt.h:1034: error: expected declaration specifiers or ‘...’ before ‘PCONTEXT’
In file included from afl.c:24:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from afl.c:24:
wine/winbase.h:1342: error: expected declaration specifiers or ‘...’ before ‘CONTEXT’
wine/winbase.h:1481: warning: type defaults to ‘int’ in declaration of ‘CONTEXT’
wine/winbase.h:1481: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
afl.c: In function ‘ACM_GetStream’:
afl.c:46: warning: cast to pointer from integer of different size
afl.c: In function ‘acmDriverAddA’:
afl.c:73: warning: cast from pointer to integer of different size
afl.c: In function ‘acmDriverEnum’:
afl.c:134: warning: cast from pointer to integer of different size
afl.c: In function ‘acmDriverID’:
afl.c:157: warning: cast from pointer to integer of different size
afl.c: In function ‘acmDriverOpen’:
afl.c:232: warning: cast from pointer to integer of different size
afl.c: At top level:
afl.c:260: warning: cast from pointer to integer of different size
afl.c: In function ‘MSACM_UnregisterDriver’:
afl.c:303: warning: cast from pointer to integer of different size
afl.c: In function ‘MSACM_GetDriverID’:
afl.c:342: warning: cast to pointer from integer of different size
afl.c: In function ‘MSACM_GetDriver’:
afl.c:350: warning: cast to pointer from integer of different size
afl.c: In function ‘MSACM_GetObj’:
afl.c:358: warning: cast to pointer from integer of different size
afl.c: In function ‘acmStreamOpen’:
afl.c:414: warning: cast from pointer to integer of different size
afl.c:426: warning: cast from pointer to integer of different size
afl.c:464: warning: cast from pointer to integer of different size
afl.c:471: warning: cast from pointer to integer of different size
afl.c:493: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamClose’:
afl.c:517: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamConvert’:
afl.c:564: warning: cast from pointer to integer of different size
afl.c:564: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamPrepareHeader’:
afl.c:612: warning: cast from pointer to integer of different size
afl.c:612: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamReset’:
afl.c:650: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamSize’:
afl.c:693: warning: cast from pointer to integer of different size
afl.c:693: warning: cast from pointer to integer of different size
afl.c: In function ‘acmStreamUnprepareHeader’:
afl.c:744: warning: cast from pointer to integer of different size
afl.c:744: warning: cast from pointer to integer of different size
make[2]: *** [afl.o] Error 1
make[2]: Leaving directory `/home/ralyon/src/gyachi/gyvoice'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ralyon/src/gyachi'
make: *** [all] Error 2
```

I'm guessing this is expected? Voice chat is one of the primary reasons I use gyachi so is there any way to get this working? BTW I do have wine-dev installed and wine does work fine on this pc.

Thanks for all your help,
ralyon

---

### Post by loell on 2008-05-17
gyachi's wine is self contained its in **gyvoice** source directory, so wine-dev won't have any effect, i guess you'll gonna have to settle with installing gyachi through the use of getlibs if you would like to use the room voice chat.

---

### Post by ralyon on 2008-05-17
That answered the second question, but what about the first. I still want to help make a deb for 64 bit if you want it.

ralyon

---

### Post by Sef on 2008-05-17
> That answered the second question, but what about the first. I still want to help make a deb for 64 bit if you want it.

A 64-bit deb would be great.  I would help out, but I have no idea, how to do it.

---

### Post by loell on 2008-05-17
could you a make clean

then redo the whole process of compiling? see if theres any change.

---

### Post by ralyon on 2008-05-18
I did a make clean, autogen, configure --prefix=/usr --disable-wine, make and make install without any errors, but still not able to connect. Same problem as before.

ralyon

---

### Post by loell on 2008-05-19
the developer just made a few changes to better x64

can you try building 1.1.32? get it from the CVS

also do a **make uninstall** to uninstall 1.1.31 before compiling 1.1.32

see if it can connect now..

---

### Post by ralyon on 2008-05-19
Ok, did a sudo make uninstall, moved the folder and downloaded a fresh copy from the cvs, ./autogen.sh, ./configure --prefix=/usr --disable-wine, make, make install with no errors and same issue when I tried to log in.

Log file:
```
GYachE Improved, version 1.1.32
Copyright 2007, Gregory D Hosler
Copyright 2006, Stefan Sikora and Zoltan Csala
Copyright (c) 2003-2005, Erica Andrews
http://gyachi.sourceforge.net/
License: GNU General Public License

INSTANT MESSAGE SESSION LOG
Mon May 19 18:20:36 2008

_____________________

  * Logging PM to file : '/home/ralyon/.yahoorc/gyach/log/gyachi-logs/2008-05-19.182036.txt' *

GyachE Improved, version 1.1.32
Copyright (c) 2007-2008 Gregory D. Hosler
Copyright (c) 2006 Stefan Sikora
Copyright (c) 2003-2005, Erica Andrews
http://gyachi.sourceforge.net/
License: GNU General Public License

CONNECTION LOG
05/19/2008 18:20:36
_____________________

GyachE Improved 1.1.32 
http://gyachi.sourceforge.net/
 Plugin Loaded:  'Blowfish-Internal' 
 Plugin Loaded:  'Gpgme' 
 Plugin Loaded:  'MCrypt' 
 Plugin Loaded:  'GyachI-libNotify' 
 Loaded 4 plugins from '/usr/lib/gyachi/plugins'.

    ** Could not login: Connection timed out. [ Could not login: Connection timed out. ] **
  Disconnected from Yahoo!    See Ya!  Online for  0 : 00 : 19

```

Debug file:
```
GyachE Improved, version 1.1.32
Copyright (c) 2007-2008 Gregory D. Hosler
Copyright (c) 2006 Stefan Sikora
Copyright (c) 2003-2005, Erica Andrews
http://gyachi.sourceforge.net/
License: GNU General Public License

CONNECTION LOG
05/19/2008 18:20:36
_____________________


[05/19/2008 18:20:36] STARTING CONNECTION - CONNECTION SETTINGS:
Using Web Login Method: No
User: ralyon96
Host: scs-dcnb.msg.yahoo.com
Port: 5050
Initial Chat Room: Linux, FreeBSD, Solaris:1
Packet Debugging: Yes
Initially Invisible: No


--------------------------------
05/19/2008 18:20:36
--------------------------------
sess id   : 4294967295
data len  : 0
pkt type  : 0x57 (87)
59 4d 53 47 00 00 00 00 00 0d 00 00 00 00 00 00 00 00 00 57 
Y  M  S  G  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  W  
                                                   

[05/19/2008 18:20:36] OUTGOING PACKET SENT: Size: 33, Data: [YMSG
W]

[05/19/2008 18:20:37] TEXT BUFFER ADDITION: [2m[#8F4CB1mGyachE Improved 1.1.32 
http://gyachi.sourceforge.net/[x2m[30m


[05/19/2008 18:20:37] TEXT BUFFER ADDITION:  Plugin Loaded[#8F4CB1m:  'Blowfish-Internal' 
[30m

[05/19/2008 18:20:37] TEXT BUFFER ADDITION:  Plugin Loaded[#8F4CB1m:  'Gpgme' 
[30m

[05/19/2008 18:20:37] TEXT BUFFER ADDITION:  Plugin Loaded[#8F4CB1m:  'MCrypt' 
[30m

[05/19/2008 18:20:37] TEXT BUFFER ADDITION:  Plugin Loaded[#8F4CB1m:  'GyachI-libNotify' 
[30m

[05/19/2008 18:20:37] TEXT BUFFER ADDITION: [#73B7DBm Loaded 4 plugins from '/usr/lib/gyachi/plugins'.

[30m

[05/19/2008 18:20:55] TEXT BUFFER ADDITION:   

[05/19/2008 18:20:55] TEXT BUFFER ADDITION:   [#C81447m** Could not login: Connection timed out. [ Could not login: Connection timed out. ] **[30m


[05/19/2008 18:20:55] TEXT BUFFER ADDITION:   [#0000D9m[1mDisconnected from Yahoo!    See Ya![x1m[30m  Online for  0 : 00 : 19



[05/19/2008 18:20:55] INFO-DIALOG MESSAGE: 'Could not login: Connection timed out.'
```

Is there anything else I can try? This user name and password works on yahoos website and pidgin.

---

### Post by loell on 2008-05-19
start gyachi from the terminal , and in the connection menu check **packet debugging** once you attempt to log in, switch to the terminal, copy and paste the output.

---

### Post by ralyon on 2008-05-19
I already had that checked from when I gave you the logs and nothing comes up in the terminal. Just drops back to a prompt when I close gyachi.

I forgot to mention that I also renamed the .yahoorc folder and it created a new one to make sure it wasn't a setting throwing it off.

---

### Post by loell on 2008-05-21
hi, there seems to no packet sent, so this probably is a bug for 64bit gyachi. if you would be so kind to bring this up in gyachi forum?

[http://gyachi.sourceforge.net/forums.shtml]("http://gyachi.sourceforge.net/forums.shtml") in the open discussion.

---

### Post by ralyon on 2008-05-26
Well, I've posted there, but I haven't had much response. Was there some way that I could get more attention for that?

---

### Post by loell on 2008-05-26
unfortunately none :(

a bug is left at the mercy seat of the developer(s),  he is on travel/work, as far as i can tell.

---

### Post by Envy Geek on 2008-05-26
Ralyon,
I had the same problem, so I dove into the source and came up with something. I think I fixed it(i.e. It worked for me). 
I changed all the u_long to u_int in the source files.  
What I think happens is this: u_long for 64 bit systems is 8bytes, but the source of course was expecting 4bytes(default for 32 bit system). I probably broke something else, but it logs in now, and this is a start if you have time to look at it. 
Hope this helps.
 
Godspeed 

Note: I posted this in the GYachE Improved forum also.

---

### Post by loell on 2008-05-26
wow, good digging on the code :)

---

### Post by loell on 2008-05-27
@ralyon and envy geek, could you compile versions 1.1.26 and 1.1.27?

so if we can confirm if its also affects previous versions and rule out the suspicion that this might be a cause of code change.

---

### Post by Envy Geek on 2008-05-27
Yup, It's most likely a change between 1.1.26 and 1.1.27.
1.1.26 works unchanged.
1.1.27 does not.

---

### Post by mark clark on 2008-07-15
just wonder if  post download   on here  for 64 bit

---

### Post by nazrysamaratin on 2008-11-02
loell, how to install * Gyachi - gtk+ Yahoo Client with webcam and room voice chat features( i see it at ur lunchpad). i use hardy 64bit 
( newbie ubuntu & linux )
 
go to terminal 

deb [http://ppa.launchpad.net/loell/ubuntu](http://ppa.launchpad.net/loell/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/loell/ubuntu](http://ppa.launchpad.net/loell/ubuntu) hardy main

sudo apt-get instal Gyachi - gtk+

that it right
sorry for my English not my mother tongue

---

