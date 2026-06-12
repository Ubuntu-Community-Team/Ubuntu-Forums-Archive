---
title: "VMWare Player if I need flash"
date: 2006-09-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by osaeris on 2006-09-05
I have recently installed the AMD64 version of Dapper and enjoy it very much. I have noticed a bit of a boost in speed overall and feel better about actually using all of the 64bit proc instead of just having it.

Since I am using VMWare player I thought I may as well use the Browser Applicance image from VMWare website to use firefox if I need flash for any reason.  

I skimmed the instructions for running 32 bit firefox / flash / java etc but figured I don't really need to do that stuff when I have the .vmx lying around. If there are any other programs which refuse to run in the 64 bit environment (haven't found any yet) the same applies.

Does anyone else think this is a sensible route?

---

### Post by Kilz on 2006-09-05
So you are going to install a complete virtual machine to run a 32bit browser? You will start it when you need flash? There are a lot of sites that use flash. Running a browser on a virtual machine isnt that bad an idea. But you will have to wait for it to start. Then the browser will run slower compaired to one installed on a non vm. The vm itself is going to eat up 6-8 gig of hd space. May I offer the suggestion of simply downloading the automatic setup script from my howto and type in 2 commands to install it. The link is in my signature.

---

### Post by mrw on 2006-09-05
I would recommend chroot. I've installed it and the 32-bit Firefox with flash. Works fine.

---

### Post by Kilz on 2006-09-05
> **mrw said:**
> I would recommend chroot. I've installed it and the 32-bit Firefox with flash. Works fine.

Chroots are ok. They were needed in breezy to run 32bit applications in 64bit, but not in Dapper. It may be usefull if you want to run a lot of 32bit applications like development enviroments. But if its just to install a browser its a lot of files that you dont need. It would be faster than a vm though.

---

### Post by kuja on 2006-09-05
True enough, keeping in mind also that chroot method also eats quite a bit of hard drive space, and requires a massive download just to get it working....

---

### Post by osaeris on 2006-09-05
Yeah, you're right Kilz I installed using your script. Pretty snappy too. Like the fact that you get 2 firefox icons so get to choose. Worked really smooth.

Steve

---

