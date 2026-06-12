---
title: "hoary gnome startup broken?"
date: 2005-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by callahan on 2005-03-12
I updated my hoary distribution again this morning and while now the kernel works again, gnome no longer starts up.  It boots up and then starts X normally with gdm.  However when I log in I just get a flat brown screen and a cursor.

  Michael

---

### Post by weichsel on 2005-03-13
I have the same problem after updateing my hoary amd64.
An error I recieved from Synaptic was:

E: /var/cache/apt/archives/ia32-libs_0.5ubuntu3_amd64.deb:  Fehler beim 
Erzeugen des symbolischen Verweises »./usr/lib32/libGL.so.1«: Datei 
oder Verzeichnis nicht gefunden

^^^German 
~~~Translation:
E: /var/cache/apt/archives/ia32-libs_0.5ubuntu3_amd64.deb:  Error creating 
symbolic link »./usr/lib32/libGL.so.1«: File
or Directory not found

---

### Post by Dromio on 2005-03-13
I'm having the same issue (brown screen and cursor, nothing else) on a fresh install of Hoary direct from the CD.  I've got an A64 + nvidia card and used pretty much all default options during the installation.

---

### Post by minio on 2005-03-13
Try to change name of /etc/aliases to /etc/aliases.db .

---

### Post by callahan on 2005-03-13
Both /etc/aliases and /etc/aliases.db exits.  One is a simple text file and one appears to be a berkley db file.

  Michael

---

### Post by minio on 2005-03-14
Maybe you should try upgrade/reinstall postfix package. I think I did it before Gnome started to work again. But with latest upgrade my Hoary installation become really broken so i am not sure about anything now. :-(

---

### Post by callahan on 2005-03-14
The ia32-libs workaround in the other thread fixes this.

  Michael

---

### Post by Reb on 2005-03-15
Available here:
[http://www.ubuntuforums.org/showthread.php?t=19551](http://www.ubuntuforums.org/showthread.php?t=19551)

---

### Post by thoffland on 2005-07-02
I was having the same problem, I fixed it by doing this: 

Login and boot to the brown screen
ctrl/alt/F1
sudo killall esd
ctrl/alt/F7
the boot screen came up and showed the desktop
my pc was freezing up here and there, but still let me manipulate the settings.
gstream-properties (in a run box)
changed to alsa (later back to OSS) on the top one and oss on the bottom one. 

Did a full reboot, and it was ok again.

I also changed my xmmx to use OSS since that's all it works with, that's prolly just me though since i'm on USB speakers.

---

