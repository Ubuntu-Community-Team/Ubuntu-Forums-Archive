---
title: "FINALLY: Stable Flash for Ubuntu AMD64"
date: 2008-10-20
forum: x86 64-bit Users
---

### Post by Emblem Parade on 2008-10-20
So far it's amazing: no crashes, no stutters, no problems. I'd love to hear of other people's experiences with this. For me, it seems like a long and painful chapter of Ubuntu history is finally reaching its end.

The magic combination is the new Flash 10 with nspluginwrapper 1.1.2. Here's how to get it working for you.

**THIS IS FOR HARDY HERON**

1. A build of nspluginwrapper 1.1.2 is available on psyke83's PPA. Just add the following repository:

```
deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
```

Note that this PPA also contains the latest version of PulseAudio, which has also been treating me well.

IMPORTANT! Don't run a package upgrade quite yet! Just update the list of packages. The next script should take care of first removing packages that you don't want upgraded.

2. To install Flash 10, I slightly modified this terrific script, originally by Romeo-Adrian Cioaba. It makes sure to clean out any old versions of Flash you have.

The script relies on Cappy's wonderful [getlibs]("http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb"), so make sure you install it first.

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Another minor update by tal.liron[at]gmail[dot]com
# Released under GPL

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar zxvf install_flash_player_10_linux.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so Firefox can find it."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
```

---

### Post by Nikos.Alexandris on 2008-10-21
Thanks for the post but it does not work for me unfortunately :-?

Kind regards, Nikos

p.s. details about my machine and previous attempts to get flash working on it can be foud in Kilz sticky "flash9" thread.

---

### Post by istblacken on 2008-10-21
for some reason getlibs couldn't install libcurl3 libnss3-1d libnspr4-0d those packages and so i installed them manually and put them into /usr/lib32. then added the PPA and it works nicely now. for those who can't get it work you may want to try the same as i do.

---

### Post by Emblem Parade on 2008-10-21
I do have all optional respitories enabled... that could be the issue.

Nikos.Alexandris, tell us exactly what didn't work, at what step it failed, and maybe we can improve this guide together.

---

### Post by null_pointer_us on 2008-10-21
EDIT: nvm, I shouldn't have done the update when prompted. But you might want to warn people not to do any updates (when prompted) between steps 1 and 2; instead, let your script fix up all the dependencies.

---

### Post by Nikos.Alexandris on 2008-10-21
Hi!

I've been struggling to get flash to work with FFX3 for months now but no luck. Some weeks ago I tried Kilz' steps. I have a bunch of posts in Kilz thread (beginning from post #339 and on till post #376 I think) and a bug report as well [1]. Probably post #352 [2] gives an overview of what I am trying. The "strange" thing is that flash works with Opera and Epiphany but not with FFX3.

Now, I've tried the script of this thread but no luck. I also see the packages libcurl3 libnss3-1d libnspr4-0d getting installed. I don't know, I must have done something wrong at some point in my machine :-?

Anyhow, thank you for your concern.

Nikos

[1] [https://bugs.launchpad.net/ubuntu/+bug/270868](https://bugs.launchpad.net/ubuntu/+bug/270868)
[2] [http://ubuntuforums.org/showpost.php?p=5799399&postcount=352](http://ubuntuforums.org/showpost.php?p=5799399&postcount=352)

---

### Post by fignig on 2008-10-21
when will the flash10 from adobe be stable for the hardy version? or will we have to wait for the intrepid for the release to come out?

---

### Post by Amorget on 2008-10-21
Worked for me :)  Hopefully it will be more stable so I won't need to restart FF every time I went to see a video.

---

### Post by Emblem Parade on 2008-10-21
> when will the flash10 from adobe be stable for the hardy version?

Flash 10 is stable for Hardy Heron. Adobe now includes Linux and Ubuntu specifically as an officially support platform. You can download a .deb directly from Adobe. Except... that we're talking about 32bit support for now. This guide is specifically for AMD64.

> Hopefully it will be more stable so I won't need to restart FF every time I went to see a video.

Update: after a week of working extensively with this setup, I still have had no crashes. However, I did have one of those slowdowns in which Firefox hangs. After 30-or-so seconds, it continues. Once a week, though, is incredible compared to what I used to have, which was Firefox hanging about 50% of the times.

---

### Post by null_pointer_us on 2008-10-22
> **Emblem Parade said:**
> Update: after a week of working extensively with this setup, I still have had no crashes. However, I did have one of those slowdowns in which Firefox hangs. After 30-or-so seconds, it continues. Once a week, though, is incredible compared to what I used to have, which was Firefox hanging about 50% of the times.

Well, I got Flash 10 working on my AMD64 box, and I have to say that the new Flash is still flaky.

Dilbert.com frequently hangs the browser because some process named npviewer.bin goes into 100% CPU usage until I manually kill the task. This didn't happen with Flash 9, BTW.

Rhapsody.com occasionally works. I can login reliably now, but the Play/Add buttons to queue music seldom work unless I close and re-open Firefox (without signing out and in again). No idea why these failures are random...but it's annoying to have to wrestle with my computer when I just want to listen to some music. (This is the kind of thing I hate in Windows.)

The biggest improvement with Flash 10 is that, even when I have Rhapsody.com playing music in its little player window, I can browse to other Flash-enabled sites in other tabs without locking up Firefox; in fact, the Flash animations in all open tabs now seem to work independently of each other.

A definite improvement overall, but it's not what I'd call stable.

---

### Post by Emblem Parade on 2008-10-22
> Well, I got Flash 10 working on my AMD64 box, and I have to say that the new Flash is still flaky.

Are you using nswrapperplugin 1.1.2, too? I had the same trouble with Flash 10, until I upgraded nswrapperplugin. That, for me, was the magic combination.

---

### Post by Fr@nKy on 2008-10-22
Well... it's still not as stable as it is in Ubuntu 32-bit and both are still lagginf behind Windows :(

---

### Post by Emblem Parade on 2008-10-22
> Well... it's still not as stable as it is in Ubuntu 32-bit and both are still lagginf behind Windows

True, but it's now about as equal as 32-bit Ubuntu for me, which is a huge step forward. Until now, I would run Windows in VirtualBox just for Flash. I can finally retire that kludge.

Just so you know -- Adobe is working on 64bit Flash (for all platforms, not just Linux), but the challenges are pretty enormous and it's going to take some more time. Basically, the whole ActiveScript virtual machine needs to be rewritten for a new architecture, and this was a component that was not originally by Adobe in the first place. I've read on some blogs that a 64bit Flash has already been demoed. It might take a few more months, but we'll eventually see Adobe supporting 64bit.

At least now we can finally use nspluginwrapper successfully.

---

### Post by null_pointer_us on 2008-10-22
> **Emblem Parade said:**
> Are you using nswrapperplugin 1.1.2, too? I had the same trouble with Flash 10, until I upgraded nswrapperplugin. That, for me, was the magic combination.

Synaptic reports nspluginwrapper 1.1.2 was installed, as your guide recommends.

Rhapsody.com's web player window just crashed when I closed a Buy.com window in another browser window's tab. I had launched Firefox from a console window, so here's the output:

```
(npviewer.bin:6190): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:6190): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
*** NSPlugin Wrapper *** ERROR: NPN_GetURLNotify() get args: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_HandleEvent() invoke: Connection closed

