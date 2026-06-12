---
title: "VLC Quits unexpectedly when opening avi files"
date: 2008-10-29
forum: x86 64-bit Users
---

### Post by rickerkioz on 2008-10-29
Looked around and didn't see the answer, but, I'm running an AMD 64 Hardy Heron ATI x1950 and lately VLC has been giving me problems when opening avi files.  

It just quits, the program opens, no error messages or anything.

I'm a newcomer to all this, so I'm not sure exactly what I should include.  Any suggestions welcome!

Thanks!

---

### Post by Thelasko on 2008-10-29
You can see the error messages by running VLC in the terminal.  It's probably just a setting in VLC's preferences.

---

### Post by rickerkioz on 2008-11-01
Ran it in terminal, here's what I got:  

VLC media player 0.8.6e Janus
[00000344] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Value in failed request:  0x5800006
  Serial number of failed request:  108
  Current serial number in output stream:  109

---

### Post by pulpo69 on 2008-11-01
you use an outdated version of vlc (actual 0.95) in intrepid it's 0.94.maybe you have to install additional codecs (medibuntu repos).
i'm on intrepid (64bit) and vlc is running fine, for me it's the best mediaplayer.

---

### Post by Thelasko on 2008-11-03
In VLC's preferences, try changing the video output mode.  I believe you are currently using Xvideo, try changing it to XV or something else.

---

