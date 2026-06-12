---
title: "TeamSpeak won't launch from menu."
date: 2009-05-27
forum: x86 64-bit Users
---

### Post by rdmike on 2009-05-27
Hi all,

I have teamspeak installed and it works well if I launch it from the terminal but will not launch at all from the menu, very strange. I installed it using the kpackageget (I think it's called lol) and no clue what the issue is. Any ideas on how to fix the issue? Thanks!

---

### Post by rdmike on 2009-05-28
Bump

---

### Post by pixel :-) on 2009-05-28
you can edit the menu, with right click.

play with the options, one should work

if you can't make it work, post the details of what commands you have tried in the menu.

Try explicit path

try runing from the folder of the execuatable (boinc have to be run this way)
cd "/the path" ; executable_name

try putting various paths in a script

---

### Post by rdmike on 2009-05-28
Hey,

That worked. The original command was padsp teamspeak and I deleted the padsp, poof everything good. I'm not sure why but it works lol. Thanks!

---

### Post by pixel :-) on 2009-05-28
You may have sound issues

sound is OK? padsp is some kind of wraper for diferent sound systems

If quality of sound is low, or if the application monopolizes the sound(no system sounds), that was it.

Its not very important, but if you get bothered, run the command
(padsp -d teamspeak) in a terminal and see what it complains about (-d debug out put)

---

### Post by rdmike on 2009-05-29
Will do thanks Pixel!

---

