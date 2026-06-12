---
title: "no sound kubuntu 8.10"
date: 2008-11-21
forum: x86 64-bit Users
---

### Post by aeleneski on 2008-11-21
I just installed fresh on new laptop. Fired up amarok, installed mp3 software, and no sound. I open up alsamixer and turn up the sound, but still hear nothing. Here is lshw:

>         *-multimedia                                                            
             description: Audio device                                          
             product: SBx00 Azalia (Intel HDA)                                  
             vendor: ATI Technologies Inc                                       
             physical id: 14.2                                                  
             bus info: pci@0000:00:14.2                                         
             version: 00                                                        
             width: 64 bits                                                     
             clock: 33MHz                                                       
             capabilities: pm bus_master cap_list                               
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel  

---

### Post by aeleneski on 2008-11-23
Please, I have tried many things, upgrading alsa to latest version, adding options to /etc/modprobe.d/alsa-base (there are so many combinations). Is there any more information I can provide to help diagnose? This is the only thing not working on my laptop.

---

### Post by C. Wizard on 2008-11-23
Did you go into system settings and check your sound output preferences?  Just a thought.

---

### Post by aeleneski on 2008-11-24
I am trying to follow this guide [http://ubuntuforums.org/showthread.php?t=205449&highlight=stopping+multiple+soundcards+from+switching]("http://ubuntuforums.org/showthread.php?t=205449&highlight=stopping+multiple+soundcards+from+switching") 

And this part "Configuring default soundcards / stopping multiple soundcards from switching", when I do 

```
cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

```


How do I have two of the same card? Could this be the cause of my problems?

---

### Post by aeleneski on 2008-12-02
Well I update all my packages today and have set 
/etc/modprobe.d/alsa-base to have

options snd-hda-intel model=auto

Then if I go into alsa-mixer and turn up the sound on all elements, I am now able to get sound out of my two front headphone jacks. But still no sound out of the laptop speakers. Anyone have any ideas?

---

