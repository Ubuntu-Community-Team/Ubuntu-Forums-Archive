---
title: "update without internet connection"
date: 2006-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by voolger on 2006-01-27
hello guys,

i have no internet connection for my ibook G3 900MHZ because the setup for the internal software modem is difficult, as in other threads alreaday mentioned. what i know is how to download files at another computer transfer these files to ubuntu via CD. But there starts my problem. How do I upgrade or bring ubuntu 5.10 ppc uptodate with those debian (*.deb) packages that I've just downloaded from [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/). Rather mor obscure - Which files do i need to download from the folders multiverse, universe or main? I understand that i will need to know how to run dpkg for those *deb packages. Am I wrong? Its all a bit new for me.

thanks for your help.

ciao voolger

---

### Post by adwait on 2006-01-27
If you have download some packages (.deb), then copy then on the target computer and use
```
sudo dpkg -i <file.deb>
```

The password is your normal user password.

---

### Post by voolger on 2006-01-27
thanks for your answer adwait. 

so it is similar to the rpm way of installing new packages? 
it seems to be very similar, because of the option -i for install.

Which files do i need to download from the folders multiverse, universe or main?

ciao voolger

---

### Post by adwait on 2006-01-27
Whatever you need..........<anything.deb> is installable. Y

Yes it is similar to the RPM way, except that RPM is used in Red Hat (hence Redhat Package Management) while this is the Debian way of doing things.

---

