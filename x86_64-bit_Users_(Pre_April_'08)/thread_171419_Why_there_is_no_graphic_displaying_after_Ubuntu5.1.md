---
title: "Why there is no graphic displaying after Ubuntu5.10, 64 been installed on AMD 64-bit?"
date: 2006-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by sidy on 2006-05-06
Hello there, (I'm still not able to display graphics screen)

=After the third time I've installed ubuntu version 5.10, 64bit for my 64bit-PC,

=The machine is:
AMD 64 processor
Seprom + or - 3000 (sorry I can't be specific on this).
1024 ram.
80 hdd (master, where my datos are).
40 hdd (slave, where I am trying to install).
(I am afraid I dont know the graphic card, I will find out).
21 inch monitor.2 hdds, 80 as master and 40 as sleave), the installation has been done on 40 (all my datos are in the 80).


=Then, in stead of go to login happened the following:


'biiiiiiiiiiiiiiiiii! biiiii! biiiii! biii!' sound,
and
a black screen with a little line like this ' - ' on the left-top-corner. nothing else!
From there I can only go to ctrl+alt+F1 to commands.
But I don't know the right commands

=I have been to 'sudo dpkg-reconfigure xserver-xorg', and change the driver device to 'vesa' (mine was s3), it didin't work.

=Then I did it manually, It got worse that a needed to install every thing again.

=CAN YOU PLEASE SEND ME COMMANDS OF HOW CAN I DISPLAY?

By the way, I've used the live cd, is the same problem.

Regards.

Sidney.

---

### Post by Phil_McCrackin on 2006-05-06
I had the same issue... do you have more than one port for your monitor? 
If so try plugging the monitor into your other port. If that is the prob it's easy to fix.

---

### Post by usernamed on 2006-05-07
My AMD64 machine came with integrated ATI graphics, I had to add a line to my xorg.conf before the Xserver would work on my machine.

To do that, type:

 sudo nano /etc/X11/xorg.conf

and scroll down the xorg.conf until you see the "Device" section.  Add the following line in that section of the xorg.conf.

Option    "NoAccel"    "True"

Save the file, then try restarting X.  I hope this helps for you, if not you'll need to find the make and model of your graphics card, and search for advice specific to that hardware.

---

### Post by sidy on 2006-05-07
Hi there again.

I have trying plugging the monitor into your other port, it didn'y work.

Then I added the following line in the section of the xorg.conf.
Option "NoAccel" "True", didn't work, same of the beginning.

=Now, to find the make and model of my graphic card, and search for advice specific to that hardware. Which way shall I go? Root or Physic?

= If root, can you give me directions please?

= If physic, I have the following:
* FCC (Tested and comply with FCC Standard *
=Above side, I have this on a stiker:
'(01)04710958851697(21)SN0437T003409'
-Then two black squares, a kind of chip, of 2x1cm size. One next the other, with the following:
a kind of log HT, 'HD28W16M1625VD-75T
                                              0420B'
-Another two little ones with written:
One with written
'45 AHK 5K
AKTUB' (the last B if not B, 8 (can't see well)).
Other with:
'APW7058
AG47P' (the second, it not G is C).

On the other side (underneath side):
-a sticker with 'FX5200LP'.
-a bigger silver square 8x5x1,5cm (moves if I push, but don't shake).
-3 litle chips with these written
'APM3055L
CFAC6'
-Another with
'CX1117-ADJ
4293T'
-Another with
'59725VF512
20-4C-5A
3425330 AA'
-Another little silver with
'TKN27.000'
-Others, like battery AAA 1cm long, with
2 with
'FC*n
470uF6.3v' 
Other 2 with 
'FC*n
1000uF6.3v'
One with
'FC*n
1500uF6.3v'.

-A part of it a lot of little numbers near the mechanisms.

I WILL BE WAITING FOR YOUR HELP PLEASE!

Thanks again.

---

### Post by usernamed on 2006-05-07
Unfortunately, I'm not an expert on graphics cards, so I don't recognise anything here, but I believe that nVidia have a range of cards called GeForce FX???? so you may have an nVidia graphics card.  Try typing in 'lspci -v|grep -a2 VGA'

The '|' symbol (also known as the pipe symbol) is made by pressing shift+backslash (on a UK keyboard).  Post the results up here.  If you do have an nVidia graphics card, then just follow the nVidia how-to that you'll find by searching the ubuntu forums.

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

form "s3" to "nv" for nVidia, (good gess from unsernamed)

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

### Post by usernamed on 2006-05-08
Ubuntu works differently to a lot of other linux distros, in order to execute a command as root, you have to prefix the command with 'sudo'.  For example, if I wanted to mount a drive I'd type 'sudo mount /dev/hda2 /mnt/harddisk2' or similar.

When you hit enter, sudo will ask you to enter your user password (the same one you use to log into ubuntu).  Enter your password, and the command will execute as if you were root.

---

### Post by sidy on 2006-05-08
Thank you,

That worked fine.

'sudo ...'

---

