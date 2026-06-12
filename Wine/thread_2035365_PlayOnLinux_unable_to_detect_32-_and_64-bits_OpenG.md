---
title: "PlayOnLinux unable to detect 32- and 64-bits OpenGL libraries; Steam immediate crash"
date: 2012-07-30
forum: Wine
---

### Post by Breadified on 2012-07-30
First off, hello and thank you in advance to any and all who reply! I've been raised with Windows, and after running Ubuntu in Wubi for a little while I switched over just this morning to Precise Pangolin.

A big thing for me was still being able to use Steam, which I was able to do in the Wubi installation. When I installed it using PlayOnLinux today though, I noticed that as well as being unable to initiate Steam, POL reports that it cannot locate the 32- and 64-bits OpenGL libraries when I start it up - which I guess might be causing the problem?

To be honest, I am not tech savvy but I'd like to be. Here's the most recent log from Steam crashing.

[07/30/12 18:27:03] - Running wine-1.4.1 Steam.exe (Working directory : /home/scott/.PlayOnLinux/wineprefix/Steam/drive_c/Program Files/Steam)
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directoryfixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005160, 0x3f036b20, 0x3f036b18
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005160, 0x3f036b58, 0x3f036b50
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005160, 0x3f036ae8, 0x3f036ae0
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005160, 0x3f036b90, 0x3f036b88
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005160, 0x3f036bc8, 0x3f036bc0
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  1197
  Current serial number in output stream:  1197

Thanks again for any help!

Breadified.

---

### Post by Toz on 2012-07-30
Hello and welcome to the forums.
I'm going to move this thread to the Wine forum for better visibility.

Are you running the 64-bit version of ubuntu and if so, have you installed the ia32-libs package?

---

### Post by cwwilson721 on 2012-07-30
You need to install your proprietary drivers for your videocard/chip, under "System Settings > Additional Drivers"

---

### Post by Breadified on 2012-07-31
Hi guys, thanks for your fast replies! The legendary customer support from the Ubuntu community strikes again, I see.

@Toz: Yes I installed the ia32-libs package and I am running 64-bit Ubuntu.

@cwwilson721: I've been trying to install the "ATI/AMD proprietary FGLRX graphics driver (post-release updates)" but I keep getting an error when I try to. A little searching on-line told me this was a widespread problem. Any hints?

---

### Post by Toz on 2012-07-31
Try installing the other set of drivers - not the "post-release" ones.

---

### Post by Breadified on 2012-07-31
Have just done so and restarted my system, met with the same notifications on POL regarding the OpenGL libraries. Also just tried Steam - same crash error.

---

### Post by cwwilson721 on 2012-07-31
Read the sticky's on the top of this forum, and let us know what hardware you have.

---

### Post by Breadified on 2012-07-31
Alright, here we go.

Lenovo G770
Intel i5 2430M 2.4GHz processor
8GB RAM
AMD 6650 2GB (running the proprietary driver w/o updates as recommended)

Running Ubuntu 12.04 LTS with all updates that came up after install, also ia32-libs is installed as Toz mentioned. PlayOnLinux 4.1.3, Wine 1.4.

Sorry if I missed anything, just let me know.

---

### Post by Breadified on 2012-08-03
As an aside, I tried installing the Linux Catalyst drivers from support.amd.com and have had no luck installing after a few tries. If it's appropriate, I can provide the error message on request (didn't take a note of it at the time, but will re-run it if it's relevant).

---

### Post by Breadified on 2012-08-05
Okay, so I repeatedly purged and installed POL, eventually deciding to  delete the file "/etc/apt/sources.list.d/playonlinux.list" (although I am pretty sure the word old was in there somewhere) as I was getting errors when using "apt-get update" to do with this file. This seems to have rectified the problem with the request for 32- and 64-bits OpenGL libraries.

So now the issue only remains with Steam crashing. I have activated debugger but cannot find a way of copying and pasting the log...sending to pastebin.com does not work (even after installing curl) because it tells me the API is outdated. Is there any simple way to post the debug log to here rather than typing it out manually?

Thanks,
Breadified.

---

### Post by Breadified on 2012-08-05
Attached is the log from when Steam crashes running through POL. Any help would be appreciated.

Cheers,
Breadified.

---

### Post by Breadified on 2012-08-09
Still having this problem with Steam crashing. Anyone out there who has any ideas?

---

### Post by Toz on 2012-08-09
What does the following return:
```
glxinfo | grep -i render
```

Did you install Steam using the HowTo from this page: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444&iTestingId=72339]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444&iTestingId=72339")

---

### Post by Breadified on 2012-08-09
That command returns the following -

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

- and I installed it using those instructions prior to running that command (and of course testing once more). After this I also updated POL to the latest version, which has resulted in the previous 32- and 64-bits errors coming back.

---

### Post by Breadified on 2012-08-09
Also, the command-

```
fglrxinfo
```-returns the exact same error too. However, when using-

```
sudo apt-get install fglrx fglrx-amdcccle
```-as advised by [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide) returns that my driver is already the latest version. Should I try purging the driver install and reinstalling?

EDIT: Never mind the question at the end. I did that previously and it didn't help any. Also, I have of course rebooted my computer before running the commands (and after, before running them again just to make sure my memory wasn't off).

---

### Post by Breadified on 2012-08-09
Okay...I believe the issue may be solved. I purged POL and used Winetricks to install Steam as advised above. Using the forum above I "purged" the driver from my system following the "Removing the driver" section. After doing so, I tried again to run Steam and it worked without any errors (of course, not through POL - through Winetricks). Now installing "Civilization V" and am yet to come up against any errors. I am a very happy man!

Summary: it appears using Winetricks and NOT using the proprietary Catalyst drivers (at least on my system) solves the issues of crashes and missing OpenGL libraries.

Thanks for your help, folks. I'll report back if I come up against any more errors or interesting nuances.

EDIT 2: [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers) is an incredibly useful page for the installation of the proprietary drivers. I found the "Alternative method" the most helpful.

---

