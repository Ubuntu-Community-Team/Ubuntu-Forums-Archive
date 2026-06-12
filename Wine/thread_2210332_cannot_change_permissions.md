---
title: "cannot change permissions"
date: 2014-03-10
forum: Wine
---

### Post by christon74 on 2014-03-10
Hello every ubunter :D

This morning I tried up to six times installing Word_ using Wine installer. And every time the install failed. I cannot remember exactly what the error message was but I suspect it has much to do with the permissions. I tried to change 'read only' to 'read and write' but Ubuntu won't let me. It clearly says I cannot change permissions. Huh? 
Ubuntu versions I have installed: 
One PC with dual boot _ Vista/ Ubuntu 12.04 LTS
second PC with dual boot: XP/ Zorin lite

Thanks in advance for any tip.

Chris.

---

### Post by rackit on 2014-03-10
Try going from the cli and using sudo i.e. sudo chmod 777 *filename*

---

### Post by christon74 on 2014-03-10
Hello Jerry, thanks for the answer but I have a question: what is the' cli'? :confused:

---

### Post by rackit on 2014-03-10
cli - Command Line interface - hit ctrl-alt-t to open a terminal, cd to the directory your file is in, sudo chmod 777 *filename*

If that doesn't help, tell me the file name and the directory it is in - I'll try to help from there.

---

### Post by christon74 on 2014-03-11
Hello Jerry and thank you for time and trouble. I am not sure what the file is_ I suppose it is the install. I have just tried the line of command you are suggesting and here is the result:
sudo chmod 777 install.exe
chmod: cannot access 'install.exe': No such file or directory

---

### Post by deadflowr on 2014-03-11
It helps to know which version of word and which version of wine.

Some versions work better than others.
(That statement can go both ways)

I can't see the need to set permissions beyond the executable bit.(maybe)

---

### Post by christon74 on 2014-03-11
christophe@christophe-TPS01:~$ sudo chmod 777 /media/WKSSTE02CD1/MSWord
[sudo] password for christophe: 
Sorry, try again.
[sudo] password for christophe: 
chmod: changing permissions of `/media/WKSSTE02CD1/MSWord': Read-only file system
christophe@christophe-TPS01:~$

---

### Post by christon74 on 2014-03-11
christophe@christophe-TPS01:~$ chmod x /media/WKSSTE02CD1/MSWord
chmod: invalid mode: `x'
Try `chmod --help' for more information.
christophe@christophe-TPS01:~$ chmod 777 /media/WKSSTE02CD1/MSWord
chmod: changing permissions of `/media/WKSSTE02CD1/MSWord': Read-only file system
christophe@christophe-TPS01:~$ chmod rwxr /media/WKSSTE02CD1/MSWord
chmod: invalid mode: `rwxr'
Try `chmod --help' for more information.
christophe@christophe-TPS01:~$

---

### Post by christon74 on 2014-03-11
Hello again Jerry and every Ubunter :)
I think it best to give it all up. Installing Works Suite 2002 or Word proves beyond my capabilities. I have just tried copying the files from the CD rom to 'downloads'. Then I have changed the permission and yes I can choose 'read and write' and make executalbe. I have entered the key, accpeted the terms and conditions blah blah blah but the install fails all the same and it stops _ after asking me to send an error report_
My conclusion: Works Suite 2002 is absolutely incompatible with Ubuntu 12.04

---

### Post by rackit on 2014-03-12
Have you tried usinf LibreOffice? Is there a reason you need to you Works?

---

### Post by christon74 on 2014-03-12
Yes Rackit:D I already have Libreoffice installed. Why do I want to install works? 
Well because there are some features Libreoffice does not offer... and just for the hell of installing a windows app :lolflag:

---

