---
title: "I'm having trouble installing applications..."
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tecnix on 2006-01-09
Can someone please help me out?, I am having trouble installing applications like LimeWire or AIM.

---

### Post by aysiu on 2006-01-09
[QUOTE=Tecnix]Can someone please help me out?, I am having trouble installing applications like LimeWire or AIM.[/QUOTE] [http://makuchaku.info/amnesty/#limewire](http://makuchaku.info/amnesty/#limewire)
```
sudo apt-get install gaim
```

---

### Post by dombleu on 2006-01-09
Gtk-gnutella is another gnutella client. It works just fine and is mucho easier to install. But you got to have the 0.96 version on:

[http://gtk-gnutella.sourceforge.net/](http://gtk-gnutella.sourceforge.net/)

---

### Post by Tecnix on 2006-01-11
what do i put in for password?

---

### Post by dombleu on 2006-01-11
To use the sudo command. Your user should be listed in /etc/sudoers. But if you are the first user originally configured during installation, I think you should be alright.

Anyway, you should use your own password. ( The one you use on logon screen... )

```
man sudo
```

in a terminal should get you more information on the sudo command and the mentallity behind it.

Have fun!

:)

---

### Post by Tecnix on 2006-01-11
what do i do if it says permission denied?

---

### Post by und3rtug4 on 2006-01-11
If you are using Gnome, then you must:

Click on SYSTEM -> ADMINISTRATION -> Synaptic Package Manager

Enter the password

Search for the aplications that you want

Click on the right button and select; MARK FOR INSTALATION

Then, when you have selected all the packages that you want, click on

APPLY

Wait a moment, and VOILA!


#########################

If you are using the command line mode, you must do this:

(this will refresh your sources...)
sudo apt-get update
sudo apt-get upgrade

then type:

sudo apt-get install (package name without ()'s )

;)

---

### Post by und3rtug4 on 2006-01-11
[QUOTE=Tecnix]what do i do if it says permission denied?[/QUOTE]

Check the properties of the file, and make sure that the file has permission to execute!

something like this:

-rwxr--r--

Or just a click on the execute option, on properties --> permissions

---

### Post by Tecnix on 2006-01-11
Thanks! :)

---

### Post by und3rtug4 on 2006-01-11
Glad to help you out!

;)

---

### Post by Tecnix on 2006-01-11
so how would i like install aim same way?

---

### Post by Tecnix on 2006-01-11
now does aim install the same way and where is my trash located i hit remove from panel on accident :confused:

---

### Post by Tecnix on 2006-01-11
nvm about the trash i found it

---

### Post by ssam on 2006-01-13
[QUOTE=Tecnix]so how would i like install aim same way?[/QUOTE]

as in aol instant messenger?

use gaim, it is installed by default and should be in applications -> internet.

is does all the major instant messenging protocols.

---

