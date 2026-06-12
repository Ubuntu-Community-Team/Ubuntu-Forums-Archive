---
title: "Installing Ventrilo, using ventriloctrl"
date: 2008-09-30
forum: Wine
---

### Post by yange on 2008-09-30
After searching through the forums I found this guide: 

[http://ubuntuforums.org/showpost.php?p=2662867&postcount=83](http://ubuntuforums.org/showpost.php?p=2662867&postcount=83)

Simply I am an Ubuntu noob, but my skills with navigating through the OS are improving. Anyways, where the instructions on the post say to, MAKE, I do not understand how to do this... I have tried playing around with the terminal and searching online but haven't gotten anywhere. 

Thank you, Yange.

---

### Post by aoanla on 2008-09-30
All of the instructions in "code" blocks are literal instructions you need to type at the terminal. (In the case of the make, you need to be in the directory you extracted the ventriloctrl into, but it does say that.)

---

### Post by yange on 2008-09-30
I don't understand then, when it says "in the directory"... I extracted the file into my documents folder, is that the proper way? Or is their a step I missed? I simply open up my terminal, copy and pasted the path and typed "make" before that.

khagan@khagan-desktop:~$ make '/home/khagan/Documents/ventriloctrl-0.3' 
make: Nothing to be done for `/home/khagan/Documents/ventriloctrl-0.3'.

---

### Post by aoanla on 2008-09-30
No, because it doesn't say "run make on the directory" it says to use make /when you're in the directory/.

So:

cd /home/khagan/Documents/ventriloctrl-0.3
make

(cd changes to the directory specified, so you're in the directory then.)

---

### Post by yange on 2008-09-30
Ah I see, told ya I'm a total noob. Thank you much dude! peace

---

