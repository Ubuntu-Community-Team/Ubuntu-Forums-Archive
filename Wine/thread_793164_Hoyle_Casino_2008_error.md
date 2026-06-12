---
title: "Hoyle Casino 2008 error"
date: 2008-05-13
forum: Wine
---

### Post by milanvora2 on 2008-05-13
I'm trying to install Hoyle Casino 2008. I installed it and 9it complained for a few misisng dll's. So i downloaded them and copied them. 
Now when i run it, I get the following error:

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\common\\.wine\\drive_c\\Program Files\\Encore\\Hoyle Casino 2008\\Hoyle Casino.exe" failed, status c0000142


Any ideas how to solve this ?

---

### Post by JoeDuncan on 2008-05-14
It's a bug in Ubuntu. See this thread:

[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by milanvora2 on 2008-05-15
Followed instructions, no improvement:

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\common\\.wine\\drive_c\\Program Files\\Encore\\Hoyle Casino 2008\\Hoyle Casino.exe" failed, status c0000142

---

### Post by Kinst on 2008-05-15
It doesn't like your MSVCR80.dll file. You can find msvcr80 in /windows/winsxs/ but this folder has really confusing organization. Try putting msvcr80.dll in /windows/system32 or something.

---

