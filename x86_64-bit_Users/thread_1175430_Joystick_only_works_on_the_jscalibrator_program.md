---
title: "Joystick only works on the jscalibrator program"
date: 2009-06-01
forum: x86 64-bit Users
---

### Post by jppinto on 2009-06-01
I am running ubuntu 8.10 64bits and I am trying to use a Trust QZ 501 PREDATOR 5 axis - 5 buttons joystick.

Even though the jscalibrator program detects it and seems to recognize and calibrate all the axis and buttons, NO OTHER PROGRAM is able to use the axis of the joystick.

For example, if we try to run supertux2, the only thing that works are the buttons.

A solution to go around this issue is simply to unplug the joystick and plug it into a USB that hasn't been calibrated with jscalibrator. And run the applications with the unconfigured joystick. This way, the axis seem to work, but the joystick cannot be used because it is not correctly calibrated!

How to calibrate the joystick? Any help, suggestoions, or light into this issue is deeply appreciated.

---

### Post by jppinto on 2009-06-01
SOLVED

used: 

 jscal -c /dev/input/js0
 jscal -p /dev/input/js0 >> Desktop/joystick.cal
 sudo mv Desktop/joystick.cal /etc/joystick.cal
 source /etc/joystick.cal

 added "source /etc/joystick.cal" to ~/.bashrc file

the jscal calibrated some of the axis as being inverted. In order to fix it, I changed signs in the joystick.cal file, on the data values that corresponded to the axis that were wrong.

Note that jscalibrator does not calibrate properly the joystick and from that configuration the analog axis stop working. That is why I used jscal.

Hope this will help someone in the future.. if not maybe ME :D

---

### Post by pwc on 2009-06-07
jppinto, could you expand on this:

used:

jscal -c /dev/input/js0
jscal -p /dev/input/js0 >> Desktop/joystick.cal
sudo mv Desktop/joystick.cal /etc/joystick.cal
source /etc/joystick.cal

Are these terminal commands? Not sure what to do here, I,m trying to set up new Logitech joystick.

thanks, pwc

---

### Post by TheBuzzSaw on 2009-06-08
A less elegant solution is to simply restart your computer after using the calibration program. I don't remember the technical reasons behind this, but something about this program disables the joystick device in all other programs. If you simply run those other programs *before* launching the calibrator, they should detect it just fine.

---

### Post by jppinto on 2009-06-08
> **pwc said:**
> jppinto, could you expand on this:

used:

jscal -c /dev/input/js0
jscal -p /dev/input/js0 >> Desktop/joystick.cal
sudo mv Desktop/joystick.cal /etc/joystick.cal
source /etc/joystick.cal

Are these terminal commands? Not sure what to do here, I,m trying to set up new Logitech joystick.

thanks, pwc

Yes, they are desktop commands. Instead of using the program "jscalibrator" I used "jscal". Those are the commands I used in the right order.

In case you get the axis inverted, you might want to edit the "joystick.cal" file. Simply erase all minus "-" signs, and it should be OK.

**So how to do this Step-by-step?**

1 - open Terminal program (Applications-Accessories-Terminal)
2 - type the following set of commands (press enter after each line):

[I]jscal -c /dev/input/js0
jscal -p /dev/input/js0 >> Desktop/joystick.cal
sudo mv Desktop/joystick.cal /etc/joystick.cal
source /etc/joystick.cal[/I]

3 - check your joystick for inverted axis using your favourite game. If all is OK you can jump to step 8.

4 - If you have inverted axis, type:

*sudo gedit /etc/joystick.cal*

5 - remove all minus signs
6 - back in the terminal type:

*source /etc/joystick.cal*

7 - test your favourite game... by now it should be working.

8 - to avoid having to source the /etc/joystick.cal file every time you start your PC, add add "source /etc/joystick.cal" to ~/.bashrc file. Do this by typing in terminal:

*gedit ~/.bashrc file*
write in an new line, in the end of the file: "*source /etc/joystick.cal*" (without the "")

or, in alternative you can simply type in the terminal:

[I]cp ~/.bashrc ~/bashrc.old
echo "source /etc/joystick.cal" >> ~/.bashrc[/I]