(firefox:6153): GLib-CRITICAL **: g_hash_table_insert_internal: assertion `hash_table != NULL' failed
*** NSPlugin Wrapper *** ERROR: NPP_NewStream() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_HandleEvent() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_HandleEvent() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_HandleEvent() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_HandleEvent() invoke: Connection closed

(snipped)
```

Is the nspluginwrapper package the source of Flash instability? It would be easier to believe that the plugin wrapper is buggy than to believe that Adobe would roll out a major Flash revision in this condition. Though Adobe hasn't exactly had a history of writing stellar software -- their Windows PDF plugin has crashed a ton of IE and FF browser windows.

---

### Post by Fr@nKy on 2008-10-22
> **Emblem Parade said:**
> True, but it's now about as equal as 32-bit Ubuntu for me, which is a huge step forward. Until now, I would run Windows in VirtualBox just for Flash. I can finally retire that kludge.

Just so you know -- Adobe is working on 64bit Flash (for all platforms, not just Linux), but the challenges are pretty enormous and it's going to take some more time. Basically, the whole ActiveScript virtual machine needs to be rewritten for a new architecture, and this was a component that was not originally by Adobe in the first place. I've read on some blogs that a 64bit Flash has already been demoed. It might take a few more months, but we'll eventually see Adobe supporting 64bit.

