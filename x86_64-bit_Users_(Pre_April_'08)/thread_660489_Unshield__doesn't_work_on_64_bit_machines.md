---
title: "Unshield : doesn't work on 64 bit machines"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Aifel on 2008-01-06
So, unshield doesn't work on 64-bit machines. There is a patch available, but patching is one of the few things I haven't figured out yet in Linux... :(
So, can anyone walk me through a patch, or just make a pre-patched version available?

---

### Post by koenbeek on 2008-01-16
There is a bug about this in launchpad : [https://bugs.launchpad.net/ubuntu/+source/unshield/+bug/172901](https://bugs.launchpad.net/ubuntu/+source/unshield/+bug/172901)

I've created a debdiff to correct the problem and am awaiting sponsorship

I'll attach a few debian packages with the applied patch for 64bit ubuntus

to install : download the .deb files and store in a directory
then type
sudo dpkg -i *unshield*deb

---

### Post by koenbeek on 2008-01-16
I haven't been able to test these patched packages as I don't have a suitable .cab file to test

could you say whether the new packages worked for you or attach a .cab file so I can test ?

 cheers,

   Koen

---

### Post by koenbeek on 2008-01-24
I've finally found some cab files that caused issues and can confirm that the .deb files I attached are working

---

### Post by DjCoke on 2008-02-09
Can confirm indeed that it works, finally can i install ut2004

---

### Post by kaivalagi on 2008-02-24
Didn't work for me. I am trying to extract wireless card drivers for use with ndiswrapper, as I need to get at the driver/inf files.

I have a 590K cab file I need to get inside, anyone fancy giving it a try? Nether cabextract or unshield with patches works for me :confused:
 
I've attached it in a bz2 archive for what it was worth :)

 I am trying to stabilise a RT2651wireless card (EDIMAX EW-7128G) so if anyone knows of an alternative route, that would help too. Need to use static ip / wpa for mythtv...

Any help is very much appreciated

---

### Post by koenbeek on 2008-02-25
I think you also need a data1.hdr file

without it, you get a 

[COLOR=Red]Failed to open data1.cab as an InstallShield Cabinet File[/COLOR]

error message

---

