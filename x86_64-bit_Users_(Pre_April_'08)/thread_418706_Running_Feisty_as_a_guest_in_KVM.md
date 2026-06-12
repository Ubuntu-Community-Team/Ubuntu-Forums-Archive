---
title: "Running Feisty as a guest in KVM"
date: 2007-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by RyanBrooks on 2007-04-22
I am trying to install Ubuntu Feisty x64 Server as a guest OS using KVM on my Feisty x64 installation, so I can set up a secure, sandboxed VM for running gforge. I've successfully set up KVM, and it boots Knoppix, etc without problems, but when I try running the Ubuntu installer it falls over and hangs. I have used qemu-system-x64, as there is a known bug relating to ISOLINUX loaders, but the installer only gets to the menu, and when you select "install" it goes to a blank screen with a still cursor in the top left of the screen.

I have been playing with this for a few days now and haven't made any inroads. Any ideas would be greatly appreciated.

Thanks

Ryan

---

