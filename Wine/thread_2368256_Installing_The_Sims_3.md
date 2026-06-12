---
title: "Installing The Sims 3"
date: 2017-08-08
forum: Wine
---

### Post by apol1 on 2017-08-08
Hello Im trying out wine to install the Sims 3 from a PC disk, Ive followed any instructions Ive found online but the app still won't launch. Would anyone be willing to help me trouble shoot? Thx :)

---

### Post by lisati on 2017-08-08
I don't know if the advice given [here]("https://ubuntuforums.org/showthread.php?t=2243117") will help (it's for Sims 4) but it might be worth checking out.

My own experience with the Sims is with the original Sims, running natively on Windows, several years ago. If I remember correctly, it required me to keep the disk in the CD/DVD drive.

---

### Post by apol1 on 2017-08-09
Thx I went and checked it out, I got a bit more info but I still seem to be running into the same problem, Ive come across essentially the same instructions over and over, but each time i follow them the Sims simply won't launch, I have an icon and the download manager installed but nothing. Come to think of it I doubt Ive ever gotten Wine to work properly in any case.

Ive tried this video tutorial

[https://www.youtube.com/watch?v=1me6ebGWKEo](https://www.youtube.com/watch?v=1me6ebGWKEo)

Then tried to install the sims 3, at the very end of the install i this error message

The Program ISBEW64.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience 

This can be caused by a problem or a deficiency in wine.

Next I tried this tutorial

[http://www.wikihow.com/Install-Wine-on-Ubuntu](http://www.wikihow.com/Install-Wine-on-Ubuntu)

and at step 5 I got this in terminal

```
 winecfg
err:winedevice:ServiceMain driver L"WineBus" failed to load
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:iphlpapi:NotifyAddrChange (Handle 0x103e368, overlapped 0x103e380): stub
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:iphlpapi:NotifyAddrChange (Handle 0x10fe8a0, overlapped 0x10fe8ac): stub
wine: configuration in '/home/user/.wine' has been updated. 
```

Thats all I got for the moment, I'll look more into it in the morning, in the meantime anyone with any info please let me know what you think of this. Thx in advance :)

---

### Post by sccman on 2017-08-11
That would be a good start.

Try fixing those err's. If that doesn't work, feel free to let us know :D

---

### Post by apol1 on 2017-08-24
Alright I got it, it looks like I had some ghost files hidden in the background, no more errors! I next made a new attempt to install the Sims 3 I clicked on the desktop shortcut, the launching animation started then it stopped, Im guessing it crashed. I next tried PlayOnLinux since I had some nasty errors on there before. I got the following message

PlayOnLinux has encountered an error. If the program does not work correctly, it might be the cause of the problem.

Error in main
Sims3Launcher crashed.
Select its shortcut and click on "Debug" in the side panel to get more details.

I clicked on debug and got a huge document, Id attach for everyone to see it but I can't seem to get anything uploaded.

Any thoughts? Thx :)

---

