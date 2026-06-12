---
title: "Installing 64-bit Vista in VirtualBox"
date: 2009-05-12
forum: x86 64-bit Users
---

### Post by mazz0 on 2009-05-12
I'm having trouble installing 64 bit Windows Vista in Virtual Box on my 64 bit Hardy - the Windows Installer won't load, saying the CPU doesn't support 64 bit!  I installed the 64 bit VirtualBox (which isn't in Universe - why's that?), in 64 bit Ubuntu, so I don't get this! :(  There doesn't seem to be an option in Virtualbox to emulate a 64 bit CPU.  Anyone know what I'm doing wrong?

---

### Post by pixel :-) on 2009-05-12
> Make sure that the virtual machine profile is configured for a 64-bit guest operating system. From the VirtualBox GUI select the machine, click the settings button at the top, and then select Linux for the guest and Red Hat (64-bit) as the Linux version. Cheers!

[http://ubuntuforums.org/showthread.php?t=1153401](http://ubuntuforums.org/showthread.php?t=1153401)

If it doesn't work, continuou there with your question.

---

### Post by teixidoj on 2009-05-12
I recommend that you choose the dual boot option. I currently run XP in virtual box, even though XP works well; I still cant get all of my drivers to work such as sound and some others.

---

### Post by Melk79 on 2009-05-12
You can add their repository using their instructions if you don't want to install separately. [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)  Scrolling down to repo part.

---

### Post by jespdj on 2009-05-13
> **teixidoj said:**
> I recommend that you choose the dual boot option. I currently run XP in virtual box, even though XP works well; I still cant get all of my drivers to work such as sound and some others.
Sound should work normally in Windows XP in VirtualBox.

The only thing is that hardware accelerated graphics are not well supported on VirtualBox. The current version of VirtualBox does have some support for OpenGL (so programs running in the virtual machine that are using OpenGL will have access to hardware acceleration), but not Direct3D, which most Windows games use.

---

### Post by vectorm12 on 2009-05-13
> **mazz0 said:**
> I'm having trouble installing 64 bit Windows Vista in Virtual Box on my 64 bit Hardy - the Windows Installer won't load, saying the CPU doesn't support 64 bit!  I installed the 64 bit VirtualBox (which isn't in Universe - why's that?), in 64 bit Ubuntu, so I don't get this! :(  There doesn't seem to be an option in Virtualbox to emulate a 64 bit CPU.  Anyone know what I'm doing wrong?

I believe Virtual Box requires your CPU to support Intel VT-x/AMD-V in order for it to run a 64bit OS. Note that older 64bit CPUs rarely supported these extensions and thus are unable to run virtual 64bit OS:es(correct me if I'm wrong)

---

### Post by jespdj on 2009-05-13
You are right, vectorm12.

If you have an Intel processor, use the [processorfinder](http://processorfinder.intel.com/) to find the features of your processor. Sometimes, if your processor supports it, you also need to enable hardware virtualization support in the BIOS of your computer to be able to use it.

---

