---
title: "ndiswrapper for AMD64?"
date: 2005-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by pailhead on 2005-08-04
Is there a copy of ndiswrapper for the AMD64 platform?  I've checked the repo's and it's not in there.. 

Anyone?

---

### Post by Doctoxic on 2005-08-05
[QUOTE=pailhead]Is there a copy of ndiswrapper for the AMD64 platform?  I've checked the repo's and it's not in there.. 

Anyone?[/QUOTE]
 I have just ordered some A64 kit and would also like to know about this
.
Many thanks

Doc

---

### Post by emrys on 2005-08-06
[QUOTE=pailhead]Is there a copy of ndiswrapper for the AMD64 platform?  I've checked the repo's and it's not in there.. 

Anyone?[/QUOTE]

I used ndiswrapper 1.2 in breezy 64-bit just compiling it from source: [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

Is not that hard. You just have to install some packages to meet dependencies and that's all.

Wifi with Broadcom works wonderfull now...

---

### Post by Cyberman on 2005-08-08
[QUOTE=emrys]I used ndiswrapper 1.2 in breezy 64-bit just compiling it from source: [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

Is not that hard. You just have to install some packages to meet dependencies and that's all.

Wifi with Broadcom works wonderfull now...[/QUOTE]
 How would one compile this and set it up?

ahh, nevermind..
I found this [link](http://ubuntuforums.org/showthread.php?t=31926&page=1&pp=10&highlight=ndiswrapper)

---

### Post by emrys on 2005-08-08
[QUOTE=Cyberman]How would one compile this and set it up?

ahh, nevermind..
I found this [link](http://ubuntuforums.org/showthread.php?t=31926&page=1&pp=10&highlight=ndiswrapper)[/QUOTE]

./compile
./make
./make install

Some dependencies problems, maybe some permisions problems but after that, it should work

---

### Post by locutus42 on 2005-08-11
[QUOTE=emrys]I used ndiswrapper 1.2 in breezy 64-bit just compiling it from source: [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

Is not that hard. You just have to install some packages to meet dependencies and that's all.

Wifi with Broadcom works wonderfull now...[/QUOTE]

Which Broadcom driver are you loading? I've only found this package, 64-bit_Broadcom_54g_Drivers.zip, and the netbc564.inf/bcmwl564.sys won't connect to my 802.11b WAP and has locked up the system.

Thanks. BTW, I'm running a Compaq R4000 with a Broadcom BCM4306 802.11b/g chip.

---

### Post by emrys on 2005-08-11
[QUOTE=locutus42]Which Broadcom driver are you loading? I've only found this package, 64-bit_Broadcom_54g_Drivers.zip, and the netbc564.inf/bcmwl564.sys won't connect to my 802.11b WAP and has locked up the system.

Thanks. BTW, I'm running a Compaq R4000 with a Broadcom BCM4306 802.11b/g chip.[/QUOTE]

This is what I am using, the netbc564.inf (having the .sys in the same directory (I don't know if it's necessari though)).

I have an ACER 1502.

Works like a charm.

---

