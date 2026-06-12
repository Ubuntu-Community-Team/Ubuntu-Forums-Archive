---
title: "Hi got some simple question about kubuntu"
date: 2008-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Strike_105x on 2008-01-16
Well simple for those ho have some time in kubuntu :)) I have kubuntu 7.10 installed are the tutorial in this section usable for kubuntu or just for ubuntu? like the ones to install video drivers or to install firefox,java, flash & codecs/players ?

Also i have an ati 9600 XT do the drivers that come with kubuntu are enough or for some lets say game aplications/mame/pSX or other do i need to install other drivers ?

---

### Post by Strike_105x on 2008-01-16
i cant seem to edit my previous thread i got a new question cant seem to copy a file on an partion (using dolphin) i keep getting message acces denied

---

### Post by Kilz on 2008-01-16
> **Strike_105x said:**
> Well simple for those ho have some time in kubuntu :)) I have kubuntu 7.10 installed are the tutorial in this section usable for kubuntu or just for ubuntu? like the ones to install video drivers or to install firefox,java, flash & codecs/players ?

Also i have an ati 9600 XT do the drivers that come with kubuntu are enough or for some lets say game aplications/mame/pSX or other do i need to install other drivers ?
Welcome to Ubuntu,
For the most part they will apply to both if instructions to use a terminal commands are given. But its always best to report what version and flavor of the os you are running if you have specific questions on how to do something.

If you like playing games you may need to install the proprietary drivers from ATI. These are not in the repositories. [This howto should help you.]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually")

> **Strike_105x said:**
> i cant seem to edit my previous thread i got a new question cant seem to copy a file on an partion (using dolphin) i keep getting message acces denied
Some parts of the operating system are not editable by users. This is a safety feature. Just as you cant edit , neither can viruses or malware. Its one of the main reasons those things do not effect linux. ```
kdesu dolphin
``` enterd into the terminal will open dolphin in administrator mode. Be very careful what you do in this mode as you can fubar your system.

---

### Post by Strike_105x on 2008-01-16
Thx verry much could someone also tell me how to acces add/remove programs with root ?

---

### Post by Strike_105x on 2008-01-16
(like i said i have Kbuntu 7.10 with kde interface) i cant seem to be able to select firefox in add/remove (managed to enter with sudo)

---

### Post by Kilz on 2008-01-16
> **Strike_105x said:**
> (like i said i have Kbuntu 7.10 with kde interface) i cant seem to be able to select firefox in add/remove (managed to enter with sudo)

I believe that it is better to use Adept with kubuntu. Also the root login is disabled in all flavors of Ubuntu. You can use sudo and kdesu to do whatever you would with root.

---

### Post by Strike_105x on 2008-01-17
I tried to Install the video drivers how it is said in this thread:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually)
but i couldnt acces the ati catalyst control center (am i not supose to see that?) also i want some something to see if everything is working ok on my PC (i mean my components) last thing the xorg ATI drivers i ccan get throught adept are they not good ?

---

### Post by Kilz on 2008-01-17
> **Strike_105x said:**
> I tried to Install the video drivers how it is said in this thread:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually)
but i couldnt acces the ati catalyst control center (am i not supose to see that?) also i want some something to see if everything is working ok on my PC (i mean my components) last thing the xorg ATI drivers i ccan get throught adept are they not good ?

The drivers in the repositories are open source versions and do not have all the fatures that the ATI ones have like accleration. This is important if you want to run games or anything that uses the accelerated drivers like Blender and some other 3d applications.
Its possible that there is just a missing menu item for the control. Open a terminal and type in amdcccle. Another test to see that things are ok is to type fglrxinfo in the terminal. This should show ati. Mine looks like this
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6747 (8.40.4)

Yours may differ slightly.

---

### Post by Strike_105x on 2008-01-18
First of all i would like to thank all the people ho helped me by answering my questions especially Kilz ho answered to every question i posted. I really begane to envoy kubuntu but have one problem right now i have installed vlc but i cant get it to run when i tried with sudo i got the folowing error:

VLC media player 0.8.6c Janus
starting VLC root wrapper... using UID 1000 (strike105x)
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 631 error_code 11 request_code 149 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

can anyone help me pls ?

also i have installed the xorg ATi drivers with out problems but psx (a playstation emulator) is running verry slow could someone know what the problem is 2 this 2 ?

---

### Post by Strike_105x on 2008-01-18
Think i found the problem can anyone tell me the command to acces Restricted-manager i dont see it in the Utilities or System menu

---

