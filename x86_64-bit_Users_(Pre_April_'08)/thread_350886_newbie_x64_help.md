---
title: "newbie x64 help"
date: 2007-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by rftserv on 2007-02-01
Please help! I'm a newbie who is enjoying something different. However, there are two things that i need ubuntu to do, and i can't! do it. I have 2.6.15-27-amd64. 
Firstly, what name is given to this version?
I want to load a flashplayer, but having followed several sets of instructions, still cant get to work.....version unsupported etc......
I also want to rip cds into mp3 or wma format and download to mp3 players. When i try easyubuntu, loads most files, but not audio codecs.
Is there a simple way to sort this?

---

### Post by pseudonym on 2007-02-01
> **rftserv said:**
> I have 2.6.15-27-amd64. 
Firstly, what name is given to this version?
That would be Ubuntu Dapper.

> **rftserv said:**
> I want to load a flashplayer, but having followed several sets of instructions, still cant get to work.....version unsupported etc......
Best way I find is to run 32-bit Firefox at the present time. The 'official' howto for that is [here]("http://www.ubuntuforums.org/showthread.php?t=202537").

> **rftserv said:**
> I also want to rip cds into mp3 or wma format and download to mp3 players. When i try easyubuntu, loads most files, but not audio codecs.
Is there a simple way to sort this?
Never used easyubuntu, so can't help there. To set up mp3 playback manually, see [this section]("https://help.ubuntu.com/community/RestrictedFormats/MP3") of the [Ubuntu Restricted Formats wiki]("https://help.ubuntu.com/community/RestrictedFormats"). There is also information there about every other multimedia task, including CD ripping. For this task, I would also recommend Grip as your ripping tool. It's got more features than the default Sound Juicer.

---

### Post by rftserv on 2007-02-01
thanks for your help - i'll give it a go!!

---

### Post by rftserv on 2007-02-02
Got stuck straight away! i need to install the "browser install script".If i click on the link, i download a tar file...what do i do with it then to run the script....please be patient - i'm sure this is very elementary!!
P.s I guess i do not need to install firefox 2, ice weasel and flock just to get the flashplayer going, do i?

---

### Post by pseudonym on 2007-02-02
> **rftserv said:**
> Got stuck straight away! i need to install the "browser install script".If i click on the link, i download a tar file...what do i do with it then to run the script....
First open up the .tar file with File Roller, the GNOME archive utility (it's like Winzip). You should be able to do this by double-clicking on the file in the Nautilus file browser.

Further instructions are in the readme contained in the .tar file. I quote from it here (by now, you've already done the first step) -

'Extract the browser + base-plugins.tar.gz to your desktop. 
It will create a base-plugins folder. Open the folder.
Inside you will find a base-plugins file

Doubble click on the base plugins file. Select "Run In Terminal"

Answer the simple questions.

You will have to agree to the flash and java license.

The installer will setup everything including a menu enrty.
 It will also delete the ffinstall folder when its done.

The rest of the plugins can be installed by 
following this howto. If you need any help 
please post on the howto thread.
http://www.ubuntuforums.org/showthread.php?p=1174435'

[The author means the howto where you downloaded the .tar file from - the one I linked to in my first post.]

> **rftserv said:**
> P.s I guess i do not need to install firefox 2, ice weasel and flock just to get the flashplayer going, do i?

No, when you run the script you get to choose which browser you want. Choose only one.

HTH

---

