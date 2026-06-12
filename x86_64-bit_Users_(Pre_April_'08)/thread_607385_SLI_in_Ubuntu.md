---
title: "SLI in Ubuntu?"
date: 2007-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by steeviee on 2007-11-08
I was reading some posts on the SLI forum and noticed other fellow linux configuring SLI to work with their flavors of linux, and I was wondering if Ubuntu is SLI capable in Gutsy?
I am running x64 Gutsy with two nv 8800 gts with intel Q6600.
After I installed Ubuntu I am absolutly in love with this OS, I would really like it if I was able to use the full extent of my system, That is still the reason I am using a triple boot system instead of 100% linux.
Thanks in advance!

---

### Post by stmiller on 2007-11-08
SLI works in Linux. I have no personal experience, but check out this article, for instance:

[http://www.phoronix.com/scan.php?page=article&item=860&num=1](http://www.phoronix.com/scan.php?page=article&item=860&num=1)

---

### Post by fain on 2007-11-08
To have SLI in linux you use 
```
nvidia-xconfig
```
You can see the exact syntax with
```
$nvidia-xconfig -A
```
But heres the syntax
```
  --sli=SLI, --no-sli
      Enable or disable SLI.  Valid values for SLI are 'Off', 'Auto', 'AFR',
      'SFR', 'AA', 'AFRofAA'.

```
So to enable sli in alternate frame rendering you would
```
sudo nvidia-xconfig --sli=AFR
```
then restart X
"ctrl+alt+backspace"

To check this configuration you could open
```
nvidia-settings
```
it will say "SLI" next to your card listed as gpu0

edit: oops its in the graphics card info listed under "x screens"   screen 0 (SLI)
if you have 1 screen that is.

---

### Post by go_beep_yourself on 2007-11-09
> **steeviee said:**
> I was reading some posts on the SLI forum and noticed other fellow linux configuring SLI to work with their flavors of linux, and I was wondering if Ubuntu is SLI capable in Gutsy?
I am running x64 Gutsy with two nv 8800 gts with intel Q6600.
After I installed Ubuntu I am absolutly in love with this OS, I would really like it if I was able to use the full extent of my system, That is still the reason I am using a triple boot system instead of 100% linux.
Thanks in advance!

If you have the nvidia driver installed, then do man nvidia-xconfig and hit the / key then type sli and hit enter to search the man page for sli. hit n to see the next search result.

---

