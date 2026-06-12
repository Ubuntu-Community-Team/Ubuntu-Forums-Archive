---
title: "Trouble installing Visual Basic 6.0 (vb6) in Xubuntu 12.04"
date: 2013-02-21
forum: Wine
---

### Post by Controll on 2013-02-21
I am following the simple little guide on WineHQ for trying to install.

[http://appdb.winehq.org/appview.php?versionId=130](http://appdb.winehq.org/appview.php?versionId=130)

I get about as far as installing Dcom98 until I run into all sorts of problems.

[http://wine-wiki.org/index.php/Dcom98](http://wine-wiki.org/index.php/Dcom98)

Using wine-wiki I've tried to get Dcom98 working, but Dcom98 has been abandoned I think?

I kinda just need some help, maybe a link to a good tutorial.

If I left any info out just let me know.

---

### Post by Mark Phelps on 2013-02-21
You need to read the test results for using Ubuntu 10.04 -- they say NOT to install DCOM98.

Since this hasn't been updated since 10.04, my guess is that it won't work with newer Ubuntu versions.

---

### Post by Controll on 2013-02-21
> **Mark Phelps said:**
> You need to read the test results for using Ubuntu 10.04 -- they say NOT to install DCOM98.

Since this hasn't been updated since 10.04, my guess is that it won't work with newer Ubuntu versions.

Is there any advice you could give me for installing visual basic 6 in xubuntu then?

---

### Post by Mark Phelps on 2013-02-21
Wish I had some, but I don't.

I messed around with Wine a LOT a few years ago -- largely as an experiment to see if I could completely let go of Windows, including such things as IE and MS Office.

What I found (after a LOT of experimentation with Wine, including POL and WineTricks) was the following:
1) Some stuff that is used routinely in MS Windows just plain does not work -- Like current IE versions and some Office components
2) Some apps just don't work -- like stuff I used every day
3) Even if, by some miracle, an app DOES work, an update will come along that will "break" it -- and you're back to trial-and-error again

Understand, it took CodeWeavers, and lots of trial-and-error testing, and major customizing work -- to get SOME of Office 2010 components working "OK" in Wine -- and by then, Office 2013 was already out.

Conclusion: While Wine, and its companions, can provide hours of entertainment and hacking enjoyment, if you need to use Windows apps daily, and interchange Office documents with other folks using CURRENT MS Office versions, there is really no substitute for doing this in Windows -- which is why many of us STILL dual-boot with Windows.

---

### Post by Controll on 2013-02-21
> **Mark Phelps said:**
> Wish I had some, but I don't.

I messed around with Wine a LOT a few years ago -- largely as an experiment to see if I could completely let go of Windows, including such things as IE and MS Office.

What I found (after a LOT of experimentation with Wine, including POL and WineTricks) was the following:
1) Some stuff that is used routinely in MS Windows just plain does not work -- Like current IE versions and some Office components
2) Some apps just don't work -- like stuff I used every day
3) Even if, by some miracle, an app DOES work, an update will come along that will "break" it -- and you're back to trial-and-error again

Understand, it took CodeWeavers, and lots of trial-and-error testing, and major customizing work -- to get SOME of Office 2010 components working "OK" in Wine -- and by then, Office 2013 was already out.

Conclusion: While Wine, and its companions, can provide hours of entertainment and hacking enjoyment, if you need to use Windows apps daily, and interchange Office documents with other folks using CURRENT MS Office versions, there is really no substitute for doing this in Windows -- which is why many of us STILL dual-boot with Windows.

Yeah if something like this becomes too much of a hassle I just have to go with Windows, gotta get work done some how.

Thanks for your responses.

---

