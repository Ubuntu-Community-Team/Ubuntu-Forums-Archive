---
title: "Newbie with missing channels"
date: 2007-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by num1bryanp on 2007-12-06
Hello Everyone,

It’s another NEWBIE, I just put together the following AMD 64 bit system:

1-ASUS M2NPV-VM Micro ATX AMD Motherboard
1-AMD Athlon X2 BE-2400 2.3GHz Socket AM2 Processor
1-Patriot 2GB (2 x 1GB) 240-Pin DDR2 800 (PC2 6400) Dual Channel Kit Memory
1-CORSAIR CMPSU-450VX ATX12V V2.2 450W Power Supply 
1-Western Digital Caviar SE16 500GB 3.5" SATA 3.0Gb/s Hard Drive
2-Hauppauge WinTV-PVR-150 MCE Tuner Card w/MCE2 Remote 
1-LITE-ON 20X DVD±R DVD Burner Black IDE Model DH-20A4P-04
1-SILVERSTONE SST-LC17-B Black Computer Case

I have loaded and installed Mythbuntu-7.10-amd64 and configured it using the whole disk. It came up easy!

It seams to only have one little problem the PVR-150s can only see channels 2-13?
I have tried removing one of the boards and this does not change anything.

I also saw on the forum where someone else recommended trying the following:

Try using "ivtv-tune" to change the channel on the card to something you don't think you get. Use "cat" to put the output of the card directly into an MPEG file, then play that.
Code:
j@jmedia:~$ ivtv-tune --device=/dev/video0 --channel=70
j@jmedia:~$ cat /dev/video0 > test.mpg
CTRL+C to terminate the cat command, play the MPEG with your favorite program.
do this if you have ivtv-utils installed.

The first line gave a response like: ~ /dev/video0  450.XXX Mhz (Signal Detected)
The Second: Generated the test file which the local video players were not able to view but the audio was right for the station. Was the file made wrong or do I just have the wrong player?

Open VLC-
file>open capture device>PVR>OK
open terminal- 
Code: ivtv-tune -c25
Would be channel 25
for a desktop "remote control", go to [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)
i have a PVR150, so i know this will work for you.

Response: /dev/video0:  229.250 Mhz (Signal Detected)

Still no change I only have channels 2-13 :(

Thanks,
Bryan

---

### Post by num1bryanp on 2007-12-06
Hello All,

Why do my WinTV-PVR 150 cards only see channels 2-13 when I run a channel scan?  How do I troubleshoot this problem?

I have loaded and installed Mythbuntu-7.10-amd64 and configured it using the whole disk. Setup as a front and backend system.

System: ASUS M2NPV-VM Motherboard, AMD Athlon X2 BE-2400, 2GB DDR2 800 (PC2 6400) Memory,Hauppauge WinTV-PVR-150

Thanks,
Bryan

---

### Post by rsambuca on 2007-12-06
Please don't make more than one thread on the same topic.

---

### Post by num1bryanp on 2007-12-06
Sorry for starting a second thread but I bought this hardware just for building a PVR system and if it is not going to work Newegg only has a 30-Day return policy on most hardware, and 7 days on the CPU, which as of tomorrow I will get to keep.

I start this adventure looking at LinuxMCE , and put my first hardware list together based on going LinuxMCE, and after much help from the LinuxMCE forum the hardware list was created and ordering. I then found out LinuxMCE is not supporting 64bit yet, yes I was not doing very good homework on my part. But one of folks in the LinuxMCE forums said I should look at MythTV because it did everything I wanted to do.

After looking at the different quick start applications for MythTV I found Mythbuntu-7.10-amd64, and thought my answers have been solved. It installed just like it said it would and it works great so far with the sight exception I cannot seem to get any channels than 2-13.

I am a Newbie at Linux and MythTV so any help at resolving this issue would be greatly appreciated.

Thanks,
Bryan

---

### Post by num1bryanp on 2007-12-06
Hello,

I had left the Video Source, Channel Frequency Table set to 'default' once I changed it to 'us-cable' my card started working fine.

Some thinks are so simple to fix once you understand :-)
Bryan

---

