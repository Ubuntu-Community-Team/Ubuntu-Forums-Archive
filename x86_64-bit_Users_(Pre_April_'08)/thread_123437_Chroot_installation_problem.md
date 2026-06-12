---
title: "Chroot installation problem"
date: 2006-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cenwio on 2006-01-30
I've followed the chroot installation steps given in thread [http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit]("http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit")
and I have problems with step 5 when I must install synaptic to the chroot enviroment.
After executing "sudo apt-get install synaptic" I get the following:

root@christo:/# sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate

Anyone got some ideas where the problem is?

Would be grateful for any ideas. :confused:

---

### Post by John Jason Jordan on 2006-01-30
[QUOTE=Cenwio]I've followed the chroot installation steps given in thread [http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit]("http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit")
and I have problems with step 5 when I must install synaptic to the chroot enviroment.
After executing "sudo apt-get install synaptic" I get the following:
<snip>
Anyone got some ideas where the problem is?[/QUOTE]
I followed the same instructions and had no problems. 

Are you in chroot when you do the apt-get command?

Also, I didn't have to install Synaptic. It was installed automatically within chroot. To access it I just type "sudo dchroot -d synaptic32" form an ordinary terminal window. Synaptic32 then launches. Any applications I install with Synaptic32 are automatically installed in the chroot environment.

---

### Post by Cenwio on 2006-01-30
Thanks for your reply!

[QUOTE=John Jason Jordan]I followed the same instructions and had no problems. 

Are you in chroot when you do the apt-get command?

Also, I didn't have to install Synaptic. It was installed automatically within chroot. To access it I just type "sudo dchroot -d synaptic32" form an ordinary terminal window. Synaptic32 then launches. Any applications I install with Synaptic32 are automatically installed in the chroot environment.[/QUOTE]

Yep, i've entered the chroot with sudo chroot /chroot/

I tried the "sudo dchroot -d synaptic32" from an ordinary terminal window but all I got was

(hoary) synaptic32
bash: synaptic32: command not found
dchroot: Child exited non-zero.
dchroot: Operation failed.

...which means that synaptic needs to be installed?

Thanks

---

### Post by John Jason Jordan on 2006-01-30
[QUOTE=Cenwio]Yep, i've entered the chroot with sudo chroot /chroot/

I tried the "sudo dchroot -d synaptic32" from an ordinary terminal window but all I got was

(hoary) synaptic32
bash: synaptic32: command not found
dchroot: Child exited non-zero.
dchroot: Operation failed.

...which means that synaptic needs to be installed?[/QUOTE]
I've been using Linux for only about six months, and only as a user. The only problems I know how to fix are the ones I learned about the hard way. :(

But first, are you using Hoary or Breezy?

And second, to get into my chroot environment all I have to do is type "dchroot" from a terminal. I don't even need sudo just to get into the chroot environment. Once I'm inside chroot my terminal becomes a chroot terminal and can do anything within chroot that you can do with a terminal. Theoretically, to launch the Synaptic32 installed within my chroot, once I am inside chroot, all I should need is "sudo synaptic32," but that doesn't work for some reason. So far I know a few command line things, but I have a great deal yet to learn. So I am not able to figure out why it doesn't work. I just launch it from outside chroot with "sudo dchroot -d synaptic32." 

Note that I don't know what the "-d" does either. I just copied that from the command that a local guru gave me. It seems to be necessary, as I made launch items for my chroot applications on the panel Applications menu and I had to enter it for all of them. E.g., the launch item properties for Acrobat Reader 7.0 says "dchroot -d acroread" instead of just "acroread," which is what it would say if it were installed in the 64-bit world.

If I am launching the chroot Synaptic with "sudo dchroot -d synaptic32" then I assumed the executable file must be "synaptic32." But if I try the find command it doesn't show up. I even tried "find *ynap*.* and came up empty. Then I exited chroot to the 64-bit world and tried "find *ynap*.*" again and still got nothing. So I don't know what the filename for the Synaptic executable is. If we knew that you could just search for the executable to find out if it is installed.

Maybe someone else can offer more help.

---

