---
title: "Installing new Programms with no internet connection."
date: 2008-08-01
forum: x86 64-bit Users
---

### Post by drfish on 2008-08-01
Hi,

I just installed Ubuntu on my laptop and i'm just experimenting. I moved from Windows XP and i'm one of those who's used to just double-clicking the exe and then just installing. I understand that I have to use the repository in the Add/Remove programs but i'm my laptop doesn't have an internet connection. What I used to do was download exe on to my memory stick and then transfer that to my laptop.

Basically, what i'm trying to say is what's the best option for me?

Thanks

---

### Post by gsmanners on 2008-08-01
Install via CD/DVD:

[http://monkeyblog.org/ubuntu/installing/#add_cd](http://monkeyblog.org/ubuntu/installing/#add_cd)

---

### Post by opscure on 2008-08-01
Download .deb files with another computer, store to portable media, and use dpkg -i to install them from your portable media.

You can access a listing of the packages from 
[http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2)
and you can get the corrisponding packages in the list from:
[http://us.archive.ubuntu.com/ubuntu/pool/universe/](http://us.archive.ubuntu.com/ubuntu/pool/universe/)

Sorry to be a bit vague with the command above (thanks John.Michael.Kane for explaining it better).

So, you would want to use this command within terminal.  (Applications->Accessories->Terminal)
You will want to change directories first to your media and then install... assuming you burn the .deb files to a cd:
```

cd /media/cdrom 
sudo dpkg -i filename.deb

```
would install the filename.deb file to your system from the cdrom directory

---

### Post by drfish on 2008-08-01
Sorry to ask something stupid but I am totally new to this. What's dpkg -i?

---

### Post by John.Michael.Kane on 2008-08-01
> **drfish said:**
> Sorry to ask something stupid but I am totally new to this. What's dpkg -i?

dpkg -i is short for install, it could also be typed as dpkg --install

Examples
```
sudo dpkg -i foo.deb 
sudo dpkg --install foo.deb
```

---

### Post by lswb on 2008-08-01
Actually, with the packages downloaded to a USB stick or other portable drive, just plug in the drive, when nautilus or other file manager opens a window of you can double-click on the .deb files, and a grapical package manager should start up.

---

### Post by drfish on 2008-08-01
Ok thanks. Or i guess my second option if .dev files arnt provided is to use the .tar files

---

### Post by opscure on 2008-08-02
the .tar.gz files are usually the packaged source (as on sf.net), to install these you should follow the included readme or install files.

usually for source packages you would type:
./configure
make
sudo make install

---

