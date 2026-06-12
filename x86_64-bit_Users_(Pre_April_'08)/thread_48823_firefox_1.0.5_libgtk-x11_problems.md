---
title: "firefox 1.0.5 libgtk-x11 problems"
date: 2005-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by nrayever on 2005-07-14
i just downloaded firefox 1.0.5 installer, and i just give a try to install it. but i got this message error:

```
./firefox-installer-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
``` 

but i don't get it, because i have libgtk installed!!  ](*,)  ](*,) 

if anyone knows how to solve this problem i will appreciate it.

---

### Post by badrinarayan on 2005-07-14
Well, [apt-file](http://wiki.linuxquestions.org/wiki/Apt-file) says the following

```
badri@codebox:~$ sudo apt-file search libgtk-x11-2.0.so.0
libgtk2.0-0: usr/lib/libgtk-x11-2.0.so.0
libgtk2.0-0: usr/lib/libgtk-x11-2.0.so.0
libgtk2.0-0: usr/lib/libgtk-x11-2.0.so.0
libgtk2.0-0: usr/lib/libgtk-x11-2.0.so.0.600.4
libgtk2.0-0: usr/lib/libgtk-x11-2.0.so.0.600.4
libgtk2.0-0: usr/lib/libgtk-x11-2.0.so.0.600.4
libgtk2.0-0-dbg: usr/lib/debug/usr/lib/libgtk-x11-2.0.so.0.600.4
libgtk2.0-0-dbg: usr/lib/debug/usr/lib/libgtk-x11-2.0.so.0.600.4
libgtk2.0-0-dbg: usr/lib/debug/usr/lib/libgtk-x11-2.0.so.0.600.4

```

So, make sure you have libgtk-2.0-0 installed.

Regards
Badri

---

### Post by nrayever on 2005-07-14
according to synaptic libgtk-2.0-0 is installed. and when i tryed using apt-file, no answer is obtained!!

```
nrayever@NFORCE:~$ sudo apt-file search libgtk-x11-2.0.so.0
nrayever@NFORCE:~$ sudo apt-file search libgtk-x11-2.0.so.0
nrayever@NFORCE:~$ sudo apt-file search libgtk-x11-2.0.so.0
nrayever@NFORCE:~$ cd ../..
nrayever@NFORCE:/$ sudo apt-file search libgtk-x11-2.0.so.0
nrayever@NFORCE:/$
``` 

right know i'm trying to reinstall lib-gtk from synaptic, i hope this works.

---

### Post by badrinarayan on 2005-07-14
You have to [FONT=Courier New]sudo apt-file update[/FONT] first.

Try [FONT=Courier New]locate libgtk-x11[/FONT] to see if you have the file. Also check that the path is in [FONT=Courier New]LD_LIBRARY_PATH[/FONT]

```
badri@codebox:~$ locate libgtk-x11
/usr/lib/libgtk-x11-2.0.so.0.600.4
/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.la
/usr/lib/libgtk-x11-2.0.a
/usr/lib/libgtk-x11-2.0.so
badri@codebox:~$ echo $LD_LIBRARY_PATH
/usr/lib/
badri@codebox:~$

```

You could also query dpkg directly (better)
```

badri@codebox:~$ sudo dpkg -L libgtk2.0-0 | grep libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.600.4
/usr/lib/libgtk-x11-2.0.so.0
badri@codebox:~$

```

Good Luck!

Regards
Badri

---

### Post by nrayever on 2005-07-14
ok, now i got something!! thanks for that badrinarayan. i will try right know to install firefox 1.0.5. i believe that may be that libgtk-2.0-0 dbg was missing.

```
nrayever@NFORCE:~$ sudo apt-file search libgtk-x11-2.0.so.0
ia32-libs-gtk: usr/lib32/libgtk-x11-2.0.so.0
ia32-libs-gtk: usr/lib32/libgtk-x11-2.0.so.0.400.10
libgtk2.0-0: usr/lib/libgtk-x11-2.0.so.0
libgtk2.0-0: usr/lib/libgtk-x11-2.0.so.0.600.4
libgtk2.0-0-dbg: usr/lib/debug/usr/lib/libgtk-x11-2.0.so.0.600.4
``` 

thanks for your help!!

---

### Post by nrayever on 2005-07-14
mmmmm, this is making me a bit angry.

```
nrayever@NFORCE:~/firefox-installer$ sudo dpkg -L libgtk2.0-0 | grep libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.600.4
/usr/lib/libgtk-x11-2.0.so.0
nrayever@NFORCE:~/firefox-installer$ locate libgtk-x11
/usr/lib/libgtk-x11-2.0.so.0.600.4
/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.la
/usr/lib/libgtk-x11-2.0.a
/usr/lib/libgtk-x11-2.0.so
nrayever@NFORCE:~/firefox-installer$ echo $LD_LIBRARY_PATH

nrayever@NFORCE:~/firefox-installer$
``` 

i have no path for for it!! may i ask u, how can i fix it??
thanks badrinarayan

---

### Post by badrinarayan on 2005-07-14
Sure. Type [FONT=Courier New]export LD_LIBRARY_PATH=/usr/lib/[/FONT] in a command window. To make it permanent, you may want to add this to */etc/bash.bashrc*

Regards
Badri

---

### Post by nrayever on 2005-07-14
badri, i hope you're pacient with me and this fu$%&# s%&#. because it not working!!. i just made it step by step as you told me. and i still get this message:

```
nrayever@NFORCE:~$ cd firefox-installer
nrayever@NFORCE:~/firefox-installer$ echo $LD_LIBRARY_PATH
/usr/lib/
nrayever@NFORCE:~/firefox-installer$ ./firefox-installer
./firefox-installer-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
nrayever@NFORCE:~/firefox-installer$
``` 

any idea???

nrayever

---

### Post by badrinarayan on 2005-07-14
Are you on AMD-64? You may be interested in this thread too : [http://ubuntuforums.org/showthread.php?t=16767](http://ubuntuforums.org/showthread.php?t=16767) that appeared in my googling.

Also try [FONT=Courier New]ldd /usr/lib/libgtk-x11-2.0.so.0[/FONT] and refer to [http://enterprise.linux.com/article.pl?sid=05/05/15/1115252](http://enterprise.linux.com/article.pl?sid=05/05/15/1115252)

Regards
Badri

---

### Post by nrayever on 2005-07-14
badri

according to ld command libgtk, have all it's dependencies ok. and according to me generic firefox-installer from mozilla should work ok for any linux processor, because once i installed 1.0.4 from that file provided by mozilla.

i don't really get if it's any kind of bug or any other broken dependency. i'm not able to install firefox 1.0.5. pretty strange!! but i don't have a clue on it.
thanks for your help!!

nrayever

---

### Post by kurtbendl on 2006-07-14
[HTML]<pre>I just had the exact same problem, I think. 
So, here's what I did:

Started konsole
typed:
  sudo su -
  vi /etc/apt/sources.list

Editing that file, I found a line that was #commented out,
and uncommented that:

  # Line commented out by installer because it failed to verify:
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

(Why did it do that? That's just stooopid.)

Then, I went ahead and uncommented the "universe" stuff, cause
I know I'll want packages from there.

Next, I needed to update the package listing, so I typed:
  aptitude update

Finally, I install the package:
  aptitude install firefox

Magic!! The nifty button magically appeared in my menu and... It works!!!

I hope this helps you, too!
:-)
 -kb

</pre>[/HTML]
> **nrayever said:**
> i just downloaded firefox 1.0.5 installer, and i just give a try to install it. but i got this message error:

```
./firefox-installer-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
``` 

but i don't get it, because i have libgtk installed!!  ](*,)  ](*,) 

if anyone knows how to solve this problem i will appreciate it.

---

