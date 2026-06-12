---
title: "MP3 for K3b?"
date: 2005-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pse on 2005-03-19
I'm having this little problem with K3b on Hoary...I can't decode mp3 files. I do have libmad installed, but I cannot find any plugin for it... Is it in the repositories?

---

### Post by Pse on 2005-03-20
I guess I'll have to compile K3b myself ](*,)
I've just remembered that I'd need to install all KDE development files to do that...I guess I'll put up with a simple MP3-to-WAV script =)

---

### Post by negatory on 2005-03-24
I've followed [this](http://www.ubuntuforums.org/showthread.php?t=21044&highlight=mp3+k3b) and it worked for me...
Pedro Carrico

---

### Post by Pse on 2005-03-26
Thanks for your reply. Well, I am using the 64-bit version of K3b, and I've already tried following similar steps in order to get it to work, but I haven't been successful. I'll try installing a 32-bit copy of K3b and getting the plugins...why hadn't I thought about that?

---

### Post by Pse on 2005-03-26
Well, I have a weak mind, so I went and downloaded K3b-64 from Debian's pure64 repositories ](*,) Everything seems to be working fine now =)

---

### Post by raum13 on 2005-03-31
[QUOTE=Pse]I guess I'll have to compile K3b myself ](*,)
I've just remembered that I'd need to install all KDE development files to do that...I guess I'll put up with a simple MP3-to-WAV script =)[/QUOTE]


Hi 

the deb way to go is 

apt-get source k3b
apt-get build-dep k3b
apt-get install libmad0 libmad0-dev
cd k3b-0.11.23
dpkg-buildpackage -tc 
dpkg -i ../k3b_0.11.23-0ubuntu1_i386.deb ../k3blibs_0.11.23-0ubuntu1_i386.deb


with this you get a k3b which has 

/usr/share/apps/k3b/plugins/k3bmaddecoder.plugin
/usr/lib/kde3/libk3bmaddecoder.la
/usr/lib/kde3/libk3bmaddecoder.so

included. these are only included if during the compile the file mad.h is found. And as libmad0-dev is not required to compile k3b it is not downloaded during the "apt-get build-dep k3b" without the extra install you get a mp3 free k3b. (politcal reasons or just forgotten ?) 

cu r13

---

### Post by Pse on 2005-03-31
Cool! Thanks for that raum! But...if you're compiling K3b from deb-src, you'll still need all those dev packages from KDE that are required. I just got a precompiled 64-bit package from Debian's Pure64 repositories and seems to be working fine.
I guess Ubuntu has omitted Mp3 support due to legal reasons...

---

### Post by Equinox on 2005-04-08
Just install libmad0-dev and libmad0 .. Once you have those run k3b and it should burn MP3s fine... No need to recompile.. It's quite intelligent at detecting things.

---

### Post by Pse on 2005-04-08
In fact, I think I tried that. You have to have MP3 support enabled at compile time for it to detect it, I believe...

---

