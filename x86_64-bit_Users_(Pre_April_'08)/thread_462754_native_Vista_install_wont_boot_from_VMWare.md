---
title: "native Vista install wont boot from VMWare"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by SexualChocolate on 2007-06-03
Hello all,

Im currently running x64 Fiesty (kernel: generic 2.6.20-15) on my HP dv2000t laptop (core 2, 2 gb ram ).  Im trying to boot to a native Vista install from VMWare (v. 6.0.0 build-45731). I get this error after grub and the Vistas boot screen.

[[img]http://www.imageplanet.us/public/thumb_466257c360b32918660788.png[/img]](http://www.imageplanet.us/public/pview/12/Screenshot-2.png)


Its Vista 32 bit version, so could that be why its messing up?

Here are my virtual machine settings

memory: 1024 mb
processors: 1
hard disk: /dev/sda (the entire disk, if i select the Vista partition I get error #17 in grub) independent persistant
Display : auto detect


Any ideas?

---

### Post by tszanon on 2007-06-04
If I recall correctly, grub does not work with Vista. If you want to have both grub and Vista, then you have to keep them both in seperate disks (and select which one to boot in the BIOS boot menu) or let Vista rewrite MBR and use a boot disk to boot Ubuntu.

About using VMWare to boot Vista, I don't think that the fact Vista is 32bit affects anything. I think you can't just boot a "pre-installed" OS with VMware before doing some tweaking. I think there's something like vmware-converter that converts real machines to virtual machines.

---

### Post by Kilz on 2007-06-04
Another point to keep in mind. What version of Vista are you trying to install to a virtual machine? Some are not licensed to be run as a vm and you can bet dollars to donuts Microsoft has tossed in a monkey wrench to make sure they dont.

---

### Post by MiD-AwE on 2007-06-05
Can it be done? I've been looking for a solution to boot vista from it's own partition with vmware. I've heard of it done with XP. I'm still looking if it can be done.

---

### Post by tszanon on 2007-06-05
I don't know if it can be done, but, if you have the Vista installation cd, you could try to install it under VMware, as a new virtual machine. If it works, then i think that there's a way to make you current Vista installation work under vmware.

If you try this, remember to check if you have the most up-to-date version of vmware.

Oh, I just noticed you're using VMware Workstation. I don't know if there's any difference, but have you tried VMware Server?

---

### Post by kpagan on 2007-10-17
I am in the same situation here.
I have Vista Business 32bit and Ubuntu 7.04 64bit
I have followed the instructions from [here ]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html") and specifically for vista from [here]("http://www.advicesource.org/ubuntu/Run_Existing_Vista_Installation_On_Ubuntu_With_Vmware_player.html")

BUT
it says to copy the IDE drivers from a Windows XP cd and to put them in the Vista system32/drivers directory.
When I tried to do that I realized that i couldn't because 2 of the drivers where used and locked, so i booted from ubuntu and copied them from there.
Then Vista could not boot at all.
I was lucky that I had kept a backup from the 4 driver files and when I restored them, Vista was fine.
But I need to make it work. 
I am trying to make the emulation with vmware-player.
Any suggestions??:confused::confused::confused::confused:

---

### Post by KingWilliam on 2008-05-08
I am trying the same thing. I used VMware server (with the latest version you can chose to use a physical disk when creating the VM) to boot my native Windows Vista. I get a bsod while booting Vista. But it starts booting which is quit much. With Windows XP there should be no problems doing this.

---

