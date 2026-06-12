---
title: "DVDrip - Audio Video Synchronization is off alot"
date: 2006-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by kufford on 2006-06-13
Hello all,

I'm trying to rip a homemade dvd into .avi format so that I can post it on google video. Unfortunately, it seems that the audio and video are far off. One thing that particularly concerns me is that when I rip the dvd, the ripping process goes to about 120-122% before stopping. Not sure what this means, but its rather annoying. I'm trying to rip it to xvid and encode the video down to 700Mb. Any tips/help will be greatly appreciated.

Thanks
Ken

---

### Post by kufford on 2006-06-13
```
Tue Jun 13 13:48:39 2006 Starting job (1): Determine number of titles
Tue Jun 13 13:48:39 2006 Executing command: dr_exec tcprobe -H 10 -i /dev/dvd && echo DVDRIP_SUCCESS
Tue Jun 13 13:48:39 2006 Job has PID 5103
Tue Jun 13 13:48:39 2006 Aborting command. Sending signal 1 to PID 5103...
Tue Jun 13 13:48:39 2006 Aborting job: Determine number of titles
Tue Jun 13 13:48:39 2006 You should analyze the last output of this job to see what's going wrong here:
Tue Jun 13 13:48:39 2006 ---- job output start ----
Tue Jun 13 13:48:39 2006 ---- job output end ----
Tue Jun 13 13:51:55 2006 Project closed.
Tue Jun 13 13:52:10 2006 Starting job (1): Determine number of titles
Tue Jun 13 13:52:10 2006 Executing command: dr_exec tcprobe -H 10 -i /dev/dvd && echo DVDRIP_SUCCESS
Tue Jun 13 13:52:10 2006 Job has PID 5402
Tue Jun 13 13:52:11 2006 Successfully finished job (1): Determine number of titles
Tue Jun 13 13:52:11 2006 Starting job (2): Probing - title #1
Tue Jun 13 13:52:11 2006 Executing command: dr_exec tcprobe -H 10 -i /dev/dvd -T 1 && echo DVDRIP_SUCCESS; dr_exec dvdxchap -t 1 /dev/dvd 2>/dev/null
Tue Jun 13 13:52:11 2006 Job has PID 5404
Tue Jun 13 13:52:11 2006 Probing - title #1: 30 percent done.
Tue Jun 13 13:52:11 2006 Set container format to 'avi'
Tue Jun 13 13:52:11 2006 Not enabling PSU core, because this movie has only one PSU.
Tue Jun 13 13:52:11 2006 Successfully probed title #1
Tue Jun 13 13:52:11 2006 Successfully finished job (2): Probing - title #1
Tue Jun 13 13:52:11 2006 Starting job (3): Probing - title #2
Tue Jun 13 13:52:11 2006 Executing command: dr_exec tcprobe -H 10 -i /dev/dvd -T 2 && echo DVDRIP_SUCCESS; dr_exec dvdxchap -t 2 /dev/dvd 2>/dev/null
Tue Jun 13 13:52:11 2006 Job has PID 5407
Tue Jun 13 13:52:11 2006 Probing - title #2: 60 percent done.
Tue Jun 13 13:52:11 2006 Set container format to 'avi'
Tue Jun 13 13:52:11 2006 Not enabling PSU core, because this movie has only one PSU.
Tue Jun 13 13:52:11 2006 Successfully probed title #2
Tue Jun 13 13:52:11 2006 Successfully finished job (3): Probing - title #2
Tue Jun 13 13:52:11 2006 Starting job (4): Probing - title #3
Tue Jun 13 13:52:11 2006 Executing command: dr_exec tcprobe -H 10 -i /dev/dvd -T 3 && echo DVDRIP_SUCCESS; dr_exec dvdxchap -t 3 /dev/dvd 2>/dev/null
Tue Jun 13 13:52:11 2006 Job has PID 5410
Tue Jun 13 13:52:11 2006 Probing - title #3: 90 percent done.
Tue Jun 13 13:52:11 2006 Set container format to 'avi'
Tue Jun 13 13:52:11 2006 Not enabling PSU core, because this movie has only one PSU.
Tue Jun 13 13:52:11 2006 Successfully probed title #3
Tue Jun 13 13:52:11 2006 Successfully finished job (4): Probing - title #3
Tue Jun 13 13:52:11 2006 Copying IFO files to /home/kufford/Desktop//holen/tmp/ifo
Tue Jun 13 13:52:12 2006 Project file saved to '/home/kufford/Desktop//holen/tmp/backup.rip'
Tue Jun 13 13:52:14 2006 This task needs about 6 MB, 18335 MB are free.
Tue Jun 13 13:52:14 2006 Starting job (1): Ripping - title #1
Tue Jun 13 13:52:14 2006 Executing command: rm -f /home/kufford/Desktop//holen/vob/001/holen-???.vob && dr_exec tccat -t dvd -T 1,-1,1 -i /dev/dvd | dr_splitpipe -f /home/kufford/Desktop//holen/tmp/holen-001-nav.log 1024 /home/kufford/Desktop//holen/vob/001/holen vob  | tcextract -a 0 -x ac3 -t vob | tcdecode -x ac3 | tcscan -x pcm && echo DVDRIP_SUCCESS
Tue Jun 13 13:52:14 2006 Job has PID 5416
Tue Jun 13 13:53:19 2006 Ripping - title #1: 10 percent done.
Tue Jun 13 13:54:16 2006 Ripping - title #1: 20 percent done.
Tue Jun 13 13:55:10 2006 Ripping - title #1: 30 percent done.
Tue Jun 13 13:55:58 2006 Ripping - title #1: 40 percent done.
Tue Jun 13 13:56:41 2006 Ripping - title #1: 50 percent done.
Tue Jun 13 13:57:23 2006 Ripping - title #1: 60 percent done.
Tue Jun 13 13:58:03 2006 Ripping - title #1: 70 percent done.
Tue Jun 13 13:58:41 2006 Ripping - title #1: 80 percent done.
Tue Jun 13 13:59:17 2006 Ripping - title #1: 90 percent done.
Tue Jun 13 13:59:51 2006 Ripping - title #1: 100 percent done.
Tue Jun 13 14:00:23 2006 Ripping - title #1: 110 percent done.
Tue Jun 13 14:00:57 2006 Ripping - title #1: 120 percent done.
Tue Jun 13 14:01:13 2006 Executing command: dr_exec tcprobe -H 25 -i /home/kufford/Desktop//holen/vob/001 && echo DVDRIP_SUCCESS
Tue Jun 13 14:01:16 2006 Program stream units calculated
Tue Jun 13 14:01:16 2006 Not enabling PSU core, because this movie has only one PSU.
Tue Jun 13 14:01:16 2006 Successfully finished job (1): Ripping - title #1
Tue Jun 13 14:01:16 2006 This task needs about 0 MB, 14262 MB are free.
Tue Jun 13 14:01:16 2006 Starting job (1): Grabbing preview - title #1 ,frame #78222
Tue Jun 13 14:01:16 2006 Executing command: mkdir -m 0775 /tmp/dvdrip5363.ppm; cd /tmp/dvdrip5363.ppm; dr_exec transcode  -H 10 -o snapshot -y ppm,null -x vob,null -i /home/kufford/Desktop//holen/vob/001 -c 1-2 -L 1048474 && dr_exec convert -size 720x480 /tmp/dvdrip5363.ppm/snapshot*.ppm /home/kufford/Desktop//holen/tmp/holen-001-preview-orig.jpg && dr_exec convert -size 720x480 /tmp/dvdrip5363.ppm/snapshot*.ppm gray:/home/kufford/Desktop//holen/tmp/holen-001-preview-orig.raw && rm -r /tmp/dvdrip5363.ppm && echo DVDRIP_SUCCESS
Tue Jun 13 14:01:16 2006 Project file saved to '/home/kufford/Desktop//holen/tmp/backup.rip'
Tue Jun 13 14:01:16 2006 Job has PID 5752
Tue Jun 13 14:01:17 2006 Job has PID 5766
Tue Jun 13 14:01:17 2006 Job has PID 5767
Tue Jun 13 14:01:17 2006 Successfully finished job (1): Grabbing preview - title #1 ,frame #78222
Tue Jun 13 14:01:17 2006 Executing command: identify -ping /home/kufford/Desktop//holen/tmp/holen-001-preview-orig.jpg
Tue Jun 13 14:01:17 2006 Executing command: convert /home/kufford/Desktop//holen/tmp/holen-001-preview-orig.jpg -crop 720x480+0+0 /home/kufford/Desktop//holen/tmp/holen-001-preview-clip1.jpg
Tue Jun 13 14:01:17 2006 Executing command: identify -ping /home/kufford/Desktop//holen/tmp/holen-001-preview-clip1.jpg
Tue Jun 13 14:01:17 2006 Executing command: convert /home/kufford/Desktop//holen/tmp/holen-001-preview-clip1.jpg -geometry '632!x472!' /home/kufford/Desktop//holen/tmp/holen-001-preview-zoom.jpg
Tue Jun 13 14:01:17 2006 Executing command: identify -ping /home/kufford/Desktop//holen/tmp/holen-001-preview-zoom.jpg
Tue Jun 13 14:01:17 2006 Executing command: convert /home/kufford/Desktop//holen/tmp/holen-001-preview-zoom.jpg -crop 624x464+4+4 /home/kufford/Desktop//holen/tmp/holen-001-preview-clip2.jpg
Tue Jun 13 14:02:10 2006 This task needs about 699 MB, 14261 MB are free.
Tue Jun 13 14:02:10 2006 Starting job (1): Transcoding video - title #1, pass 1
Tue Jun 13 14:02:10 2006 Executing command: mkdir -m 0775 -p '/home/kufford/Desktop//holen/tmp' && cd /home/kufford/Desktop//holen/tmp && dr_exec transcode -H 10 -a 0 -x vob -i /home/kufford/Desktop//holen/vob/001 -w 760,50 -b 128,0,0 -s 1.141 --a52_drc_off -f 24,1 -M 2 -Y 4,4,4,4 -B 1,11,8 -R 1 -y xvid,null -o /dev/null --print_status 20 && echo DVDRIP_SUCCESS 
Tue Jun 13 14:02:10 2006 Job has PID 5805
Tue Jun 13 14:07:10 2006 Transcoding video - title #1, pass 1: 10 percent done.
Tue Jun 13 14:11:40 2006 Transcoding video - title #1, pass 1: 20 percent done.
Tue Jun 13 14:16:17 2006 Transcoding video - title #1, pass 1: 30 percent done.
Tue Jun 13 14:20:48 2006 Transcoding video - title #1, pass 1: 40 percent done.
Tue Jun 13 14:25:20 2006 Transcoding video - title #1, pass 1: 50 percent done.
Tue Jun 13 14:29:59 2006 Transcoding video - title #1, pass 1: 60 percent done.
Tue Jun 13 14:34:40 2006 Transcoding video - title #1, pass 1: 70 percent done.
Tue Jun 13 14:38:41 2006 Successfully finished job (1): Transcoding video - title #1, pass 1
Tue Jun 13 14:38:41 2006 Starting job (2): Transcoding video - title #1, pass 2
Tue Jun 13 14:38:41 2006 Executing command: mkdir -m 0775 -p '/home/kufford/Desktop//holen/tmp' && cd /home/kufford/Desktop//holen/tmp && dr_exec transcode -H 10 -a 0 -x vob -i /home/kufford/Desktop//holen/vob/001 -w 760,50 -b 128,0,0 -s 1.141 --a52_drc_off -f 24,1 -M 2 -Y 4,4,4,4 -B 1,11,8 -R 2 -y xvid -o /home/kufford/Desktop//holen/avi/001/holen-001.avi --print_status 20 && echo DVDRIP_SUCCESS 
Tue Jun 13 14:38:41 2006 Job has PID 6538
Tue Jun 13 14:53:32 2006 Transcoding video - title #1, pass 2: 10 percent done.
Tue Jun 13 15:06:34 2006 Transcoding video - title #1, pass 2: 20 percent done.
Tue Jun 13 15:19:15 2006 Transcoding video - title #1, pass 2: 30 percent done.
Tue Jun 13 15:32:01 2006 Transcoding video - title #1, pass 2: 40 percent done.
Tue Jun 13 15:45:58 2006 Transcoding video - title #1, pass 2: 50 percent done.
Tue Jun 13 15:59:55 2006 Transcoding video - title #1, pass 2: 60 percent done.
Tue Jun 13 16:13:25 2006 Transcoding video - title #1, pass 2: 70 percent done.
Tue Jun 13 16:24:04 2006 Successfully finished job (2): Transcoding video - title #1, pass 2

```

That is the rip log. When I looked at it again, it appears that the file is only encoded to roughly 70%.

---

### Post by w0lfrain on 2006-08-25
I have the same problem.  Does anyone have any idea?

Thanks.

---

### Post by morequarky on 2006-08-25
just a pet peeve...but...it is either "allot" or "a lot".  ALOT is not a word in English.

Have a great day :) :) :D

---

