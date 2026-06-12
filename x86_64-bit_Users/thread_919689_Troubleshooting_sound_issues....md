---
title: "Troubleshooting sound issues..."
date: 2008-09-14
forum: x86 64-bit Users
---

### Post by StormPCs on 2008-09-14
I have a Quad Core AMD running 64 bit Ubuntu Hardy 8.04 and my sound sort of works but it is distorted and doesn't seem to output the sound properly.

The funny thing is that when I run Sun Virtualbox with an XP Pro VM the sound works much better.  The virtual machine only uses one core.  Do you think quad cores could be an issue?

Thanks for your input.

---

### Post by Kilz on 2008-09-14
> **StormPCs said:**
> I have a Quad Core AMD running 64 bit Ubuntu Hardy 8.04 and my sound sort of works but it is distorted and doesn't seem to output the sound properly.

The funny thing is that when I run Sun Virtualbox with an XP Pro VM the sound works much better.  The virtual machine only uses one core.  Do you think quad cores could be an issue?

Thanks for your input.

I dont think so the virtual machine uses virtual hardware. The virtual sound card is probably an old soundblaster the kernel has perfect drivers for.

---

### Post by tuxxy on 2008-09-14
What sound card are you using?

---

### Post by StormPCs on 2008-09-14
> **tuxxy said:**
> What sound card are you using?

This is what I get from cat /proc/asound/cards

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe020000 irq 21

---

### Post by Yellow Pasque on 2008-09-14
Try OSS4 (link in sig)

---

### Post by StormPCs on 2008-09-15
> **Temüjin said:**
> Try OSS4 (link in sig)

I have no sound now.  It appears I no longer have a sound device installed.

HELP!!!!:confused:

---

### Post by poja86 on 2008-09-15
I also have a distorted sound issue on a quad core amd machine.

I have followed some steps but have hit road blocks. Let me first outline my problem and hopefully we will both find an answer.

I have onboard audio: Realtek ALC-883 I found the drivers here:
[http://www.realtek.com.tw/downloads/]("http://www.realtek.com.tw/downloads/")

This is where the road block is... When I tried to install the drivers, i get an error that says "/usr/lib64/libasound.so" & "/usr/lib64/libasound.so.2" "no such file or folder"

I am using the 64 bit Ubuntu 8.04 and I do have "/usr/lib64/libasound.so.2", but i don't have "libasound.so" and have been unable to resolve this issue.

---

### Post by poja86 on 2008-09-15
Note: I know lots of other people have found help on the ALSA site, but if my answer is there, I'm still looking. :p

[http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

Also this thread is pretty useful.

[http://ubuntuforums.org/showthread.php?t=616845]("http://ubuntuforums.org/showthread.php?t=616845")

---

### Post by hazelnut on 2008-09-16
I have discovered the sure fire way to solve most sound problems in Hardy Heron:

sudo killall pulseaudio

Works absolute wonders for me.  Bet it works for you too :)

Now if someone could help me with preventing pulseaudio from starting up, my life will be grand again.  I tried apt-get remove pulseaudio, but that tried to remove ubuntu-desktop among some other important apps.

---

### Post by Nettoyer on 2008-09-19
I'm new to linux, but would it help if you blacklist the module?

---

