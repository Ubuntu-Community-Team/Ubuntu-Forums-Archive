---
title: "wine installs without c drive"
date: 2007-08-18
forum: Wine
---

### Post by zorkerz on 2007-08-18
Im running gutsy gibbon and trying to play warcraft in wine. I have installed wine from the ubuntu repos (v0.9.42) and from winehq's feisty repos (v0.9.43 they have no Gutsy repos yet).

I first notice errors when opening winecfg
 >  winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.It looks to me like the drive_C and its windows directory are not getting setup or installed properly. In fact neither of them exist a all. I have searched around but can't find any commands or steps in the installation that I have skipped. Does anyone know what I can do to set this up correctly?

thanks

---

### Post by zorkerz on 2007-08-18
oops solved my problem.
I had an old wine directory from a different computer and needed to delete it and start fresh.

```
rm -rf ~/.wine
```

gooday

---

