---
title: "Grey Window in Matlab 2007 and ubuntu 8.10 AMD64"
date: 2008-11-30
forum: x86 64-bit Users
---

### Post by jlfqam on 2008-11-30
Hi again,
I've installed ubuntu 8.10 AMD 64bit.
However when I installed matlab 2007b at the startup I 
got a grey screen. Only the startup button appeared at the bottom left side of the screen. It was active and could select applications, etc but all of them opened as grey background empty windows. I have upgraded on line but nothing changed in relation to that problem.

Earlier,I managed to install and run matlab 2007 on ubuntu 7.10 which I later on upgraded on line to ubuntu 8.04. However when I upgraded this latter version on line I found the same problem with the already installed matlab.
I decided to re install a fresh ubuntu 8.10 AMD64 session as I mentioned above.
This matlab is the only third party application I have installed so far.
Thanks for your support.

JLF

---

### Post by jlfqam on 2008-12-12
Hi,
I found the solution in the mathworks page
[http://www.mathworks.com/support/solutions/data/1-30BSFV.html](http://www.mathworks.com/support/solutions/data/1-30BSFV.html)
followed the link
[http://www.mathworks.com/support/solutions/data/1-1812J.html?solution=1-1812J](http://www.mathworks.com/support/solutions/data/1-1812J.html?solution=1-1812J)
then
[http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f98533.html&http://www.mathworks.com/support/solutions/data/1-1812J.html?solution=1-1812J#f122001](http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_external/f98533.html&http://www.mathworks.com/support/solutions/data/1-1812J.html?solution=1-1812J#f122001)

Downloaded the self extracting package 
Linux x64 *  filesize: 17.58 MB 
from
[http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)
and followed the steps in
[http://www.java.com/en/download/help/5000010500.xml#enable](http://www.java.com/en/download/help/5000010500.xml#enable)
changed the attributes of the file and folder
installed the package into
/usr/java

sudo ./jre-6u11-linux-x64.bin
and set the matlab environment variable
sudo setenv MATLAB_JAVA /usr/java/jre1.6.0_11
Now I can see matlab as it should

Greetings

JLF

---

### Post by jlfqam on 2008-12-12
Hi
sorry
the setting of matlab's environment variable is

export MATLAB_JAVA=/usr/java/jre1.6_11

Greetings

JLF

---

