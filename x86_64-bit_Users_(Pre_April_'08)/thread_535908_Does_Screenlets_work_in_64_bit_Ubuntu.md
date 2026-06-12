---
title: "Does Screenlets work in 64 bit Ubuntu?"
date: 2007-08-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by volksolwagen57 on 2007-08-27
Does Screenlets work in 64 bit? I don't have Compiz or Beryl installed since I can't get them working correctly. Can someone help me with this? Thanks for your help in advance.

---

### Post by John.Michael.Kane on 2007-08-27
Yes screenlets install under 64bit. follow the direct below.
[Installation instructions for Ubuntu Edgy Eft/Feisty Fawn/Gutsy Gibbon users]("http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users")

Also the screenlets graphical tool is listed under system-->preferences


Note: some functions may not work without composting enabled.

---

### Post by jamesford on 2007-08-27
they work great, been runnig them as long as i can remember almost

---

### Post by fuoco on 2007-08-27
Someone has maybe the source for the deb package? or a place where the .dsc is found, so that i can build it for myself on a powerpc arch? (i couldn't find a deb for that nowhere)

---

### Post by John.Michael.Kane on 2007-08-27
> **fuoco said:**
> Someone has maybe the source for the deb package? or a place where the .dsc is found, so that i can build it for myself on a powerpc arch? (i couldn't find a deb for that nowhere)

Source file is right on the site.
[http://www.screenlets.org/index.php/Download](http://www.screenlets.org/index.php/Download)

---

### Post by fuoco on 2007-08-27
> **SD-Plissken said:**
> Source file is right on the site.
[http://www.screenlets.org/index.php/Download](http://www.screenlets.org/index.php/Download)

I meant the source from which the debian packages are built. as in the debian/ directory inside the source code.

---

### Post by John.Michael.Kane on 2007-08-27
> **fuoco said:**
> I meant the source from which the debian packages are built. as in the debian/ directory inside the source code.

If all you wantl is to make a .deb for your use or few friends, you can pass the checkinstall command.  when you compile a software type "sudo checkinstall -D" instead of "sudo make install", it should install the software giving synaptic all the needed informations to see it and create a .deb.

Or use one of these methods

[Howto make debian standard debs from scratch]("http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall")
[BuildingWithoutHelper]("http://women.debian.org/wiki/English/BuildingWithoutHelper")

---

### Post by sorcererx84 on 2007-08-29
@fuoco: Here's a ppc deb for you :D

---

### Post by fuoco on 2007-08-30
> **sorcererx84 said:**
> @fuoco: Here's a ppc deb for you :D

Thanks but it won't work, it says wrong architecture. May I ask how you built it? if you provide me with the source of the package, aka the "debian" subdirectory I can build it myself on my system and it's bound to work.

---

### Post by John.Michael.Kane on 2007-08-30
> **fuoco said:**
> Thanks but it won't work, it says wrong architecture. May I ask how you built it? if you provide me with the source of the package, aka the "debian" subdirectory I can build it myself on my system and it's bound to work.

Theres three ways clearly posted that show you one can make a deb file for personal use, and that is without the Debian sub directory.


Edit: I just made a deb file of screenlets using the checkinstall method, and it installed without issue. Theres no reason you can't use the checkinstall method if the deb is for personal use.

---

### Post by fuoco on 2007-08-30
> **SD-Plissken said:**
> Theres three ways clearly posted that show you one can make a deb file for personal use, and that is without the Debian sub directory.


Edit: I just made a deb file of screenlets using the checkinstall method, and it installed without issue. Theres no reason you can't use the checkinstall method if the deb is for personal use.

i just don't really like the checkinstall method, i prefer not to use it. The other methods are of creating the debian subdir myself - well of course that's what i should do, but since obviously it was already done by someone else and so the .debs are in the repository I thought it could be shared with everyone.

---

### Post by volksolwagen57 on 2007-09-08
when i used to run i386 and installed screenlets, i used checkinstall and therefore prefer to install it in this way. i used the repository and installed it through apt and not all screenlets appeared. anyway, did i miss something through the amd64 installation? it seems i installed it well enough but it's just lame. i don't like it as much as my other installation.

---

### Post by rsambuca on 2007-09-08
> **fuoco said:**
> i just don't really like the checkinstall method, i prefer not to use it. The other methods are of creating the debian subdir myself - well of course that's what i should do, but since obviously it was already done by someone else and so the .debs are in the repository I thought it could be shared with everyone.

Do you want someone to come over to your house and type the commands into the keyboard for you as well?

---

### Post by fuoco on 2007-09-08
> **rsambuca said:**
> Do you want someone to come over to your house and type the commands into the keyboard for you as well?

no, thank you very much, i did it already and as i suspected it doesn't work well.

---

