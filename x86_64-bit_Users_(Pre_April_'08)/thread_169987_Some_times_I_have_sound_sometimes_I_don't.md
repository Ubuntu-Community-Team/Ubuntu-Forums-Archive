---
title: "Some times I have sound sometimes I don't"
date: 2006-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by marciovinicius on 2006-05-03
I have a curious problem in my Uduntu PC. Sometimes I turn my pc on and everything works fine... later I turn it on and I have no sound, and when I click on the volume icon a message error appears telling me that there is no sound card installed or configured... After this, it can be possible that the sound card works again (even if I don't change anything)... Unfortunately, it's much more frequent that the sound doesn't work.

I've changed to Dapper Beta 2, but the problem happens as exactly the same way. I've tried to do this <[http://ubuntuforums.org/showthread.php?t=44753]("http://ubuntuforums.org/showthread.php?t=44753")> and nothing...

What else can I do????
This is the only thing is lacking to let me adopt Ubuntu definitely...

It is very deceptive... I trust in Ubuntu, I install it and it makes me beleave it is allright,...  but it is speechless!

[SIZE=1] (sorry about the English. I'm Brazilian)[/SIZE]

---

### Post by Sef on 2006-05-03
Try copy and posting the results of the two commands listed below.

cat /proc/asounds/cards  (This will show what sound cards you have.)


sudo gedit /etc/modprobe/alsa-base  (This will show what sound card is your default.)

---

### Post by marciovinicius on 2006-05-03
The first command showed this:
> cat: /proc/asounds/cards: Arquivo ou diretório não encontrado *(file or directory not found)* But the file is there and it has 0 byte.

the second command showed this:
> - using device default
- using device default
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave and opened a blank text file...

Actualy the path "/etc/modprobe/" doesn't exist, there is a "/etc/modprobe.d/". Inside this one there is a file called "alsa-base" with this:


> # autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

The sound is off right now...

---

### Post by danko on 2006-05-04
The easiest way to fix it that I found is to put line &#8220;blacklist saa7134-alsa&#8221; in /etc/modules.d/blacklist&#8221; file and to add line &#8220;saa7134-alsa&#8221; to &#8220;/etc/modules&#8221; file.

---

### Post by marciovinicius on 2006-05-04
You mean /etc/modprobe.d/blacklist (instead of /etc/modules.d/)...
What exactly does it?

I'll try anyway (now I'm trying anything!:))

---

### Post by danko on 2006-05-04
Sorry, I ment "modprobe.d" (I'm not near my machine at the moment).

---

### Post by marciovinicius on 2006-05-04
It didn't work...

When I click on the volume this error message comes up (as used to happen before):
> O controle de volume não encontrou nenhum elemento e/ou dispositivos de controle. Isso significa que, ou você não tem o plugin correto do GStreamer instalado, ou que você não tem uma placa de som configurada.

Você pode remover o controle de volume do painel clicando com o botão direito no ícone do auto-falante no painel e selecionando "Remover do Painel" no menu.

(The volume control didn't find no element and/or device of control. It means that you don't have the right plugin of the GStreamer installed or that you don't have a sound card configured.

You can remove the volume control from the panel right-clicking on the soundspeaker icon and selecting "Remove from panel" in the menu)

When I double-click the volume icon this error message comes up (as used to happen before):
> Nenhum módulo e/ou dispositivo do GStreamer de controle de volume foi encontrado.
(No module and/or device of the GStreamer for volume control was found.)

---

### Post by danko on 2006-05-04
Wait !! Sorry,sorry...
I was browsing forums during my lunch break, and I merged in my head two different threads (tabbed browsing). My &#8220;solution&#8221; is for the problem I had recently with dapper, because sound modules were loaded in random order during boot (this can also be your problem) assigning once /dev/dsp to my sound card, and once to PCI sound of my TV cars (saa7134-alsa module).
Either way, your problem seems in some way similar to mine. If you have two sound devices, you can put the one you wish to load later in &#8220;blacklist&#8221; and &#8220;modules&#8221; file.

---

### Post by marciovinicius on 2006-05-04
Ok! but I have only one sound device (as far as i know), the onboard one. Maybe there are more than one configured (I don't know and I don't know how). When the sound works, the default sound card (in System>Preferences>Sound) is "ALi M5455".

In this case, what should I write in "blacklist" and "modules" files

Just remember that I use libesd-alsa0 and my sound stuff are configured as [this Howto]("http://ubuntuforums.org/showthread.php?t=44753")

---

### Post by marciovinicius on 2006-05-06
Can anyone else help me?...

I've noted that the sound works just after (and sometimes just before) a new upgrade and it stops after the next boot... (I don't know if it has any conection or if it is only a coincidence)

---

### Post by rextor on 2006-05-06
Hi marciovinicius,
it was similar for me too... the only difference being i never used to get any sound though. Then i installed the NVidia drivers from the CD that came with the mobo and some other nvidia specific things with apt-get.. after which i ran a "apt-get upgrade".
On next reboot the sound was working.

My specs are:
AMD Athlon64 3000+
ASUS A8N-VM mobo (GeForce 6100 + NForce 410)
Ubuntu dapper beta

Rex

---

### Post by marciovinicius on 2006-05-21
Within the CD that came with my PC there's only a file (where suppose to be the linux' drivers for sound card) called "cmpci-6.64.tar.bz2" and I have no idea about what I should do with it!

I repeat: just after each newer (automatic) upgrade of Ubuntu the sound works, but after the second boot I have no sound card again. How can it be possible the sound card desconfigure by itself???!!!](*,)

I think I should try another linux distribution (although I think I'll have the same problem) or go back to Windows... I don't want a speechless computer at all!

---

### Post by abreups on 2006-08-20
Check this solution (verifique essa solução):
[http://www.ubuntuforums.org/showthread.php?p=817147#post817147](http://www.ubuntuforums.org/showthread.php?p=817147#post817147)

Good luck.

Paulo Abreu

---

