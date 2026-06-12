---
title: "Ventrilo With Wine GSM 6.10"
date: 2008-01-25
forum: Wine
---

### Post by Derander on 2008-01-25
I know wine & ventrilo has been visited one trillion times, I'm not sure the following issue has (I know I'll be corrected if wrong.)

I've read everything I can find on the internet about my problem.

So here it is:

running wine 9.53, ubuntu 7.10.

Cannot get ventrilo to work with the GSM 6.10 codec using either ALSA or OSS, or any combination of winecfg/ventrilo settings.

I can hear/speak on non-GSM servers.

I've downloaded the msgsm32.acm codec, and copied it from an existing partition to no avail.
I've placed it in ~/.wine/drive_c/windows, drive_c/windows/system, drive_c/windows/system32, drive_c/windows/system32/drivers, also without success.

I have edited the system.ini file to include the proper line:
MSACM.msgsm610=msgsm32.acm

Ventrilo always informs me that it cannot find the codec.

This is my last ditch attempt before I throw in the towel.

---

### Post by Ferrat on 2008-01-26
I'm not 100% but I think you have to put it in the system folder and not system32 folder

EDIT:
nvm saw that you had tried that

EDIT2:
Ahh now I see your problem I think, if you downloaded the msgsm610.acm you got the wrong codec ;) 

you need msgsm32.acm

don't know for sure but you could also try editing 
MSACM.msgsm610=msgsm32.acm
to 
MSACM.msgsm610=msgsm610.acm

and see if that helps?

---

### Post by Derander on 2008-01-26
Thanks for your reply, unfortunately I typoed the name of the codec that I downloaded, it was in fact msgsm32.acm.

:-(

More information for any who care:
```

MPEGVideo2=mciqtz.drv
avivideo=mciavi32.dll
cdaudio=mcicda.dll
sequencer=mciseq.dll
vcr=mcivisca.drv
; videodisc=mcipionr.drv
waveaudio=mciwave.dll
ACM.msgsm610=msgsm32.acm
MSACM.imaadpcm=imaadp32.acm
MSACM.msadpcm=msadp32.acm
MSACM.msgsm610=msgsm32.acm
MSACM.msg711=msg711.acm
MSACM.winemp3=winemp3.acm
vidc.MRLE=msrle32.dll
vidc.MSVC=msvidc32.dll
vidc.CVID=iccvid.dll
; vidc.IV50=ir50_32.dll
; vidc.IV31=ir32_32.dll
; vidc.IV32=ir32_32.dll

```
(the contents of my system.ini

---

### Post by KumoriJinsoku on 2008-02-12
Just found your problem. Your "ACM.msgsm610=msgsm32.acm" should be "**MS**ACM.msgsm610=msgsm32.acm". Hope that helps.

---

### Post by Derander on 2008-02-18
unfortunately I have both lines in there, and I've tried without one or the other. :-/

---

### Post by FrozenFox on 2008-02-19
Some versions of the MSGSM codec for some bizarre reason don't work.

To  make your day easier, please see this thread I made (well, some of it. read the post..) with a script to install ventrilo & text-to-speech for it. Perhaps you will have better luck that way.

[http://ubuntuforums.org/showthread.php?t=686256&highlight=ventrilo](http://ubuntuforums.org/showthread.php?t=686256&highlight=ventrilo)

---

### Post by EXBreder on 2008-08-14
I have had the same problem, and have also tried all of the combinations of the GSM codec placement, along with the .ini file.

I have also tried the above script, but to no avail.

Any help would be greatly appreciated.

---

### Post by MemoryDump on 2008-08-14
can this be setup in a 2 soundcard enviroment? I have 2 cards. 1 for my speakers and 1 for my headset/mic.
will this work with PulseAudio?

thanks
-MD

---

### Post by mrThirteen on 2009-04-08
Thanks for this post.  I had to fix GSM on my Ubuntu install and I just took from this file and tried something.

I went to my windows boot partition and copied the msgsm32.acm file out of the c:\windows\system32 directory and put it in my /home/userdir/.wine/drive_c/windows/system32 folder then edited the /home/userdir/.wine/drive_c/windows/system32/system.ini file and added the line.
MSACM.msgsm610=msgsm32.acm

Shut down Vent restarted and it worked.

Again thanks for this post, I was able to get my system working because of it.

---

### Post by ksaa199 on 2010-01-30
replace msacm.msg711=msg711.acm
with msacm.msg711=msgsm32.acm

replace MSACM.msgsm610=msgsm32.acm
with msacm.msgsm610=msgsm32.acm

seems VT tries to use the msg711 instead of the msgsm610, since you dont have the msg711.acm it didnt work, oughta work now

---

