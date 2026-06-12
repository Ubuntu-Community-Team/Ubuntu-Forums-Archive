---
title: "Firefox 1.5 with Flash and Java working 100% in amd64"
date: 2006-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by kurushi on 2006-01-04
Hi

I wrote a tutorial some days ago, about how to use Firefox 1.5 with Flash and Java support in Ubuntu Breezy for amd64. The method doesn't use  the complicated (in my opinion) 'chroot' installation. 

I hope it will help you. This is the link :

:KS  [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

Tell me how is it working for you, or if you have some kind of problem


See you soon, kisses

---

### Post by tripleee on 2006-01-05
Nice howto, thanks!

Do you think it could be better coordinated with [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) perhaps?

Also, could you please add a link back to this forum. Thank you.

---

### Post by PhilOSparta on 2006-01-07
[QUOTE=kurushi]Hi

I wrote a manual some days ago, about how to use Firefox 1.5 with Flash and Java support in Ubuntu Breezy for amd64. The method doesn't use  the complicated (in my opinion) 'chroot' installation. 

I hope it will help you. This is the link :

:KS  [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

Tell me how is it working for you, or if you have some kind of problem

[/QUOTE]

Great work!  Both worked fine except the sound in flash didn't work.

On another thread, I found a solution for sound with flash.
The fix, which appears to be a common solution, worked i.e.
This line fixed my problem:
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

---

### Post by kurushi on 2006-01-07
Thank you for your tip, I wrote your comment in the wiki, to help people fix the sound problem if they have it :D

---

### Post by handy on 2006-01-07
[QUOTE=kurushi]Hi

I wrote a manual some days ago, about how to use Firefox 1.5 with Flash and Java support in Ubuntu Breezy for amd64. The method doesn't use  the complicated (in my opinion) 'chroot' installation. 

I hope it will help you. This is the link :

:KS  [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

Tell me how is it working for you, or if you have some kind of problem

See you soon[/QUOTE]


Congratulations on a very well written How-To, I know it has helped many 64bit users.

For some reason when I followed your instructions I lost Firefox alltogether?  :confused: 

Not being happy with a very recent  install of IE6 via WineTools, I chose to do a total reinstall, & give the 32bit Breezy a run.  I'm now happier in 32bit.  :p 

So, I suppose that inadvertently you did me a favour in writing the How-To anyway... :KS

Cheers,

handy

---

### Post by rplantz on 2006-01-10
[QUOTE=kurushi]Hi
Tell me how is it working for you, or if you have some kind of problem
[/QUOTE]

It works quite well for me, but I seem to have lost the ability to use yelp.

When I look at the Properties->Dependencies of the yelp package in Synaptic, I see firefox listed. I guess that yelp cannot use this new firefox installation?

Anyone else having this problem?

I've tried complete removal and then installation of yelp. Still doesn't work. I can live without yelp, but I'm curious about what went wrong.

---

### Post by gordyt on 2006-01-13
Kurushi this worked perfectly on my system.  There was one very minor deviation I noticed when I followed the procedure.  In the part where you write:

(When the installer asks you for the 'navigator path', write : /usr/local/firefox32/)

The flash installer didn't ask me anything.  It did say that it was installing the plugin to ~/.mozilla/plugins.  I let it go ahead and put it there.  I figured that at the worst, it may mess up the behavior of 64-bit Firefox, which I don't plan  on using until flash gets ported to 64-bits.  And if it does mess it up, I can always move the flash plugin to another location.

Anyway everything worked perfectly (sound included), so thanks very much!

--gordon

---

### Post by happyponcho42 on 2006-01-16
Flash and Java now seem to work now.  Thanks for the great how-to.

I do have 2 minor issues that I can't seem to find the answer to.

Firstly, after following the how-to and successfully installing Firefox 1.5 w/Flash and Java, the Firefox window seems to have lost it's logo:
[IMG]http://img16.imageshack.us/img16/1127/screenshot5im.png[/IMG]

The second issue is that around flash objects, there is always a white box.  I'm guessing this has something to do with transparency?  As I previously stated, these are just minor issues that I have no problem with, but if there are any solutions to these, it would be greatly appreciated.

Does anyone happen to suffer from the same problems and have found a work around?


Thanks

---

### Post by tripleee on 2006-01-17
[QUOTE=tripleee]Do you think it could be better coordinated with [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) perhaps?

Also, could you please add a link back to this forum. Thank you.[/QUOTE]

I went ahead and made some minor edits myself.

On a different note, I've installed according to the FirefoxNewVersion and not been using linux32. Also, I don't care much for Flash or Java, so I haven't even begun to tackle those.

For the most part, this is working, although I have experienced the following problems:
[LIST]
[*]Drag and drop freezes Firefox solid. I'm not eager to repro this in my production environment, but based on a few cases, I'd say this happens every time.
[*]Copy and paste between Firefox and GNU Emacs is completely broken. It has always been erratic, but with 1.0.7 it worked sometimes. Now it never works. (I believe there are several bugs open about this.)
[*]Firefox occasionally "times out" and takes a long time to render its windows (e.g. if I switch quickly to a different virtual desktop and then back, I can sit literally for minutes with blank windows in front of me. Other apps continue to work, it's just Firefox which is catatonic.) This used to happen with 1.0.7 as well, maybe more frequently.
[*]Firefox has crashed on me maybe half a dozen times during the week I've been using it. This is not a significantly worse track record than with 1.0.7, although subjectively, I'd say it's a little more crash-prone than 1.0.7.
[*]Displaying a system file picker (open / save as .. / etc) takes eons. It comes up just fine but then Firefox displays a spinning cursor for I think several minutes and doesn't update its windows
[*]All window titles are gone. This could be an integration problem with Sawfish, as I use that as my window manager instead of the Gnome standard (Metacity? Atrocity?)
[/LIST]
I am a heavy user of tabs, and have about 100 of them open in several Firefox windows. Performance is occasionally sluggish, but much less so than with 1.0.7, which (predictably, given the memory leaks and the even bigger memory footprint to begin with) was close to unusable for me.

I have SessionSaver which throws some errors into the JavaScript console but otherwise seems to continue to work like a charm.

I guess I ought to try with linux32 to see if it would solve any of these problems.

---

### Post by xeta on 2006-01-17
Just wanted to post that this worked for me. Thanks!

---

### Post by cnspy on 2006-01-20
does it mean that using the 32bit program on the AMD64 system?

Does this method can be used on the stardict program and the dictionary files?

---

### Post by who_cares on 2006-01-20
Is there no 64 bit version availible?

---

### Post by Heretic Monkey on 2006-01-22
I have the same problem as HappyPoncho.  The toolbar and window seem to have lost the logo from the conversion.

How would i/we go about getting it re-logo-fied?

---

### Post by zxg32 on 2006-01-23
Hi,

I'm running kubuntu-5.10-amd64 with 32-bit firefox and macromedia
flash plugin (there is no 64-bit flash plugin yet). I followed this how-to
and it can play flash audio when artsd is not running.

My question is, how is that possible? The alsa sound driver is 64-bit,
I installed ia32-libs, ia32-libs-gtk, ia32-libs-kde, but can't find any
sound related binaries under /lib32, /usr/lib32, /usr/X11R6/lib32.
How could 32-bit app use 64-bit lib?

Thanks.

---

### Post by RAOF on 2006-01-24
[QUOTE=zxg32]Hi,

I'm running kubuntu-5.10-amd64 with 32-bit firefox and macromedia
flash plugin (there is no 64-bit flash plugin yet). I followed this how-to
and it can play flash audio when artsd is not running.

My question is, how is that possible? The alsa sound driver is 64-bit,
I installed ia32-libs, ia32-libs-gtk, ia32-libs-kde, but can't find any
sound related binaries under /lib32, /usr/lib32, /usr/X11R6/lib32.
How could 32-bit app use 64-bit lib?

Thanks.[/QUOTE]The kernel can interface with 32bit code (that's necessary for it to run 32bit programs :)).  As the sound drivers are (kinda) part of the kernel, you get 32bit interfacing thrown in.

---

### Post by slavik on 2006-01-24
Would it be possible to install the 32bit 1.5 Java JRE AND the 64bit Java JDK?

---

### Post by Lothlómendil on 2006-01-24
[QUOTE=PhilOSparta]Great work!  Both worked fine except the sound in flash didn't work.

On another thread, I found a solution for sound with flash.
The fix, which appears to be a common solution, worked i.e.
This line fixed my problem:
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1[/QUOTE]
I was browsing this forum for some information on another subject, and noticed this topic. I too had the problem where flash + sound wouldn't work, and I saw this post. I entered this into the terminal, and it has entirely broken my flash. :eek: If I load any page with flash in it, Firefox crashes. I tried entering:

sudo rm /usr/lib/libesd.so.1

to undo whatever it is that was done. It didn't work. When I enter:

ls -l /usr/lib | grep esd

It says this:
```
lrwxrwxrwx   1 root root       16 2006-01-21 22:57 libesd.so.0 -> libesd.so.0.2.36
-rw-r--r--   1 root root    42576 2005-08-22 07:54 libesd.so.0.2.36
```
It says the link is gone, but it is still misbehaving.

This change is the only change I've made to anything today. Any advice on how to undo the breakage that I've caused? Oh, and you should all know that I'm still very new to Ubuntu, so take it easy on me. :) My computer information is in my signature.

---

### Post by rplantz on 2006-01-25
[QUOTE=Lothlómendil]
This change is the only change I've made to anything today. Any advice on how to undo the breakage that I've caused? Oh, and you should all know that I'm still very new to Ubuntu, so take it easy on me. :) My computer information is in my signature.[/QUOTE]

While playing around with Firefox on my amd64, I've run into this sort of thing several times. The latest is that when I launch the old 64-bit 1.0.7 version, it trashes my 32.-bit 1.5. I recently learned that I can "reset" things by deleting the file ```

~/.mozilla/firefox/******.default/compreg.dat
```
and relaunching Firefox. It generates a new compreg.dat file. (Each installation of Firefox seems to give a different name for ******.default.)

I recommend being careful with this. The first time I did it, I moved compreg.dat to another directory and changed its name. That way I could restore it if necessary.

Don't know if this will work in your case.

---

### Post by slavik on 2006-01-25
Do you have both firefox versions set to use the same profile?

---

### Post by Lothlómendil on 2006-01-25
[QUOTE=rplantz]While playing around with Firefox on my amd64, I've run into this sort of thing several times. The latest is that when I launch the old 64-bit 1.0.7 version, it trashes my 32.-bit 1.5. I recently learned that I can "reset" things by deleting the file ```

~/.mozilla/firefox/******.default/compreg.dat
```
and relaunching Firefox. It generates a new compreg.dat file. (Each installation of Firefox seems to give a different name for ******.default.)

I recommend being careful with this. The first time I did it, I moved compreg.dat to another directory and changed its name. That way I could restore it if necessary.

Don't know if this will work in your case.[/QUOTE]
Thanks for the advice, but it doesn't seem to have done the trick.

I should have just been happy with flash working the way it was, heh. It is a fresh install of Ubuntu, and everything worked fine (excluding the flash sounds), sigh. Now it seems the only way to get things to work again is to go with the 32 bit version. If anyone else has an idea on how to get things working for the 64 bit version again, I'm all ears. :D

---

### Post by Bandit on 2006-01-26
Look great. I will defently try this soon as I get my Radeon card issues resolved..
Thanks,
Joey

---

### Post by lychee on 2006-01-28
hi...

thanks for the howto; i can use java inside firefox now...

however, i cannot use the "open with" method of downloading and opening files with 64-bit applications.

for e.g. if i click on a "zip" file and choose to open it with file-roller, on the console window there are lots of gnome-segv's that look abit like:
(gnome_segv:11197): Gtk-WARNING **: /usr/lib32/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

after abit of investigation, it seems that the 32-bit-library-specific environment variables (i.e. GTK_PATH and PANGO_RC_FILE) are propagated to file-roller. If I run "GTK_PATH=/usr/lib32/gtk-2.0 PANGO_RC_FILE=/etc/pango32/pangorc file-roller" i get the same errors...

therefore, my questions are
(1) has anyone else encountered this problem?
(2) is there any workaround for it?

Thanks alot! :)

---

### Post by lychee on 2006-01-28
hmm to answer my own question, for (2), the workaround is:

instead of using the /etc/pango32/pangorc and PANGO_RC_FILE hack, use
LD_PRELOAD=/usr/lib32/libpangohack.so.0 instead.

apparently it 'overloads' pango_get_sysconf_subdirectory to return /etc/pango32 instead, so that the correct pango.modules file gets loaded. The beauty of it is that when firefox executes a 64-bit program, libpangohack.so.0 can't be loaded (as it is a 32-bit library). So everything works :) (and i just get an ugly
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0.0' from LD_PRELOAD cannot be preloaded: ignored.
occasionally, but that's fine :) )

---

### Post by bmk789 on 2006-01-28
its working great for me

---

### Post by hippomofatumas on 2006-01-29
Hi, 

This didn't work for me. I followed the instructions verbatim. I still have firefox 1.0.7 and no flash. Didn't try java. I'm new to linux and have only limited understanding. But I did do all the terminal stuff correctly, and it even said that flash was installed. Something isn't working right.

Please help this newbie,

hippomofatumas

---

### Post by tavo.buk on 2006-01-30
Its my firs try with an amd 64 and your how-to works really fine. I have a question, it is possivel to install skype in the same way? Thanks

---

### Post by rastamufasta on 2006-02-01
I'm having some trouble when I try to load java applets.. here's what I get:

VM did not start up properly
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
Could not read ack from child process
Plugin: Java VM process has died.
plugin: java process exited with status 1
Could not start JavaVM!


and a lot of these:

(firefox-bin:11607): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

Anyone know how I can fix this?   -Thanks

---

### Post by ispmarin on 2006-02-06
It worked, but the graphic window is not good: there are details that are lost, like the button to go, the buttons have no surface, just the words, etc.

---

### Post by almahtar on 2006-02-07
Worked great for me. Thank you very much!

---

### Post by MartinSco on 2006-02-08
Hello I have an AMD 64 and try to install like written on 
*[https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)*

Firefox ist running fine and  Macromedia Flash Player too

You are great !!
Thanks Martin

---

### Post by javaTard on 2006-02-09
I think I love you....... will you marry me?

Seriously, thank you for a top notch guide. i have tried fiddling with the old version that came with 5.10 64 and kept getting error after error. You are a life saver

---

### Post by hunteramor on 2006-02-10
anyone had any luck figuring out how to restore the logo/icon?

---

### Post by draven on 2006-02-13
I am unable to get FF to launch.

As non-root it does the following:

(this is strace output) [http://www.ima.umn.edu/~nate/ff32-error](http://www.ima.umn.edu/~nate/ff32-error)

As root it does this:

(this is strace output) [http://www.ima.umn.edu/~nate/ff32-error-root](http://www.ima.umn.edu/~nate/ff32-error-root)

The root output seems to point to this:

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/usr/local/firefox32/run-mozilla.sh: line 131:   394 Aborted                 "$prog" ${1+"$@"}

But other then that I have no idea why it doesn't work.

---

### Post by Freddd on 2006-02-14
I'm not allowed to do this step
> 4 - Create a folder for the 32 bits firefox installation, and copy firefox there :
      mkdir /usr/local/firefox32
      cp -r -p ./* /usr/local/firefox32/

Permission denied :(

---

### Post by manicka on 2006-02-14
[QUOTE=Freddd]I'm not allowed to do this step

Permission denied :([/QUOTE]

Try

sudo mkdir /usr/local/firefox32
sudo cp -r -p ./* /usr/local/firefox32/

---

### Post by Freddd on 2006-02-14
Thanks that did the trick :)

Now I'm not able to proceed here:
> 
6 - Write the next italic text to this file :

[Pango]

ModuleFiles=/etc/pango32/pango.modules

[PangoX]

AliasFiles=/etc/pango/pangox.aliases 

I get "couldn't save the file /etc/pango32/pangorc" when I'm trying to save the file.

I'm a novice so help is much appreciated :)

---

### Post by Freddd on 2006-02-14
Anyone? :(

---

### Post by Kwiatkowski on 2006-02-14
Websites like [www.pandora.com](www.pandora.com) need local storage for flash files activated. 

Right-click on a running flash movie, choosing properties, then the second record card (directory icon) and then moving the slider does not work. The plugin simply seems not to remember (you could check this yourself).

Do you have any ideas how to enable this caching feature an other way?

Thank you very much.

---

### Post by Freddd on 2006-02-14
Is it bad to this response when executing the following command:
> sudo apt-get install ia32-libs ia32-libs-gtk linux32
> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ia32-libs

Looks like an error message...

---

### Post by manicka on 2006-02-14
[QUOTE=Freddd]Thanks that did the trick :)

I get "couldn't save the file /etc/pango32/pangorc" when I'm trying to save the file.

I'm a novice so help is much appreciated :)[/QUOTE]

How did you open the file?

Try opening it with 

sudo gedit /etc/pango32/pangorc

---

### Post by Freddd on 2006-02-15
[QUOTE=manicka]How did you open the file?

Try opening it with 

sudo gedit /etc/pango32/pangorc[/QUOTE]

I tried it. I get an "empty" (pangorc) document opened. I wrote the text in it but I'm still not able to save it. Still getting the same message :(

---

### Post by Freddd on 2006-02-15
[QUOTE=Freddd]I tried it. I get an "empty" (pangorc) document opened. I wrote the text in it but I'm still not able to save it. Still getting the same message :([/QUOTE]

I think I know why I'm having problems. From what I know, I installed the regular version of ubuntu, not any special amd 64 version of the OS. May that be the answer to my problems? In windows I don't care about having amd64 since I use the 32bit version of XP. I'm still having problems getting flash to work though. Please tell me if I'm thinking totally wrong?

---

### Post by Jeffj on 2006-02-15
At step 10 my installation doesn't work.
I did log in as root using sudo instead of running each command as sudo.
what is pango?

I get the following errors:

firefox32 &
[1] 4774
jjm@moped:~$
(firefox-bin:4785): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:4785): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported
(QFA)Talkback error: Can't initialize.

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:4785): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported
Pango:/etc/pango32/pangorc: Error opening config file: No such file or directory

(firefox-bin:4785): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:4785): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:4785): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:4785): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:4785): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:4785): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:4785): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:4785): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:4785): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:4785): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:4785): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:4785): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/usr/local/firefox32/run-mozilla.sh: line 131:  4785 Aborted                 "$prog" ${1+"$@"}

---

### Post by Daggett on 2006-02-16
I am having problems getting it all to work in Kubuntu AMD64 with firefox-1.5.0.1.  Granted, I'm using 1.5.0.1, and the instructions call for 1.5. 

Neither flash nor java work at all.  I simply get the "missing plugin" boxes. 

The browser comes up fine, but only if I run it this way (see below).  In fact, the browser comes up fine even without the export or LD_PRELOAD.  The difference it that I can only get the browser to launch if I change to the browser directory.  

export GTK_PATH=/usr/lib32/gtk-2.0
LD_PRELOAD=/usr/lib32/libpangohack.so.0
cd /usr/local/firefox32
linux32 firefox $@

If I try to run it from outside the directory (as per the instructions for the shell file), I get this message:

/usr/local/firefox32/run-mozilla.sh: line 166: /usr/local/firefox32/firefox-bin: cannot execute binary file

Any ideas?  I don't want to go back to 1.5 unless it's necessary.

---

### Post by Enforcer on 2006-02-19
k i was able to install flash ok and that works but still cant get java to work even tho i installed it

(I am not running 64 btw.)

and the flash worked but java didnt

i followed the tut changing the paths from this

```
sudo bash

chmod 777 ./jre-1_5_0_06-linux-i586.bin

(this file name will depend on the java version you download)

./jre-1_5_0_06-linux-i586.bin

(it will ask you some questions)

mkdir /usr/local/java32

cp -r -p ./jre1.5.0_06/* /usr/local/java32

cd /usr/local/firefox32/plugins/

ln -s /usr/local/java32/plugin/i386/ns7/libjavaplugin_oji.so ./ 
```

to this

```
sudo bash

chmod 777 ~/Desktop/jre-1_5_0_06-linux-i586.bin

(this file name will depend on the java version you download)

~/Desktop/jre-1_5_0_06-linux-i586.bin

(it will ask you some questions)

mkdir /usr/lib/java

cp -r -p ./jre1.5.0_06/* /usr/lib/java

cd /usr/lib/mozilla-firefox/plugins/

ln -s /usr/lib/java/plugin/i386/ns7/libjavaplugin_oji.so ./ 
```

now the last line cmd there the 'ln -s blah blah blah' says the file already exists. This should work ok tho, unless i , hmm let me test something right quick

Edited:
K what i jsut tried was cd-ing to the usr/lib/mozilla/ and using this ln -s /usr/lib/java/plugin/i386/ns7/libjavaplugin_oji.so ./  to create or copy (not sure what this does if anyone wants to clerify) and i guess that worked but Java still inst working. So if anyone could help that b great!

---

### Post by viviena on 2006-02-20
I just want to say 'thank you' for this easy-to-follow guide. Firefox works like a dream now. :)

---

### Post by erthian on 2006-02-21
awsome!  works perfect.  great guide.  I didn't think I would ever get flash to work

---

### Post by xordae on 2006-03-02
Help! I'm using the Amd64 distro. Everything went well with the guide, Firefox32 is up and kicking, but sadly ALL checkboxes in my gnome disappeared. 

That is, they can be clicked, but they aren't there, and I cannot see if one is activated or not. (I noticed, when I switch to another Firefox theme with a background (Brushed theme) the checkboxes are there. I figure that is because they then look different, another picture set. But it still applies for my gnome.. i.e. OpenOffice and everywhere)

Any ideas?

Edit: Okay, it is not ALL checkboxes, just a certain style. As well, the borders of some boxes disappeared. Like when I open a file in OpenOffice, no borders around OK, cancel, read-only .. just the text.

2nd. Edit: Appears to be a theme problem. Other themes are okay, my custom theme isn't since that install. I'm looking into it, but it's not as big a problem anymore. ^^

---

### Post by kurushi on 2006-03-04
Sorry. I was very wrong with some solutions :(

---

### Post by Shed on 2006-03-04
[QUOTE=kurushi]
sudo echo "#!/bin/sh" >> /usr/local/bin/firefox32[/QUOTE]
Could anyone give me a clue? This line generates the error:

```
bash: !/bin/sh" >> /usr/local/bin/firefox32: event not found

```

I'm using AMD64 Breezy after the 4th March update.

---

### Post by psiko on 2006-03-10
It works great !! thanks for the how-to !!
But be carefulls, the hacks doesn't work with all gtk themes

---

### Post by heavyboots on 2006-03-30
Thanks for the excellent tutorial. Quick note if you're simultaneously working through the "How to install Firefox 1.5". If you replace the bits in here where it says /usr/local/firefox32 with /opt/firefox, it all works perfectly! (Er, except for the actual sh file firefox32--you want to leave that in /usr/local/bin, but link it back to /opt/firefox...

Anyways, thanks again, I feel much happier back in 1.5!

---

### Post by glaalex on 2006-04-04
This tutorial worked 100%.
I am new to Ubuntu (and Linux) , so i am happy that it worked the first time

Thanks

glaalex:p

---

### Post by Aphorism on 2006-04-09
Awsome post.  I added how to integrate RealPlayer10 support for this awsome firefox32 technique.  It worked for me.  YMMV.

Adjust the wiki if you spot any errors.

Thanks again brothers and sisters.

---

### Post by LazyBoy on 2006-04-12
Does  the flash on [www.macromedia.com](www.macromedia.com) have sound?  I'm not sure if flash audio is working yet.

BTW, the [www.bbc.com](www.bbc.com) stuff didn't work for me until I created a /usr/local/bin/realplay similar to the /usr/local/bin/firefox described in the guide.  Also I had to run it from the command line once to set the proxies.

Also, realplay works, but the icons are not correct.  All five buttons are some default "X" icon.  Any ideas?

Thanks,
LB

**Follow-up:**  This was solved here: [http://ubuntuforums.org/showthread.p...25#post1040925](http://ubuntuforums.org/showthread.p...25#post1040925)

---

### Post by nwillis on 2006-04-16
Has anyone else experienced trouble with the video in Flash?  I have crystal clear audio, but no picture on any Flash content (literally; I'd offer to attach a screenshot, but there ain't nothing to see).

Anyone?  heavyboots; I also installed to /opt/ -- did you have trouble w/Flash in your /opt install?

Nate

---

### Post by LazyBoy on 2006-04-28
Great how-to.

Anyone know how to fix the icons in the title bar and panel?
They've defaulted to boring X's.
(The running application icons, not the launcher icons -- see attachment.)

Thanks,
LB

**Follow-up:** This was solved below: [http://ubuntuforums.org/showthread.p...25#post1040925](http://ubuntuforums.org/showthread.p...25#post1040925)

---

### Post by LazyBoy on 2006-05-04
[QUOTE=LazyBoy]Great how-to.

Anyone know how to fix the icons in the title bar and panel?
They've defaulted to boring X's.
(The running application icons, not the launcher icons -- see attachment.)

Thanks,
LB[/QUOTE]

BTW, I'm running KDE/Kubuntu.

Also, when I log out (close my session) and log back in,
KDE/Kubuntu restarts firefox for me.  But it restarts the
old firefox.

Any ideas for this or my earlier post?

Thanks,
LB

---

### Post by exp(x) on 2006-05-06
I have the default icon issue as well. Has nobody found a solution for this yet?

---

### Post by skippy81 on 2006-05-06
When installing Realplayer, should I say yes when it asks about building symbolic links please?

---

### Post by jinxed on 2006-05-07
Great HowTo! I finally have most of Firefox working as I did in my 32bit distro.

But... and this is a BIG but... I lost ALL MPlayer plug-in functionality. I tried linking the mozilla-firefox plugins to the /usr/local/firefox32/plugins directory, but alas... my video capabilities are still shot. 

Has anyone had the same problem?

---

### Post by exp(x) on 2006-05-07
[QUOTE=jinxed]Great HowTo! I finally have most of Firefox working as I did in my 32bit distro.

But... and this is a BIG but... I lost ALL MPlayer plug-in functionality. I tried linking the mozilla-firefox plugins to the /usr/local/firefox32/plugins directory, but alas... my video capabilities are still shot. 

Has anyone had the same problem?[/QUOTE]

Try putting the plugins in ~/.mozilla/plugins

---

### Post by yalig on 2006-05-07
This HowTo is great. I installed the Firefox 1.5 and it worked. After I installed the Realplayer32 and opened the BBC web page,  a message said ".. force quit to close .." when I closed the web page . Is this usual?

---

### Post by flapane on 2006-05-08
ok now flash java and realplayer are installed, everything ok, but I can't get sound from flash videos, neither from realplayer (standalone). I googled about alsa-oss issue with 32bit applications on 64bit, but I can't solve...

---

### Post by Necro-File on 2006-05-08
It works great for me. Now I just need to figure out how to get embedded sound and embedded video sounds to work on sites like youtube and ytmnd for it to be complete.

---

### Post by flapane on 2006-05-09
well i can get sound for flash plugin but ONLY BY DISABLING ALSA SOUND SYSTEM!
audio from flash files works, and also audio from Realplayer.
why?

---

### Post by lukeblack on 2006-05-12
Works great - but when I run firefox32, it seems to run several different applications, which when I kill manually dont affect my browser. Did I install it wrong?

 5611 ?        00:00:00 firefox32
 5612 ?        00:00:00 firefox
 5617 ?        00:00:00 run-mozilla.sh
 5622 ?        00:00:00 firefox-bin

---

### Post by X3N on 2006-05-14
[QUOTE=happyponcho42]Flash and Java now seem to work now.  Thanks for the great how-to.

I do have 2 minor issues that I can't seem to find the answer to.

Firstly, after following the how-to and successfully installing Firefox 1.5 w/Flash and Java, the Firefox window seems to have lost it's logo:
[IMG]http://img16.imageshack.us/img16/1127/screenshot5im.png[/IMG]

The second issue is that around flash objects, there is always a white box.  I'm guessing this has something to do with transparency?  As I previously stated, these are just minor issues that I have no problem with, but if there are any solutions to these, it would be greatly appreciated.

Does anyone happen to suffer from the same problems and have found a work around?


Thanks[/QUOTE]

try removing "linux32" from  /usr/local/bin/firefox32/

I was having lots of problems when i had "linux32" in mine (though i'm using dapper beta2 so it might be different) 

Here was the fatal error I was getting: 
```

(firefox-bin:10242): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared object file: No such file or directory
/usr/local/firefox32/run-mozilla.sh: line 131: 10242 Segmentation fault      "$prog" ${1+"$@"}
```

I now do not get *any* errors or warnings when running firefox it is stable now. 

my  /usr/local/bin/firefox32 file looks like this: 

```
#!/bin/sh
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
/usr/local/firefox32/firefox
```

I tried it with the export commented out as well and it still worked.

---

### Post by dmery on 2006-05-16
I never see in my life a worst guide than this. Please go to Gentoo forum and learn to write a manual.
Regards,
Daniel Mery

---

### Post by dreadnought on 2006-05-17
I have just follwed these instructions and now have firefox working with java, flash and realplayer without any problems (I'm using Dapper amd64). Many thanks to those who have contributed. 

Don't understand the last comment by dmery. If I go to Gentoo forum will I see well written How Tos by dmery?

---

### Post by Strangerdave on 2006-05-18
Yeah, I followed the instructions to the letter and had no success.  I am a newbie at this so that may be a factor, but I get the following when I click on the created icon for Firefox32:

```
dave@Ubuntu:~$ firefox32 &
/usr/local/bin/firefox32: line 1: Desktop: command not found
[1] 8465
dave@Ubuntu:~$
(firefox-bin:8477): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:8477): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:8477): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported
(QFA)Talkback error: Can't initialize.

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:8477): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported
Pango:/etc/pango32/pangorc:1: A [SECTION] declaration must occur first

(firefox-bin:8477): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8477): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8477): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8477): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8477): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8477): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8477): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8477): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8477): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8477): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8477): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8477): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/usr/local/firefox32/run-mozilla.sh: line 131:  8477 Aborted                 "$prog" ${1+"$@"}

```

I don't know what any of this means, nor how to fix it.  Any and all suggestions would be greatly appreciated.

-SD-

---

### Post by LazyBoy on 2006-05-18
The new firefox doesn't show my printers in it's dialog.  :( 
The old one still does.

Any ideas?
LB

---

### Post by Kilz on 2006-05-22
Very nice toutorial. :D  32 bit firefox on amd64 was on my wishlist.

---

### Post by panurge77 on 2006-05-22
It worked for me for a couple days but now I get this error while trying to download from sourceforge

floyd@tchs:~$ firefox32

(firefox-bin:4915): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared object file: No such file or directory

(firefox-bin:4915): Gdk-CRITICAL **: gdk_drawable_get_size: assertion `GDK_IS_DRAWABLE (drawable)' failed

(firefox-bin:4915): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared object file: No such file or directory
/opt/swiftfox/run-mozilla.sh: line 131: 4915 Segmentation fault "$prog" ${1+"$@"}

Also.. sound work for flash only but not for flash with java (youtube)

---

### Post by Si Na Gréine on 2006-05-22
The problem with the icons occurs because the file /etc/gtk-2.0/gdk-pixbuf.loaders refers to icon loaders in /usr/lib/gtk-2.0 rather than in /usr/lib32/gtk-2.0. This means that 64 bit bitmap loaders are bing picked up rather than the 32-bit ones in /usr/lib32.

To fix this, we need to create a new gdk-pixbuf.loaders file that points at the 32 bit loaders. We cannot make this the default file as it might effect other true 64 bit applications. We therefore need to tell firefox to look at the 32-bit file. Here's how to do it:

Make the new file from the old file:
sed 's/\/usr\/lib\//\/usr\/lib32\//g' /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders.32

Now point Firefox at the alternative  gdk-pixbuf.loaders.32 file
<your_editor> /usr/local/bin/firefox32

insert the following line before the line beginning with "linux32"
export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32

The entire /usr/local/bin/firefox32 file now becomes:
#!/bin/sh

export GTK_PATH=/usr/lib32/gtk-2.0

export PANGO_RC_FILE=/etc/pango32/pangorc

export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32

linux32 /opt/firefox_1.5_32/firefox $@

---

### Post by panurge77 on 2006-05-22
[QUOTE=Si Na Gréine]
sed 's/\/usr\/lib\//\/usr\/lib32\//g' /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders.32[/QUOTE]

That's the most bizarre command I've ever seen in my short linux experience but guess what? It works, and I'm grateful for that. Cheers! :D

---

### Post by aimless on 2006-05-22
[INDENT]               [/INDENT]I followed this tutorial and got firefox working with Flash and Java.I have run into a few problems, though.The first one is the same one a lot of other people are having with the sound not working in Flash.Tried all the various solutions everyone has given.None of them worked.
   [INDENT][/INDENT] What I'm more concerned about now is getting the mplayer plugin to work with this setup.I've tried everything I can think of. I have two questions;[LIST=1]
[*] Is it possible to get the mplayer plugin working with this setup?
[*]Can anyone give me advice on how to do this or possibly a step by step (or a link to one) on how to do it?
[/LIST]

---

### Post by LazyBoy on 2006-05-22
Thanks Si Na Gréine!

LB

---

### Post by aimless on 2006-05-23
I guess no one knows how to get mplayer working with this setup. I tried this earlier suggestion.
---------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------
Quote:
Originally Posted by jinxed
Great HowTo! I finally have most of Firefox working as I did in my 32bit distro.

But... and this is a BIG but... I lost ALL MPlayer plug-in functionality. I tried linking the mozilla-firefox plugins to the /usr/local/firefox32/plugins directory, but alas... my video capabilities are still shot.

Has anyone had the same problem?

Try putting the plugins in ~/.mozilla/plugins
---------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------

DIDN'T WORK!!!!   It's hard to believe that this would be such a problem and big deal to get working. It's easy in the normal version of Firefox.

---

### Post by panurge77 on 2006-05-24
One last thing is youtube is still soundless. Anyone fixed that in dapper?

---

### Post by hajk on 2006-06-05
Quite an amazing tutorial FirefoxAMD64FlashJava is... everything installed and worked as the author said it would. :-D Why people keep whining about wanting to install this stuff in a chrooted 32-bit environment is beyond me. :???:  

And then I remembered that I was going to keep my 64-bit install as pure as snow, and that I also had installed 32-bit Dapper on another partition just in case I wanted to experience the joys of Flash, RealPlayer, w32codecs, etc. So, after all of this, I did a "sudo -rf /usr/local/{firefox32,java32,realplayer32}" and, oh yeah, also "sudo dpkg -i firefox" to get 64-bit Firefox going again properly.

It was quite a ride!=D>

---

### Post by gratefulfrog on 2006-06-05
Wow! That worked, just like it said, 100%!!! thanks!
GF
AMD64, Asus A7V de luxe, goobye dchroot!

---

### Post by gratefulfrog on 2006-06-09
[QUOTE=kurushi]Hi

I wrote a tutorial some days ago, about how to use Firefox 1.5 with Flash and Java support in Ubuntu Breezy for amd64. The method doesn't use  the complicated (in my opinion) 'chroot' installation. 

I hope it will help you. This is the link :

:KS  [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

Tell me how is it working for you, or if you have some kind of problem
[/QUOTE]

Hye this tutorial is gone, hijacked by the Java installation page!  Can we get it back??
thanks,
GF:confused:

---

### Post by Kilz on 2006-06-09
[QUOTE=gratefulfrog]Hye this tutorial is gone, hijacked by the Java installation page!  Can we get it back??
thanks,
GF:confused:[/QUOTE]
I wrote a email to the documentation team asking why, I refer people to the howto all the time. The java page they redirect to only has 1/3rd of the information. It doesn't help people setup 32 bit firefox , with flash and java the main concern of people running 64 a 64 bit os, just java into an already existing 32 bit installation.

---

### Post by Kilz on 2006-06-19
[QUOTE=Kilz]I wrote a email to the documentation team asking why, I refer people to the howto all the time. The java page they redirect to only has 1/3rd of the information. It doesn't help people setup 32 bit firefox , with flash and java the main concern of people running 64 a 64 bit os, just java into an already existing 32 bit installation.[/QUOTE]
It seems that they are ignoring me, so I wrote an updated Howto based on kurushi's and Im adding more plugins.
[http://www.ubuntuforums.org/showthread.php?t=202537&highlight=firefox+real+player](http://www.ubuntuforums.org/showthread.php?t=202537&highlight=firefox+real+player)

---

### Post by alphamerik on 2006-07-10
Thanks for this great tutorial!

Everything works great... except for the sound. :mad: 

The weird thing is... some applications work.  For instance, Google Video sound works, Homestar Runner flash sound works, but YouTube sound does not work.  :confused: 

I have tried creating the libesd link, and stoping artsd, neither have any effect.

Anybody have any ideas?  I am a willing subject to your experiments.

Thanks...

---

### Post by alphamerik on 2006-07-10
Nevermind, I fixed it! [-o< 

From a different thread, needed to chown:

chown -R <username>:users /home/<username>/.macromedia

This should be in the Wiki!   :rolleyes:

---

### Post by raheesom on 2006-07-28
I've followed your instructions some time ago, and largely the 32bit browser works, except that its very unstable - it will crash pretty easily.

The other problem I'm now working on, is that I'm using a java based service ([www.kanosis.com](www.kanosis.com)) which apparently needs lib libstdc++.so.5.  I've looked at the libraries I have installed (very confusing when having to remember to look at both 32bit and 64bit libraries!).   I have libstdc++.so.5 & .6 installed under 64bit.  Under 32bit only lib32stdc++6.  There doesn't seem to be a lib32stdc++5 available.

I assume FFox32 is using the 32bit libs?  Does the linux32 "environment" point the program it runs to the 32bit libs?

Maybe I need to redo my whole FFox install in a chroot environment?

It would be very useful to discuss this more directly.  Perhaps you can msg me? (& post).

Tnx
Rupert

---

### Post by bootdoc on 2006-08-18
Trying to install flash using your how to but i have a problem.
$ sudo sed 's/\/usr\/lib\//\/usr\/lib32\//g' /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders.32

I get
bash: /etc/gtk-2.0/gdk-pixbuf.loaders.32: Permission denied

what's up with the permission denied when I sudo??
Charlie

---

### Post by peter07 on 2006-08-21
This is a great Howto, everything is working. I want to use firefox64 and firefox32, and I have two questions.

1) Some extensions are used only in one browser. I'm using profiles to manage it, but I have one problem. When I have more than one profile, firefox default uses the last one. I've tried -P option, but with it I can use only 1 firefox window ( error msg ). 

2) Each time, when I have firefox64 opend I can't use firefox32. When I type ```
linux32 firefox32
``` new firefox64 window is opened. I have the same problem with firefox32. Is it possible to use firefox32 and 64 at the same time ?

---

### Post by rayohauno on 2006-09-03
> **Kwiatkowski said:**
> Websites like [www.pandora.com](www.pandora.com) need local storage for flash files activated. 

Right-click on a running flash movie, choosing properties, then the second record card (directory icon) and then moving the slider does not work. The plugin simply seems not to remember (you could check this yourself).

Do you have any ideas how to enable this caching feature an other way?

Thank you very much.


I have the same problem. I follow the hinds on FAQ in pandora.com, including the las one, that is reinstall flash, and it finally doesn't work. flash just dont remember the settings.

Can some one help us. ??

---

### Post by userfriendly on 2006-09-03
thanks very much! working on flash stuff (and viewing it, of course) was the last thing i was booting up windows for... now it's ubuntu only :) thank you, thank you, thank you!

---

### Post by sukamusiru on 2006-09-13
> **bootdoc said:**
> Trying to install flash using your how to but i have a problem.
$ sudo sed 's/\/usr\/lib\//\/usr\/lib32\//g' /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders.32

I get
bash: /etc/gtk-2.0/gdk-pixbuf.loaders.32: Permission denied

what's up with the permission denied when I sudo??
Charlie

I'm experiencing this same problem.

---

### Post by Doctor J on 2006-09-16
> **bootdoc said:**
> $ sudo sed 's/\/usr\/lib\//\/usr\/lib32\//g' /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders.32

I get
bash: /etc/gtk-2.0/gdk-pixbuf.loaders.32: Permission denied

what's up with the permission denied when I sudo??
Charlie

I don't have an explanation, but i do have an answer: add an additional step or two to the process.

[FONT="System"][/FONT]
$sudo su
#sed blah, blah, blah
#exit

---

### Post by fieldstone on 2006-09-17
There was one additional step that was necessary for me, and I'm posting it here for anyone else that might be having Flash sound problems like I was.

After trying all the other fixes, I found that extracting the files from the i386 version of the "alsa-oss" deb file, and copying them to /usr/lib32/, solved my problem. Now I've got perfect sound in 32-bit firefox.

Hope that helps anyone else who's having the same problem I was.

---

### Post by Doctor J on 2006-09-18
I have problems when i get to step 10: sound doesn't work, not even after making both of the links.  What's really weird [to me] is that i only get the flash video when i invoke "sudo firefox32" or run it as root.  Running it as me gives empty space in the browser window where the video should be.  Furthermore, any other accounts can't seem to run firefox32 from the terminal.  This just results in a permission denied error.  This is on a fairly standard Breezy installlation.

---

### Post by scharkalvin on 2006-09-18
Why can't there be a way to install a 32 bit Ubuntu package to run on an 64 bit Ubuntu system under installed 32 bit libraries?
It would require the package manager to allow selection of 32 bit packages and modifiy the install scripts as to the final directory destination, also to add the required command wrappers to install.

Another method would be a Meta package that would install the 32 bit package doing the necessary conversion.  Add something like
/user/bin/bin32 or /usr/bin32 directory to place the 32 bit binary packages in.  

I currently run BOTH the mozilla & firefox binaries in BOTH 32 and 64 bit versions on Gentoo without any problems.  Gentoo provides special binary packages under the AMD64 portage tree with any required wrappers, and each program has it's own launcher icon in the KDE menu.  So it just works!  As long as programs don't yet compile in 64 bit (OO.org) or don't have plugins (browsers) Ubuntu should provide this.  Take a look at how Gentoo does it!

---

### Post by crgutierrez on 2006-09-18
I though I had succesfully isntalled Java in my amd64, but when I try to run JGrass, it tells me I ONLY have Java 1.5.0, but need Java 1.5.0.5. :




crgutierrez@crgutierrez-amd64:~$ sh start.sh --debug --info
sh: start.sh: No such file or directory
crgutierrez@crgutierrez-amd64:~$ cd JGrass
crgutierrez@crgutierrez-amd64:~/JGrass$ sh start.sh --debug --info
[DEBUG thread=main, class=jgrass.Main, method=main] setting java.library.path, path=./lib:%{proj_lib}:%{gdal_lib}:./home/crgutierrez:./home/crgutierrez/Documents:./lib
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/JFontChooser.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/JRclient-RE817.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/JTS-1.6.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/activation.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/bsh-2.0b2.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/commons-collections.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/commons-dbcp-1.1.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/commons-httpclient.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/commons-logging.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/commons-pool-1.1.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/djep-1.0.0.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/geoapi-2.0.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/gt2-api.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/gt2-epsg-wkt.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/gt2-main.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/gt2-postgis.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/gt2-referencing.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/gt2-shapefile.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/itext-1.2.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/jai_imageio.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/jcifs-1.1.7.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/jcommon-1.0.0-pre1.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/jcommon.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/jdwglib.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/jep-2.3.0.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/jfreechart-1.0.0-pre1.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/jgrass.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/jgroups-all.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/jogl.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/jproj.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/log4j.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/org-jdesktop-layout.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/poi.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/postgresql-8.0-314.jdbc3.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/swing-layout-1.0.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/units-0.01.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/vecmath-1.3.jar
[DEBUG thread=main, class=jgrass.Main, method=main] Loading classes in package jars/xalan.jar


[IMG]/home/crgutierrez/Desktop/Screenshot.pnh[/IMG]


Help!
Carlos Raul

---

### Post by Serendipity03 on 2006-11-25
> **kurushi said:**
> Hi
>

https://wiki.ubuntu.com/FirefoxAMD64FlashJava[/url]

>

---

After weeks struggling with Edgy Eft 6.10 on an AMD 64, (my first venture

outside the Microsoft stable since '94) and Ubuntu information that could

but doesn't differentiate between 32 & 64 bit, yours are the first

instructions I have been able to follow through to a successful

installation.


I can now at least digress to watching (and hearing) news video, then see

my Ubuntu compatability problems from a wider perspective.

Thank you!

---

### Post by RAOF on 2006-11-26
> **bootdoc said:**
> Trying to install flash using your how to but i have a problem.
$ sudo sed 's/\/usr\/lib\//\/usr\/lib32\//g' /etc/gtk-2.0/gdk-pixbuf.loaders > /etc/gtk-2.0/gdk-pixbuf.loaders.32

I get
bash: /etc/gtk-2.0/gdk-pixbuf.loaders.32: Permission denied

what's up with the permission denied when I sudo??
Charlie

The problem here is that the redirection ">" actually runs in a separate environment, and doesn't inherit sed's sudo privileges.  See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for details, and a work-around.

---

### Post by tetralis on 2007-01-01
Hi,
I am using 6.10 for amd64 and it worked fine for me.

One thing was missing to get the realplayer kicking:
[FONT="Courier New"]sudo ln -s /usr/local/realplayer32/realplay /usr/local/bin/realplay[/FONT]

---

### Post by Aphorism on 2007-01-13
The documentation at [https://help.ubuntu.com/community/FirefoxAMD64FlashJava](https://help.ubuntu.com/community/FirefoxAMD64FlashJava) has been completely revised, streamlined, updated (For FF2, Flash Beta, etc.), and hopefully made simpler.  YMMV.

**PROBLEM:  Feisty (7.10) Firefox32 w/ Java**
Despite having had the technique work *flawlessly* on Edgy (6.10), Feisty has an issue with Java.  Has anyone resolved this on amd64 using the technique?

---

### Post by pladen on 2007-01-16
Thanks for the the updatet version of the howto. It's a very nice howto, really easy to follow. But I still are having problems with segmentation faults. To fix this I tried what you called the legacy instructions. That solves the problem for some applications such as evince, rhythmbox and bittornado, but it messes things up for the the file browser and the real-plugin. Does anyone know how to fix this?

---

### Post by immanueloffice on 2007-01-16
This tutorial worked for me with Firefox 2.0, amd64 and Dapper (6.06).

However, I have a problem with Evince, the gnome PDF viewer. When it is called from Firefox to open a PDF, it can't find the fonts for the menu - so the File menu and items like Print come out as box characters.

Below is the error when this occurs after starting FF from the command line:

```
(firefox-bin:11388): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/filesystems/libgnome-vfs.so: cannot open shared object file: No such file or directory

(evince:11420): Gtk-WARNING **: /usr/lib32/gtk-2.0/2.4.0/engines/libubuntulooks.so: cannot open shared object file: No such file or directory

** (evince:11420): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (evince:11420): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png

(evince:11420): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(evince:11420): Pango-WARNING **: pango_shape called with bad font, expect ugly output

```

These warnings come over and over, I guess a warning for each character it encounters and doesn't know how to draw it.

I did some searching and someone mentioned it was a problem as I am not running in a full chroot.

If I start up Evince from my menus, and then open a PDF from withing FF the menu font loads fine.

Does anyone have this too, and does anyone have any ideas for how to fix? For now, I have to make acroread my default viewer, but I prefer Evince.

Thanks for any help!

---

### Post by immanueloffice on 2007-01-23
I couldn't seem to fix this problem, and I also found that I could no longer click on email address links to have them open a new window in TB. 

So, I would say this isn't working 100%. I've decided to go back to the other Firefox and look for a workaround to install a 32bit plugin for a 64bit browser.

---

### Post by Penguinw on 2007-04-11
For me it worked the first time but now i have done a fresh install and i keep getting this error
 /usr/local/bin/firefox32: 5: linux32: not found
has anyone got any idea what i am doing wrong?

Thanks for any help.

---

### Post by Spr0k3t on 2007-04-11
Sounds like you are missing the 32bit headers.  From a terminal:

```
sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2
```

Post your findings from there.  Also, there's an alternate method with Edgy and Feisty that seems to work pretty well.  Which release are you using?

---

### Post by Penguinw on 2007-04-11
Hum it still doesnt work this is what i got after putiing in : sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ia32-libs
E: Package ia32-libs-gtk has no installation candidate

I'm using edgy because i am having a problem upgrading, which also i didn't have before. if you need anymore info please ask.

---

### Post by Penguinw on 2007-04-11
Spr0k3t: i tried it again, and this time it worked.

Thank you

---

### Post by Spr0k3t on 2007-04-12
Good to hear.

---

### Post by jiminizer on 2007-05-06
After days of trying to get this to work, trying different options, i had no luck. Maybe i'm too new to linux to understand it all.

Anyway i found a way that worked for me, even when all of the other methods did not. I added my solution to the bottom of the Wiki article for anyone else whos really struggling with this. I'ts a much simpler way of doing it in my opinion.

Cheers,
Jim

---

### Post by Aphorism on 2007-05-06
Jim said:
> After days of trying to get this to work, trying different options, i had no luck. Maybe i'm too new to linux to understand it all.

Anyway i found a way that worked for me, even when all of the other methods did not. I added my solution to the bottom of the Wiki article for anyone else whos really struggling with this. I'ts a much simpler way of doing it in my opinion.

First, Wine is NOT an option.  It is an awful way to achieve what you want, especially since the known and well tested way works flawlessly.

Did you follow the wiki to the letter?  Did you notice the note about NOT having existing processes of Firefox running?

It is literally three steps, and it works every time for everyone who successfully follows through on it:

1) Add the 32 bit emulation libraries as given on the [wiki]("http://https://help.ubuntu.com/community/FirefoxAMD64FlashJava")
2) Download and extract the Firefox binary to some location that suits you.
3) Download and copy the Flash blob binary to the plugins dir.

Done.

If you need help, please ask.  Wine is to support Windows, and we don't want Windows applications running on a Free system.

Sincerely,
TJS

---

### Post by Kilz on 2007-05-07
> **jiminizer said:**
> After days of trying to get this to work, trying different options, i had no luck. Maybe i'm too new to linux to understand it all.

Anyway i found a way that worked for me, even when all of the other methods did not. I added my solution to the bottom of the Wiki article for anyone else whos really struggling with this. I'ts a much simpler way of doing it in my opinion.

Cheers,
Jim

Wine isnt all that bad for running things you must have. But it is a 100% bug for bug copy of windows. The security is awful! Running any browser with it is not recommended.

That said, my howto is based on the original howto in this topic, but its updated. I have an automatic install script. If you cant do this manually, try the install script, link in my signature.

---

### Post by Fundi on 2007-05-07
For anyone wanting flash, perhaps you should try gnash. It's an opensource implementation of flash. It works on AMD64 platforms, but it doesn't work with all website yet. For example it can't play youtube video's but it does work with some simple flash websites. It's not great but its better than no flash.

To install:
```
sudo aptitude install gnash
```

---

### Post by avanderveen on 2007-05-31
OK, I followed the instructions *exactly*, I mean to a tee, and it did not work whatsoever, I don't know what I'm doing wrong, but it's gotta be something because it seems to be working for everyone else.

To go into more detail, I am running Dapper 6.06. After installing firefox and copying the plugin files to usr/local/firefox32/plugins I double checked that the plugins were copied correctly by navigating to the folder graphically. After making sure everything was working and recieving no errors I tested flash and java in the newly installed 32-bit Firefox, and it said that I didn't have the plugin when I visited flash and java websites. I'm wondering if you guys know of any common mistakes that people make when installing or using Firefox, or if you know of another method (besides WINE) to run 32-bit plugins in 32-bit firefox.

---

### Post by Aphorism on 2007-05-31
I can't stress this enough -- the steps are almost too easy to get boggled down on.

Unfortunately, the wiki page is getting all completely gummed up with more rubbish.  I will probably try to purge it again and remove the references to Kate and GEdit (Yet another reason to hate the G/K dilemma).  Further, at least _three_ more wiki pages have popped up to confuse the issue.  This is based on the original one that I modded based on the _truly_ original draft.  [https://help.ubuntu.com/community/FirefoxAMD64FlashJava?highlight=%28firefox%29](https://help.ubuntu.com/community/FirefoxAMD64FlashJava?highlight=%28firefox%29)

Here is a brief summary, try this, and if it fails, it is almost certainly an issue with your process:

1) Install compatibility libraries.  These are, quite simply, ia32-libs ia32-libs-gtk linux32 lib32asound2.  Use synaptic, apt-get, whatever it takes.  Note -- there are FOUR libraries you will need.

2) Download Firefox for 32 bit Linux from the official Firefox page.  Extract it to your desktop.  I won't confuse the issue by having you move it to a system directory.

3) Download the Flash plugin.  Download Java.  Extract them and look for the PLUGINS directory for both.  Simply copy the plugins to the Firefox plugins directory that you created on your desktop.

Shut down _all_ instances of Firefox.  This is a _must_ complete step.  This includes ANY windows that have the little Firefox icon.  Firefox will _always_ spawn new instances based on _any_ currently running instances.

Run Firefox by double clicking on it in your downloaded test directory.  I'd bet it will work flawlessly.

If this test works, the demon is in the details of moving it around and such.


Please post your issues.


Sincerely,
TJS

---

### Post by avanderveen on 2007-06-01
Thank-you so much for your help and quick response Aphorism. I must have just made a dumb mistake the 1st time, like running 32-bit Firefox before shutting down the 64-bit, because now it works according to your instructions which are much simpler and easier to follow others that I have read.

---

### Post by Aphorism on 2007-06-01
Extremely glad that it worked for you.  There is no reason that anyone should need to run Wine to get a perfectly running 32 bit instance of Firefox up.

Unfortunately, there are plenty of posts with misinformation and poorly outlined ideas.

I would accept some of the responsibility for that as the original wiki page I cited above has begun to get far too cluttered.

What would be nice to know is if the two 'issues' located at the top of the wiki page are still relevant?  

I will attempt to clean up the wiki page a little bit and reduce the complexity that has apparently crept in.  As I stated though, the spawning nature of Firefox often causes some confusion for people.  It is critical that people close down all instances of Firefox before attempting to switch between versions.  This includes any and all open browser windows, but also those sometimes forgotten Firefox "Downloads" windows.

Sincerely,
TJS

---

