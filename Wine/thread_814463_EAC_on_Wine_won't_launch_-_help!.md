---
title: "EAC on Wine won't launch - help!"
date: 2008-05-31
forum: Wine
---

### Post by logos34 on 2008-05-31
I can no longer launch Exact Audio Copy--all I get is this error message:

> Unhandled exception

at WndProcs.741 ->INDEX-RANGE

How do I clear it?

EAC on wine in ubuntu has worked fine for me at least since Feisty.  Now all of sudden it won't even start, and on the rare occasion it does start it refuses to recognize my cdrom drive (nor does Cdex), no matter what I do in Winecfg.  My other win apps that do not rely on cdrom drive appear to work normal.

It worked thru the update to Hardy (actually fresh install in my case, but I have a separate /home).  So something in the recent updates appear to have caused a conflict.

I tried reinstalling, deleting ~/.wine each time just to make sure, even reinstalled EAC.  

Does anyone have ANY idea what happened?  I've tried the EAC forums, but not much help over there.

Oh, and I got it to work briefly with wine 1.0-rc1, but celebrated too soon because it died after that.  I've tried a half dozen older versions, but none of them help now

---

### Post by logos34 on 2008-06-01
bump.  Any Exact Audio Copy experts out there?

---

### Post by mc4man on 2008-06-04
Finally got it working on hardy, though to early to say if it's gonna stick (as you've seen). Will have to backtrack tomorrow as to whether it was some dll overrides and or additions to system 32 or changing audio to esound d
What's interesting is with alsa I've always seen this from terminal (even in gutsy where_ eac works perfectly_)

```
wine '/home/doug/.wine/drive_c/Program Files/Exact Audio Copy/EAC.exe'
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg2: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 3.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg3: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 4.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg4: Permission denied

``` 
Now after change to esd (and working good in hardy 2 tries)

```
doug@doug-desktop:~$ wine '/home/doug/.wine/drive_c/Program Files/Exact Audio Copy/EAC.exe'
```
note no errors
The caveat is reverted to 0.9.56, disabled playback with alt. means and some other hopefully irrelevant things
_So bears more testing_

OT: posted best solution to dvd drive issue if you haven't ck'ed or fixed to your satisfaction. i never had issue with eac finding drive(s) and loading tracks, it would just always (except for _once)_ crash on extraction. Maybe with your drive links fixed ?

---

### Post by logos34 on 2008-06-04
Thanks for the response!

I want to believe this is a drive detect issue, but it may be related to sound as in your case.  B**ut I can't even get EAC to launch anymore**, whereas CDex now detects the cdrom drive fine.  Also, I'm on 64-bit ubuntu, so maybe it's something related to that (but it worked fine previously on x64 gutsy).  I've tried the reversions (even .56 or was it .57) to no avail.

---

### Post by mc4man on 2008-06-04
I'm starting to think it's an individual thing - on a 2nd machine with the same kernel, wine ver. system32, settings ect. atm no good, actually got to same error condition you described.(wouldn't detect drives). Resolved that by setting up separate profile for eac, but atm still crashes on extraction. Meanwhile on other box all is well.
Hardy seems to have some flaky behavior, ie. frustrating

---

### Post by logos34 on 2008-06-04
> **mc4man said:**
> Hardy seems to have some flaky behavior, ie. frustrating

got that right.

In general I'm pretty nonplussed by 8.04.  Certain things just shouldn't be happening (and to think this is an LTS release!)

If this had happened with just about any other app I could easily shrug it off.  But no, it has to be EAC, my favorite windows-only app.  I could live with Rubyripper I guess, but even that won't work (another story). 

EAC in the latest x86 Mandriva with wine 1.0-rc1 works fine.  I guess I'll just have to boot into that when I want a secure rip.

---

### Post by mc4man on 2008-06-04
Fixed on 2nd box
Again not 100% sure ie. did prior actions though unsuccessful contribute in a cumulative effect ?
now that it works on tester can work backwards, don't want to breath too hard on main box.
The final piece this time again was the sound, though i didn't notice that enabling esd didn't disable alsa - once I did that it worked.
Am using in separate profile with custom system32 and 4 dll overrides, will start fresh with default everything then 1 at a time
if you can get it to start, detect drives maybe any info from above will help, maybe not (64 vs. 32 bit ?)

---

