---
title: "RealPlayer install trouble"
date: 2007-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by boss429 on 2007-03-09
I'm running Ubuntu 64 bit v6.10
When I run the RealPlayer10GOLD.bin I get this error message:
```
Cannot open /home/boss429/Desktop/RealPlayer10GOLD.bin: No application suitable for automatic installation is available for handling this kind of file.
```

when I try to convert the RealPlayerGOLD10.rpm to a deb using alien it fills up the terminal with stuff like this:

```
dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libgcc_s.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libgcc_s (soname 1, path libgcc_s.so.1, dependency field Depends)

```
then finally it says:
```
y libX11 (soname 6, path libX11.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: RealPlayer-10.0.8.805: No such file or directory

```
I'm left with a locked folder called "RealPlayer-10.0.8.805" and no *.deb
this seems to happen every time I run alien on a rpm.

I'm somewhat  new to linux, and I'm sorry if I posted this in the wrong section of the forum.

---

### Post by M$LOL on 2007-03-09
You need to chmod the bin to make it executable.
Type [COLOR="Red"]chmod a+x RealPlayer10GOLD.bin[/COLOR]
followed by [COLOR="Red"]./RealPlayer10GOLD.bin[/COLOR] in Terminal.

---

### Post by boss429 on 2007-03-09
> **M$LOL said:**
> You need to chmod the bin to make it executable.
Type [COLOR="Red"]chmod a+x RealPlayer10GOLD.bin[/COLOR]
followed by [COLOR="Red"]./RealPlayer10GOLD.bin[/COLOR] in Terminal.
Thanks for the reply.
This is weird it says:
```
boss429@ubuntu:~/Desktop$ chmod a+x RealPlayer10GOLD.bin
boss429@ubuntu:~/Desktop$ ./RealPlayer10GOLD.bin
bash: ./RealPlayer10GOLD.bin: No such file or directory

```
why can't it find it when it just did chmod to it?

---

### Post by slowcoach on 2007-03-09
Won't you need the 32bit libraries installing in order to run a 32bit app. ?

---

### Post by boss429 on 2007-03-10
> **slowcoach said:**
> Won't you need the 32bit libraries installing in order to run a 32bit app. ?
I don't know.

Also does anyone know how to fix that error I get with alien?  I can't convert any .rpm files.

---

### Post by M$LOL on 2007-03-11
Dunno, try double clicking the icon maybe?

---

### Post by Kilz on 2007-03-11
> **slowcoach said:**
> Won't you need the 32bit libraries installing in order to run a 32bit app. ?

No, the 64bit version comes with some libraries already, you may need some. But you may not. In any event it will tell you if you if any libraries are needed, not just not se the file.

> **boss429 said:**
> I don't know.

Also does anyone know how to fix that error I get with alien?  I can't convert any .rpm files.
Alien only converts .rpm files to .deb files. That doesnt appear to be what you are doing here.

Right click on the .bin file, select properties. On the permissions tab make sure its executable. Next the command you should be using is

```
sudo ././RealPlayer10GOLD.bin
```

Because you are installing it. If it still cant find the file, try clicking it and select run in terminal.

---

### Post by M$LOL on 2007-03-14
How come it worked for me with just ./RealPlayer10GOLD.bin after chmoding it?

---

### Post by shirsch on 2007-03-17
[QUOTE=boss429;2272110]I'm running Ubuntu 64 bit v6.10
When I run the RealPlayer10GOLD.bin I get this error message:
```
Cannot open /home/boss429/Desktop/RealPlayer10GOLD.bin: No application suitable for automatic installation is available for handling this kind of file.
```

[CODE]dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)

This is trying to tell you that you don't have the 32-bit runtime library support to execute the installer.  Fire up Synaptic, search on **32 libs** and install everything that refers to 32 bit library support (probably don't need any dev packages).  After doing so, you should be able to execute RealPlayer10GOLD.bin without incident.

---

### Post by boss429 on 2007-03-19
> **shirsch said:**
> [QUOTE=boss429;2272110]I'm running Ubuntu 64 bit v6.10
When I run the RealPlayer10GOLD.bin I get this error message:
```
Cannot open /home/boss429/Desktop/RealPlayer10GOLD.bin: No application suitable for automatic installation is available for handling this kind of file.
```

[CODE]dpkg-shlibdeps: warning: unable to find dependency information for shared library libm (soname 6, path libm.so.6, dependency field Depends)

This is trying to tell you that you don't have the 32-bit runtime library support to execute the installer.  Fire up Synaptic, search on **32 libs** and install everything that refers to 32 bit library support (probably don't need any dev packages).  After doing so, you should be able to execute RealPlayer10GOLD.bin without incident.
Thanks! it works now.
RealPlayer didn't seem to install the plugins for firefox though, do I need to use 32 bit Firefox?

---

### Post by M$LOL on 2007-03-19
Definitely use 32 bit FF. I haven't tried the plugins in it myself though. I imagine they should work if they were made for 32b FF.

---

### Post by chunchengch on 2007-05-02
I downloaded RealPlayer10GOLD.bin, and then installed it under /usr/bin/RealPlayer with commands :

sudo chmod a+x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

after that, I find RealPlayer10 in the tray application>audio,
but, when I click the icon, nothing happens, what is wrong?:confused: 

need help ..........

---