**If you wish I can write a script file to do this automatically...**
[U]
If you have other problems or if any of these steps don't work[/U] try checking if the path "/dev/input/js0" is the same in your case, try it by writing in the terminal "ls /dev/input/js*". If you have a different path, then, simply adjust the previous commands on step 2 with your own path.

Was this info helpful?


jppinto

---

### Post by jppinto on 2009-06-08
> **TheBuzzSaw said:**
> A less elegant solution is to simply restart your computer after using the calibration program. I don't remember the technical reasons behind this, but something about this program disables the joystick device in all other programs. If you simply run those other programs *before* launching the calibrator, they should detect it just fine.

That method didn't work for me. The jscalibrator calibrations were all messed up (only the buttons worked).

That, and the fact that I had to restart, made me opt for jscal which works flawlessly in my ubuntu 64bits :)

Anyway... I'm curious to know if my previous reply is helping others making it work!

J

---

### Post by pwc on 2009-06-08
Thanks jppinto, for that very well done "how to". It worked and I'm using joystick now.
  
I'm not sure about the script. I've copied the instructions here and saved in my files so I can use in future. If you wrote script, I'd definitely get it and put in my Scripts folder, but as I see it, you'd still have to manually set things. So I guess it would save you the trouble of using the terminal, but thats not much in this "how to".

I'll keep my eyes on this thread and thanks for doing such a nice job.

pwc

---

### Post by jppinto on 2009-06-08
> **pwc said:**
> Thanks jppinto, for that very well done "how to". It worked and I'm using joystick now.
  
I'm not sure about the script. I've copied the instructions here and saved in my files so I can use in future. If you wrote script, I'd definitely get it and put in my Scripts folder, but as I see it, you'd still have to manually set things. So I guess it would save you the trouble of using the terminal, but thats not much in this "how to".

I'll keep my eyes on this thread and thanks for doing such a nice job.

pwc

Well... to be honest. Just after suggesting to write a script I decided that I really could use one! So I wrote it. The only thing that is not automated is the appended line to your ~/.bashrc file. 

Here is the script: (see attachment)

NOTE THAT: 
 a) check if the script file is executable. If not, type from inside the directory where the script is: "chmod +x *.sh"
 b) you should launch the script from a terminal
 c) the script will ask for your **SUDO** permission to copy the joystick.cal file to the "/etc" folder. It is OK. But if you are suspicious, you can look inside the script file with a text editor (gedit for example) and see that it is all just simple and basic commands!

After using this forum to solve my endless problems, I'm glad I helped someone in here! :)

J

---

### Post by pwc on 2009-06-08
OK jppinto, got your script, tried it out, works great. I've saved in my ~/Scripts folder for future use. This would be helpful info in the gamers forum, you should post it there.

Well thanks again for fixing me up, pwc

---

### Post by jppinto on 2009-06-08
> **pwc said:**
> OK jppinto, got your script, tried it out, works great. I've saved in my ~/Scripts folder for future use. This would be helpful info in the gamers forum, you should post it there.

Well thanks again for fixing me up, pwc

Feel free to add a link there.

J

---

### Post by TheBuzzSaw on 2009-06-08
> **jppinto said:**
> That method didn't work for me. The jscalibrator calibrations were all messed up (only the buttons worked).

That, and the fact that I had to restart, made me opt for jscal which works flawlessly in my ubuntu 64bits :)

Anyway... I'm curious to know if my previous reply is helping others making it work!

J
Hm. This doesn't make sense to me. Methinks you misunderstood my instructions. (Not that it matters since there is this nifty script to take care of the issue.)

If I just run my games (including stuff like ZSNES and DOSBOX) before running jscal (during that particular boot), my joystick devices work fine.

---

### Post by jppinto on 2009-06-08
> **TheBuzzSaw said:**
> Hm. This doesn't make sense to me. Methinks you misunderstood my instructions. (Not that it matters since there is this nifty script to take care of the issue.)

If I just run my games (including stuff like ZSNES and DOSBOX) before running jscal (during that particular boot), my joystick devices work fine.

When I answered you, I thought you were trying to use the jscalibrator program and not the jcal. The jscalibrator gave me headaches!

In any case the script is a better way. :)

J

---

