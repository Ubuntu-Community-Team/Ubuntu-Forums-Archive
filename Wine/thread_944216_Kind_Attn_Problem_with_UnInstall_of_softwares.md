---
title: "Kind Attn: Problem with UnInstall of softwares?"
date: 2008-10-11
forum: Wine
---

### Post by ipskhurana on 2008-10-11
hi
i have installed Ubuntu 8.041 LTS Desktop,
then i installed Wine to install some windows based apps,
i have installed windows based apps, but they are not launching..some error..
so i want to uninstall them and re-install, them, but i dont know
how to un install those windows apps.. (ACD FotoSlate)

also is there any other program like wine which supports windows apps..

actually i want some softwares to run on ubuntu,

1st one is photo print software like Acd Fotoslate (win xp based)
it has ready templates to print multiple photos on each sheet.

2nd one is i want to view & print .dwg (autocad) files

3 rd i want Ares p2p like software on Ubuntu..

4th i have installed unrar package, but still it doesnt opens
rar files.

i am not able to find Yast in Ubuntu to uninstall the softwares.
can anyone please help..in details and give links..
.. i was using win xp ..but now i switched over to
Ubuntu, and i want to continue with Ubuntu, cuase i liked it 
more than xp..

-- 
IPS Khurana

---

### Post by sokopok on 2008-10-11
I never really use Wine, so can't help you there, but another solution would be to use a virtual machine like vbox, xen, vmware, ... this way you can run a full Windows session while using linux. Should be faster also.

1. Gwenview or similar software could be an alternative for acdsee
2. use mm3d, qcad for autocad files
3. for p2p you could check this thread: [http://ubuntuforums.org/showthread.php?t=173442](http://ubuntuforums.org/showthread.php?t=173442) or just do a search in  google for: "p2p ubuntu"
4. unrar is a console based application, use Archive Manager (Gnome) or Ark (KDE)
5. Yast is Suse's package manager. Use Synaptic Package Manager

hope this helps

---

### Post by david_kt on 2008-10-11
> **ipskhurana said:**
> hi
i have installed Ubuntu 8.041 LTS Desktop,
then i installed Wine to install some windows based apps,
i have installed windows based apps, but they are not launching..some error..
so i want to uninstall them and re-install, them, but i dont know
how to un install those windows apps.. (ACD FotoSlate)

1st one is photo print software like Acd Fotoslate (win xp based)
it has ready templates to print multiple photos on each sheet.

2nd one is i want to view & print .dwg (autocad) files

3 rd i want Ares p2p like software on Ubuntu..

4th i have installed unrar package, but still it doesnt opens
rar files.



1. To uninstall program in wine, open terminal (Application > Accesories > Terminal) and type uninstaller <enter>.

2. To view and print .dwg files, use a9cad:
[http://www.a9tech.com/download/A9CADV2Setup.exe](http://www.a9tech.com/download/A9CADV2Setup.exe)
It could run easyly in wine.
Qcad could not open .dwg file, as far as I know.

3. Ares could work with wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8202](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8202)

4. For rar file, use peazip. Download [this]("http://downloads.sourceforge.net/peazip/peazip_2.3a.bin.LINUX.GTK2.i586-1.deb") file and [this]("http://giorgiotani.interfree.it/peazip-unace-plugin_1.LINUX.INSTALL-1.i586.deb") file. I have tried many other free programs in linux but none is working except peazip. There is a non free one in synaptic but I have not tried it yet.
After download above two files, install both by double clicking and the downloaded file.
After you have install peazip, right click and any rar file, choose properties > open with > add > select peazip and click add > click radio button in front of peazip to make it default program.
After this, you should be able to open any rar files.

DK

---