At least now we can finally use nspluginwrapper successfully.

Well I haven't used Ubuntu for some time, and even now I'm using Intrepid 64-bit, and I was infact considering rolling back to 32-bit because of Flash (and I really don't need 64-bit because I only have 2GB of RAM however I might be getting 4GB really soon and also I think it's a matter of principle to try to use my Core 2 Duo to its full capacity)... do you really think that Flash 10 + nspluginwrapper 1.1.2, on 64-bit, is nearly as stable as the native Flash 10, on 32-bit??

I just want to be sure that I'm not getting a worse web browsing experience just because of I'm on 64-bit :P

---

### Post by owenll on 2008-10-25
Thanks for this guide. Because I didn't know how to run the script :oops: I copied and pasted each line into the terminal. I have flash working on my x64 system

---

### Post by epitaph on 2008-10-25
This just solved two of my biggest problems with flash: pandora radio not working and vimeo.com videos just incessantly freezing.

Thanks for the easy script, my Ubuntu experience just got a little bit better!

Also, to run the script you can copy and paste the entire text into gedit and save it as a *.sh (ex: "installflash10.sh") then execute it in a terminal using the sh command (ex: browse to the directory the file is in then type "sh installflash10.sh").

---

### Post by aoanla on 2008-10-25
I can't say I'm terribly happy - the script seems to have totally broken flash in Opera (previously, it was mostly working, but sometimes crashing) and in Firefox (similarly iffy but generally working).

Any idea how I can unbreak flash again?

(After a little investigation, it appears the issue is with getlibs - as with other people in this thread, it seems to be totally unable to install the libraries, giving output like:

Unknown distro, using Debian Unstable (sid) settings
/usr/bin/getlibs: 123: shopt: not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.

and

Fatal Error: /emul/ia32-linux does not exist
Your distro may not have been detected properly
Detected as: x86_64 debian unstable
No LSB modules are available.
Distributor ID: Ubuntu Description: Ubuntu 8.04.1 Release: 8.04 Codename: hardy


this looks like getlib is a wee bit broken, and is stupidly trying to set things up in a Debianish way (while Ubuntu doesn't use a /emul/ for 32bit stuff).
)

---

### Post by Emblem Parade on 2008-10-25
Thanks to all the people trying to debug the getlibs problem! Because it works on both of my machines, I can't duplicate the problems. My guess is that it has something to do with which repositories you have,

Please, if you find an answer, post it here and I will add it to the guide!

---

### Post by CJ56 on 2008-10-25
Has anyone used this method (did I miss anything?) -

[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/]("http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/")

I uninstalled Flash 9, ran this & so far it's worked well...

---

### Post by aoanla on 2008-10-25
So, part of my problem is that the copy of getlibs I had was old - I googled around for the most recent .deb of it, and that seemed to fix the getlib errors.

---

### Post by gnichol2k8 on 2008-10-25
Hi, i am completely new to ubuntu, i love it, but having major problems getting flash sorted, i know a bit so i am not a complete novice.

any help would be appreciated.

thanks

---

### Post by deathpulse on 2008-10-25
Somebody PLEASE sticky this - this procedure works PERFECTLY!!

---

### Post by detinu on 2008-10-25
working in ubuntu 8.10 beta 64bit.

crashes here and there but ONLY the plugin, browser keeps trucking along and will still load flash in a new tab or refreshed page.

---

### Post by TWFJR on 2008-10-26
Emblem Parade, I just loaded your script hoping to resolve some issues on web sites.  I am happy to say that your script worked but I now find that AOL web sites are not loading pics or streaming. Any suggestions to resolve this problem?

---

### Post by kwill on 2008-10-27
Works with Opera as well as Firefox. I had no problems following the instructions.

---

### Post by mustard675 on 2008-10-27
Worked like a charm! Thanks!

---

### Post by stormtrooprdave on 2008-10-27
> **CJ56 said:**
> Has anyone used this method (did I miss anything?) -

[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/]("http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/")

I uninstalled Flash 9, ran this & so far it's worked well...

Had to reinstall flash after the upgrade to 8.10.  This could not be simpler - copy, paste, done.

---

### Post by oxman44 on 2008-10-27
hey guys. New to this.
 as i was using the script, I got to installing the libs and terminal would not recognize  when it asked me to continue installing. heres  a screenshot:

ox@ox-desktop:~$ echo "Getting libs"
Getting libs
ox@ox-desktop:~$ sudo getlibs -p libcurl3
The following i386 packages will be installed: libcurl3
Continue [Y/n]? y
Not understood. Aborting.

I tried multiple times, what should I do?

---

### Post by mjwood0 on 2008-10-27
Worked great for me.  Not that I was having too much of a problem, but it's nice to have the latest Flash and have it actually work.

@oxman44: did you click on the link for getlibs in the original post?  When it prompts you to save or run the download, choose run.

If you're sure it's installed correctly, you could try to run the line ```
sudo getlibs -p libcurl3
``` manually from the command line and see if it works.

---

### Post by oxman44 on 2008-10-27
hey thanks alot! that worked great now flash is working fine thanks everyone!;);)

