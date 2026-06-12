---
title: "Ventrilo &quot;runs&quot; but does not show up"
date: 2008-04-29
forum: Wine
---

### Post by garrisonwong on 2008-04-29
Hi, 

I had ventrilo working up until yesterday. What is happening now is when I try to open Ventrilo from the applications menu, there will be a window in the window list panel that says "Starting Ventrilo" which sticks around for a few seconds and then disappears. Ventrilo doesn't show up on the desktop though!

If I check my system processes, it says that Ventrilo is running. Also, if I try to open ventrilo again, the proper ventrilo window pops up telling me that "Another copy of Ventrilo is already running."

Does anyone know why this might be happening? I'm totally stumpped!

This is the output I get when I run Ventrilo from terminal.

```
garry@garry-desktop:~/.wine/drive_c/Program Files/Ventrilo$ wine Ventrilo.exe
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:create_server class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a910187f-0c7a-45ac-92cc-59edafb77b53} could be created for context 0x17

```

Any help or insight into this issue would be much appreciated!

Cheers, 
Gars

I should add that other programs work fine (like WoW). Also, I am running the latest wine and Ventrilo versions.

---

### Post by situz on 2008-04-29
do your run wine with alsa sound driver? looks so from the code. 
try to use oss, don't have any knowledge about ventrilo tho ^^

---

### Post by garrisonwong on 2008-04-29
Thanks for the reply Situz :). 

I tried changing it back to OSS.

```
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.

```

Got rid of all the nasty ALSA errors but still nothing shows up. 

Could it be an issue related to something else? If so, what else might it be? I'm a ubuntu newb.


Cheers, 
Gars

---

### Post by FrozenFox on 2008-04-29
I don't know how to "solve" your problem, but I suspect that something about your -local- wine settings got messed up.

An easy way to work around it without starting your wine setup over from scratch or mess with an otherwise working setup would be to use a script I made/edited a ways back, which creates a new wine prefix specifically for the version of ventrilo being installed:

[http://ubuntuforums.org/showthread.php?t=686256&highlight=ventrilo+script](http://ubuntuforums.org/showthread.php?t=686256&highlight=ventrilo+script)

If that doesn't fix it, there's something wrong with your wine install itself (or less likely, something else unrelated to wine). I'm betting that's not the case though.

---

### Post by situz on 2008-04-29
what version of whine and ventrilo are you using btw?

anyway i found this guide, howto ventrilo via wine:
[http://gentoo-wiki.com/HOWTO_Ventrilo_Via_Wine](http://gentoo-wiki.com/HOWTO_Ventrilo_Via_Wine)

that gays says you're supposed to use ALSA :P
maybe you just had any settings wrong, that caused all those errors?

hope this helps;P

---

### Post by garrisonwong on 2008-04-29
Hmm, the script did not work... 

Is there a way to completely remove wine and ventrilo from my system and reinstall it? 

I can't seem to uninstall Ventrilo using the wine uninstaller.
And I can't seem to uninstall wine using synaptic.


:(

---

### Post by FrozenFox on 2008-04-30
EDIT: I just checked the script. As the readme (and even the script itself tells you this) that you were told repeatedly in the thread to look at tell you quite clearly, you need to test the links before you run the script because it's likely that the codec or ventrilo exe link will be broken in time. If you get a 404 error during one of the downloads all you have to do is change the link at the top of the script to one that works. In this case, the link to ventrilo is broken. [http://www.olderan.net/raznoe/ventrilo/ventrilo-3.0.1-Windows-i386.exe](http://www.olderan.net/raznoe/ventrilo/ventrilo-3.0.1-Windows-i386.exe)  here's one link you can use in place of the old one. Simply edit the script with any standard text editor and change the link, delete the folder /home/yourname/.ventrilo3 and the file /home/yourname/ventrilo3 if they exist, and start the script again with the working link.

We can't help you without any information beyond 'its not working'.

1) What happened with the script? How did it 'not work'? Any errors? Or do you mean it installed but you had the same problem? Did you run ventrilo as the script told you to via the /home/yourname/ventrilo3 (or ventrilo2 if thats what you installed)? The script makes /home/yourname/.ventrilo3 (or .ventrilo2) depending on what you installed, a wineprefix folder. What?

2) You can't uninstall wine from synaptic? Why? Does it give you an error? Does it install and you just mean you still have the same problem upon reinstall? What?

To completely remove wine, use the 'completely remove' option in synaptic and then delete (or temporarily move.. remember youll lose everything you installed with wine if you do this) /home/YOURNAME/.wine  (notice the dot, its a hidden folder).

---

