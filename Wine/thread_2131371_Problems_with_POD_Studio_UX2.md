---
title: "Problems with POD Studio UX2"
date: 2013-04-01
forum: Wine
---

### Post by Zilveztre on 2013-04-01
HI guys, my problem is just right on the title... I recently switched to Ubuntu Studio 12.04 and tried to install my UX2 soI could make some plaing and recording... not so much for my surprise, it didn't work... tried on some toneport drivers on the net and got audio on only one channel of my headphones, but the UX2 worked on getting signal from the input. The problems was that I couldn't get to work my UX2 with Qjackctl... just didn't understand the system on making that work.

Anyway... just a few minutes ago I tried downloading the usb drivers for windows and installing then with wine... but that caused that my UX2 now doesn't even start with Ubuntu...  :? 

I'd apreciate a lot any help!!

---

### Post by xREDEMPTIONx on 2013-04-01
Hi, I have the UX2 and here's how to make it work flawlessly in Ubuntu!
 First, forget about wine and the windows drivers, you don't need them. Upgrade your kernel to a newer version like 3.8. This newer kernel has out of the box support for the UX2 and supports all the inputs and outputs on the UX2. The default 12.04 kernel doesn't. Here's an easy way to upgrade [http://www.upubuntu.com/2013/03/install-linux-kernel-385-in-ubuntu.html](http://www.upubuntu.com/2013/03/install-linux-kernel-385-in-ubuntu.html)
Next, you'll need a mixer that will allow you select the UX2 as the default card and switch inputs, etc.. I use alsamixer (type in terminal to launch) and xfce4-mixer. Isn't the default mixer in Ubuntu Studio xfce4-mixer? I don't know, I don't use it. But, both of these programs will allow you to select the card and fiddle with its controls. Once you have the newer kernel and selected the card in one of the mixer programs you can launch qjackctl, go to setup, and select the card under the interface dropdown box. Alsamixer will tell you the HW # of your card if your not sure. A program like Patchage will help immensley for making the signal connections compared to qjackctl.
 A couple of things, if you really want to get serious with the UX2 for recording with Ubuntu, I recommend checking out [http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/) I installed Ubuntu 12.04 and added the ppas for Kxstudio and I believe you can do the same with Ubuntu Studio. There is an app called Cadence, which is your Jack configuration app and its way better and easier to use than qjackctl (imo). KxStudio uses KDE for the default desktop but you can skip adding the ppa for the KDE stuff and continue to use your environment of choice. I'm running mine atop Unity with all compiz effects turned off and a lowlatency kernel and everythings works amazing well. With the amount free plugins and the ability to route your signals from the UX2 however you like, its really much better than using the UX2 in windows with Pod farm. Beware though that if you go this route you should upgrade the kernel on that system as well so you have the best driver support for your UX2 from the kernel. You can also install the driver manually if you wish- [http://sourceforge.net/projects/line6linux/](http://sourceforge.net/projects/line6linux/)
:guitar:

---

### Post by Zilveztre on 2013-04-02
Thank you very much!!! It did worked!! But I've the same problem as before... with the two options of config that alsamixer gives me on which i hear the guitar, the sound only comes out of one headphone :?

And the other thing is that I cannot figure out how to configure Qjackctl and/or Patchage to make my guitar sound with Rakarrack :? Any hint? :(

Thank you again!!

---

### Post by xREDEMPTIONx on 2013-04-02
Okay, I know exactly what is happening here, mine does the same thing when I first plug it in. Please try these steps-
1.plug in UX2 and plug headphones into UX2
2.open alsamixer and press F6 and select UX2
3.choose "Instrument" above PCM Capture Source
4.turn the volume of the "Monitor" chanel all the way down (should hear silence now)
5.open Qjackctl, (select setup and verify you have UX2 selected as interface, mine is hw:2 or hw:2,0 both seem to work the same) check that in the audio dropdown box you have selected "duplex" also the driver should be "alsa" and the sample rate should be 44100, Frames/period and periods/buffer will vary depending on your hardware, mine are 512 and 2.  leave everything else alone and hit "OK"
6.On the main Qjackctl window hit "Start", it should say "starting" and after a couple seconds say "started"
7.now open Patchage, you will see two boxes titled "system", one with "capture_1 and capture_2" and the other with "playback_1 and playback_2" in blue. These are your connection points.
8.open Rakarrack, now look in the patchage window and you should see new box for Rakarrack with inputs and outputs.
9.by left clicking and holding on the "capture_1" box, drag a connection line to the "in_1" and then again to the "in_2" box on rakarrack, then connect "out_1" to "playback_1" and "out_2" to "playback_2" (you can set rakarrack to "auto-connect" in the settings for future use)
You should be good to go now!

Also, if a mod reads this, this thread is no longer relavent to Wine:)

---

### Post by Zilveztre on 2013-04-02
Hello once again... I got now to hear the sound of my guitar... but somehow it hears kind of robotic and with a little latency :S But I'm happy that I've made this progress thanks to your help!! :D Thank youuu!!

---

