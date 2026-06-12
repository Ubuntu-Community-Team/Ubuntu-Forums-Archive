---
title: "wine + subtitleedit"
date: 2022-07-17
forum: Wine
---

### Post by klapvogn on 2022-07-17
Hi,

Im trying to get a process running in a python script which should convert sami subs to srt files, but i cant get the subprocess.call running, so i though maybe someone could take a look an see if you find a error

```
subprocess.call(["wine ./SubtitleEdit.exe", '/convert', TEMP + '*.{}'.format(s_f), 'srt', '/multiplereplace'], stdout=subprocess.DEVNULL, stderr=subprocess.STDOUT, shell='True')
```

i can't give a error as i dont get any :-(

---

### Post by TheFu on 2022-07-17
Linux has a fantastic subtitle editor. Why use WINE at all?  subtitleeditor is the name and I think the package name.

If you don't want a GUI tool, there are plenty of existing scripts that convert from 1 format to any other.  SRT is fine, but ASS  works too.  These are for text-based captions. [https://superuser.com/questions/117929/open-source-command-line-subtitle-converter](https://superuser.com/questions/117929/open-source-command-line-subtitle-converter) shows how to use ffmpeg to perform the smi --> srt conversion.

 DVD subtitles are actually graphical glyphs and the best tool I know for that is avidemux. It takes some training to learn each glyph, but once that training it done, it can be used over and over and over making follow-on conversions from glyph to text captions very fast.

---

### Post by klapvogn on 2022-07-18
Thanks, im looking at ffmpeg right now :-)

---

### Post by klapvogn on 2022-07-19
Ended up using ```
subprocess.call(f"mono {SUBTiTLEEDiT} /convert {TEMP}*.{s_f}, 'srt' ", shell=True)
```
because: ffmpeg gave me nothing but errors not matter what i tried!

Tried ```
subprocess.call(f'ffmpeg -i "{TEMP}$i" "{TEMP}$i.srt"')
```
but gave operation not permitted

---

