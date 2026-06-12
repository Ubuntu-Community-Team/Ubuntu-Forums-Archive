---
title: "Installing Wine 0.9.41 on Dapper6.06?"
date: 2007-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tur Third on 2007-07-18
Which version of Wine is best for DapperDrake 6.06?

I tried to install following instructions on the wine website but could not get it to work [http://wiki.winehq.org/UbuntuAMD64]("http://wiki.winehq.org/UbuntuAMD64")

It is a shame there is not a 64bit package, as that would make life much easier.

Is there a version that works best? recommendations please...:)

---

### Post by Kilz on 2007-07-18
> **Tur Third said:**
> Which version of Wine is best for DapperDrake 6.06?

I tried to install following instructions on the wine website but could not get it to work [http://wiki.winehq.org/UbuntuAMD64]("http://wiki.winehq.org/UbuntuAMD64")

It is a shame there is not a 64bit package, as that would make life much easier.

Is there a version that works best? recommendations please...:)

Sadly, there is no installable wine package for Dapper.  But being that I still run and like Dapper I can give you some good information.

First off, wine is 32bit. Even the packages that install to 64bit Feisty are 32bit. The packages just make installing it a little easier. The reason its 32bit , is because its a 32bit application layer, for 32bit Windows applications. You will not gain any performance increase regardless of what package you install, because they are all 32bit.
Long ago I wrote the first [howto to install wine into Dapper]("http://ubuntuforums.org/showthread.php?t=185557"). Its no longer supported on the newer versions because 64bit packages are avilable for them. But I will help and answer any questions for people running Dapper if you run into problems. The  install script is no longer updated. But the manual howto should only take a little bit to copy/paste into a terminal.

---

### Post by Tur Third on 2007-07-19
Thanks for your help, I did see your post but have not tried that. I will give it a go and let you know how I get on.

I am wondering whether I should consider upgrading to fiesty fawn. There seems to be more packages that will install on 64 bit.

---

### Post by Kilz on 2007-07-19
> **Tur Third said:**
> Thanks for your help, I did see your post but have not tried that. I will give it a go and let you know how I get on.

I am wondering whether I should consider upgrading to fiesty fawn. There seems to be more packages that will install on 64 bit.

Thats up to you. If you do , and you want to keep the present install you will have to upgrade to Edgy , then Feisty. Personally I love the stability that is Dapper. It has untill 2009 for updates, even longer than Feisty because its a long term release.  There is very little I personally need that has been added since, in fact I dont know of anything. As I pointed out above , the wine package offers no improvement other than the maybe 10 minutes it will take for the howto to install. What other packages do you think have been added?

---

### Post by Tur Third on 2007-07-19
The reason I went for 6.06 was that I wanted a stable system and it is good news to hear that you think there is not much reason to change.

You have a fair point about packages, I am not sure what is missing. Other software I had some problems with was Blender, another 32bit program. I am happy now as I have 2.44 installed with from a package with static libraries (haven't really used it much yet but have bought the new book, which I would recommend.)

I have not made much progress with wine though. This is the message I get when I try to run 'winecfg'

```
:~/Desktop$ winecfg
wine: creating configuration directory '/home/xxxx/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
wine: wineprefixcreate failed while creating '/home/xxxx/.wine'.
xxxx@xxxxx:~/Desktop$ wineserver: could not save registry branch to /home/xxxx/.wine-deEMFP/system.reg : No such file or directory
```

Looks like it can't create the directory, which is odd. This was the mesage I was getting last time. There is plenty of disk space, and permissions should be ok in my ~user directory.

Do you have any ideas?

Thanks

---

### Post by Tur Third on 2007-07-19
Sorry, just read the rest of your original post! You've listed this exact error! It looks like a video card driver problem,

---

### Post by Kilz on 2007-07-19
Yep, and that will also fix the reason Blender isnt running for you as you need accelerated graphics to run it.

---

### Post by Tur Third on 2007-07-19
Well that is not good news, I have a  'S3 Unichrome Pro VGA Adapter (rev 01)', and the driver looks to be installed from what I can tell.

section from my xorg.conf
```
Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection
```

Strangely I don't think I have a problem with Blender (just tried rendering the default block, without problem). I also did have wine working on this PC from an RPM with Mandriva2007.

Hmmm, have to give this some thought.

---

### Post by Tur Third on 2007-07-25
An update: I have bought a shiny new nvidia GeForce 6200 graphics card. This seems to have resolved the problem with wine as promised on your guide. Thanks.

I have not really tested yet, as I have been too busy playing ppracer!:)

---

