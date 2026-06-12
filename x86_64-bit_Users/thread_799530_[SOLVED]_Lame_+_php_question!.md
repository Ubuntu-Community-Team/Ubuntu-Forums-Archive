---
title: "[SOLVED] Lame + php question!"
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by radopenev on 2008-05-19
Hi ,everyone!
Please I need a help! 
I've got  installed LAME version 3.96.1
In terminal everything is OK :

rado@UbuntuRado:/var/www/uploadTest$ /usr/bin/lame -b 32 ChrisBrown.mp3 NewChrisBrown.mp3 
ID3v2 found. Be aware that the ID3 tag is currently lost when transcoding.
LAME version 3.96.1 ([http://lame.sourceforge.net/](http://lame.sourceforge.net/))
Resampling:  input 44.1 kHz  output 16 kHz
Using polyphase lowpass filter, transition band:  5484 Hz -  5677 Hz
Encoding ChrisBrown.mp3 to NewChrisBrown.mp3
Encoding as 16 kHz  32 kbps j-stereo MPEG-2 Layer III (16x) qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA
  5499/5502  (100%)|    0:13/    0:13|    0:13/    0:13|   14.907x|    0:00
average:  32.0 kbps   LR: 223 (4.054%)   MS: 5278 (95.95%)

ReplayGain: -6.0dB
rado@UbuntuRado:/var/www/uploadTest$

I've made a simple php-script.
<?php
exec ("/usr/bin/lame -b 32 ChrisBrown.mp3 NewChrisBrown.mp3");
?>
But the output is :

sh: mpg123: command not found
I'm trying:
<?php
exec ("zip myZIP.zip mediaplayer.swf ChrisBrown.mp3 LameMistake.txt Lame.php");
?>
Zip-creation is ok ,but when un-zip there isn't "mp3"(swf txt php are ok)
Maybe something with php.ini?!? 
Many thanks for any help!:)
Best regards!

---

### Post by radopenev on 2008-05-28
Everything is OK when I put the php-script outside of the "files" directory
:)

---

