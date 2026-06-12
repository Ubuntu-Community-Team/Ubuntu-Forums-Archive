---
title: "Can't select ALSA in Winecfg"
date: 2008-01-07
forum: Wine
---

### Post by erikcw on 2008-01-07
I can't change the sound drive in winecfg from OSS to ALSA.  The option is in the list, but the checkbox won't work (and I can't uncheck OSS).  The configure option does'n work either, it just adds a fixme into the terminal output (see last line)

The terminal has the following output:
> 
erik@turbo:/tmp$ winecfg
fixme:shell:MLSetMLHInstance (0x77b50000,0x7eb40000) stub
fixme:shell:MLClearMLHInstance (0x77b50000)stub
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default:0
fixme:win:WinHelpA Unknown help command 10


Why can't I change this?

Thanks!

---

### Post by gunz0 on 2009-09-16
i have the same problem i'm using wine 1.1.29 on ubuntu 9
and I'm stuck with OSS because i can't unchecked the box or select another checkbox
I wana use ALSA only
I'm a newby on wine so if you guys can help me to set winecfg with ALSA i'll apreciate 
thx

---

