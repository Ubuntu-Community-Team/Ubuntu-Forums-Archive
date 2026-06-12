---
title: "fault report, what now?"
date: 2015-06-19
forum: Wine
---

### Post by decrepit on 2015-06-19
I'm trying to get GPSResults running in wine. This program analyses gps files we use for speed windsurfing.
 I'm very close I can open a GPS file and see the tracks, but get an incomplete analyses. I opened from the terminal today, and got this feedback.

```

[EMAIL="mike@Percy:~/.wine"]mike@Percy:~/.wine[/EMAIL]/drive_c/GPSResultsV6$ wine GPSResults.exe
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:event:wait_for_withdrawn_state window 0x10296/3e00012 wait timed out
[EMAIL="mike@Percy:~/.wine"]mike@Percy:~/.wine[/EMAIL]/drive_c/GPSResultsV6$  

```
Does this mean anything to anybody, any hint what I should do next?

---

### Post by decrepit on 2015-06-25
Wonder of wonders the fault was in GPSResults, the latest version works fine.

---

