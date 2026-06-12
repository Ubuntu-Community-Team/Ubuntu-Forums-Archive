---
title: "IEs4Linux and wine on x64 7.04. Both installed properly, but IEs4Linux won't open."
date: 2007-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tim T on 2007-04-24
I just did a fresh install for 7.04 x64 ubuntu and desperately need IEs4Linux to work. I did some searching and found out how to install wine. that installed fine. I also installed IEs4Linux which installed without a hitch. Upon opening it, however, I get this:

john@Linux:~$ ie6
fixme:actctx:CreateActCtxW 0x33fa80 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x33f848
fixme:actctx:DeactivateActCtx 00000000 00f00bad
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
fixme:actctx:ReleaseActCtx 0xf00baa
john@Linux:~$ 


I'm hoping theres a simple fix, but since i'm still wet behind the ears in terms of linux, I'm not entirely sure where to start. Ideas?

---

### Post by Enverex on 2007-04-25
When you compiled Wine your OpenGL headers and/or XOrg development files were missing so Wine has been built without support for any sort of X connection or rendering (read: you wont be able to see anything so it will fail).

---

### Post by Tim T on 2007-04-25
Well that's no fun! So are you suggesting I reinstall wine?

---

### Post by Kilz on 2007-04-26
> **Tim T said:**
> Well that's no fun! So are you suggesting I reinstall wine?

How did you install wine?

---

### Post by Tim T on 2007-04-26
A script I had found for x64 users on this forum. Let me see if I can find it...

Edit: only took a sec. It's post #3 found here: [http://ubuntuforums.org/showthread.php?t=330336&highlight=wine+on+x64](http://ubuntuforums.org/showthread.php?t=330336&highlight=wine+on+x64)

---

### Post by Enverex on 2007-04-26
> **Tim T said:**
> A script I had found for x64 users on this forum. Let me see if I can find it...

Edit: only took a sec. It's post #3 found here: [http://ubuntuforums.org/showthread.php?t=330336&highlight=wine+on+x64](http://ubuntuforums.org/showthread.php?t=330336&highlight=wine+on+x64)

No, that script is fine as it basically just does the default things required to build Wine on a 64bit Ubuntu system (although the version of Wine it downloads is rather old).

The things that I'm talking about being unsupported are anything that alters the original Wine source to install or that installs extra things inside Wine after it's been installed.

---

### Post by Tim T on 2007-04-26
> **Enverex said:**
> No, that script is fine as it basically just does the default things required to build Wine on a 64bit Ubuntu system (although the version of Wine it downloads is rather old).

The things that I'm talking about being unsupported are anything that alters the original Wine source to install or that installs extra things inside Wine after it's been installed.

Good on the script then... however i'm not following you. I'm on a newly installed os, and have downloaded all the latest updates. IEs4Linux is the first app i'm trying to install for wine. does that help at all?

---

### Post by Enverex on 2007-04-26
> **Tim T said:**
> Good on the script then... however i'm not following you. I'm on a newly installed os, and have downloaded all the latest updates. IEs4Linux is the first app i'm trying to install for wine. does that help at all?

Sure if you want to use IE, but that's a modified version of Wine, so with that installed you can't report any bugs to Wine or comment/submit testing data on the AppDB. IEs4Linux isn't an app you install in Wine though, it itself is a modified version of Wine.

---

### Post by Kilz on 2007-04-26
> **Tim T said:**
> Good on the script then... however i'm not following you. I'm on a newly installed os, and have downloaded all the latest updates. IEs4Linux is the first app i'm trying to install for wine. does that help at all?

If your not interested in reporting bugs to wine or making entries to the wine app database, but just want ies4linux (and other applications) to work. You can use the setup script in my signature.

---

### Post by Tim T on 2007-04-27
> **Kilz said:**
> If your not interested in reporting bugs to wine or making entries to the wine app database, but just want ies4linux (and other applications) to work. You can use the setup script in my signature.

Will your script install over the current version of wine? Will I need to remove the old version of wine i have installed via the old script?

---

### Post by Kilz on 2007-04-27
> **Tim T said:**
> Will your script install over the current version of wine? Will I need to remove the old version of wine i have installed via the old script?

Yes it will install the current version of wine 9.35, it should also overwrite the files you installed.

---

### Post by Tim T on 2007-04-28
THANK YOU! I have my math finals online this week and desperately needed IE to work, and the combo of reinstalling wine and ie fixed it!

---

