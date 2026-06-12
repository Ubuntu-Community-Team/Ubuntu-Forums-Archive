---
title: "Howto: FreeNX on Hoary AMD64"
date: 2005-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Drain on 2005-08-04
Well, I went and did it. After much complaining (mostly my own) I went and compiled my own packages for FreeNX for my AMD64 box. This howto is a guide to where I got the information, and (surprise) how to get FreeNX running on your AMD64 box. 

**Three things first:**
One - What is FreeNX and why would I use it?
FreeNX is a remote desktop tool that is faster and more secure than (plain) VNC. If you can't figure out how that's useful, think about this - imagine accesing your linux desktop from your friend's WindowsXP computer over a modem line, and having it move just as smooth as if you were sitting at your own chair. It's pretty nice. :-)

Two - Where can I learn more?
[NoMachine](http://www.nomachine.com) are the creators of the NX protocol. While they create a commercial product, they also release the source code under GPL for use by anybody.

[FreeNX](http://freenx.berlios.de) is the open-sourced version of the NX protocol, and much of the work has been done by [Fabian Franz and Kurt Pfeifle](http://dot.kde.org/1120050176/). 

[The Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=1968) already has several threads about getting FreeNX running on Ubuntu. With the help of that particular thread, and the work of [Nicholas Lee](http://stateless.geek.nz/2005/06/27/building-freenx-04-on-ubuntu-hoary/) (how to build FreeNX on Hoary) and [Darren Oakley](http://oakley.bioinformaticsonline.co.uk/?q=node/18) (how to get FreeNX up and running), I only needed to stand on their shoulders a little. :-)

Three - Some caveats:
A. You'll be downloading and creating several packages. This can be tricky, and it's entirely possible that I was just incredibly lucky that I didn't blow up my own computer. So consider yourself warned - if your computer blows up, I take no responsibility. ;-)
B. I haven't tried to create an AMD64 client package (yet!). So while this guide can help you connect *_TO*_ an AMD64 box running Ubuntu/FreeNX, if you're trying to connect *_FROM*_ a AMD64 to another box running FreeNX, these might not be entirely helpful.
C. While I'm on this note, I have no idea whether any of these instructions apply to the PPC version. I'd love to hear about it though! ;-)
D. There are some issues with FreeNX, as its still being developed. One of the ones I ran into (and that I've seen on the forum) is that Gnome and KDE currently aren't playing well with it - so you'll have to install XFCE. It took me a while to read through the forums to see that as a solution, and I'm sure there are more things than that, so all I can advise is to search the forums first and then ask questions.
E. I hope that this thread continues to be a work in progress. I hope to update it later on, and I hope that questions will get asked and answered.

**Now on to the show!**

I'm going to try and outline how to do most of this by the commandline. You can do a lot of this through Synaptic or other GUI, but I'll leave that as an exercise to the reader. If any off the commands like "apt-get" or "edit your sources.list file" are foreign to you, might I suggest reading [www.ubuntuguide.org](www.ubuntuguide.org) first? 

First of all, I got started by installing XFCE 4.2 - It's the window manager that worked for me, since Gnome and KDE didn't at the time. 

[FONT=Fixedsys]$ sudo apt-get install xfce4[/FONT]

Next, I added two lines to my /etc/apt/sources.list (Later on, you can comment them out). 

[FONT=Fixedsys]deb [http://debian.tu-bs.de/project/kanotix/unstable/](http://debian.tu-bs.de/project/kanotix/unstable/) ./
deb-src [http://debian.tu-bs.de/project/kanotix/unstable/](http://debian.tu-bs.de/project/kanotix/unstable/) ./[/FONT]

If I recall correctly, at this point, if you attempted to simply go "apt-get install freenx" you would get an error message saying that you couldn't, because you didn't have "nxagent" and "nxproxy" installed, and they didn't appear to be in the repository (at least not for AMD64). So you have to build the packages, and to do that, I downloaded a whole bunch of other packages:

[FONT=Fixedsys]$ sudo apt-get install build-essential cdbs autotools-dev patchutils autoconf bzip2 zlib1g-dev libpng12-dev libjpeg-dev xlibs-dev libfreetype6-dev libmikmod2-dev libssl-dev libxaw7-dev automake1.9 expect[/FONT]

(Since I am doing this from memory and other guides, there may be a few missing, or you may already have them installed. Read any error messages carefully, and let me know if there is anything I should add)

Check to make sure you have all the dependencies for both nxagent and nxproxy:

[FONT=Fixedsys]$ sudo apt-get build-dep nxagent
$ sudo apt-get build-dep nxproxy[/FONT]

Now get the actual source files for FreeNX.

[FONT=Fixedsys]$ sudo apt-get source nx freenx[/FONT]

(Side note: I suppose you could type "sudo apt-get -b source nx freenx" and have apt build the packages automagically, but I did it the same way Nicholas Lee did it in his instructions).

So now you've downloaded 3 files (a .orig.tar.gz , a .dsc , and a .diff.gz) for both nx and freenx, so that's 6 files. That also created two directories, one for the nx source (as of this writing, 1.4.0.2), and one for the freenx source (as of this writing, 0.4.3). Let's start the package-making process. 

[FONT=Fixedsys]$ cd nx-1.4.02/
$ sudo fakeroot dpkg-buildpackage -b 
$ cd ..
$ cd freenx-0.4.3/
$ sudo fakeroot dpkg-buildpackage -b
$ cd ..[/FONT]

Those two "dpkg-buildpackage" commands will take a few moments, and (if you're new to this) a lot of text will scroll by. If there are any error messages at the end, make a note. Sometimes they make sense (and you can fix them by installing the right package and trying again), and other times, you'll want to ask in the forums. In the end, I ended up with 8 files: freenx_0.4.3-0a1_all.deb, nxdesktop_1.4.0.2-0alpha4_amd64.deb, libnxcomp0_1.4.0.2-0alpha4_amd64.deb     nxlibs_1.4.0.2-0alpha4_amd64.deb, libnxcompext0_1.4.0.2-0alpha4_amd64.deb, nxproxy_1.4.0.2-0alpha4_amd64.deb, nxagent_1.4.0.2-0alpha4_amd64.deb, nxviewer_1.4.0.2-0alpha4_amd64.deb .

Install the packages!:

[FONT=Fixedsys]$ sudo dpkg -i *.deb[/FONT]

If everything has installed correctly, from there on out you can follow the installation directions from other locations. For the record, however, here is what I ended up doing. When you're presented with the initial text mode of NX setup screen, I selected "Custom"

**Setup commands** 

First I checked to see if the service was up and running, and it gave me a little "OK" message. The next command sets up the appropriate directories for the nx user. I then listed the users who can use nx, (and since I don't recall whether this was necesary on my install or not) added myself as a user and gave myself a password.

[FONT=Fixedsys]$ sudo nxserver --status
$ sudo nxsetup --install --setup-nomachine-key
$ sudo nxserver --listuser
$ sudo nxserver --adduser drain
$ sudo nxserver --passwd drain[/FONT]

Any of the sxserver or nxsetup commands are documented by typing out --help after the command. 

At this point, you're ready to connect from another computer. I connected from a dual-boot  x86 machine I've got at home. The windows client can be found on nomachine's site: http://www.nomachine.com/download/1.5.0/client/nxclient-1.5.0-103.exe

I followed the setup wizard, and when choosing what desktop to use, I selected "Unix" "Custom" and filled in the "Run the following Command" box with "startxfce4". A sample of something like that can be found [on this Fedora site.](http://fedoranews.org/contributors/rick_stout/freenx/) 

There is a screenshot of this below! :-) 

For the other part of the dual boot, I followed Darren Oakley's blog (see above) as to how to install the nxclient. There are instructions to edit your sources.list file and apt-get install the correct file. After that, setup is strikingly similar to the Windows client. 

And that's it! (whew!) Go forth, and good luck!

---

### Post by Tamir on 2005-08-04
Beautiful. great howto, can you please send me .deb files to my email?
I realy want to host it on my repository (don't forget to send me all of the .orig.tar.gz, .dsc. .diff).

Email - [email]tamir@nooms.de[/email]
Are you interested?

---

### Post by Drain on 2005-08-04
[QUOTE=Tamir]Beautiful. great howto, can you please send me .deb files to my email?
I realy want to host it on my repository (don't forget to send me all of the .orig.tar.gz, .dsc. .diff).

Email - [email]tamir@nooms.de[/email]
Are you interested?[/QUOTE]

Check your email - everything you need (8 deb files and 9 of 10 source files) should be in those 3 archives, and that last source file can be downloaded from the link I gave you (it's 32MB, too big for most email attachments).

---

### Post by Daz on 2005-08-13
Fantastic tutorial Drain!

I have not tried it yet, but we should be getting an AMD64 server at work soon (fingers crossed!) and this was one of the things I really wanted to get an idea of how to sort.

On the subject of you not being able to get your FreeNX to work with Gnome or KDE, I believe that this is an issue with the ver. 0.4 packages - i've tried using them (kanotix debs) on an i386 ubuntu box and Gnome/KDE doesn't work either.

I'm not sure where you could get them from, but if you could get hold of some FreeNX 0.3 source packages, you may have more luck with running Gnome/KDE (the current version of FreeNX in the backports is 0.3.1).

That said, GREAT WORK!!!!!

 :grin:

---

### Post by WatsonJX on 2005-08-13
I am following your Howto to build amd64 on debian unstable.

I got one error in nx-1.4.0.2/nxcomp/RenderExtension.h.

It turns out could be fixed by a forward declaration for
class RenderMinorExtensionStore;

Then I manage to get authenticated from windows client, but nxagent segfault  in nxlibs. It's in XFindOnExtensionList() of nx-1.4.0.2/nx-X11/lib/X11/InitExt.c.

Do you know how to build the nx-X11 lib separately with -g so i can debug it?

I try do make in nx-X11 directory but got error "PLATFORM not defined" blahblah.

Thanks so much!

---

### Post by WatsonJX on 2005-08-14
Found the problem. Now nxagent seems not crash after libX11-nx.so is recompiled with -O instead of -O2.

Windows client can connect and get a X console now. However I cannot run any other commands. If I set it to startxfce4 or just a simple xterm, it still disconnect immediately.

Anywhere to check nxagent logs?

---

### Post by WatsonJX on 2005-08-14
OK, from nomachine.com doc i find the session log in ~/.nx/.

Now I am able to start 'xterm', and then run twm. But other X apps such as xfce4-session, xfce4-panel, gnome-session will fail for error:

The program 'xfce4-session' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 186 error_code 14 request_code 55 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Anybody has some ideas? I submit a service request at nomachine.com

---

### Post by Drain on 2005-08-18
Sorry I'm a bit late to reply to this thread - I just thought I'd toss in my two cents here and there though. 

[QUOTE=Daz]I'm not sure where you could get them from, but if you could get hold of some FreeNX 0.3 source packages, you may have more luck with running Gnome/KDE (the current version of FreeNX in the backports is 0.3.1).[/QUOTE]

Tamir has added NXserver to his Ubuntu 64-bit repository, and DancingSun has requested that we use a few of the older versions in an attempt to get Gnome and KDE working. Last I heard, it wasn't working, but we had only stepped back to 0.4.2 , instead of the current version I had going at 0.4.3 (to the best of my memory). We'll have to give the 0.3.1 version a shot (the .tar files are at the following webpage:
[http://developer.berlios.de/project/showfiles.php?group_id=2978](http://developer.berlios.de/project/showfiles.php?group_id=2978))


[QUOTE=WatsonJX]Now I am able to start 'xterm', and then run twm. But other X apps such as xfce4-session, xfce4-panel, gnome-session will fail for error:[/QUOTE]

Sorry WatsonJX - I have no idea what to do or suggest at the moment. You have gone beyond the realms of my experience. I know that there is a webpage at no machine that talks about the building of the components ([http://www.nomachine.com/documentation/building-components.php)](http://www.nomachine.com/documentation/building-components.php)), but don't know how helpful that is to you. I am interested to hear about whether or not you get any response for help from NoMachine - if you're trying to compile the free, GPL'd version of their product, and asking for help with their commercial product, I don't know if they'd be quick to respond. (Which isn't meant to disparage anyone, I'm just a pessimist at heart. :-) )

---

### Post by appleman77 on 2005-08-24
Did anyone fix this for Hoary AMD64?  The current version doesn't work and when I add the repositories above, I get an error.  Any suggestions?

I'd love to try out FreeNX on my AMD64...no luck trying to compile it myself.

---

### Post by Tamir on 2005-08-25
[QUOTE=appleman77]Did anyone fix this for Hoary AMD64?  The current version doesn't work and when I add the repositories above, I get an error.  Any suggestions?

I'd love to try out FreeNX on my AMD64...no luck trying to compile it myself.[/QUOTE]
 You just need to wait somedays :) as I told you, we are only two main packagers.

---

### Post by Drain on 2005-08-28
[QUOTE=appleman77]Did anyone fix this for Hoary AMD64?  The current version doesn't work and when I add the repositories above, I get an error.  Any suggestions?

I'd love to try out FreeNX on my AMD64...no luck trying to compile it myself.[/QUOTE]

I wonder if this has anything to do with the fact that it switched to version 0.4.4. (Hopefully I'll be able to try it out in a week or so and provide a further update). 

Has anyone out there tried to build a more recent version, and willing to let us know how it's going?

---

### Post by greythorne on 2005-10-14
drain can you be kind enough to tell what hardware do i need to do the setup, because i have a winxp desktop lying arnd and i want to be able to use it thru ubuntu.

thnx.

and btw is it ok if i use your screenshot?

---

### Post by Drain on 2005-10-15
[QUOTE=greythorne]drain can you be kind enough to tell what hardware do i need to do the setup, because i have a winxp desktop lying arnd and i want to be able to use it thru ubuntu.

and btw is it ok if i use your screenshot?[/QUOTE]

The original setup I had is my Ubuntu computer(s) at home and my Windows XP desktop at work. At the time, it also looked like I could connect from my parents Windows 98 computers as well, but I haven't had much luck since I moved, and I haven't had enough time lately to experiment and tweak the system. So you need two internet-connected computers, and I might be reading your post wrong, but it sound like you only have one. Hardware requirements are quite low for FreeNX - I used to run it on an old K6-2 with 128MB of RAM. 

And when you say that you "i want to be able to use it [WinXP] thru ubuntu." I'm afraid that it is a one-way direction at the moment. The free versions of the NX software only have the ability to connect to a computer running linux; so you can't set it up so that you can use linux to connect to a windows server, unless you go to the Nomachine.com website and purchase their packages. 

Hope that clears some things up. Good luck.

PS - I don't know why you want to use my screenshot, but go ahead and be my guest, the link is right there onthe forum.

---

### Post by waster on 2005-11-09
FreeNX is broken on AMD64 at the moment.

Best way is to get server deb packages from nomachine, personal edition.

I simply did
<code>
dpkg -i --force-architecture
</code>

and it all worked fine.

---

### Post by Inhibit on 2005-11-14
Ack.  In response to the initial posters statement that NX Client wasn't working I've posted a workaround.  The method was a bit of a kludge, but it works.  There's a quick guide up at [http://pcburn.com/article.php?sid=941]("http://pcburn.com/article.php?sid=941") Please excuse any errors, it's 1:30am and I've been awake for far too long :).

---

### Post by krosswindz on 2005-11-24
I downloaded the latest available sources from [http://debian.tu-bs.de/project/kanotix/unstable/]("http://debian.tu-bs.de/project/kanotix/unstable/") and built them. I find that nxagent segfaults: > nxagent[2990]: segfault at ffffffffffffffe4 rip 00002aaaab3e5b88 rsp 00007fffff9800a0 error 6

Anyone have any idea as to what might be the reason. I am running debian AMD64 sarge. Any help on this is appreciated.

---

### Post by Loiosh on 2006-02-08
I believe the problem may be in what the 'nx-X11' package is. the nx-X11 package is a modified version of the full xorg implimentation. That is, it is the full install, with drivers, of the X server. That is why the build takes so long.

Unless freenx is poking into X11 for some drivers, the only reason that software would be included is that it is required to install a freenx-patched version of X. Hopefully I am incorrect about that.

---

### Post by MrIch on 2006-03-26
who can help me getting nxclient on amd64 dapper system?

---

### Post by SIGUA on 2007-04-27
It doesn't work! :( 

All that I've done is:

$ sudo apt-get install xfce4

$ sudo gedit /etc/apt/sources.list
(and I've added the two following lines at the end of the file)
deb [http://debian.tu-bs.de/project/kanotix/unstable/](http://debian.tu-bs.de/project/kanotix/unstable/) ./
deb-src [http://debian.tu-bs.de/project/kanotix/unstable/](http://debian.tu-bs.de/project/kanotix/unstable/) ./
(I save and close)

$ sudo apt-get update

$ sudo apt-get install build-essential cdbs autotools-dev patchutils autoconf bzip2 zlib1g-dev libpng12-dev libjpeg-dev xlibs-dev libfreetype6-dev libmikmod2-dev libssl-dev libxaw7-dev automake1.9 expect
(It's great! The only possible error is 'Nota, seleccionando libjpeg62-dev en lugar de libjpeg-dev' (in Spanish), 'Note, libjpeg62-dev has been selected instead of libjpeg-dev' (The message translations to English, more or less))

(And the errors comes here)
$ sudo apt-get build-dep nxagent
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
E: No pude abrir el fichero /var/lib/apt/lists/debian.tu-bs.de_project_kanotix_unstable_._Sources - open (2 No existe el fichero ó directorio)
(It comes to say that the file debian.tu-bs.de_project_kanotix_unstable_._Sources wasn't able to open because the file doesn't exist)

(And the same for '$ sudo apt-get build-dep nxproxy' ofcourse)


What's wrong?
Do I have to do anything else? :mad: 

Thanks in advance!

---

### Post by mozkill on 2007-12-06
Can someone tell me if this would work  on Ubuntu 7.10 ???

> # Download the DEBs from [http://www.nomachine.com/download-package.php?Prod_Id=1](http://www.nomachine.com/download-package.php?Prod_Id=1)
# Change your working directory to the location where you saved the package and install it by running from a console:

  # sudo dpkg -i nxclient_3.0.0-89_x86_64.deb
  # sudo dpkg -i nxnode_3.0.0-93_x86_64.deb
  # sudo dpkg -i nxserver_3.0.0-79_x86_64.deb

If not , what should I do?

---

### Post by saru411 on 2007-12-06
> **mozkill said:**
> Can someone tell me if this would work  on Ubuntu 7.10 ???



If not , what should I do?

please dont resurrect posts that are 8 months old and haver to do with a version of ubuntu over 2 years old. if you would search you could easily find this thread that will answer your questions

[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

