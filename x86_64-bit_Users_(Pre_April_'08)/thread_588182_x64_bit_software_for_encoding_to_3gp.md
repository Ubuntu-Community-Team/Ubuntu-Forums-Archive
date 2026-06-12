---
title: "x64 bit software for encoding to 3gp?"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by s_spiff on 2007-10-23
I wanted to know if there are/is any player/software which will allow me to encode .avi or .wmv files to .3gp, allowing me to adjust the fps, bitrate etc.? 
I heared mencoder can do it, but its a CLI based. Any GUI based?

As for CLI based mencoder, can someone tell me what is the exact command to encode a video?

---

### Post by John.Michael.Kane on 2007-10-23
> **s_spiff said:**
> I wanted to know if there are/is any player/software which will allow me to encode .avi or .wmv files to .3gp, allowing me to adjust the fps, bitrate etc.? 
I heared mencoder can do it, but its a CLI based. Any GUI based?

As for CLI based mencoder, can someone tell me what is the exact command to encode a video?
there is a gui for this.
[How to convert movies to 3gp (mobile phones)]("http://ubuntuforums.org/showthread.php?t=216083")

Or

Here is how you could do it using ffmpeg I have not tested the below methods fully.

For reference:
```
ffmpeg [[infile options][-i infile]]… {[outfile options] 
```

To convert from MPG to 3GP
```
ffmpeg -i yourfile.mpg -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -ab 32 -y yourfile.3gp
```

To convert from AVI to 3GP
```
ffmpeg -i yourfile.avi-s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 -y yourfile.3gp
```

To convert from 3GP to AVI
```
ffmpeg -i yourfile.3gp -f avi -vcodec xvid -acodec mp3 -ar 22050 yourfile.avi
```

---

### Post by s_spiff on 2007-10-23
Woah dude! you rule. Thank you sooo much!

---

