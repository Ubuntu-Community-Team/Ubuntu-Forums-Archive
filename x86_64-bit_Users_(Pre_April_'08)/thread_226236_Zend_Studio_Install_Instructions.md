---
title: "Zend Studio Install Instructions"
date: 2006-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by bbzbryce on 2006-07-31
I'm posting this because it took me awhile to figure out how to install and run Zend Studio on amd64 version of linux.  This is based off of this tutorial: [Zend Studio 64bitness]("http://www.tenshu.net/archives/2005/06/01/zend-studio-64bitness")

This method worked for me with Zend Studio 5.0.0.

Open a terminal and browse to the location of your ZendStudio-X_X_X.bin file.
Type in: cat ZendStudio-X_X_X.bin | sed -e 's/=2.2.5/=a.a.a/g' >ZendStudio-X_X_X.bin.1

Install by typing sudo ./ZendStudio-X_X_X.bin.1
where X_X_X corresponds to your file.

Once installed open /usr/local/Zend/ZendStudioClient-X.X.X/bin/ZDE

Perform a search for `uname` = "Linux".  IN my 5_0_0 zend its line 1479 and it says:
if [ `uname` = "Linux" -a -n "`which strings 2>/dev/null`" ]; then

Comment that line out with a # and paste this in below it:
if [ `uname` = "Linux" -a `uname -m` != "x86_64" ]; then

I can't verify that this wont cause any problem as it doesn't incorporate everything from the commented out line, but I've had no problems with it like this.

Run by executing this file now.

---

### Post by jimmygoon on 2006-07-31
Not to try to tell you NOT to use Zend, but I used to be addicted to it until I learned of jedit... you may take a look at it and see if it will suffice for your needs....

---

### Post by bbzbryce on 2006-07-31
I've used jedit for java before, however I find for php developing Zend is quite amazing. I have tried phpEclipse however it isn't all that great.  I love Eclipse for java development though.

Does jedit have good php support?

---

