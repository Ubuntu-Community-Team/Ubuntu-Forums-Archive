---
title: "Best way to run Windows apps"
date: 2007-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by M$LOL on 2007-02-19
I'm using Edgy (64 bit) and I'm looking for the best way to run a few Windows apps, including a couple of fairly recent games. I know I can go for Wine or VMware, but I'm not sure which is best. I've heard of WineX, but I don't know much about it. What should I go for?

Thanks.:)

---

### Post by solar george on 2007-02-19
Try wine first as it is free and you won't lose anything by trying.

---

### Post by cmost on 2007-02-19
After you try WINE, then I recommend a full Windows installation running in VMware or QEMU (whichever you prefer).  Both VMware Server & QEMU are free.  If you want a commercial product, try VMWare Workstation or Parallels, or the recently released Virtual DOS toolbox.  I've found the most reliable way to run Windows programs is in Windows.  On the other hand, I've found Windows to be most reliable when it's used only occasionally within Linux.  :-)  Good luck!

---

### Post by LeslieL on 2007-02-19
If you don't mind spending a bit of money use Crossover Office, available from Codeweavers. It's based on Wine, and part of the money you spend will go towards further Wine development. i find it much easier to use than fiddling around with Wine;

---

### Post by Kilz on 2007-02-19
If the Windows apps are games you might consider paying the $15 for Cedega, it used to be called WineX. The money paid will be less than the hours of setup you will do with wine. You might also want to look into Linux applications that have the same functionality like DVDShrink = K9copy

---

### Post by bernardfrancois on 2007-02-19
I use VMware, it runs the operating system natively (using virtualisation).
There's also qemu, which does emulation (a lot slower), but can also do virtualisation if you instal an additional module (which I failed to intall for some reason).
Xen is another virtualisation program, but I didn't try it yet. I think it's good, but probably VMware is better (because it exists longer).

---

### Post by M$LOL on 2007-02-19
So, for best performance it's a VM? Can I install this stuff via Synaptic?

If I use an emulator or WINE, is there any way to turn it off or on depending on whether I want exes to execute or not?

Thanks for the help. :)

---

### Post by Kilz on 2007-02-19
> **M$LOL said:**
> So, for best performance it's a VM? Can I install this stuff via Synaptic?

If I use an emulator or WINE, is there any way to turn it off or on depending on whether I want exes to execute or not?

Thanks for the help. :)

A VM is ok for office applications and such, but I have never had good results running games on them. You might be able to play solitaire, but dont even think about say Halflife 2 or Oblivion.

---

### Post by cmost on 2007-02-19
Kilz is right.  VMware does not support accelerated video, at least not at the moment.  Rumors abound about imminent new releases from both VMware (VMware Fusion) and Parallels that will finally add support for accelerated (i.e., openGL and DirectX) video displays within virtual machines.  If you're a gamer, and your primary goal of running Windows apps in Linux is games then I suggest you dual boot to gain access to full hardware acceleration.

---

### Post by NewSpecter on 2007-02-22
> **cmost said:**
> Kilz is right.  VMware does not support accelerated video, at least not at the moment.  Rumors abound about imminent new releases from both VMware (VMware Fusion) and Parallels that will finally add support for accelerated (i.e., openGL and DirectX) video displays within virtual machines.  If you're a gamer, and your primary goal of running Windows apps in Linux is games then I suggest you dual boot to gain access to full hardware acceleration.
I heard that [Parallels ]("http://www.parallels.com")will make 3d support available with the following upgrade, but I don't know the date of release - they still keep it secret. I think that it'll appear in half  a year or even less...
Dual boot is a better option for games that a VM. Any VM(I use Parallels) eats a lot of RAM. And it doesn't support 3d graphics as it has been already mentioned. I don't play and that's why Parallels is an ideal option for me!

---

### Post by NewSpecter on 2007-02-22
> **Kilz said:**
> A VM is ok for office applications and such, but I have never had good results running games on them. You might be able to play solitaire, but dont even think about say Halflife 2 or Oblivion.
As I have already said, both Fusion and Parallels don't have 3d graphics support. I know little about fusion, but Parallels announced that they are working on this officially. It's not a myth then. But Still it will not be possible to run heavy games due to high RAM requirements!

---

