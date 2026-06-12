---
title: "Is Swap need for fglrx ?"
date: 2009-05-18
forum: x86 64-bit Users
---

### Post by sim-value on 2009-05-18
Hi !

I just got the Karmic testing release and oh wonder ... the 64 Bit ATI drivers of course do not work ...

Well that wouldnt be the problem because its Alpha but the REAL Problem is that they dont work on **any** 64 Bit Linux/OS (Vista x64 needed some hours...) No mather if that is Hardy,Jaunty,Intrepid,Gentoo or any other ...

I do not have a Swap partition though (and never had one) so the question : does FGLRX x64 need Swap ? (x86 doesnt)

/me

---

### Post by Yellow Pasque on 2009-05-18
You can always use a swap file: [https://help.ubuntu.com/community/SwapFaq#Example%20of%20making%20a%20swap%20file](https://help.ubuntu.com/community/SwapFaq#Example%20of%20making%20a%20swap%20file)

---

### Post by sanderj on 2009-05-19
> **sim-value said:**
> 
I do not have a Swap partition though (and never had one) so the question : does FGLRX x64 need Swap ? (x86 doesnt)

/me

No.

---

### Post by shabazzk on 2009-05-19
> **sim-value said:**
> Hi !

I just got the Karmic testing release and oh wonder ... the 64 Bit ATI drivers of course do not work ...

Well that wouldnt be the problem because its Alpha but the REAL Problem is that they dont work on **any** 64 Bit Linux/OS (Vista x64 needed some hours...) No mather if that is Hardy,Jaunty,Intrepid,Gentoo or any other ...

I do not have a Swap partition though (and never had one) so the question : does FGLRX x64 need Swap ? (x86 doesnt)

/me

Are you saying that the ATi 64 bit drivers do NOT work?

---

### Post by skymera on 2009-05-20
What is your ATi graphics card?

---

### Post by Sef on 2009-05-22
If you want to use hibernation or suspend, then swap is needed.

---

### Post by Melcar on 2009-05-23
Karmic uses the 2.6.30 kernel right?  Fglrx does not yet support it (it doesn't even support 2.6.29 yet).

---

### Post by sim-value on 2009-05-23
> **shabazzk said:**
> Are you saying that the ATi 64 bit drivers do NOT work?

Yes thats what im saying

Its an HD3650

And as said they dont work on 64 bit on all linux versions i tried (8.04-9.10 and gentoo)

---

### Post by shabazzk on 2009-05-25
1. What version of Ubuntu are you running?

2. What kernel version do you have?

Note to get the answers to 1 and 2, if your using GNOME, check the system tab under system monitor, which can be found under System > Administration menu on the top taskbar; these instructions assume Ubuntu 8.10+.

3. How did you install the ATi drivers?[LIST]
[*]3rd party utility.
[*]Using Ubuntu hardware driver activation applet.
[*]Downloaded from AMD site and ran the installer.
[*]Downloaded from AMD site, build DEB packages and manually installed.
[/LIST]

4. When you say they do not work, do you mean they will not even install, or they install but performance is bad?

5. What version of the ATi drivers are you trying to install?

Excuse all the questions, but without the proper info, we would waste time having you do things that you may have already tried. Answer these questions and I'm sure we can all help you, better and faster.

Background:
 I have gotten ATi drivers to work, since version 9.1 with an Readeon 2400HD Pro I brought for $35 off Craigslist. Having them, correctly install and configured, greatly improved performance with Compiz and XBMC. I have also installed them on an ATi 3300HD. I must admit that trying to install via Ubuntu did NOT work the first time, so I had to install them manually by downloading from ATi site and build DEB packages. Using tutorial from the internet I am fond of. But I will try to install the Ubuntu way so that I can help others use that method. Although, Ubuntu will probably NOT have the latest version in their repo. So maybe I will find a PPA that works with UBuntu and keeps them up-to-date.

Note: they also work for me on Window 7 RC1.

---

### Post by Duskao on 2009-05-26
I'm using Ubuntu 9.04 64 bit. I have a Radeon 4850 and I am using catalyst 9.5 drivers and they actually work quite well. I first used the fglrx from "Hardware Drivers". However when 9.5 came out I downloaded it from amd and installed it using sudo sh and the file. Worked great for me.

---

