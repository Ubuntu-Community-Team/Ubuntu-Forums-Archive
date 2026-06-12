---
title: "Watching live TV with HVR-1600 Analog Tuner"
date: 2009-01-18
forum: x86 64-bit Users
---

### Post by Equinox93 on 2009-01-18
System Configuration is as follows--
  OS: Mythbuntu 8.10
  Capture Card: HVR-1600
  Non-standard software: Latest NV driver binary install.
  Antinnea: Philips PHDTV1 Silver Sensor UHF/HDTV Digital Indoor TV Antenna connected via the "TV"(analog) port.

MythTV Configuration-----------------

==Capture Card
Card type: MPEG-2 encoder card (PVR-x50, PVR-500)
Video device: /dev/video0 (had to type it in)
Probed info: Hauppauge HVR-1600 [cx18]
Default input: Tuner 1

==Video Sources
Video Source Name: schedulesdirect
Listings grabber: North America (Schedulesdirect.org) (internal)
User ID: ..
Password: ..
Data Direct Lineup: PCxxxx
Perform EIT Scan: (not selected)
Channel frequency table: us-bcast

==Input Connections
Capture Device: [MPEG : /dev/video0]
Input: Tuner 1
Display Name (optional): OTA1
Video Source: schedulesdirect
External channel change command: (blank)
Preset tuner to channel: (blank)
Starting channel: 3
>Next
Input priority: 0
Input Group 1: Generic
Input Group 2: Generic

[Channel scan finds a number of channels.]


==Channels
Displays a number of channels, including 3 my default channel.  I changed the default from 2 to 3 as I'm not quite sure what if anything is actually on 2.

==Loading the MythTV frontend & selecting Watch TV
Results in a black screen, about a 6 second delay then dropping
me back to the Mythbuntu main screen.
Mythbackend log excerpt:
TVRec(1): Changing from None to WatchingLiveTV
TVRec(1): HW Tuner 1->1
AutoExpire: CalcParams(): Max required Free space: 2.0 G B w/freq: 15 min


Not ivtv driver???

log has many lines of:
eno: Input/output error (5)
TVRec(1): Changing from watchingLiveTV to None
MPEGRec(/dev/video0) Error: error reading from /dev/video0

================
dmesg has multiple lines of:
DVB: frontend 0 frequency 863000000 out of range(64000000. . 858000000)

But those were apparently from the channel scan.

Any advice you have would be most appreciated.  If you'd like additional information just tell me what to attach to this post.

---

### Post by Equinox93 on 2009-02-11
Is something wrong with my problem description or where I posted this?  I've tried to find help on IRC, on here, pretty much everywhere I could think of but I have no idea what's wrong with this and I at least expected some sort of reply?

Time to give up on Mythbuntu?  I tried to buy a card that was well supported, and use hardware that was well supported in general.  I'm not trying to run this on some 10 year old computer so why is it this hard?

---

### Post by kintarooe on 2009-02-12
Did you setup your LiveTV storage group?  It looks like it cannot record the stream and therefore show a blank screen.

---

