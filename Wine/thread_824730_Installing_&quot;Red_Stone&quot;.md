---
title: "Installing &quot;Red Stone&quot;"
date: 2008-06-10
forum: Wine
---

### Post by purenirvana94 on 2008-06-10
I would like to install the game "Red Stone" that I had on my computer before I installed Ubuntu.  Wine runs the .exe file, but comes up with this error message after the "Terms of Agreement" page, as it should be installing:

Title of box: Error!! in cNUX::MergeExtract

Contents: '*.exe' File Not Open

Then an OK button.  Is there a way to fix this?

---

### Post by cogadh on 2008-06-10
Run the install from the terminal and post Wine's output. Chances are, there is something in its error messages that may explain what is happening.

---

### Post by purenirvana94 on 2008-06-10
heres what I did in terminal:

sudo apt-get install home/jeff/Desktop/SetupRS.exe
password
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package home

Was this wrong?  Am I supposed to tell terminal to use wine?  I'm rather new with ubuntu and am unsure how to do that if that is what I need to do.

---

### Post by purenirvana94 on 2008-06-10
jeff@jeff-laptop:~$ wine c:\\setuprs\\setuprs.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Intel ICH6 Modem, disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:shell:BrsFolder_OnCreate flags 30 not implemented



That's what I get when I try running the loader with wine through terminal.  After it says all that, the installer still loads, and allows me to click next, accept the terms and conditions, then this error appears when it should begin installing:

Title:  Error!! in cNUX:MergeExtract

Contents: ':\setuprs\setuprs.exe' File Not Open



The installer runs, but it fails at that error message, before the game begins installing.

---

### Post by cogadh on 2008-06-10
First get rid of those preloader error problems:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

Then run the install again and see what pops up.

---

### Post by purenirvana94 on 2008-06-10
I got it working, thanks for everything :)

---

### Post by bytesmaker on 2008-07-22
Hi. I trying to install this game too. But when I do > # wine SetupRS_07082008.exe this error appear: "fixme:shell:BrsFolder_OnCreate flags 30 not implemented". What thats means? The wine version is 0.9.25.

Thanks.

---

