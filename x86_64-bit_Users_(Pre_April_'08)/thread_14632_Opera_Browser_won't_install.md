---
title: "Opera Browser won't install"
date: 2005-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kamco on 2005-02-08
I am a new Ubuntu user. I have been trying to install the Opera browser but keep getting an error message that  the i386 .deb package is the wrong match for the x86_64.  I thought that I would be able to run 32-bit progams without trouble. I tested on a Mandrake 10.1 64 bit machine  and the .rpm package worked fine there.  I've downloaded both the regular and static versions of the Opera .deb package but I get the same results with either one. Again, I am a newbie, but there must be a simple way to to this. Can anyone give me the correct proceedure?

---

### Post by Avatar on 2005-08-03
[QUOTE=Kamco]I am a new Ubuntu user. I have been trying to install the Opera browser but keep getting an error message that  the i386 .deb package is the wrong match for the x86_64.  I thought that I would be able to run 32-bit progams without trouble. I tested on a Mandrake 10.1 64 bit machine  and the .rpm package worked fine there.  I've downloaded both the regular and static versions of the Opera .deb package but I get the same results with either one. Again, I am a newbie, but there must be a simple way to to this. Can anyone give me the correct proceedure?[/QUOTE]


same problem, did you find any solution?

---

### Post by weird_c00kie on 2006-10-16
it's been a while, so you guys hopefully worked it out, but it may be of use to someone in the future. i got opera to install by downloading the .deb file from the website and then using
> sudo dpkg --force-architecture -i filename.deb on it, after having navigated to the correct directory in the terminal
:)

---

### Post by John Jason Jordan on 2006-10-16
> **weird_c00kie said:**
> it's been a while, so you guys hopefully worked it out, but it may be of use to someone in the future. i got opera to install by downloading the .deb file from the website and then using
 on it, after having navigated to the correct directory in the terminal
:)

The syntax is correct, but you neglected to mention that for 64-bit Dapper you have to download the Other/Static Deb, not the one labeled Ubuntu. Then use the --force-architecture syntax and it installs fine.

---

### Post by kuja on 2006-10-16
> **John Jason Jordan said:**
> The syntax is correct, but you neglected to mention that for 64-bit Dapper you have to download the Other/Static Deb, not the one labeled Ubuntu. Then use the --force-architecture syntax and it installs fine.
The regular deb works fine too. You just need to have ia32-libs-openoffice.org (for 32-bit asound) and ia32-libs-kde (for 32-bit qt) installed to make it work. I find that this looks a bit better.

---

### Post by alek01 on 2007-02-17
Thank you. But where do find that version on the Opera site? I can't find it.
Thansk again for your help.
Alek

---

### Post by Princey on 2007-02-19
> **alek01 said:**
> Thank you. But where do find that version on the Opera site? I can't find it.
Thansk again for your help.
Alek

First, fire up synaptic or Adept whichever you have (Ubuntu uses Synaptic, Kubuntu uses Adept). Do a search for ia32 libs and mark for installation ia32-libs-openoffice.org (for 32-bit asound) and ia32-libs-kde. Click apply changes so that they're installed.

Had over to [http://www.opera.com]("http://www.opera.com") and click "Download Opera for Linux". Chose Ubuntu Edgy in the box of choices and download to your desktop.

Once complete, open the terminal/konsole and type the following: ```
cd desktop
``` This should take you to desktop prompt. Type or copy or paste the following code ```
sudo dpkg --force-architecture -i op
``` and press the **TAB** key on the keyboard. As long as that's the only file with the first two letters op it should complete the rest of the name (it's easier that way as the file name can be long). Press the enter key, input your password when asked for (don't worry if you don't see anything. Just type it away). 

That's it, you're done.  As long as you have java installed already, it should run properly. Just type opera in the terminal window and it should launch it. It should show up in your applications menu under network.

---

