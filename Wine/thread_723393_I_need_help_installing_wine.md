---
title: "I need help installing wine"
date: 2008-03-13
forum: Wine
---

### Post by X3zh on 2008-03-13
Hello, 

I can not install wine. I already tried loads of times with the commands I have seen in other threads, but it just won't work.

when I try to install wine, my terminal gives me this text:

Some packages could not be installed. This can mean that you requested an impossible situation or, if you are using the instable version (I don't know if version is correct, since I am traslating this from Swedish.) that some necessary packages have not yet been created or moved out from "Incoming".


I appreciate help very much. Thank you.

---

### Post by Resonance378 on 2008-03-13
What version of Ubuntu?

Did you go here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) ??

---

### Post by X3zh on 2008-03-13
Ubuntu 7.10

---

### Post by X3zh on 2008-03-13
When I am going to install wine in the terminal it saus that libaudio2 is missing or something.. This is getting annoying, can anyone help me?

---

### Post by Tom--d on 2008-03-13
Go on 

System > Admin > Software sources

Enable all the things on the first tab sept for Source code and the Cd/DVD

Which you are there, just enable the updates. Its on the tabs.

This should enable you to install software (Dont know why its not default in Ubuntu).

Then install Wine through the Add/remove.

Reply what happens.

---

### Post by X3zh on 2008-03-13
I love you guys, the problem was fixed. Thanks for the help :)

---

### Post by bhocay on 2008-03-13
> **X3zh said:**
> When I am going to install wine in the terminal it saus that libaudio2 is missing or something.. This is getting annoying, can anyone help me?

try : **sudo apt-get -f install** after installer failed

---

