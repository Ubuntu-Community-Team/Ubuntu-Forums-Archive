---
title: "No sound in TV Time"
date: 2009-11-03
forum: x86 64-bit Users
---

### Post by Nuxer-India on 2009-11-03
I recently bought a Pixelview Playtv Pro 4 TV tuner card for my PC. Ubuntu 9.10 64 bit detected my card. I installed TV Time for watching tv. Picture is very perfect in Tv time but it produce no sound. I checked every possible method and didnt find a solution. Please help me........

---

### Post by hkkea on 2009-11-04
I am using tvtime too, it is working fine in my system. Some sound input channels are set to 0 by default, you need to change it through sound setup, or do it in command line. ie.
[COLOR=#B45F06]$ amixer -c 0 sset [COLOR=#741B47]Line[/COLOR],0 60% 60% unmute[/COLOR][COLOR=#B45F06]
[/COLOR]
in my case, it use 'Line' channel for sound input, you may change it to 'Master Front' or PCM or CD or whatever......

---

### Post by Nuxer-India on 2009-11-04
This command is not worked for me  :cry: . Sound is not muted.

---

### Post by ppjose on 2009-11-04
same problem??

[http://ubuntuforums.org/showthread.php?p=8238477](http://ubuntuforums.org/showthread.php?p=8238477)

---

### Post by Nuxer-India on 2009-11-04
> **ppjose said:**
> same problem??

[http://ubuntuforums.org/showthread.php?p=8238477](http://ubuntuforums.org/showthread.php?p=8238477)


I only have video on tvtime.

---

