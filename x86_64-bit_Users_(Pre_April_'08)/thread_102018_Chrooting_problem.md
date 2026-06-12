---
title: "Chrooting problem"
date: 2005-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dronny on 2005-12-11
I got this trying run something using 32-bit chroot, created using instruction somewhere in this part of forum:
```

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :0.0
```

---

### Post by Ferrat on 2005-12-11
They instrucktions you used I guess are the once for Hoary where its best to replace alla hoary with breezy 

If you got Chroot running acoring to it, 
open a terminal
enter 
```

sudo synaptic32

```

Install X and Xlibs under the 32bit system

---

### Post by Dronny on 2005-12-11
As you say, I need separate installation of X.Org for 32-bit chroot... So, how do you think synatic32 will run before this? )

Why never mentioned about this in a chroot how-to? That's ~40Mbytes to download...

Maybe a silly question after all: will I need to run another X for 32-bit applications? That hurts...

---

### Post by rplantz on 2005-12-11
[QUOTE=Dronny]
Maybe a silly question after all: will I need to run another X for 32-bit applications? That hurts...[/QUOTE]

I'm not sure about what is going on, but I just launched arcroread32 and opened a 350 page document. The System Monitor showed that my memory usage went from 45% to 47% (out of my 1GB). I had Opera running at the same time. I haven't felt any pain yet. :-)

---

### Post by Dronny on 2005-12-11
> I'm not sure about what is going on, but I just launched arcroread32 and opened a 350 page document. The System Monitor showed that my memory usage went from 45% to 47% (out of my 1GB). I had Opera running at the same time. I haven't felt any pain yet.

It means, no other X is running. Good. So why do I need to install X and Xlibs uder a chroot?

All what i did was:

1) followed all th instructions in the how-to
2) typed 'synaptic32' under normal environment or 'synaptic' under chroot or just 'apt-get install firefox' (passed normally) and 'firefox'
3) got message pasted in the first post: "connection to ":0.0" refused by server" etc...

---

### Post by HankB on 2005-12-11
[QUOTE=Dronny]It means, no other X is running. Good. So why do I need to install X and Xlibs uder a chroot?
[/quote]
X is a client server architecture. The server is the display. The clients are the programs that you run. They use the server to display output for them. Some people make the point that X is really a protocol description for the messages sent between the server and the client. In fact, at home where I have too many computers running Linux, I can 'ssh' to different systems and run X applications and they display side by side on my desktop with applications I run locally. 

Your clients need various (32 bit) libraries in order to communicate with the (64 bit) server. You get those as a side effect of installing X.

> 

All what i did was:

1) followed all th instructions in the how-to
2) typed 'synaptic32' under normal environment or 'synaptic' under chroot or just 'apt-get install firefox' (passed normally) and 'firefox'
3) got message pasted in the first post: "connection to ":0.0" refused by server" etc...

"connection ... refused" means that your client tried to connect to the server and the server is configured not to accept connections for this client. I'm less clear on this because I'm not sure what the client looks like to the server. I used to display remotely by telnetting to remote hosts and then setting the DISPLAY variable to point to the one I was coming from. The client would establish a TCP/IP connection to the server. I had to tell the server to accept connections from the romete host because for security reasons, this is usually disallowed. (see the xhost command.) On modern systems, the X server is configured to not accept TCP/IP connections and the standard method is to tunnel the connection from a remote machine using SSH ('ssh -X <remote>'.) Then as far as the server is concerned, the connection looks like a local connection.

I don't know what the connection looks like from a chroot, so I'm afraid this is about as much help as I can provide. My guess is that the 32 bit client is trying a TCP/IP connection and the server is not listening for those or the server gets the connection and determines that the client does not have permission to use the display. You might check logs (in /var/log) to see if you can find a clue.

Sorry I could not be more help. I'm getting ready to install a 32 bit chroot myself.

thanks,
hank

---

### Post by Dronny on 2005-12-11
HankB, thans for such detailed answer, it's now more clear for me. The ting, that is still totally unclear - how to install 'X libraries'. I've tried yet 'apt-get install xorg*', but i think now, that is a server part and I don't need it.

---

