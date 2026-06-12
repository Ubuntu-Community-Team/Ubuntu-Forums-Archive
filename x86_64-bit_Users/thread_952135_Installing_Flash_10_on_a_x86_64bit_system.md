---
title: "Installing Flash 10 on a x86 64bit system??"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by MasterNetra on 2008-10-18
I was excited to learn that adobe is finally starting to pay attention to ubuntu and had released a version of Flash 10 for linux (and a download for .deb noting ubuntu) however when i tried to use the .deb to install the installer claims its the wrong architecture and has 'i386' next to it... What gives? Is it hating cause my system is 64 bit??

---

### Post by SunnyRabbiera on 2008-10-18
Because adobe doesnt openly support 64 bit at this time.
For you you may have to install flash 10 the old fashioned way.

---

### Post by MasterNetra on 2008-10-18
Maybe I should do a fresh install of 8.10 (32 bit) when it comes out -.- How do I do the old fashion install of Flash 10?

---

### Post by Sef on 2008-10-18
> Maybe I should do a fresh install of 8.10 (32 bit) when it comes out -.- How do I do the old fashion install of Flash 10?
With Intrepid Ibex, 8.10,and Hardy Heron, 8.04, read [Kilz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490").  Before running the command, do this command: ```
sudo apt-get upgrade
```.   That insures that you are using the latest packages in the repositories.

---

### Post by empty_tank on 2008-10-18
try [http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)

It works for me using hardy amd64

---

### Post by MasterNetra on 2008-10-18
I'm using intel processors not amd :P "Intel Core 2 duo"

---

### Post by empty_tank on 2008-10-19
when i posted about installing adobe 10 in hardy amd64, I meant the ubuntu hardy x86 64 bit version, which is also called amd64 version.  I am using a dell vostro 1400 with intel core2 duo.

No problems with adobe 10 so far.

---

### Post by jmszr on 2008-10-19
This is from Tombuntu.com,

copy and paste this in the terminal:

wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh) && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh

All done.   Worked fine for me-AMD64 3200+

---

### Post by Kilz on 2008-10-19
Please be aware that by entering that command you are running a script. Please make sure to download and read all scripts before installing them to make sure they do what they are supposed to. This script may be ok but never install something you dont know about.

---

### Post by sethvath on 2008-10-19
I second that. Instead of wget-ing the file from an unknown server that might be prone to hacking or malicious modification of contents, save the script to your desktop, read and make sure nothing suspicious is going on. Chmod the file then execute and run.

---

### Post by Retrograde77 on 2008-10-19
Have just recently switched to 8.10 x64 from 8.04 x86 and used the guide that is a the top of this forum.
Flash 10 and no issues so far, very impressed. :)

---

