---
title: "Wine without sound, why?"
date: 2006-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by flapane on 2006-06-06
I ran winecfg, a lot of programs and games run well (simcity3000,c&c etc etc), but I can't get sound, even if in wine control panel it says Realtek sound adapter (and it should be right).
Maybe it's due to 64bit distro? But I have the oss-alsa wrapper installed....

---

### Post by Kilz on 2006-06-06
[QUOTE=flapane]I ran winecfg, a lot of programs and games run well (simcity3000,c&c etc etc), but I can't get sound, even if in wine control panel it says Realtek sound adapter (and it should be right).
Maybe it's due to 64bit distro? But I have the oss-alsa wrapper installed....[/QUOTE]
Nope, Im running 64 bit ubuntu Dapper and have sound in wine.

---

### Post by flapane on 2006-06-06
maybe do i need some audio package?
if i run winecfg, i can read in the shell:
flapane@a64:~/Desktop$ winecfg
fixme:shell:_SHGetDefaultValue (5,L""), LoadString failed, missing translation?
err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:module:load_builtin_dll failed to load .so lib for builtin L"winenas.drv": libaudio.so.2: cannot open shared object file: No such file or directory
fixme:shell:_SHGetDefaultValue (5,L""), LoadString failed, missing translation?
fixme:shell:_SHGetDefaultValue (5,L""), LoadString failed, missing translation?
flapane@a64:~/Desktop$

---

### Post by Kilz on 2006-06-06
[QUOTE=flapane]maybe do i need some audio package?
if i run winecfg, i can read in the shell:
flapane@a64:~/Desktop$ winecfg
fixme:shell:_SHGetDefaultValue (5,L""), LoadString failed, missing translation?
err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:module:load_builtin_dll failed to load .so lib for builtin L"winenas.drv": libaudio.so.2: cannot open shared object file: No such file or directory
fixme:shell:_SHGetDefaultValue (5,L""), LoadString failed, missing translation?
fixme:shell:_SHGetDefaultValue (5,L""), LoadString failed, missing translation?
flapane@a64:~/Desktop$[/QUOTE]

[What you can do is go here]("http://packages.ubuntu.com/") and search for the needed lib's with Search the contents of packages. Look for 32 bit packages. Use the archive program to extract them, open the data archive within that. Then copy the contents of the extracted /usr/lib to the /usr/lib32 folder in your file system.

---

### Post by flapane on 2006-06-06
i think /usr/lib32 because /usr/lib brings me to lib64, where libasound is installed.
How can I extract the files from a debian package?

---

### Post by Kilz on 2006-06-06
[QUOTE=flapane]i think /usr/lib32 because /usr/lib brings me to lib64, where libasound is installed.
How can I extract the files from a debian package?[/QUOTE]

Right click on the .deb file and choose "Extract here" you may need to install the dpkg-dev to do that if it doesn't work. Yes the files go in /usr/lib32. But when you extract a .deb file, then extract the data archive in it you will see a /usr/lib folder placed wherever you extracted to. The files in that extracted folder are placed in /usr/lib32.

---

### Post by flapane on 2006-06-06
thanks, it seems almost to go!!
I selected alsa in winecfg, but it says:
flapane@a64:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libaudiofile.so.0: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory


SImcity3000 seems to go, but audio blocks after 20 25secs.
If i select OSS, I can't hear anything.
I installed libarts,libasound,libesd,libaudio

---

### Post by ssmaxss on 2006-06-07
How have you installed wine on 64-bit dapper?

---

### Post by flapane on 2006-06-07
[QUOTE=ssmaxss]How have you installed wine on 64-bit dapper?[/QUOTE]

wine i386

---

### Post by Kilz on 2006-06-07
[QUOTE=ssmaxss]How have you installed wine on 64-bit dapper?[/QUOTE]

[Check out this howto]("http://www.ubuntuforums.org/showthread.php?t=185557&highlight=wine+64+bit")

---

### Post by AmphetaMarinE on 2006-06-26
> 
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libaudiofile.so.0: cannot open shared object file: No such file or directory

To fix this, I did :
```

#sudo apt-get install esound

```
Still have the other error you get, but working on it....

---

