---
title: "X64 Install question / problem"
date: 2008-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Biciclettapc on 2008-02-22
Ok in addtion to the other VC problem [http://ubuntuforums.org/showthread.php?t=703795](http://ubuntuforums.org/showthread.php?t=703795)

 I am having with a old system for my son I have built up a new box for myself. 

Specs are AMD 64 x2 4000+, Gigabyte Nvida 7025 Mobo and a Gforce 8400 pcie 16 VC.

The Hdd had a copy of Ubu already installed (had bad mobo first go around) and the machine booted right up great.  The copy of Ubu was x386 on the hdd as I had issues at intial build with the 64 bit version.  Since I had a mobo issue first go around I assumed it was that.  

Well, now I want to load the 64 bit version of Ubu.  Here is whats happening.... I start the system up with the cd in and it comes to the Ubu live screen.  VC setting is for PCIe card on DVI.  It posts to bios, then comes to the install screen for Ubu.  I select install and the video goes blank and never comes back.  So, I tried going to the onboard graphics on VGA and restart the new install.  Same issue....

If I alt+Ctl+F1 I do not get a command prompt.

Bad Disk?

---

### Post by Kilz on 2008-02-22
Its possible, did you check the md5sum of the iso image? But its also possible that there are video driver issues. You might want to use the Alternate CD to install the 64bit version.

---

### Post by Yellow Pasque on 2008-02-23
> **Kilz said:**
> IYou might want to use the Alternate CD to install the 64bit version.

Indeed. We have lots of users with recent nvidia cards/chipsets that need to use the alternate installl CD.

---

### Post by CapnJ on 2008-02-23
I'm having the same problem with the alternate install cd.  Perhaps move to an older version?

---

### Post by Biciclettapc on 2008-02-23
Thanks, did that and it worked.  Actually just now bringing things up and checked mail on the machine.  Had to enable restricted Nvida driver before I could enable effects and such.

New Linux, Ubu user so any cool things or links would be great!

Thanks for the help!

---

### Post by Biciclettapc on 2008-02-23
Oh, I do have a question.....  I use opera in addtion to firefox, I think the graphics are a bit cleaner with opera and surf using both.  Opera is un-able to be installed from add/remove?

Do I need to d/l opera direct?  Is this a 64 bit issue?

---

### Post by Kilz on 2008-02-23
> **Biciclettapc said:**
> Oh, I do have a question.....  I use opera in addtion to firefox, I think the graphics are a bit cleaner with opera and surf using both.  Opera is un-able to be installed from add/remove?

Do I need to d/l opera direct?  Is this a 64 bit issue?

[You may want to look at this page]("http://www.monkeyblog.org/ubuntu/installing/"). It gives information on using Synaptic. Add/remove is very limited.

---

