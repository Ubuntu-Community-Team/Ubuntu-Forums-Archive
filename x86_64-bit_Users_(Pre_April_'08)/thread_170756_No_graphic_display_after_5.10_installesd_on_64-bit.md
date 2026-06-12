---
title: "No graphic display after 5.10 installesd on 64-bit."
date: 2006-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by sidy on 2006-05-05
Hello there,

After the second time I've installed ubuntu 5.10 on my 64bit-PC, (2 hdds, 80 as master and 40 as sleve), the instalation has been done on 40 (all my datas are in the 80).

Then, in stead of go to login happened the following:


'biiiiiiiiiiiiiiiiiiiiiii! biiiii! biiiii! bii!' sound,
and
a black screen with a little line like this   ' - ' on the left-top-corner. nothing else!


from here I cannot go any where, unless a press the power bottom, which is not right, then I can go through the 'recovery mode' and access the root.


Aditional information, 
On root to get access to the 80hdd, came up the following error:

'(nautilus:6535): GTK-Warning **:cannot open display'

After I had done the following:

mount
cd /mnt
ls
mkdir hda1
ls
mkdir hda2
ls
mkdir hda3
ls
mount /dev/hda1 /mnt/hda1
mount /dev/hda2 /mnt/hda2
mount /dev/hda3 /mnt/hda3
cd hda2
ls
cd home
ls
nautilus

(nautilus:6535): GTK-Warning **:cannot open display.

CAN YOU PLEASE SEND ME COMMANDS OF HOW CAN I DISPLAY?

By the way, I've used the live cd, is the same problem.

Regards.

Sidney.

---

### Post by mips on 2006-05-05
Uhmm, did you install the 32bit or 64bit version ??? All you said is that you install onto a 64bit pc but we don't know which version ?

Try, **sudo dpkg-reconfigure xserver-xorg**

Tells us a bit more about your hardware devices/specs

---

### Post by sidy on 2006-05-05
I didn't do any partition when installing, and I don't know what is devices/specs, but I did as you said then it says 

'devices/specs is not installed.'

what shall I do?

(sorry about the triple threats, I'm desperatee, with no much experience on PC stuff)

---

### Post by mips on 2006-05-05
[QUOTE=sidy]I didn't do any partition when installing, and I don't know what is devices/specs, but I did as you said then it says 

'devices/specs is not installed.'

what shall I do?

(sorry about the triple threats, I'm desperatee, with no much experience on PC stuff)[/QUOTE]

Did you install the 32bit or 64bit version of Ubuntu ?
What hardware is in you machine, graphics card etc. ?
Did you run the **sudo dpkg-reconfigure xserver-xorg** command ?

---

### Post by sidy on 2006-05-05
Yes I run the **sudo dpkg-reconfigure xserver-xorg** command ?[/QUOTE]
But after was the same.

 I installed 64 bit version of Ubuntu.

The machine is:
AMD 64 processor
Seprom + or - 3000 (sorry I can't be specific on this).
1024 ram.
80 hdd (master, where my datas are).
40 hdd (slave, where I am traying to install).
 (I am afraid I dont know the graphic card, I will find out).
21 inch monitor.

thank you, again

---

### Post by mips on 2006-05-05
Have you tried the 32bit version ?

---

### Post by glenn45 on 2006-05-06
Here's a suggestion. maybe your graphics card has no driver. try changing the X1186.config file,. or maybe X.conf file im not sure. try searching for this file using locate command. then once you have located it, edit the file and change  in the "Device" section the 
Driver "vesa" 

maybe that will work.

---

### Post by sidy on 2006-05-06
Hello again,

=I have been to 'sudo dpkg-reconfigure xserver-xorg', and change the driver device to 'vesa' (mine was s3), it didin't work.

=Then I did it manually, It got worse that a needed to install every thing again.

=I don't know how to apply the commands 'X1186.config file' or 'X.conf file', command not found.

=I'm very please to have your help.

Regards.

Sidney.

---

### Post by turbojugend_gr on 2006-05-06
Hi there!
First of all try to re-install ubuntu, since you never used it you won't loose anything to try so. During the new installation do not agree to anything you do not fully understand. Can you rememeber if you were ever asked anything regarding to screen resolutions???
Propably you weren't but if you were then in the new installation be carefull and choose the resolutions you know that your monitor is capable of.
Propably that's not the case. Here i have to note that the friend telling you to change to VESA was refering to the MONITOR entry in the configuration file, not the graphics card, so restore your previous settings and your monitor to standart VESA.
I hope i gave you a hint. I am also using amd64 kernel and i need to inform you that you could also try the 32bit version with no problem.

---

### Post by turbojugend_gr on 2006-05-06
I also have to add, that the xorg.conf is a file located : /etc/X11/xorg.conf

---

### Post by sidy on 2006-05-07
Hi,

When I applyed '/etc/X11/xorg.conf'
says 'permition denied'

I also installed the versio 32-bit (mine says, version 5.10 for your PC), with no difference, so I installed again the version 64-bit.
I payed attention do what you said about screen resolution, I stayed with the option the CP chosen:
"1024x768" "800x600" "640x480", with no difference.
My standard graphic card is s3 and didn't find how to change tho monitor to vesa.

More Help will be welcome, I'm trying then all.

Thank you again.

---

### Post by mips on 2006-05-07
[QUOTE=sidy]
When I applyed '/etc/X11/xorg.conf'
says 'permition denied'
[/QUOTE]


You need to use **sudo** before any command to have admin privilages. So whatever command you used to edit add sudo followed by a space in front of the command.

---

### Post by sidy on 2006-05-07
I'm not luck.
Now it is saying:

sudo: /etc/X11/xorg.conf: command not found

thank you, again

---

### Post by sidy on 2006-05-07
:D HELLO EVERY ONE;) 

I'm so happy! It's been nearly a month and specially the last 48 hours working hard "we" found the solution.

\\:D/ MY PC HAS GRAPHIC DISPLAY WORKING:-\" 

After many ways "we" have tryed, the last tryed was.
-I went to the graphic card (physic), jot down the FX5200LP number.
-Then on root went to:

sudo dpkg-reconfigure xserver-xorg

-In there I've changed the standard graphic 

form "s3" to "nv" for nVidia,

-then enter. The next screen I deleted all information about S3 and put:

nv nVidia FX5200LP

-Then enter. And just the normal log in with graphic screen.

I just want thank all of you for keep trying through many ways.

Thank you;) 

Sidney.

---

### Post by sidy on 2006-05-07
:D HELLO EVERY ONE;) 

I'm so happy! It's been nearly a month and specially the last 48 hours working hard "we" found the solution.

\\:D/ MY PC HAS GRAPHIC DISPLAY WORKING:-\" 

After many ways "we" have tryed, the last tryed was.
Ctrl+Alt+F1
-I went to the graphic card (physic), jot down the FX5200LP number.
-Then on root went to:

sudo dpkg-reconfigure xserver-xorg

-In there I've changed the standard graphic 

form "s3" to "nv" for nVidia,

-then enter. The next screen I deleted all information about S3 and put:

nv nVidia FX5200LP

-Then enter. And just the normal log in with graphic screen.

I just want thank all of you for keep trying through many ways.

Thank you;) 

