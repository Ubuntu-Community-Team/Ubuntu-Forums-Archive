---
title: "Ubuntu PPC users - call for some help."
date: 2006-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by TomaszD on 2006-02-20
Sorry for posting this here, but I can't find *anyone* who is using Ubuntu Breezy PPC anywhere else.
 
I have a small request. I have a small repository for the Psi-Pedrito (modified Psi) Jabber client, for i386 and AMD64. I'd like to make a PPC package as well and I have no idea nor do I want to invest the whole week's time to figure out crosscompiling. The repository is [here](http://psi-pedrito-ubuntu.go.pl). What I would like one of you to do is download my source package, compile it, checkinstall it and send the .deb back to me so I can prepare a proper .deb package and make a repository with it. I will give step-by-step instructions, anyone can handle this. You can delete the Psi client afterwards easily if you hate it ;)
 
We do everything in the terminal. First download the source package.

cd
wget [http://tomasz.nukysrealm.net/psi.tar.gz](http://tomasz.nukysrealm.net/psi.tar.gz)
tar xvfz psi.tar.gz
cd psi

Now install needed dependencies and programs.

sudo apt-get build-dep psi
sudo apt-get install build-essential checkinstall
sudo apt-get install libxss1 libxss-dev

Now that this is done we can run the usual stuff to compile.

./configure --prefix=/usr
make
sudo checkinstall

Checkinstall will launch now. When it asks if you want build documentation, answer No (hit N). The package description is irrelevant, I will change this anyway, so put anything there, hit enter (twice I think). Now you will be shown the deb setup. Only two things are important here. Package name and version (and version string must contain some numbers, else it will fail). Hit the appropriate numbers to change the values (package name should be psi, version number should be 0.10-pedrito-2006-02-03). After this is done, hit enter to install the package and generate the .deb. If you wish you can remove psi from your computer by issuing sudo apt-get remove psi (you might want to check it out though, a greatly enhanced version). What I need is the generated .deb package lying in the psi folder. Open your file manager now and send the .deb file to me via email (dominikowski<at>gmail<dot>com) or just post it here.
 
Big thanks to anyone who takes all the trouble to make this for me! 

PS I don't expect to be flooded with .deb packages, but if you want to do this please post so that someone else doesn't duplicate the effort. Thanks again.

---

### Post by TomaszD on 2006-02-21
Why doesn't anyone want to do this for me? I'm not asking much, just copy and paste 10 commands in the terminal and proceed with checkinstall as I've written. Anyone, and I mean anyone can do this. The ubuntu community has been nothing short of very helpful to me and I've always been helpful to others (don't look at my post count as it doesn't indicate anything). Pretty please?

---

### Post by TomaszD on 2006-02-21
Someone has already done this for me.

---