---

### Post by s_shuffle on 2008-10-28
This was a Great  info!!!

 I just had to remove the apt-get of ia32libs - because I had installed it before . and it worked perfect.
- But the installation of the new nspluginwrapper is capital - since I tried before with version 0.9.x  and I was getting this error :
 *[COLOR="Red"]*** NSPlugin Viewer  *** ERROR: libnss3.so: cannot open shared object file: No such file or directory[/COLOR]*

 So once again Thanks

---

### Post by TWFJR on 2008-10-29
The pre-release  8.10 resolved my issues.

---

### Post by Hadraniel on 2008-10-31
I just set up my brandnew PC, with Ubuntu 8.10 AMD64.
The script works just perfect. Fire&forget. Thanks! :KS

---

### Post by TECsBrain on 2008-12-24
Awesome - I had the same problem in 32-bit Mint Felicia (based on Intrepid) but, reading the script, didn't see anything specific to that version; Felicia ships with nspluginwrapper 1.1.0 instead of 1.1.2, so I used this script to clear Flash and update, with much success.

---

### Post by Kilz on 2008-12-25
> **TECsBrain said:**
> Awesome - I had the same problem in 32-bit Mint Felicia (based on Intrepid) but, reading the script, didn't see anything specific to that version; Felicia ships with nspluginwrapper 1.1.0 instead of 1.1.2, so I used this script to clear Flash and update, with much success.

Why would a 32bit Mint have nspluginwrapper installed? Its only use is to make the 64bit browser in the 64bit os see a 32bit plugin. A 32bit distro would not have a 64bit browser.

---

### Post by obsrv on 2008-12-25
From the default repositories in 9.04 A2 Ubuntu flash is very stable. I watch YouTube a lot and it is ok. No cracshing, no sound problems.

---

### Post by dspisak on 2008-12-25
Hello.  I loaded the 64-bit Adobe flash player into 8.10 and everything (streaming FM audio, YouTube video and audio) works.  However, if I try to run a video at the CNN.com website the video starts to load then Firefox crashes.  I am new to ubuntu and I do not know how to fix this problem.  Any help is appreciated.  TIA

system:
CPU - AMD Athlon 64
OS - ubuntu 8.10, kernel 2.6.27-9-generic #1 x86_64
Flash - version 10
Browser - Firefox 3.0.5, canonical - 1.0, x86_64

Dan

---

