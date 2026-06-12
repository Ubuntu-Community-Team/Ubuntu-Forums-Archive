---
title: "Command &amp; Conquer 3 run problems"
date: 2008-01-01
forum: Wine
---

### Post by at0myx on 2008-01-01
Hello, I was trying to run Command & Conquer 3: Tiberium Wars through Wine and was having trouble.

I installed it, dropped in the right DLLs according to the Wine website, applied a patch, and put in a no-cd crack.

At first when I would try to run it, it would give me some security module missing error.  After looking in the Wine comments and bugs, I added the registry key:HKEY_LOCAL_MACHINE\System\MountedDevices 

because the error seemed similar to mine.  Well, the security module error didn't pop up but the splash screen just hangs and the game never opens.

Can anyone help me with this?

P.S.  One thing I am not sure I did right is that the website said to kill all desktop managers.  I didn't know what that meant so I just disabled all desktop effects and killed the compiz process.

---

### Post by at0myx on 2008-01-02
No help for C&C3?

---

### Post by cameran on 2008-01-02
i'm betting your problem stems from the crack.  remove the game and reinstall it and don't apply a crack, but enter the MountedDevices fix and leave your dvd in the drive.   

i have the game running fine on wine without a crack using the 0.9.49 cursor patch since 0.9.51 & 52 don't display my cursor.

i did try a crack for the game after i first installed it and patched and it caused me problems.

cameran

---

### Post by at0myx on 2008-01-02
Eh, if that's the case it probably won't work since this is a copy of my brother's disc. Oh well, I guess I will have to either stick to xbox or dual boot.

---

### Post by yowshi on 2008-02-21
what friggin cursor patch is this. where are these supposed lists of dll's to drop and where do i drop them... i cant find any of this on the CnC 3 page on the winehq site


for the record i am geting a fatal error string manager not loading error. i cant even install the 1.9 patch because it gives me the same error. i installed it from a dvd image moutned using the mount command in the cli


update. i got the latest wine update and not getting the string error anymore. now i am getting a no aspi layer found error. alright managed to get all that running with the nocd crack and patches installed yayme. now i cant register for an online account though

---

