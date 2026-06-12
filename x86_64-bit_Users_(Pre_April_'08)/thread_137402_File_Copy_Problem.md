---
title: "File Copy Problem"
date: 2006-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by eheron on 2006-02-27
I have just installed Breezy on my AMD and i want to copy some files from my Windows partition.  It is mounted correctly and I can access  the drive but when i try to copy anything from it nothing happens.  What can I do to fix this problem?

---

### Post by RAOF on 2006-02-28
What (exactly) are you doing?  Is it giving any error messages?  Have you tried copying from a terminal with "cp /path/to/source/* /path/to/destination"?  What errors, if any, has that given?

---

### Post by eheron on 2006-02-28
i am trying to copy a video from my windows partition on my second hard drive.  I have tried both drag and drop and right click copy paste.  i have tried to copy it from the term but it tells me that i do not have permission for the drive.

---

### Post by RAOF on 2006-03-01
I don't suppose you could try again and copy/paste **exactly** what you typed in the terminal and what the result was?

If you select text from the terminal window, middle-click will copy it into the current program.

---

### Post by eheron on 2006-03-01
ekb5010@ubuntu:~$ cp /media/Downloads /home/ekb5010/Downloads/
cp: cannot stat `/media/Downloads': Permission denied
ekb5010@ubuntu:~$



That is what comes up in the term when i try to copy the folder downloads from the drive.

---

### Post by Sommer on 2006-03-01
you have to select the hardisk (hda'X'), where 'X' is a number

Type;

sudo cp /media/hda'X'/Downloads/* /home/ekb5010/Downloads/ -aRf

nb: Remeber sudo, and the 'X' is a number. The '-aRf' make life easyer.!!!!

---

### Post by Sommer on 2006-03-01
oh, and type & behind the -aRf

so i goes like

sudo cp /media/hda'X'/Downloads/* /home/ekb5010/Downloads/ -aRf &

then you can kill it by using the ps aux - command.

---

### Post by eheron on 2006-03-01
I tried what you suggested and this was the result:

ekb5010@ubuntu:~$ sudo cp /media/hdd/Downloads/ /home/ekb5010/Downloads/ -aRf &
[1] 10229
cp: cannot stat `/media/hdd/Downloads/': No such file or directory
ekb5010@ubuntu:~$

---

### Post by ttread on 2006-03-01
In the console, navigate to the folder:

cd /media/Downloads

Then list some files and look at the permissions:

ls -l *

You should see something like rwxr--r-- for each file.  If all the r's do not appear then there's a permissions problem, fixable with chmod, i.e.:

sudo chmod 744 *

Hope this helps.
-Ted

---

