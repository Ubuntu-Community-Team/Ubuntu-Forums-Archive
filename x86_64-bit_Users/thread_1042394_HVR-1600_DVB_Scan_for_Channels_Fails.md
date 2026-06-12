---
title: "HVR-1600 DVB Scan for Channels Fails"
date: 2009-01-17
forum: x86 64-bit Users
---

### Post by Equinox93 on 2009-01-17
I'm using a HVR-1600 card connected to a "Philips PHDTV1 Silver Sensor UHF/HDTV Digital Indoor TV Antenna" from Amazon.com(It was $20 when I bought it--Why it's $80 now I have no clue)

OS: Mythbuntu 8.10, 64-bit
Non standard component: Latest NV Driver binary installer.

Connecting the antinnea to the ATSC port I have the following configuration:

Capture Card
  Card type: DVB DTV capture card (v3.x)
  DVB Device Number: 0
  Frontend ID: Samsung S5H1409 QAM/Subtype: ATSC

Video Sources
  Video Source Name: schedulesdirect
  Listings grabber: North America (Schedulesdirect.org) (internal)
  User ID: ..
  Password: ..
  Data Direct Lineup: PC:xxxxx
  Perform EIT Scan: (not selected)
  Channel frequency table: us-bcast

Input Connections
  Capture device: DVB:0
  Input: DVBInput
  Display Name: ATSC-OTA
  Video Source: schedulesdirect
  Use quick tuning: Live TV only
  Unencrypted channels only: selected.
  Allow audio only channels: selected.
  Use dishnet long-term EIT data: not selected.

  Starting channel: Please add channels to this source.

Scan for channels returns no results.

If I configure this card as an analog source and switch the antinnea position I will successfully scan for channels however watching them results in "not ivtv driver???" errors.  Since analog broadcast is going away rather soon I dont think it's worth getting that working.

Any advice would be most appreciated.

---

### Post by cariboo on 2009-01-17
Can you recieve any over-the-air dtv channels on  a regular tv?

Jim

---

### Post by Equinox93 on 2009-01-18
> **cariboo907 said:**
> Can you recieve any over-the-air dtv channels on  a regular tv?

Jim

Oops.  This was silly of me.  I dont have a DTV however I assumed the signals were already available in the US..Apparently they are not.  I'll go back to diagnosing the analog TV issues now ;)

---

