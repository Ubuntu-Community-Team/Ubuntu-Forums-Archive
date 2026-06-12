---
title: "HELP installing ActiveSync under Wine!"
date: 2008-03-10
forum: Wine
---

### Post by djbon2112 on 2008-03-10
I'm trying to get my smartphone (Motorola Q) connected with Ubuntu, and so far nothing has worked at all. Running ActiveSync under WINE is my last hope. I've been reading around and apparently it works for most people, however I can't get it to.

I've tried this with 4.1, 4.2 and 4.5.

After it prompts with the EULA, it says "there is already a version of ActiveSync on your computer" (there isn't), then it tells me to remove it and try the setup again. I just continue, it says it'll replace the existing application, however the install location seems messed (it's given as "\") and it won't let me change it, and when it starts installing it immediately stops with an error.

Here's the terminal output when I run it...
```
joshua@joshua-laptop:~/Desktop$ wine "setup(2).exe"
fixme:advapi:LookupAccountNameW (null) L"joshua" (nil) 0x34f7fc (nil) 0x34f800 0x34f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"joshua" 0x134038 0x34f7fc 0x135270 0x34f800 0x34f7f4 - stub
fixme:wtsapi:WTSQuerySessionInformationA Stub (nil) 0xffffffff 5 0x7e0f122c 0x7e0f1230
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 2 ignored L"Upgrade" table values
err:richedit:ReadStyleSheet ReadStyleSheet: missing style number
err:msi:msi_dialog_maskedit_control mask template is empty
err:msi:ITERATE_Actions Execution halted, action L"CA_AbortSetup" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
```

Anyone have any advice? Please don't bother recommending Synce or anything else instead, I've tried them all and can't get them working with my phone. I'm not so much interested in "syncing" it with anything, as simply having access to the device, being able to transfer files to the root filesystem on the device (no memory card), installing applications, etc.

Little update: 3.0 installs, but it can't detect my device (I think it's just too out of date). I get the same errors as above trying to install >4.1 after installing 3.0, and I also can't seem to remove 3.0.

---

### Post by LoneWolfJack on 2008-03-11
I don't have a real advice for you how to get it running, but judging by the wine output, it doesn't look good.

Also, your first stop for WINE apps should always be the AppDB ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=8980]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8980")),
which in this case will tell you ActiveSync has a garbage rating...

Good luck!

---

### Post by djbon2112 on 2008-03-11
Yea, I've given up on this route, instead now trying to get the Q detected in a VMWare install running Windows XP, which seems to be going a lot better! Thanks though.

---

### Post by prshah on 2008-03-11
> **djbon2112 said:**
> Yea, I've given up on this route, instead now trying to get the Q detected in a VMWare install running Windows XP, which seems to be going a lot better! Thanks though.

This ([http://ubuntuforums.org/archive/index.php/t-521229.html](http://ubuntuforums.org/archive/index.php/t-521229.html)) seems to have worked for somebody... YMMV

Cheers,
PRShah

---

### Post by djbon2112 on 2008-03-11
> **prshah said:**
> This ([http://ubuntuforums.org/archive/index.php/t-521229.html](http://ubuntuforums.org/archive/index.php/t-521229.html)) seems to have worked for somebody... YMMV

Cheers,
PRShah

No, it's useless to me since it can only read an SM card, and I don't have one. Thanks though.

---

### Post by prshah on 2008-03-11
> **djbon2112 said:**
> No, it's useless to me since it can only read an SM card, and I don't have one. Thanks though.

"Basically what it does is makes your Moto Q readable as a flash sd card instead of a smart device. "

Maybe worth another look? [http://ubuntuforums.org/showthread.php?t=521229](http://ubuntuforums.org/showthread.php?t=521229)

Cheers,
PRShah

---

