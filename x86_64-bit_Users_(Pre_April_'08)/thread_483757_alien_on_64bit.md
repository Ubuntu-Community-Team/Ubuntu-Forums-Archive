---
title: "alien on 64bit"
date: 2007-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by kzm. on 2007-06-25
i was fooling around with some rpm packages and alien. i notice i get the same error:
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)

is there a workaround this?

---

### Post by Lapino on 2007-06-25
I've had this problem too, and only thing I could think of to solve it is using a chrooted 32-bit environment.

---

### Post by roystonvasey on 2007-09-09
> **Lapino said:**
> I've had this problem too, and only thing I could think of to solve it is using a chrooted 32-bit environment.

I've got this issue too. how do what you describe here? how do you make a 32-bit environment? thanks!

---

### Post by Kilz on 2007-09-09
> **kzm. said:**
> i was fooling around with some rpm packages and alien. i notice i get the same error:
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)

is there a workaround this?

The problem is you are trying to convert a 32bit or i386 package and with 64bit alien that inly makes 64bit debs. In other words you cant use alien to make a 32bit rpm into a 64bit deb. You could do it if you have a 64bit rpm.

> **Lapino said:**
> I've had this problem too, and only thing I could think of to solve it is using a chrooted 32-bit environment.
You could always just compile the application instead of using alien. Chroots are more trouble than they are worth and difficult to install.

---

### Post by paetyndog on 2008-02-07
*Still learning this stuff ...*

Dunno how you installed it, but if you used Wubi, it seems the Wubi installer incorrectly detected my system as 64 bit hardware cuz it tries to download the AMD64 ISO image. Even though its not 64 bit, the ubuntu  install went OK on and actually came up and was functional - even detected and configured my wireless card flawlessly !!! 

However, I had some issues with some important (required for my VPN to work) RPM packages I was converting to .deb using alien - messages like
[FONT="Fixedsys"]dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)[/FONT]

I stumbled across and appended this same reply to  [this thread]("http://ubuntuforums.org/showthread.php?p=4286552") and have since launched the Wubi-7.10-alpha-rev386.exe with the **--32bit**  option - 
Right now its downloading the corrected ubuntu-7.10-desktop-i386.iso image. 

I'll update this post with my results on running alien on the corrected kernel architecture

---

### Post by Kilz on 2008-02-07
You have 64bit hardware if the 64bit version installed and started. It would not install or start if you didnt have 64bit hardware. It was not incorrectly chosen, you are making the choice now to install a operating system not specifically designed for your 64bit hardware.

---

### Post by Yellow Pasque on 2008-02-07
> **Kilz said:**
> You could always just compile the application instead of using alien. Chroots are more trouble than they are worth and difficult to install.
+1 to this. Chroots aren't too bad (though I wouldn't recommend them to beginners), and should only be used if the source can't be built for 64-bit for some reason.

If you need help building something, try posting in this forum. Though it may not happen instantly, someone should either be able to give you instructions to build yourself or build you a .deb. That's what we're here for.

So the question is: What rpm are you trying to convert?

---

