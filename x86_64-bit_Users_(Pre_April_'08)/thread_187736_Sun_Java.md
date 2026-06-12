---
title: "Sun Java?"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-06-03
I need to run a program that requires Sun Java Runtime Environment 1.4.2. It gives error messages if I try to run it on whatever default Java is installed on my Ubuntu-64 Breezy computer. The error message was incomprehensible to me, but I asked a local Linux guru, who said it was "roughly translated:  The main thread of your program took exception to not finding a defined class named 'sun.misc.Launcher.'"

The program is Treeform, web site:
[http://www.ece.ubc.ca/~donaldd/help/help.htm]("http://www.ece.ubc.ca/~donaldd/help/help.htm")

It has a link to Sun's Java download page:
[https://sdlc1d.sun.com/ECom/EComActionServlet;jsessionid=6E86D146B6D960CEC89965F1660CBE7C]("https://sdlc1d.sun.com/ECom/EComActionServlet;jsessionid=6E86D146B6D960CEC89965F1660CBE7C")

from where I downloaded the JRE self-extracting file j2re-1_4_2_12-linux-i586.bin. I downloaded this one as there was not one specifically listed for 64-bit Linux. So before trying to install it, my questions are:

1) Can I install and run Sun Java as well as whatever is already installed?

2) Do I have the right Sun Java file? Will it install OK on my 64-bit Ubuntu?

3) I can't find specific instructions on Sun's site for installing it. I haven't done anything with the file because I don't know if double-clicking on it just extracts it (probably), or also installs it, in case I should/can not install it on Ubuntu-64. Assuming I can install it, how do I do that?

---

### Post by John Jason Jordan on 2006-06-03
Never mind. I found it in Synaptic.

However, I have one additional problem. The program I am running with it has an option to export its files as JPG or PNG images in either 300 or 600 dpi. I can export as JPG at 300 dpi, but the other options say I need to allocate more RAM to Java. The command line I use to launch the app is

java -jar TreeForm.jar 
(TreeForm is the name of the program.)

Is there an option I can stick somewhere in there to allocate more RAM to Java?

---