### Post by xREDEMPTIONx on 2013-04-02
Glad I could help! Not sure what to tell you about the robotic sound, I dont hear anything like that. Do all the presets in Rakarrack sound like that? Also, to reduce latency, try changing the Frames/Period in qjackctl from 512 to 256. Make sure Patchage is set to the same. If you encounter lots of xruns you can try increasing the Periods/Buffer to 3. You may have to experiment a little with those settings.

---

### Post by Zilveztre on 2013-04-03
I'll try experimenting with the settings then... and yes, all presets hears like that. It's kind of annoying -.- I'll let you know about what I find!

---

### Post by Zilveztre on 2013-04-04
Ok, I've been doing my research and my experiments with the sound of my UX2 and I discovered that the problem is with all kind of sound that I hear from the computer, not only the sound of my guitar :S And I just don't have a clue on where to look :?

---

### Post by xREDEMPTIONx on 2013-04-04
This only happens with the UX2? If you unplug the UX2 and use the speakers or headphones on the computer is the sound okay?

---

### Post by Zilveztre on 2013-04-05
Exactly, the computer sound is okay... the thing is on the UX2 :? (Which btw works like a charm on windows, so the UX2 isn't the problem, hardwarewise xD)

---

### Post by xREDEMPTIONx on 2013-04-05
hmm, could you maybe post your jack settings from qtjackctl? Also, what the kernel you are using?

---

### Post by Zilveztre on 2013-05-20
Sorry for the very (VERY) late response, I've moved out and didn't have internet until a few days ago. Here's a screen of my Qjackctl settings:


[IMG]http://imageshack.us/a/img833/1637/asdasdasd1.png[/IMG]


[IMG]http://imageshack.us/a/img18/7996/asdasd2p.png[/IMG]

This is my kernel:
> 
german@Asd:~$ uname -a
Linux Asd 3.5.0-28-lowlatency #32-Ubuntu SMP PREEMPT Fri Apr 26 11:05:07 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


And here's the messages window of the Qjackctl when I press on the start button:
> 
 [COLOR=#999999]01:16:11.674 Patchbay desactivada.[/COLOR]
 [COLOR=#999999]01:16:11.771 Reiniciar estadísticas.[/COLOR]
 [COLOR=#cccc99]01:16:11.779 Cambios en las conexiones ALSA.[/COLOR]
 [COLOR=#999999]01:16:11.789 D-BUS: Disponible (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No existe el archivo o el directorio
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]01:16:11.800 Cambió el gráfico de conexiones ALSA.[/COLOR]
 (qjackctl.real:3049): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:3049): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:3049): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:3049): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:3049): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:3049): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]01:22:35.666 D-BUS: El servidor JACK no puede iniciarse. Disculpa[/COLOR]
 Mon May 20 01:22:26 2013: Starting jack server...
 Mon May 20 01:22:26 2013: JACK server starting in realtime mode with priority 10
 Mon May 20 01:22:26 2013: control device hw:2
 Mon May 20 01:22:26 2013: control device hw:2
 Mon May 20 01:22:26 2013: Acquired audio card Audio2
 Mon May 20 01:22:26 2013: creating alsa driver ... hw:2|hw:2|256|2|44100|0|0|nomon|swmeter|-|32bit
 Mon May 20 01:22:26 2013: control device hw:2
 Mon May 20 01:22:26 2013: configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
 Mon May 20 01:22:26 2013: ALSA: final selected sample format for capture: 16bit little-endian
 Mon May 20 01:22:26 2013: ALSA: use 2 periods for capture
 Mon May 20 01:22:26 2013: ALSA: final selected sample format for playback: 16bit little-endian
 Mon May 20 01:22:26 2013: ALSA: use 2 periods for playback
 Mon May 20 01:22:31 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Mon May 20 01:22:31 2013: [1m[31mERROR: Driver is not running[0m
 Mon May 20 01:22:31 2013: [1m[31mERROR: Cannot open client name = dbusapi[0m
 Mon May 20 01:22:31 2013: [1m[31mERROR: failed to create dbusapi jack client[0m
 Cannot connect to server socket err = No existe el archivo o el directorio
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:3049): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:3049): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 Mon May 20 01:22:35 2013: [1m[31mERROR: ALSA: poll time out, polled for 8706079 usecs[0m
 Mon May 20 01:22:35 2013: [1m[31mERROR: JackAudioDriver::ProcessAsync: read error, stopping...[0m
 Mon May 20 01:22:35 2013: control device hw:2
 Mon May 20 01:22:35 2013: Released audio card Audio2
 Mon May 20 01:22:35 2013: control device hw:2
 Mon May 20 01:22:35 2013: Saving settings to "/home/german/.config/jack/conf.xml" ...
 [COLOR=#ff0000]01:22:37.804 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.[/COLOR]
 Cannot connect to server socket err = No existe el archivo o el directorio
 Cannot connect to server request channel
 jack server is not running or cannot be started



Yesterday somehow It worked, I could hear the audacious music through my UX2 but as soon as I touched the volume control on the device qjackctl crashed (and the same happened when I did the same with the volume control on my computer). No idea of what to do next really :?

---

### Post by jamesisin on 2013-07-06
I was having that robotic sound, but the latest kernel seems to have fixed it.  However, I have no *input* option for UX2.  (I am running 13.04 with the latest kernel.)  Any ideas?

---

