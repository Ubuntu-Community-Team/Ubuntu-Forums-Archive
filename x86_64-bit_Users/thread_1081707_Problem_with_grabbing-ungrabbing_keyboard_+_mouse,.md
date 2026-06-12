---
title: "Problem with grabbing-ungrabbing keyboard + mouse, in VirtualBox with WinXP"
date: 2009-02-26
forum: x86 64-bit Users
---

### Post by trexgrec on 2009-02-26
Hello all.

I have recently installed successfully VirtualBox 1.5.6 in Ubuntu 8.04 64B, and I managed to install WinXP 32b version in a virtual hard drive.

During the installation, I was continuously having problems switching the mouse and the keyboard from VirtualBox to my system. I checked this problem online and I saw that many more people were having the same problem with the mouse, and that a temporary solution is to press the "Print Screen" button, to at least have access to the mouse, without switching to Cntr-Alt-F1, etc. However, grabbing and ungrabbing the mouse + Keyboard doesn't work with my system, despite the instructions in the Ubuntu forums regarding the right Cntr Key.

After a long time, I managed to find a trick. When the mouse is ungrabbed but the keyboard "seems" to be grabbed (the right arrow is green color), I placed the mouse cursor on the lower part of the vm window, and "somehow" the keyboard was finally recognized my VirtualBox. I could type but I could not use the mouse. When I clicked into the vm window, there was a message saying that the mouse would be grabbed if I wanted, and it was! The mouse was working but the keyboard was not!!!!! I pressed the right Cntr key SO MANY TIMES, it didn't work. So, I can either use the mouse OR the keyboard, but NEVER both!!!!!

Does anyone have an idea what I am doing wrong?
Thanks

---

### Post by cariboo on 2009-02-26
Have you tried a different keyboard, I've never had the problem with the Right-Ctrl not working.

Jim

---

### Post by trexgrec on 2009-02-27
I did! The problem was not solved. I do not believe its a hardware problem. Also, other people had the same problem. Maybe I should install v 2.1.4 ?

---

### Post by trexgrec on 2009-02-27
OK, kind of false alarm. I installed the latest version of VirtualBox, the 2.1.4, and the mouse problem is fixed!

---

### Post by 3Miro on 2009-02-27
I had noticed that upon initial instalation of VB, if you click inside the client window, a message pops up regarding grabbing adn ungrabbing the mouse. If you click OK on the message, the mouse is ungrabbed (i.e. you ar eback on the host) and the next time you click the client machine, the mesage pops up again. The only solution is to check the "don't show with message again" box.

---

### Post by John Jason Jordan on 2009-02-27
> **3Miro said:**
> I had noticed that upon initial instalation of VB, if you click inside the client window, a message pops up regarding grabbing adn ungrabbing the mouse. If you click OK on the message, the mouse is ungrabbed (i.e. you ar eback on the host) and the next time you click the client machine, the mesage pops up again. The only solution is to check the "don't show with message again" box.

If you install the Guest Additions module you will be able to use your mouse seamlessly between the virtual machine and your host operating system. You also need Guest Additions to enable the virtual machine to see files on your Linux partition.

---

