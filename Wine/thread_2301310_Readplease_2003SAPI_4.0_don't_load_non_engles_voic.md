---
title: "Readplease 2003/SAPI 4.0 don't load non engles voice"
date: 2015-11-01
forum: Wine
---

### Post by www2 on 2015-11-01
Hi I have problem with loading SAPI4 voice from Lernout & Hauspie TTS3000 in wine.
I found four that this problem is in a chance/addition/deletion of one of the build patch for ubuntu.
The version of wine that have this problem are:
wine 1.4 (only in ubuntu 15.04 and 15.10)
wine 1.6 (only in ubuntu 15.04 and 15.10)
wine 1.7 ppa (start in between Jan-April 2015)

I have no data for ubuntu release 14.10

Test case:
1. Install a clean wine prefix
2. download[1] and install ReadPlease2003
3. download[2] and install one of the adons voices for SAPI4, the file name for the installer start with lhtts.
4. run readplease2003.

If this problem is fix you see a flag under the area for the voice/language selection.

[1] [https://sites.google.com/a/readerpal.com/readplease/](https://sites.google.com/a/readerpal.com/readplease/)
[2] [http://www.v3mail.com/download/ttsengines.htm](http://www.v3mail.com/download/ttsengines.htm)

---

