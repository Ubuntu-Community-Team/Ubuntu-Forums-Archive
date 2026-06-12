---
title: "Install Moomoo trading on Ubuntu"
date: 2022-03-29
forum: Wine
---

### Post by Peter_APIIT on 2022-03-29
Dear All, 
I new to ubuntu and wine. I would like to install a investment trading platform called moomoo trading to ubuntu. Is this possible. If so, how to do it? 

[noparse]https:(doubleslash)www(dot)moomoo(dot)com/download[/noparse]


I really appreciate your help on this.

---

### Post by Peter_APIIT on 2022-03-30
Please help me on this. It is very important to me. Appreciate your help.

---

### Post by Peter_APIIT on 2022-03-30
moomoo program is not available on Wine Application Database. Any other method to run moomoo on LInux By VM??

---

### Post by DuckHook on 2022-04-01
The usual method to test an app's unknown functionality in WINE is to just try it. You can even contribute to the WINE project itself by being the first to register this app and posting your results and your experiences.

WINE has the versatility to create a prefix—that is to say, a unique and isolated WINE instance—that you can install your app into and try. If it doesn't work you can simply delete the prefix. Here's a short primer on WINE prefixes: [https://linuxconfig.org/using-wine-prefixes](https://linuxconfig.org/using-wine-prefixes)

Note that you may have to tweak WINE to run your app. There are so many factors involved in tweaking that it is impossible to address them in a forum thread. Installing Winetricks is always a good starting point for such tweaking. Explanation here: [https://wiki.winehq.org/Winetricks](https://wiki.winehq.org/Winetricks)

If your app won't run in WINE no matter how much you tweak it, then running it within a VM is the obvious next step. Setting up a Windows VM is not especially difficult, but it is involved. Again, providing a simple recipe on a forum thread is asking too much, but there are many online tutorials for doing so. A web search will return dozens of hits. First, you must decide which VM platform you want to use. New users unfamiliar with VMs tend to find the commercial VM platforms like VirtualBox or VMWare a bit friendlier to use. If you are looking for VMs native to Linux (already built into the kernel and therefore more efficient) then the two I am aware of are KVM and Xen. I use KVM quite successfully. But then, I also use VirtualBox and like it too.

Here's the first tutorial that a quick web search returned with respect to installing Win 10 in KVM: [https://getlabsdone.com/install-windows-10-on-ubuntu-kvm/](https://getlabsdone.com/install-windows-10-on-ubuntu-kvm/)

Good Luck and Happy Ubuntu-ing!

---

