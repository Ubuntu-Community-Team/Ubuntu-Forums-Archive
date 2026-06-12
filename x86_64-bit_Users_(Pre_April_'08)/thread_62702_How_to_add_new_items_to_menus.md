---
title: "How to add new items to menus"
date: 2005-09-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrisv on 2005-09-05
Hello everyone,

I am pretty new to Ubuntu and linux, so please bear with me. I installed a couple of games using synaptic and the instalation went fine and the games run fine, however I have to type in the name of the game to run it, and I want to install a shortcut in my menu folder. Shortcuts did not appear automaticaly (as they do in Windows). 

Well I checked in the help section on how to add an item to a menu. There was a sort of complicated procedure that required you to create your own file. Well I created a file allright, but then hit a problem. Ubuntu help tells me to start a file manager window and type in "applications-all-users:///" in the location bar. I do that but my file manager says it cant find the location. 

So as you can see I am stuck. Please help. 

Also plz let me know if there is an easier way to get the applications I install with synaptec into the menu bars.

---

### Post by KingBahamut on 2005-09-05
Making sure you have the extra repositories , backports more specifically. 
[http://ubuntuguide.org](http://ubuntuguide.org)
do a 

apt-get install smeg 

use smeg to create the entries you dont see. 

Also of note, it helps to refresh gnome everytime you install something 

do a 

killall gnome-panel

---

### Post by chrisv on 2005-09-05
[QUOTE=KingBahamut]Making sure you have the extra repositories , backports more specifically. 
[http://ubuntuguide.org](http://ubuntuguide.org)
do a 

apt-get install smeg 

use smeg to create the entries you dont see. 

Also of note, it helps to refresh gnome everytime you install something 

do a 

killall gnome-panel[/QUOTE]
 I checked ubuntuguide.org and it says that i should not use apt-get but I should use "wget" and "sudo dpkg" because I have an amd64 install. Is that correct or is that old info. 

Also what does this mean:
"Making sure you have the extra repositories , backports more specifically."

Which depositories should I have? 

Thanks for answering so quickly.

---

### Post by KingBahamut on 2005-09-05
backports specifically Chris.

---

### Post by chrisv on 2005-09-05
[QUOTE=KingBahamut]backports specifically Chris.[/QUOTE]
 Well thanks, I installed smeg and was able to add the menu easily.

---

### Post by Lu523 on 2005-09-16
I found this useful also. Thanks for the good info.

---

