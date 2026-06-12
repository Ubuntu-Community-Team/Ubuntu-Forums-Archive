---
title: "Gnome-Terminal broken after update."
date: 2006-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by smallville on 2006-08-17
Hello, I'm relatively new to linux - installed a 64 bit version of Ubuntu, hoping to run Compiz/Xgl (wich I've installed and ran on a 32bit version just two days ago...using guides.) Anyways, fresh installation of Ubuntu 64bit... modified my sources.list to the following:

```

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
```

my backup code looked like this:

```
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
```

Right after apt-get update finished, my terminal 'shortcut' was broken. Can't recall the error, but I'm sure it was just telling me the source wasn't there.

Anyways, I used Synaptic Packet Manager to try to install gnome-terminal...
But I get the following error: 

```
gnome-terminal:
  Depends: gnome-terminal-data (=2.14.2-0ubuntu1) but 2.14.2-0ubuntu2 is to be installed
```

gnome-terminal-data -is- installed...but it doesn't work correctly, obviously. So, anyways...I'd prefer the command-line interface for installing compiz..so, if anyone can help me - I'd gladly appreciate it. Also, maybe a newb question, but does ubuntu have any kind of "system restore" functionality, like windows?
hehe

Anyways, thanks in advanced.
            -Smallville

---

### Post by moma on 2006-08-17
I have a similar annoying problem in Ubuntu 6.06 (32 bits).
gnome-terminal is broken because of some missing packages.

$ sudo apt-get upgrade 
Failed to fetch
[http://www.beerorkid.com/compiz/pool/main/v/vte/libvte4_0.12.2-0ubuntu2_i386.deb](http://www.beerorkid.com/compiz/pool/main/v/vte/libvte4_0.12.2-0ubuntu2_i386.deb)  
404 Not Found
[http://www.beerorkid.com/compiz/pool/main/v/vte/libvte-common_0.12.2-0ubuntu2_all.deb](http://www.beerorkid.com/compiz/pool/main/v/vte/libvte-common_0.12.2-0ubuntu2_all.deb)  
404 Not Found
[http://www.beerorkid.com/compiz/pool/main/v/vte/python-vte_0.12.2-0ubuntu2_i386.deb](http://www.beerorkid.com/compiz/pool/main/v/vte/python-vte_0.12.2-0ubuntu2_i386.deb)  
404 Not Found

Am investigating the problem....

Temporary solution:
Press **ALT + F2** and run **xterm**. 
Start "gnome-terminal" from command line (in xterm) and report errors here.

[COLOR="Red"]EDIT:[/COLOR]
The packages were in 
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
Added it into /etc/apt/sources.list.

But howto help you....

[COLOR="Red"]EDIT:[/COLOR]
You may try 
$ [COLOR="Green"]sudo apt-get install --reinstall  gnome-terminal[/COLOR]
or
$ [COLOR="Green"]sudo apt-get install --reinstall --force-yes gnome-terminal[/COLOR]

---

### Post by smallville on 2006-08-17
Ok, I ran
[COLOR="Lime"]$ sudo apt-get install --reinstall --force-yes gnome-termina[/COLOR]l
But I still get the same er
[COLOR="Red"]depends: gnome-terminal-data (=2.14.2-0ubuntu1) but 2.14.2-0ubuntu2 is to be installed[/COLOR]
but gnome-terminal-data -is- installed... but maybe a newer version? dunno.
ror.

By the way, When I press Alt+F2, a window pops up called "Run Application", I can't run commands from it. Doubt it's the 'xterm' you're talking about.
So, I killed Gnome (Ctrl+Alt+Backspace) and ran the commands from the normal command-line. No luck.

---

### Post by GZ1 on 2006-08-17
At least 32bit version works fine. I upgraded 2 boxes, first 3 hours again, second now. 2.14.2-0ubuntu2 adds real transparency - long awaited. 
Just wait a bit.

---

### Post by smallville on 2006-08-19
Hey, I fixed my problem. All I did is go into System->Preferences->Keyboard
then, I changed my layout. It was set on Generic 101-key PC, but I changed it to Microsoft Office Keyboard (windows doesn't even have the support for this keyboard.) Go penguin!

Anyways, I got gdesklets and compiz running fully optimal. :) Thanks for your help.

---

