---
title: "Vb express"
date: 2012-01-06
forum: Wine
---

### Post by coolguysraju on 2012-01-06
I am installing vb express 2010 through wine and during installation it shows unknown error dialoge box Can anyone solve this problem,also during installation it install in C:/visual studio 2010 where my another operating system window 7 installed my question is can i use the same install file in window 7 without extra installing in window 7,can anybody help me from this.

---

### Post by cap10Ibraim on 2012-01-06
are you dual booting ubuntu and windows 7 ? 
 if yes 
  then this is C is not the same partition where windows is installed , I think wine use this virtual drive C 
plus I don't think you will get VB2010 express to work with wine 
If you don't want to leave linux 
 consider installing a virtual machine

---

### Post by Azdour on 2012-01-06
Hi,

I would also take a note of:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19993](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19993)

It does not seem to work with wine.

---

### Post by QIII on 2012-01-06
Aside frome the fact that it is garbage in Wine, how would you test your product?  A VB.NET project would not run in Linux.  I don't think Mono would even be helpful since it wraps only the C# libraries.  Besides that, Mono has been dumped and spun off to a third party and is somewhat in limbo right now.

You will probably need to virtualize Windows or dual boot.

---

### Post by KdotJ on 2012-01-06
> **QIII said:**
> Aside frome the fact that it is garbage in Wine, how would you test your product?

Very good point.. if you're developing for Windows, it's is best to do it and test it on Windows. 

I second the idea of a VM.

---

### Post by oldos2er on 2012-01-06
Thread moved to Wine.

---

### Post by anewguy on 2012-01-06
Yep - VB will be a no-go, and indeed wine virtualizes the drive as C.  If you are trying to bring VB to Linux, you could try Gambas instead, though I personally am not familiar with using it.  If you are looking to do cross-platform development then you will need to use another tool - Java, perhaps C or C++ with GTK (requires installing GTK for Windows on the Windows machine, but it's free), python (again, I'm not familiar with it, but I believe it also requires installing something in Windows), etc..

If you want to develop in VB - perhaps for school, perhaps for fun, perhaps because it's the easiest way for you to go right now (hey, I come from the whatever works for you camp ;) ), you should probably either dual-boot or at least run one of the OS's in a virtual machine.

Dave ;)

---

### Post by directhex on 2012-01-08
> **QIII said:**
> A VB.NET project would not run in Linux.  I don't think Mono would even be helpful since it wraps only the C# libraries.

[https://launchpad.net/ubuntu/+source/mono-basic/+publishinghistory](https://launchpad.net/ubuntu/+source/mono-basic/+publishinghistory)

---