### Post by sepius on 2009-07-26
another thanks to jppinto.  This has helped me.  Just wondering though, is there a way to put in a null zone in the centre of the calibration?

---

### Post by jppinto on 2009-07-26
> **sepius said:**
> another thanks to jppinto.  This has helped me.  Just wondering though, is there a way to put in a null zone in the centre of the calibration?

I don't know what you mean by "null zone", but you might try to look into the man pages of jcal. Just write "man jscal" in a terminal.

---

### Post by sepius on 2009-07-26
Sorry about null zone.  Usually the centre of a joystick is a bit slack and when calibrated exactly, means there could be a slight pull left, right, up or down.  The "null zone" is a small zone around the centre that measures the centre but allows some very minor movement.  I hope this makes sense.

To put in practical terms, I have calibrated my joystick now three times, and if I do a ~$jscal -t /dev/input/js0 , it returns "jscal: axes not calibrated" because the centre is out by one or two points.  Thinking now, I suspect those who own digital joysticks do not have this problem.

Man page gives nothing more than --help.  Will do more surfing and see what I can find out.  Might have a closer look at the output as well.

---

### Post by jppinto on 2009-07-26
> **sepius said:**
> Sorry about null zone.  Usually the centre of a joystick is a bit slack and when calibrated exactly, means there could be a slight pull left, right, up or down.  The "null zone" is a small zone around the centre that measures the centre but allows some very minor movement.  I hope this makes sense.

To put in practical terms, I have calibrated my joystick now three times, and if I do a ~$jscal -t /dev/input/js0 , it returns "jscal: axes not calibrated" because the centre is out by one or two points.  Thinking now, I suspect those who own digital joysticks do not have this problem.

Man page gives nothing more than --help.  Will do more surfing and see what I can find out.  Might have a closer look at the output as well.


Ok, Post what you find in here. I'm curious on what you'll find out. I'm no PRO on this but I'd expect that you'd have to think "outside the box" and look into the program that reads the calibration file that jscal creates.

---

### Post by sepius on 2009-07-26
Right, was easy in the end, but discovered something else in the process.

If you calibrate and do a jstest, the main axis will not zero easily, this is why I need the null zone, or dead zone, another name I discovered.

When you calibrate with jscal, take note of the number displayed when the axis are at the centre.

Write the file to the desktop, and open with gedit.

The file will have al sorts of numbers, but you will see a number of 2 sets of similar numbers that will be the same as the numbers you saw while calibrating.

If you change these numbers by reducing the first and increasing the second, this will create a null zone.  I changed mine by a value of +-6.  When you run jstest, while your joystick is at rest, it will display zeros on the axis you null zoned.

I hope this makes sense.

The issue I discovered was that, when I run FlightGear, my calibration changes.  Not sure what is going on there, but that will be another story, I was happy to just find how to null zone :).

If people are after a better how to, just post back here and I will put something together with examples.

---

### Post by jppinto on 2009-07-26
> **sepius said:**
> Right, was easy in the end, but discovered something else in the process.

If you calibrate and do a jstest, the main axis will not zero easily, this is why I need the null zone, or dead zone, another name I discovered.

When you calibrate with jscal, take note of the number displayed when the axis are at the centre.

Write the file to the desktop, and open with gedit.

The file will have al sorts of numbers, but you will see a number of 2 sets of similar numbers that will be the same as the numbers you saw while calibrating.

If you change these numbers by reducing the first and increasing the second, this will create a null zone.  I changed mine by a value of +-6.  When you run jstest, while your joystick is at rest, it will display zeros on the axis you null zoned.

I hope this makes sense.

The issue I discovered was that, when I run FlightGear, my calibration changes.  Not sure what is going on there, but that will be another story, I was happy to just find how to null zone :).

If people are after a better how to, just post back here and I will put something together with examples.

Interesting... did you find any explanation of the output file of jscal? 
Good work!

---

### Post by sepius on 2009-07-26
Actually no.  I found the source code, but it has been 15 years since I have done any real C programming, and the code has very few remarks, possibly because the coder is Czech. It's sponsored by Suse according to the opening remarks.

There does not appear to be much except what is in the man and help, which just seems to be copied all over the net.

Funny thing, when I googled "jscal null zone" the first result sent me back to this thread :).

---