Sidney.

---

### Post by sidy on 2006-05-07
Now that Graphic Problems is gone.
I need to mount the hdds 'A' hda1, hda2, hda3, to get access tothe other hd '80'.

but on terminal it tell me to be on root.

HOW CAN I BE ON ROOT?

Thanks again.

---

### Post by xparisinflamesx on 2006-05-07
Hi, im new to linux, tried installing today. 
But i hit the same problem as you! 
You say You changed "s3" to "nv", well i have an ATI graphics card and was wondering what you should change "s3" to for that?? Thanks

---

### Post by mips on 2006-05-07
[QUOTE=sidy]Now that Graphic Problems is gone.
I need to mount the hdds 'A' hda1, hda2, hda3, to get access tothe other hd '80'.

but on terminal it tell me to be on root.

HOW CAN I BE ON ROOT?

Thanks again.[/QUOTE]

Whenever you need to run a command as root or edit a file as root add **sudo** followed by a **space** in front of the command you are using.

ie. sudo gedit /etc/fstab

---

### Post by sidy on 2006-05-08
[QUOTE=xparisinflamesx]Hi, im new to linux, tried installing today. 
But i hit the same problem as you! 
You say You changed "s3" to "nv", well i have an ATI graphics card and was wondering what you should change "s3" to for that?? Thanks[/QUOTE]


My sugestion is trying to do what I did.
Where you see s3 you have a list of many others like, nv, s3, vesa, etc. I don't know what would be the ATI, but it could be samething similar to 'ati'.

The next screen delete all the standard code and write this:

(mine was 'nv nVidia FX5200LP')

your could be 'ati ATI ???????'

(Yours could be 'ati' 'ATI' then this letters and numbers that I took from the graphic card on a litle stiker.) 

I'm new on Linux as well, but I hope it can help you.

---

### Post by sidy on 2006-05-08
[QUOTE=mips]Whenever you need to run a command as root or edit a file as root add **sudo** followed by a **space** in front of the command you are using.

ie. sudo gedit /etc/fstab[/QUOTE]

Thank you.
It worked fine.


'sudo ...'

---

### Post by xparisinflamesx on 2006-05-08
[QUOTE=sidy]My sugestion is trying to do what I did.
Where you see s3 you have a list of many others like, nv, s3, vesa, etc. I don't know what would be the ATI, but it could be samething similar to 'ati'.

The next screen delete all the standard code and write this:

(mine was 'nv nVidia FX5200LP')

your could be 'ati ATI ???????'

(Yours could be 'ati' 'ATI' then this letters and numbers that I took from the graphic card on a litle stiker.) 

I'm new on Linux as well, but I hope it can help you.[/QUOTE]

Ok thanks, how do u find out what model it is? i.e. when do u press Ctrl+Alt+F1?

---

### Post by mips on 2006-05-08
Most accurate way is to open the PC and record the info on the gfx card/chip imho.

---

