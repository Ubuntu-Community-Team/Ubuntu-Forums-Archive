---
title: "Wine versus Virtual Box"
date: 2008-10-23
forum: Wine
---

### Post by DeepSandwich on 2008-10-23
Can you guys tell me what sort of advantages Wine has over VB, or vice verse?

I have a large list of software that i currently use on my windows system that i use for work and school. Is there a way to tell what programs will and will not work in Ubuntu through Wine, or through VB?

I use stuff like photoshop, autocad, solidworks, acrobat, mathcad, matlab, and a few games (especially ones made by Valve). Will certain programs run faster in ubuntu depending on if i use Wine or VB?

---

### Post by rocky5051 on 2008-10-23
I've never used VirtualBox before, but I have used QEMU to run a few different operating systems to do (simple) tasks I couldn't do without said OS.

Running an operating system under a virtual machine provides a nearly completely, and fairly stable solution to running Windows programs under a Linux installation. The major drawbacks to virtual machines, however, are that if your CPU doesn't support acceleration features (although most modern CPU's do) the virtual machine software uses, you'll experience horrible slowness, as the virtual machine is running under one big process, and it's not a "real-time" deal for the operating system, so it's slow.

In fact, even with acceleration features working, it's still slower. In addition to that, unless you have a very powerful machine, you wouldn't be able to run games using a virtual machine as most do not support graphics hardware acceleration, or D3D.

Wine, on the other hand, provides "seamless" Windows integration without the use of Windows code, or emulation. In one respect this means most programs will run near (or equally) as fast as they would have in Windows, but the drawback is there are many programs that have issues that keep them from working fully, or only work with workarounds (which can sometimes be difficult to do), or just don't work at all.

Wine can handle games. In fact, there are several (if you check out the Wine appDB) which work fairly well. But again, Wine is buggy, but for someone who needs to use a large collection of software from Windows and cannot find a Linux alternative, Wine is the way to go.

To summarize, if you were only going to run one program, you could use a virtual machine. However, if you need to use more than one (and several are games or...using an example you present, AutoCAD), then you may wish to use Wine. Before using Wine and chucking a Windows installation, you should make sure what you want to use has been tested and is known to work.

Hope that helps.

---

### Post by Therion on 2008-10-23
I've never used Wine or QEMU but I do use Virtual Box.  Pros and Cons...  Hmmm...  

Well, I'd say THE biggest con regarding using VB is no 3D acceleration followed closely by the feeling of being tied to Windows as a whole.  Personally, I find that using VB is about as close to being behind an actual "Windows PC" as you can get; how you see that is up to you, but the "illusion" is that good, that's really my point: If you didn't know any better you'd think you were behind an actual Windows box.  Speed has never been an issue on MY system but I'm running a C2D 8500 with 2GB of RAM.  

The couple applications I need to run a VM for do run seamlessly and without any problem to speak of.  It's not a perfect world, there is the *occasional* bug or hitch or frustration but hey, it's Windows <shrug>...  What can ya do?  VB, in short is great if you need the MS version of things like Office and such.  Not so hot if you want to run games or do 3D editing.

---