### Post by HankB on 2005-12-11
apt should install all of the stuff that you need for a given application. I just set up a 32 bit chroot following the directions in [http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit) and when I went to install firefox from within the chroot, I got:
```
root@baobab:~# apt-get install firefox
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  cpp cpp-4.0 defoma file fontconfig libatk1.0-0 libcairo2 libexpat1 libfontconfig1 libfreetype6 libgdbm3 libglib2.0-0
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libice6 libidl0 libjpeg62 libkrb53 libmagic1 libpango1.0-0 libpango1.0-common
  libpng12-0 libsm6 libtiff4 libx11-6 libxau6 libxcursor1 libxdmcp6 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxrandr2
  libxrender1 libxt6 perl perl-modules psmisc ttf-bitstream-vera ucf x-common
Suggested packages:
  cpp-doc gcc-4.0-locales defoma-doc psfontmgr x-ttcidfont-conf dfontmgr firefox-gnome-support latex-xft-fonts xprint
  libfreetype6-dev krb5-doc krb5-user ttf-kochi-gothic ttf-kochi-mincho ttf-thryomanes ttf-baekmuk ttf-arphic-gbsn00lp
  ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp libterm-readline-gnu-perl libterm-readline-perl-perl
Recommended packages:
  libft-perl libatk1.0-data libglib2.0-data hicolor-icon-theme perl-doc debconf-utils
The following NEW packages will be installed:
  cpp cpp-4.0 defoma file firefox fontconfig libatk1.0-0 libcairo2 libexpat1 libfontconfig1 libfreetype6 libgdbm3 libglib2.0-0
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libice6 libidl0 libjpeg62 libkrb53 libmagic1 libpango1.0-0 libpango1.0-common
  libpng12-0 libsm6 libtiff4 libx11-6 libxau6 libxcursor1 libxdmcp6 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxrandr2
  libxrender1 libxt6 perl perl-modules psmisc ttf-bitstream-vera ucf x-common
0 upgraded, 44 newly installed, 0 to remove and 0 not upgraded.
Need to get 26.3MB of archives.
After unpacking 84.6MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

I'm not sure why it needed the C compiler, but I went ahead and installed what it asked for anyway. I can run firefox from the chroot (as long as I shut down the 64 bit version first. :???: ) But I still cannot run flash. :confused:

---

### Post by Dronny on 2005-12-11
HankB, try 'apt-get install flashplayer-mozilla' now.

---

### Post by HankB on 2005-12-11
[QUOTE=Dronny]HankB, try 'apt-get install flashplayer-mozilla' now.[/QUOTE]


Yes, works now.

Thanks!

---

### Post by Dronny on 2005-12-11
And my problem rests unsolved...

---

### Post by Patsoe on 2005-12-12
Dronny: I'm just guessing, but this may be your problem: if you run an X-app from within the chrooted environment, it might not be able to find the X-server.

e.g. if I type 
```

me@host:~$ dchroot
Executing shell in 'breezy32' chroot.
me@host:~$ acroread

(acroread:10354): Gtk-WARNING **: cannot open display:
me@host:~$ 

```
is what I get. Therefore, I instead type
```

me@host:~$ dchroot -d
Executing shell in 'breezy32' chroot.
me@host:~$ acroread

```
where the difference is the '-d' option, to preserve the environment. Apparently then, the referrers to the X-server (or whatever) remain set. This is all relatively new to me, so I can't explain very well yet. Hope it helps.

---

### Post by Dronny on 2005-12-12
I'm always using a '-d' option. I'll try without it, but i don't think it would be useful...

---

### Post by Patsoe on 2005-12-12
no, it will only be worse without the -d
what we're you trying to run?

---

### Post by Dronny on 2005-12-12
synaptic, firefox (installed using apt-get), xclock... everyting with the same message as result

---

### Post by HankB on 2005-12-12
[QUOTE=Dronny]And my problem rests unsolved...[/QUOTE]

Have you looked at the xhost command?

Can you provide more information on what you're doing? Exactly how are you getting into the chroot? What procedure did you follow to set up your chroot? Have you gone back and rechecked all of the steps to make sure you haven't overlooked anything?

-hank

---

### Post by nalmeth on 2005-12-12
if as hankb asks you have followed all the steps correctly (making sure every instance of 'hoary' has been changed to 'breezy' including in sources.list) try symlinking the app to you 64-bit and running it from there
(remove 64-bit firefox or whatever you need to avoid confusion)
(from 64-bit terminal)
sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/firefox
if this command says do_dchroot already exists try
sudo ln -s /usr/local/bin/firefox /usr/local/bin/do_dchroot
firefox
I don't exactly understand the nature of your problem, so if this is redundant and doesn't help you, then I am sorry.
Somebody correct me if I'm wrong, but you might just want to install the i386 kernel if you don't want to deal with chrooting. Apparently 32-bit runs very well on 64-bit processors. I haven't tried myself, but I am considering it.

---

