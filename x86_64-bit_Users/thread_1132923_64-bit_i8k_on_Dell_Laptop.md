---
title: "64-bit i8k on Dell Laptop"
date: 2009-04-22
forum: x86 64-bit Users
---

### Post by michael37 on 2009-04-22
A post on Jaunty! Jaunty is going public tomorrow, and the development forums will be closing... so I'm posting here!

I just discovered that i8k kernel module is available on 64-bit Jaunty.  Great news!  It used to be i386 only. 

Does anyone know why gkrellm-i8k (works well on i386) is not available for 64-bit?  Can it be done?

Should I be using dellfand instead?  Does that work on 64-bit?

---

### Post by michael37 on 2009-04-27
Dellfand works on 64-bit.  i8k and i8kfan work as well.

---

### Post by michael37 on 2009-04-27
How to install gkrellm and gkrellm-i8k on 64-bit computer.  

[LIST=1]
[*] Make sure that i8k module loads.  Step by step instructions are in points 1-4 of [thread=842775]this thread[/thread].

[*] Install i8kutils and gkrellm ```
sudo apt-get install i8kutils gkrellm
```

[*] Download build environment ```
sudo apt-get install build-essential
```

[*] Download the source code for i8k plugin ```
wget http://ftp.de.debian.org/debian/pool/main/g/gkrellm-i8k/gkrellm-i8k_2.5.orig.tar.gz
``` or simply point your browser to [http://www.coding-zone.com/?page=i8krellm](http://www.coding-zone.com/?page=i8krellm) and download the file using the browser.

[*] Build and install the package.
```

tar xvfz gkrellm-i8k_2.5.orig.tar.gz
cd i8krellm-2.5
make
make install

```

[*] Start GKrellM via Applications/System Tools/GKrellM system monitor and enable the plugin.  Open the configuration shown below by right-clicking within the GKrellM window.

[img]http://ubuntuforums.org/attachment.php?attachmentid=111435&stc=1&d=1240868922[/img]

[img]http://ubuntuforums.org/attachment.php?attachmentid=111436&stc=1&d=1240868961[/img]

[/LIST]

---

### Post by thyraios on 2009-04-29
I get an error when trying to build the plugin (these are the last 4 lines):

> i8krellm.c: In function ‘gkrellm_init_plugin’:
i8krellm.c:1505: error: ‘_i8k_styleid’ undeclared (first use in this function)
i8krellm.c:1505: warning: implicit declaration of function ‘gkrellm_add_meter_style’
make: *** [i8krellm.o] Error 1

I don't know how to output all "make" process.
I followed the steps (i8k module is working - I have sensors-applet)

---

### Post by michael37 on 2009-05-01
> **thyraios said:**
> I get an error when trying to build the plugin (these are the last 4 lines):

I don't know how to output all "make" process.
I followed the steps (i8k module is working - I have sensors-applet)

The code looks all right for me (as in the error shouldn't occur) and I don't get this error myself.  A fair warning: I am running an updated 64-bit Ubuntu 9.04.  I haven't tried it on any other version or any other computer since this is the only version I run on this Dell laptop.

If you are stuck, try contacting the plugin author at [http://www.coding-zone.com/?page=i8krellm](http://www.coding-zone.com/?page=i8krellm)

---

### Post by thyraios on 2009-05-06
I'm running too Ubuntu 64 9.04 on a Dell Inspiron 1525 but it's not working for me. I cannot find a way to contact the plugin author.

---

### Post by michael37 on 2009-05-07
Not sure why you folks are having problems.  I will try to post a binary plugin.   I don't have skills to build my own deb package though :(

---

### Post by michael37 on 2009-05-20
Apologies for the delay.  

```

tar xvfj i8krellm-plugin.tar.bz2
cp ./i8krellm.so ~/.gkrellm2/plugins

```

Continue with step 5.

---

### Post by thyraios on 2009-05-22
Thanks a lot for this. The plugin is working except that I cannot control the fan. It shows me 2 fans although I have only one and it does not respond to any of my modification. I've also tried the howto on [http://ubuntuforums.org/showthread.php?t=842775](http://ubuntuforums.org/showthread.php?t=842775) using the swallow applet and still nothing. Regardless of how much I use my CPU or HDD the speed never gets over 90000 RPM (wich is really arround 3000) but I guess this is a problem related to my laptop (Inspiron 1525), at least that's what I found in other threads. But anyway the plugin is really helpful. Thank you

---

### Post by michael37 on 2009-05-23
> **thyraios said:**
> Thanks a lot for this. The plugin is working except that I cannot control the fan. It shows me 2 fans although I have only one and it does not respond to any of my modification. I've also tried the howto on [http://ubuntuforums.org/showthread.php?t=842775](http://ubuntuforums.org/showthread.php?t=842775) using the swallow applet and still nothing. Regardless of how much I use my CPU or HDD the speed never gets over 90000 RPM (wich is really arround 3000) but I guess this is a problem related to my laptop (Inspiron 1525), at least that's what I found in other threads. But anyway the plugin is really helpful. Thank you

Glad it works for you.  I have E1505/6400 and the fan works.  By trial and error I found that the only fan is  "right" or "second" fan. 

If you want to troubleshoot the fan behavior on the low level, you may want to consider using dellfand.  It works for me (command line only, not as integrated as i8k), but it uses a different method from i8k.

---

### Post by thyraios on 2009-05-24
dellfand won't work either. it can control only the first fan and since my second fan is the active one it won't make any difference. I've also found by doing "dmesg | grep i8k" that I get this message "i8k: unable to get SMM BIOS version". I'm doing some googling over it now.

---

