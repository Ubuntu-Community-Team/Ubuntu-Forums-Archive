---
title: "OpenDX 4.4.0 on Edgy, VPE issue"
date: 2006-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by bed on 2006-10-27
I recently installed ubuntu 6.10 (Edgy) as well as OpenDX 4.4.0 (from unbuntu repository). The software seems to work properly, I mean you can start it and run programs (.net files). Unfortunately, the Visual Program Editor (VPE) has a display issue, the page tabs appears but are vertically elongated and covers all the window, and there is no area to insert interactors to build a program.

Here a screenshot of the problematic VPE:

[ATTACH]18343[/ATTACH]

When I run dx from a script I get this error:

[INDENT]Starting DX user interface
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
Major opcode of failed request:  14 (X_GetGeometry)
  Minor opcode of failed request:  0
  Resource id in failed request:  0x2
  Serial number of failed request:  436
  X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
Major opcode of failed request:  14 (X_GetGeometry)
  Minor opcode of failed request:  0
  Resource id in failed request:  0x2
  Serial number of failed request:  3002[/INDENT]


- The software was working correctly in Dapper (OpenDX 4.3.2).
- I tried to install OpenDX(4.4.4, 4.4.0,and 4.3.2) manually and I got the same issue in Edgy
- I have AMD64 architecture with ubuntu ATI drivers

If anyone as an idea of what is going on.

Thank you

---

### Post by jorgeinglessis on 2006-10-31
I have exactly the same problem with the dx-4.4.0 for the repository, I have a amd64 distribution too and I'm using a nvidia card.
I'm trying to compile the 4.4.4 version from the source buy I get this error:

memory.c:69:23: error: linux/sys.h: No such file or directory

---

### Post by bed on 2006-10-31
When I was compiling openDX 4.4.4 I got the same problem,

jorgeinglessis said,
> memory.c:69:23: error: linux/sys.h: No such file or directory

I solved this issue by doing a symbolic link,
```
sudo ln -s /usr/src/linux-headers-2.6.17-10/include/linux/sys.h /usr/include/linux/sys.h 
```

You will need the header source of your kernel.

---

### Post by Gominolas on 2007-04-26
bed said,
>  Unfortunately, the Visual Program Editor (VPE) has a display issue, the page tabs appears but are vertically elongated and covers all the window, and there is no area to insert interactors to build a program.


Hello.

I have recently installed kubuntu feisty fawn AMD64 version and I'm facing the same problem. Moreover, I could check that kubuntu edgy 64 behaves in the same way.

OpenDX version: 4.4.0
Graphic card: ATI

Any help welcomed.  
Thanks

---

### Post by jinzishuai on 2007-05-13
I have the same problem on a Kubuntu Fesity also.
I  tried to apt-get install dx for  the 4.4.0 version and compiling the source for 4.4.4.
Same problem with VPE in both cases.
I had the same sys.h error in compilation. I simply commented out that line and it compiles.

I would appreciate a note if you figure it out.
Thanks.

Shi

---

### Post by bed on 2007-05-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/dx/+bug/110404](https://bugs.launchpad.net/ubuntu/+source/dx/+bug/110404) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Here a temporarly solution to this VPE issue:

From this [**post**]("https://bugs.launchpad.net/ubuntu/+source/dx/+bug/110404")  where this VPE issue was reported as a bug. Someone proposed to rebuild the dx package from source without optimization. In other word the compilers flags in all makefiles have to be set to "-O0" instead of "-O2".

For me, it worked with the source of OpenDx 4.4.4, ATI card, and Edgy.

Thanks and hope this issue will eventually be fixed.

---

### Post by jinzishuai on 2007-05-30
Great. This works for me.
Here is what I did:
CXXFLAGS="-O0" FFLAGS="-O0" CFLAGS="-O0" ./configure

---

### Post by aev on 2008-03-27
Same problem on Gutsy, AMD 64 dual core, Nvidia drivers.:confused:

---

### Post by aev on 2008-04-02
I compiled OpenDx-4.4.4 on Gutsy64 with the suggested flags from the above posts and still get the same VPE error.:(:confused:

---

### Post by msrinath80 on 2008-07-10
Just a heads up for those wishing to build dx 4.4.4 from source. In addition to the -O0 switch for CFLAGS, CXXFLAGS and FFLAGS and the symbolic link for sys.h, one needs to make some more modifications in the source code to get dx to build successfully with Gcc 4.3.x. The suggested changes are indicated here ([http://www.mail-archive.com/opendx2-dev@lists.berlios.de/msg04634.html](http://www.mail-archive.com/opendx2-dev@lists.berlios.de/msg04634.html))

Apparently, this helps get rid of the following error message:

Main.C:52: error: first argument of &#8216;int main(unsigned int, char**)&#8217; should be &#8216;int&#8217;

If anyone needs help applying the fixes shown on the above webpage, just holler.

---

