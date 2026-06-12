---
title: "No load font, arrrgh!"
date: 2011-09-10
forum: Wine
---

### Post by PC_load_letter on 2011-09-10
```
No load font, arrrgh!
```

This is the error message that I get from Wine 1.2.3 running on Ubuntu studio Lucid 32bit, when trying to run a windows application, with the result that the GUI of the app is displayed but with no labels showing (and there is supposed to be quite a few). 

The weird thing is, although the ttf font (Bitstream Vera Sans) came with the app, and I put it in **~/.fonts**, and **/usr/share/fonts/truetype/** Wine DOES load the font in notepad, but it does not load it in the GUI and when I run the app from terminal I get this silly error above. I changed the compatibility of this app in Wine to Win 7 to no avail. 

Any help is appreciated, or is this a bug?

---

### Post by PC_load_letter on 2011-09-11
Bump of the day. Here is more info if you want. Beware, the application that is missing the labels from the GUI is not the energyXT program (DAW for running synth and audio fx plugins VSTs). EnergyXT runs great with wine (I'm running the latest demo version), the problem is with one of the plugins, without the labels on the knobs, it's worse than useless. 

The error message occur at the exact moment that I drag and drop the plugin into the workspace of energyXT.

```
**$ env WINEPREFIX="/home/muse/.wine" wine C:\\windows\\command\\start.exe /Unix /home/muse/.wine/dosdevices/c:/users/Public/Start\ Menu/Programs/energyXT\ 2.5.4/energyXT\ 2.5.4.lnk**
wine: cannot find L"C:\\windows\\system32\\plugplay.exe"
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
muse@Kholal:~$ fixme:mixer:ALSA_MixerInit No master control found on M Audio Audiophile 24/96, disabling mixer
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
Jack: JackClient::SetupDriverSync driver sem in flush mode
Jack: JackPosixSemaphore::Connect jack_sem.1000_default_energyXT
Jack: Already connected name = energyXT
Jack: Clock source : system clock via clock_gettime
Jack: JackLibClient::Open name = energyXT refnum = 3
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_1 type = 32 bit float mono audio port_index = 23
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_2 type = 32 bit float mono audio port_index = 24
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_3 type = 32 bit float mono audio port_index = 25
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_4 type = 32 bit float mono audio port_index = 26
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_5 type = 32 bit float mono audio port_index = 27
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_6 type = 32 bit float mono audio port_index = 28
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_7 type = 32 bit float mono audio port_index = 29
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_8 type = 32 bit float mono audio port_index = 30
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_9 type = 32 bit float mono audio port_index = 31
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_10 type = 32 bit float mono audio port_index = 32
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_11 type = 32 bit float mono audio port_index = 33
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_12 type = 32 bit float mono audio port_index = 34
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_13 type = 32 bit float mono audio port_index = 35
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_14 type = 32 bit float mono audio port_index = 36
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_15 type = 32 bit float mono audio port_index = 37
Jack: JackClient::PortRegister ref = 3 name = energyXT:in_16 type = 32 bit float mono audio port_index = 38
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_1 type = 32 bit float mono audio port_index = 39
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_2 type = 32 bit float mono audio port_index = 40
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_3 type = 32 bit float mono audio port_index = 41
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_4 type = 32 bit float mono audio port_index = 42
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_5 type = 32 bit float mono audio port_index = 43
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_6 type = 32 bit float mono audio port_index = 44
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_7 type = 32 bit float mono audio port_index = 45
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_8 type = 32 bit float mono audio port_index = 46
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_9 type = 32 bit float mono audio port_index = 47
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_10 type = 32 bit float mono audio port_index = 48
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_11 type = 32 bit float mono audio port_index = 49
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_12 type = 32 bit float mono audio port_index = 50
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_13 type = 32 bit float mono audio port_index = 51
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_14 type = 32 bit float mono audio port_index = 52
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_15 type = 32 bit float mono audio port_index = 53
Jack: JackClient::PortRegister ref = 3 name = energyXT:out_16 type = 32 bit float mono audio port_index = 54
Jack: JackClient::Activate
Jack: JackClient::StartThread : period = 10666 computation = 0 constraint = 10666
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackClient::kBufferSizeCallback buffer_size = 1024
Jack: JackClient::kActivateClient name = energyXT ref = 3 
Jack: JackClient::Connect src = system:capture_1 dst = energyXT:in_1
Jack: JackGraphManager::RecalculateLatency port_index = 23
Jack: JackGraphManager::RecalculateLatency port_index = 24
Jack: JackGraphManager::RecalculateLatency port_index = 25
Jack: JackGraphManager::RecalculateLatency port_index = 26
Jack: JackGraphManager::RecalculateLatency port_index = 27
Jack: JackGraphManager::RecalculateLatency port_index = 28
Jack: JackGraphManager::RecalculateLatency port_index = 29
Jack: JackGraphManager::RecalculateLatency port_index = 30
Jack: JackGraphManager::RecalculateLatency port_index = 31
Jack: JackGraphManager::RecalculateLatency port_index = 32
Jack: JackGraphManager::RecalculateLatency port_index = 33
Jack: JackGraphManager::RecalculateLatency port_index = 34
Jack: JackGraphManager::RecalculateLatency port_index = 35
Jack: JackGraphManager::RecalculateLatency port_index = 36
Jack: JackGraphManager::RecalculateLatency port_index = 37
Jack: JackGraphManager::RecalculateLatency port_index = 38
Jack: JackGraphManager::RecalculateLatency port_index = 39
Jack: JackGraphManager::RecalculateLatency port_index = 40
Jack: JackGraphManager::RecalculateLatency port_index = 41
Jack: JackGraphManager::RecalculateLatency port_index = 42
Jack: JackGraphManager::RecalculateLatency port_index = 43
Jack: JackGraphManager::RecalculateLatency port_index = 44
Jack: JackGraphManager::RecalculateLatency port_index = 45
Jack: JackGraphManager::RecalculateLatency port_index = 46
Jack: JackGraphManager::RecalculateLatency port_index = 47
Jack: JackGraphManager::RecalculateLatency port_index = 48
Jack: JackGraphManager::RecalculateLatency port_index = 49
Jack: JackGraphManager::RecalculateLatency port_index = 50
Jack: JackGraphManager::RecalculateLatency port_index = 51
Jack: JackGraphManager::RecalculateLatency port_index = 52
Jack: JackGraphManager::RecalculateLatency port_index = 53
Jack: JackGraphManager::RecalculateLatency port_index = 54
Jack: JackClient::Connect src = system:capture_2 dst = energyXT:in_2
Jack: JackClient::Connect src = system:capture_3 dst = energyXT:in_3
Jack: JackClient::Connect src = system:capture_4 dst = energyXT:in_4
Jack: JackClient::Connect src = system:capture_5 dst = energyXT:in_5
Jack: JackClient::Connect src = system:capture_6 dst = energyXT:in_6
Jack: JackClient::Connect src = system:capture_7 dst = energyXT:in_7
Jack: JackClient::Connect src = system:capture_8 dst = energyXT:in_8
Jack: JackClient::Connect src = system:capture_9 dst = energyXT:in_9
Jack: JackClient::Connect src = system:capture_10 dst = energyXT:in_10
Jack: JackClient::Connect src = system:capture_11 dst = energyXT:in_11
Jack: JackClient::Connect src = system:capture_12 dst = energyXT:in_12
Jack: JackClient::Connect src = energyXT:out_1 dst = system:playback_1
Jack: JackClient::Connect src = energyXT:out_2 dst = system:playback_2
Jack: JackClient::Connect src = energyXT:out_3 dst = system:playback_3
Jack: JackClient::Connect src = energyXT:out_4 dst = system:playback_4
Jack: JackClient::Connect src = energyXT:out_5 dst = system:playback_5
Jack: JackClient::Connect src = energyXT:out_6 dst = system:playback_6
Jack: JackClient::Connect src = energyXT:out_7 dst = system:playback_7
Jack: JackClient::Connect src = energyXT:out_8 dst = system:playback_8
Jack: JackClient::Connect src = energyXT:out_9 dst = system:playback_9
Jack: JackClient::Connect src = energyXT:out_10 dst = system:playback_10
Jack: JackGraphManager::RecalculateLatency port_index = 23
Jack: JackGraphManager::RecalculateLatency port_index = 24
Jack: JackGraphManager::RecalculateLatency port_index = 25
Jack: JackGraphManager::RecalculateLatency port_index = 26
Jack: JackGraphManager::RecalculateLatency port_index = 27
Jack: JackGraphManager::RecalculateLatency port_index = 28
Jack: JackGraphManager::RecalculateLatency port_index = 29
Jack: JackGraphManager::RecalculateLatency port_index = 30
Jack: JackGraphManager::RecalculateLatency port_index = 31
Jack: JackGraphManager::RecalculateLatency port_index = 32
Jack: JackGraphManager::RecalculateLatency port_index = 33
Jack: JackGraphManager::RecalculateLatency port_index = 34
Jack: JackGraphManager::RecalculateLatency port_index = 35
Jack: JackGraphManager::RecalculateLatency port_index = 36
Jack: JackGraphManager::RecalculateLatency port_index = 37
Jack: JackGraphManager::RecalculateLatency port_index = 38
Jack: JackGraphManager::RecalculateLatency port_index = 39
Jack: JackGraphManager::RecalculateLatency port_index = 40
Jack: JackGraphManager::RecalculateLatency port_index = 41
Jack: JackGraphManager::RecalculateLatency port_index = 42
Jack: JackGraphManager::RecalculateLatency port_index = 43
Jack: JackGraphManager::RecalculateLatency port_index = 44
Jack: JackGraphManager::RecalculateLatency port_index = 45
Jack: JackGraphManager::RecalculateLatency port_index = 46
Jack: JackGraphManager::RecalculateLatency port_index = 47
Jack: JackGraphManager::RecalculateLatency port_index = 48
Jack: JackGraphManager::RecalculateLatency port_index = 49
Jack: JackGraphManager::RecalculateLatency port_index = 50
Jack: JackGraphManager::RecalculateLatency port_index = 51
Jack: JackGraphManager::RecalculateLatency port_index = 52
Jack: JackGraphManager::RecalculateLatency port_index = 53
Jack: JackGraphManager::RecalculateLatency port_index = 54
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!
No load font, arrrgh!

```

---

### Post by PC_load_letter on 2011-09-13
Just for future reference. This problem does occur if you use any of this developer's VSTs on the Muse Receptor hardware, which is also running Linux.

The solution is due to the developer himself, [Urs Heckmann]("http://u-he.com"), and all you need is simply to copy the **l_10646.ttf** font in the Windows fonts directory. Just to be on the safe side I also copied it to the ~/.fonts  
Works like a charm now.

---

