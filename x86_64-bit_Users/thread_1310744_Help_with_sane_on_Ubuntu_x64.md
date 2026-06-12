---
title: "Help with sane on Ubuntu x64"
date: 2009-11-02
forum: x86 64-bit Users
---

### Post by Eichhorn on 2009-11-02
Hello, I'm pretty new in linux, so i have a question.
I have 64bit Ubuntu 9.10 and Xsane (scanning app), for my Epson RX610 i need plugin from epkowa, BUT there is only i386 .deb and archive called pipslite_1.4.0-5.tar.gz.
And so my question is: How to run this thing on my PC? Cause i have no idea what i can do, cause when I'm trying to run install-sh it writes :"no input file..." Help me please, I really need working skanner.
P.S. I used search and didn't found the same theme so if smt sorry.
P.P.S. My english isn't perfect so don't kick me for mistakes :p
******************************************************************************
Guys, I really need your help...

---

### Post by Damanther on 2009-11-02
I followed these steps... (from another post) and it works for me on my 64bit system.

Steps:
$ sane-find-scanner

write down the product and device id

$ sudo gedit /etc/sane.d/epson.conf

add product and device id to the usb section in /etc/sane.d/epson.conf file. also uncomment(delete #) "usb /dev/usb/scanner0" found at the bottom of the file.

$ sudo gedit /etc/sane.d/dll.conf

Next make sure /etc/sane.d/dll.conf lists epson and epson2 is deleted or make sure it has a # in front of it.

Restart the computer,and your scanner should work now.

Now I would like to get the CD printing portion working...If anyone has some suggestions please let me know.

---

### Post by Eichhorn on 2009-11-02
Thank you I'll try it, but 1 more question. In all tutorials people use "sudo" but isn't it easier to use "sudo su" 1 time and not print "sido" before every command?

Nope, that didn't work for me (

OK, I just did it, downloaded iScan for my printer and then xsane saw it, I'm really happy, it's buggy but it doesn't changes anything, so now I just need to uninstall iscan cuz it cause boot problems)

***********************************************
I hate epson ( just i uninstalled iscan xsane stopped it's work... anyway I solved my first problem =)

---

