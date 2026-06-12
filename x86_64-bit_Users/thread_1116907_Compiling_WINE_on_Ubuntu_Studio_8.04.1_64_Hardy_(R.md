---
title: "Compiling WINE on Ubuntu Studio 8.04.1 64 Hardy (RT)"
date: 2009-04-05
forum: x86 64-bit Users
---

### Post by teddyk on 2009-04-05
Hi,

I've been trying to compile WINE on Ubuntu Studio Hardy 8.04.1 (RT), 64-bit.

I have created all of the links as described at [http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit"), yet ./configure still won't find any of the IA32 libraries I just linked. Also does not find other weird significant libraries such as OpenGL in general.

I've done apt-get build-dep wine, and also tried to reinstall any applicable libraries to no avail.

The binary packages available work just fine, however I need to compile my own version for a serious bug fix to run Everquest Titanium on emulated servers.

I'm also a total linux noob, so sorry if the answer is glaring. 

Here is the error text I am getting from using "CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v":

> 
configure: libxcursor 32-bit development files not found, the Xcursor extension won't be supported.
configure: libxi 32-bit development files not found, the Xinput extension won't be supported.
configure: XShm 32-bit development files not found, X Shared Memory won't be supported.
configure: XShape 32-bit development files not found, XShape won't be supported.
configure: libXxf86vm 32-bit development files not found, XFree86 Vidmode won't be supported.
configure: libxrandr 32-bit development files not found, XRandr won't be supported.
configure: libxinerama 32-bit development files not found, multi-monitor setups won't be supported.
configure: libxcomposite 32-bit development files not found, Xcomposite won't be supported.
configure: libGLU 32-bit development files not found, GLU won't be supported.
configure: libhal 32-bit development files not found, no dynamic device support.
configure: libgnutls 32-bit development files not found, no schannel support.
configure: libsane 32-bit development files not found, scanners won't be supported.
configure: libgphoto2 32-bit development files not found, digital cameras won't be supported.
configure: liblcms 32-bit development files not found, Color Management won't be supported.
configure: libcapi20 32-bit development files not found, ISDN won't be supported.
configure: libcups 32-bit development files not found, CUPS won't be supported.
configure: fontconfig 32-bit development files not found, fontconfig won't be supported.
configure: libldap (OpenLDAP) 32-bit development files not found, LDAP won't be supported.

configure: WARNING: libxrender 32-bit development files not found, XRender won't be supported.

configure: WARNING: No OpenGL library found on this system.
OpenGL and Direct3D won't be supported.

configure: WARNING: libxml2 32-bit development files not found, XML won't be supported.

configure: WARNING: libxslt 32-bit development files not found, xslt won't be supported.

configure: WARNING: OpenSSL 32-bit development files not found, SSL won't be supported.

configure: WARNING: libjpeg 32-bit development files not found, JPEG won't be supported.

configure: WARNING: libpng 32-bit development files not found, PNG won't be supported.



It's weird because most of those libraries are the libraries I explicitly made those links to as per the WINE guide, right?

So where am I going wrong here?

Thanks!

Teddy

---

### Post by 3Miro on 2009-04-05
Are you using AMD64 or ia64 (what kind of CPU do you have)?

To run 32-bit windows program under 64-bit Linux, you do not need wine 64-bit, just install the wine version from the repos and/or add the winehq repo: [http://www.winehq.org/download/](http://www.winehq.org/download/). Wine 64-bit is only needed to run 64-bit windows programs.

It seems that you are trying to compile the 32-bit version of wine (-m32 option), why do you need to compile it? Just use the one from the repos.

---

### Post by teddyk on 2009-04-05
> **teddyk said:**
> The binary packages available work just fine, however I need to compile my own version for a serious bug fix to run Everquest Titanium on emulated servers.

I need to add a bug fix otherwise player models won't display. Have tried Cedega but it won't launch and I'd much rather run WINE (also other players have said WINE works best).

I have an Intel chip.

---

### Post by 3Miro on 2009-04-05
AMD64 refer to the format for AMD Athlon64 and Phenom CPUs as well as Intel Core 2 Duo/Quad and some of the older Pentium 4/D (definitely not all of them). As far as I know, ia64 refers to the Intel alpha processors, I don't think you have one do you?

To install a bugfix, I think you need git, which is much easier way to compile the thing. 

[http://wiki.winehq.org/RegressionTesting](http://wiki.winehq.org/RegressionTesting)

The article above is for Regression Test, but it includes instructions on how to compile wine in general. I think you can use git to "install" the bigfix and then recompile (don't have to do the regression test). I have done that on my machine and it worked following the instructions.

---

### Post by 3Miro on 2009-04-05
Look at the bottom of the link for adding a "patch" to git.

---

### Post by stchman on 2009-04-06
No need to compile WINE, it is available in the repos or WINE has their own repos.

---

