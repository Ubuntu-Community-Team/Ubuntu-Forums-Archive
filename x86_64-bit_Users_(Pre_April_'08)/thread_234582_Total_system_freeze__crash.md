---
title: "Total system freeze / crash"
date: 2006-08-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by stookie on 2006-08-11
Hi all, Im getting total system freezes or crashes running Ubuntu 6.06 64bit. I get the same symptoms running Kubuntu 6.06 64bit live DVD. (It happens with Kubuntu live a lot more than Ubuntu installed though).

At different times, everything will stop, and the screen will show pure white or occasionally white with oh so slimming black vertical stripes. Sometimes its just as xdm (gdm?) starts, sometimes its hours later. One sure way to get the freeze is to play around in Inkscape, usually it happens within 2 minutes.

Nothing responds at all. Its the only computer in the house, so I cant check if something deep inside is alive, but not even caps lock or num lock works on the keyboard, so it doesnt look good...

Ive tried running the VESA xorg driver rather than the ATI driver, no difference.

Ive tried the K8 and generic x86-64 kernels, both do it.

As a dual boot system, Windows 2000 runs without a problem.

Details:
CPU: AMD Athlon 64 3500+ (Venice F)
MB: ECS RS482-M
Mem: 512 Mb (2×256 Mb)
Graphics: X200 on-board (ATI)
Disks: 1 ATA hard disk, 1 DVD R, 1 DVD RW

I would really appreciate at least some pointers in where to look (if not a fix!). I use other Unix systems quite a lot, but this is my first time in Linux for a few years, and my first time in Ubuntu.

Thanks guys...

---

### Post by stookie on 2006-08-21
Right, after spending more time in Sys-V style init scripts than is healthy for a sane person, it seems its the PowerNow stuff thats causing the crash.

Im currently running with the runlevel as for the default installation, but with S10powernowd.early and S20powernowd removed, and the crashes are gone.

When I can stand to think about this issue again, Ill try and find the correct way to notify the maintainer, or raise it as a bug.

---

### Post by CaveMole on 2006-09-13
My case may be similar.
x86_64 Dapper Drake, with fglrx Xorg driver.

In my case, all is well, until I try to restart, logout, shutdown.
It seems that something in the Xserver shutdown and/or gdm is freezing the system.

I had it running for a while.   Then it started doing this.

This is the 3rd install I've done, and fell into this trap again.

info at:

  [http://nmosug.org/admin-wiki/index.php/3rd_Dapper_Drake_Install_Log#gdm](http://nmosug.org/admin-wiki/index.php/3rd_Dapper_Drake_Install_Log#gdm)
  [http://nmosug.org/admin-wiki/index.php/Ubuntu](http://nmosug.org/admin-wiki/index.php/Ubuntu)

Any ideas?

---

### Post by CadetD on 2006-09-28
Ahaa! So I not the only one. Whew. 

I keep getting unexplained crashes. The system locks up. 
No rhyme or reason. 

Dapper 6.06 
AMD64 Opteron dual-core x 2. 
4GB RAM

None of the logs show any reason for the crash.

---

### Post by FyreBrand on 2006-09-29
I don't think this is just happening on 64 bit.  I have a P4 3Ghz EM64T that I'm running a 32bit 686 SMP kernel on.  I am getting constant lockups when I logout and try and login to another user.  The screen goes whitish and sometimes back to brown. The keyboard is locked up and I can't restart xserver or exit to the command prompt.  It just started happening a couple days ago.

---

### Post by kleeman on 2006-09-29
Sounds like a  fglrx (ati proprietary 3d driver) issue to me...

---

### Post by CadetD on 2006-09-29
> **kleeman said:**
> Sounds like a  fglrx (ati proprietary 3d driver) issue to me...

OK, I'll bite. I am running ATI All-in-wonder 9600. 
Anyone else locking up also using ATI with proprietary drivers?

---

### Post by mushr00m on 2006-10-16
same system, similar issues.

I had been getting hard locks with my upgrade to dapper in the way back with the proprietary drivers. A Kernel upgrade fixed the problems in a way I've never really understood.

Anyways. Started to get hard locks again in CLI rescue mode, GDM(with vesa or ati drivers), and via VNC.

I can't figure it out but it is probably ATI.... reminds me why I'm an nvidia man.  To bad I didn't have it in the budget to spring for the 64bit board with onboard nvidia instead of ati.

System:
amd sempron 3800
ati x200
1Gb ram.

Not that posting the system specs are gonna help.... except for the people who are having the same prob will find this thread by searching.

---

### Post by sinpalabras on 2006-10-20
hi my system feeze to but i can swich to terminal an reboot from there.Anyway , i m on ubuntu 6.06 amd64 install nvidia driver.

---

### Post by envis on 2006-10-25
im on a amd 64 unbuntu 6.06 and my motherboard is all NVIDIA and everytime i try to do either ctrl-alt-backspace, ctrl-alt-F3 (or Fsomething), or log out it freezes.. its been doing that for what? a week at least its very annoying id like to be able to fix that without having to reinstall everythin... :(

---

### Post by kleeman on 2006-10-25
I was having similar problems with freezes on a 64bit system with an nvidia 7950 so I installed the new beta drivers from nvidia (instructions for this are on the forum somewhere). No freezes anymore.

---

### Post by Aurora on 2006-11-08
> **stookie said:**
> Right, after spending more time in Sys-V style init scripts than is healthy for a sane person, it seems its the PowerNow stuff thats causing the crash.

Im currently running with the runlevel as for the default installation, but with S10powernowd.early and S20powernowd removed, and the crashes are gone.


Hello,

I have NO IDEA what those files are or what they do, but I backed them up and removed them, and it no longer crashes.  Thanks for risking insanity in the bowels of the init scripts.

Those files are found in /etc/init.d/ and /etc/rs2.d/ through /etc/rs5.d/  .  I entered sudo thunar (use the name of your favorite graphical text editor) and cut and pasted them into backup folders I created.

I know it would be faster if I would just learn the commands and do it from the command line...but I'm a former classic Mac user ;)

Paul in Seattle

---

### Post by sinpalabras on 2006-11-17
i upgrade to edgy eft and no more x freeze. Install the nvidia driver 1.0-8776 from the edgy repos.by.

---

### Post by CadetD on 2006-11-18
Thanks. Upgrading is tricky since I have a custom kernel. 
Also, I am running an ATI card. 

On the other hand, STOOKIE posted a not about the AMD PowerNow. 
So, just for kicks, I disabled the feature in the BIOS.

Haven't had a crash in 3 days now. Let's see if that lasts.

If the problem turns out to be the PowerNow feature, who do we talk to about it? AMD or Ubuntu developers? :-k

---

### Post by Doz3r on 2007-03-21
I've tried deleting the powernow files mentioned, but I still get crashes when I try and log out. I tried looking for a powernow option in the bios but couldn't find one.

I use an ATI card 
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

Does anyone know if maybe if I change my driver this might be fixed?

My last option is to remove the log out button, although that seems very messy, but just incase, how would I do that.

Thank you for helping a new un :).

---

### Post by sinpalabras on 2007-03-21
Hi Doz3r  you sould make a new thread this one is to old. Make clear in the title that you have a ATI card so you get  help from the right people first (ATI users) first. Good luck

---

### Post by loumsmith on 2007-06-16
My 7.1 install recently started freezing.  I installed Envy.  Removed the Nvidia driver and then had envy re-install the driver.  No lockups so far.
Louis

---

### Post by koji36 on 2007-08-17
thy

---

