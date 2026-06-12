---
title: "gnome-terminal error"
date: 2007-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ZypherXII on 2007-08-20
Hey there, 
I just  got a clean ubuntu 64bit installation down, updated. But after setting my nvidia-settings for 2 monitors, when i open gnome-terminal it just pops up saying "starting terminal..." and it disappears again. So i started xterm and typed gnome-terminal and it gave me the following error:

The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive th error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

What do I do?

[EDIT: Sorry for the misplacing of forum :(]

--
Cheers,
ZypherXII

---

### Post by Kagee on 2007-08-21
I have the exact same problem, but on 32bit

Hey there,
I just got a clean ubuntu 32bit installation down, updated. But after setting my nvidia-settings for 2 monitors, when i open gnome-terminal it just pops up saying "starting terminal..." and it disappears again. So i started xterm and typed gnome-terminal and it gave me the following error:

The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
(Details: serial 105 error_code 2 request_code 78 minor_code 0)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive th error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)


Tried xfce4-terminal:

The program 'xfce4-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadColor (Invalid Colormap parameter)'.
(Details: serial 241 error_code 12 request_code 1 minor_code 0)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive th error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by Jouke74 on 2007-08-21
Well my suggestion would be to try one monitor first... I assume that the program/driver and/or settings that make the two monitors work have some compatibility problem with the terminal programs.

---

### Post by Kagee on 2007-08-21
I got these two links on an norwegian forum. gnome-terminal works... i've still got problems with screensavers av tilda.....

[https://bugs.launchpad.net/ubuntu/+source/l...6.17/+bug/58232](https://bugs.launchpad.net/ubuntu/+source/l...6.17/+bug/58232)

[https://answers.launchpad.net/ubuntu/+sourc.../+question/9430](https://answers.launchpad.net/ubuntu/+sourc.../+question/9430)

---

### Post by Belisarius on 2007-08-25
I've just been playing with Compiz on my dual head setup and after installing my terminal broke with the same error. The only thing extra I had changed in my xorg.conf was to set:

> Section "Extensions"
	Option "Composite" true
EndSection

This was put in to try and stop a screen flicker when using conky. When I set this back to false gnome-terminal starts again.

Hope this helps

Andy

---

### Post by chapeaurouge on 2008-03-29
Same thing here, on ubuntu 64bits... Using xterm for now.

---

### Post by chapeaurouge on 2008-03-29
Workaround can be found here:

[http://bugzilla.gnome.org/show_bug.cgi?id=354767](http://bugzilla.gnome.org/show_bug.cgi?id=354767)

---

