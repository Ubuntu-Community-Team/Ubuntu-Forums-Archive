---
title: "Trouble Compiling Similar Song Selectors"
date: 2007-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by tjbk_tjb on 2007-01-20
So, I have attempted to get several programs that select songs similar to a selected song, preferably in Amarok.

First, I attempted to get SmartDJ (an Amarok plugin) to work. After I installed it and all dependencies, it would shut down after running for a few seconds. I isolated the problem to the songanalysis program, which output as follows on any file I fed it (MP3, OGG, or WAV).

```

$ ./songanalysis ~/path/name/Song.mp3
Song analysis, yeah!
Scanning /home/tjbk_tjb/path/name/Song.mp3...
Analyzing /home/tjbk_tjb/path/name/Song.mp3
Analysis took 0 seconds
```

After some research, it seemed that [other users]("http://rudd-o.com/projects/songanalysis/") had similar problems, but no solutions that worked.

After a while, I decided to try BpmDj. After downloading it, attempting to compile, and using some fixes I got from a Gentoo ebuild, I got the following errors during make.
```
signals-template.cpp: In member function ‘void BasicSignal<Type, Channels>::operator=(const BasicSignal<Type, Channels>&) [with Type = double, int Channels = 2]’:
kbpm-play.cpp:83:   instantiated from here
signals-template.cpp:153: warning: comparison between signed and unsigned integer expressions
signals-template.cpp: In member function ‘void BasicSignal<Type, Channels>::smooth(int) [with Type = double, int Channels = 2]’:
kbpm-play.cpp:83:   instantiated from here
signals-template.cpp:209: warning: comparison between signed and unsigned integer expressions
signals-template.cpp: In member function ‘void BasicSignal<Type, Channels>::operator=(const BasicSignal<Type, Channels>&) [with Type = short int, int Channels = 2]’:
kbpm-play.cpp:84:   instantiated from here
signals-template.cpp:153: warning: comparison between signed and unsigned integer expressions
signals-template.cpp: In member function ‘void BasicSignal<Type, Channels>::smooth(int) [with Type = short int, int Channels = 2]’:
kbpm-play.cpp:84:   instantiated from here
signals-template.cpp:209: warning: comparison between signed and unsigned integer expressions
signals-template.cpp: In member function ‘Sample<Type, Channels> BasicSignal<Type, Channels>::normalize_abs_max() [with Type = short int, int Channels = 2]’:
kbpm-play.cpp:84:   instantiated from here
signals-template.cpp:161: warning: format ‘%g’ expects type ‘double’, but argument 2 has type ‘int’
signals-template.cpp:161: warning: format ‘%g’ expects type ‘double’, but argument 3 has type ‘int’
signals-template.cpp: In member function ‘void Haar<input, output, Channels>::execute() [with Input = double, Output = double, int Channels = 2]’:
kbpm-play.cpp:101:   instantiated from here
signals-template.cpp:554: warning: comparison between signed and unsigned integer expressions
signals-template.cpp: In member function ‘void Haar<input, output, Channels>::execute() [with Input = short int, Output = double, int Channels = 2]’:
kbpm-play.cpp:102:   instantiated from here
signals-template.cpp:554: warning: comparison between signed and unsigned integer expressions
wavelet-analyzer.logic.cpp: In function ‘void normalize_draw_decompose(Array<1, float>&, QPainter&, int, int, int)’:
wavelet-analyzer.logic.cpp:83: warning: passing ‘double’ for argument 2 to ‘void QColor::setHsv(int, int, int)’
bpm-analyzer.logic.cpp: In member function ‘long unsigned int BpmAnalyzerDialog::phasefit_diff(long unsigned int)’:
bpm-analyzer.logic.cpp:147: warning: comparison between signed and unsigned integer expressions
bpm-analyzer.logic.cpp: In member function ‘long unsigned int BpmAnalyzerDialog::phasefit_mult(long unsigned int)’:
bpm-analyzer.logic.cpp:159: warning: comparison between signed and unsigned integer expressions
bpm-analyzer.logic.cpp: In member function ‘long unsigned int BpmAnalyzerDialog::phasefit(long unsigned int, long unsigned int)’:
bpm-analyzer.logic.cpp:186: warning: comparison between signed and unsigned integer expressions
bpm-analyzer.logic.cpp:187: warning: comparison between signed and unsigned integer expressions
bpm-analyzer.logic.cpp: In member function ‘void BpmAnalyzerDialog::readAudio()’:
bpm-analyzer.logic.cpp:232: warning: comparison between signed and unsigned integer expressions
bpm-analyzer.logic.cpp:252: warning: comparison between signed and unsigned integer expressions
bpm-analyzer.logic.cpp:253: warning: comparison between signed and unsigned integer expressions
bpm-analyzer.logic.cpp: In member function ‘void BpmAnalyzerDialog::readAudioBlock(int)’:
bpm-analyzer.logic.cpp:298: warning: comparison between signed and unsigned integer expressions
bpm.cpp: In member function ‘double BpmCounter::measure()’:
bpm.cpp:111: warning: comparison between signed and unsigned integer expressions
bpm.cpp:116: warning: comparison between signed and unsigned integer expressions
bpm.cpp:117: warning: comparison between signed and unsigned integer expressions
/usr/bin/ld: warning: i386 architecture of input file `noise-ogg.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `noise-mp3.o' is incompatible with i386:x86-64 output
/usr/bin/ld: warning: i386 architecture of input file `logo-png.o' is incompatible with i386:x86-64 output
pixmap-cache.cpp: In member function ‘QPixmap* PixmapCache::insert(Song*, QPixmap*)’:
pixmap-cache.cpp:32: error: cast from ‘void*’ to ‘int’ loses precision
pixmap-cache.cpp: In member function ‘void PixmapCache::remove(Song*)’:
pixmap-cache.cpp:38: error: cast from ‘Song*’ to ‘int’ loses precision
pixmap-cache.cpp: In member function ‘QPixmap* PixmapCache::find(Song*, Song*, int, int)’:
pixmap-cache.cpp:52: error: cast from ‘Song*’ to ‘int’ loses precision
make: *** [pixmap-cache.o] Error 1
```

On second examination, Sourceforge stated that the source was for i386.

I also tried MusicIP, which is an i386 binary, so that didn't work well.

Are there any alternatives programs, patches, or modifications I could use to achieve my goal?

Edit: My problem was that I had to change all instances of "int" in pixmap-cache.* to "long"

Edit2: Spoke too soon. I got a "kbpm-play: common.cpp:32: void common_init(): Assertion `sizeof(signed4)==4' failed." after compiling.

---

